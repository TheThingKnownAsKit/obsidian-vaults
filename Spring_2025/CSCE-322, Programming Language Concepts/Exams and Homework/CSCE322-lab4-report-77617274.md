CSCE-322, Programming Language Concepts
Dr. Hoang-Dung Tran
Ella Moody
emoody4@huskers.unl.edu
2025

# Task 1
## 1.a
```
(define the-grammar
  '((program (myexpression) a-program)
    ; previously implemented code
    (myexpression ; new code
     ("let" (separated-list identifier "=" myexpression ",")
        "in" myexpression) let-exp)
    ; previously implemented code
)
```
New coded added to sllgen-grammar-77617274.rkt to implement local binding

```
(define eval-expression
  (lambda (expr env)
    (cases myexpression expr
	  ; previously implemented code
      (let-exp (id-list exp-list in-exp) ; new code
               (let* ((values-list (map (lambda (exp) (eval-expression exp env)) exp-list))
                                        (local-env (binding id-list values-list env)))
                                   (eval-expression in-exp local-env)
                 ))
      ; previously implemented code
      )
    )
  )
```
New code added to myinterpreter-77617274.rkt to implement local binding

## 1.b
```
; Task 1.b Testing (Local Binding)
(display "\nElla Moody 77617274")
(display "\n Test case i: let x=y, y =5 in x")
(display "\n  Expected result: Error of value-of: No binding for y")
(display "\n  Actual Result: ") (display (myinterpreter "let x=y, y =5 in x")) ; Comment this part out for the rest to run
(display "\n Test case iii: let a=1, b=2, c=3 in (+ a (+ b c))")
(display "\n  Expected result: 6")
(display "\n  Actual Result: ") (display (myinterpreter "let a=1, b=2, c=3 in (+ a (+ b c))"))
(display "\n Test case ii: let a=1 in let b=2, c=3, d=4, e=5 in (+ a (+ b (+ c (+ d e)))))")
(display "\n  Expected result: 15")
(display "\n  Actual Result: ") (display (myinterpreter "let a=1 in let b=2, c=3, d=4, e=5 in (+ a (+ b (+ c (+ d e))))"))
```
Test cases for local binding in myinterpreter-77617274.rkt

![[Pasted image 20250501165000.png]]
Results of testing when the error line is commented out

![[Pasted image 20250501165031.png]]
Results of testing when the error line is not commented out

# Task 2
## 2.a
```
(define the-grammar
  '((program (myexpression) a-program)
    ; previously implemented code
    (myexpression ; new code
     ("if" myexpression "then" myexpression "else" myexpression) if-exp)
    ; previously implemented code
   )
)
```
New coded added to sllgen-grammar-77617274.rkt to implement conditional expressions

```
(define true?
  (lambda (x) (not (zero? x))))

(define eval-expression
  (lambda (expr env)
    (cases myexpression expr
      ; previously implemented code
      (if-exp (cond-exp then-exp else-exp) ; new code
              (if (true? (eval-expression cond-exp env))
                  (eval-expression then-exp env)
                  (eval-expression else-exp env)))
      ; previously implemented code
      )
    )
  )

```
New code added to myinterpreter-77617274.rkt to implement conditional expressions

## 2.b
```
; Task 2.b Testing (Conditional Expressions)
(display "\n\nElla Moody 77617274")
(display "\n Test Case i: if 5 then 10 else 20")
(display "\n  Expected result: 10")
(display "\n  Actual Result: ") (display (myinterpreter "if 5 then 10 else 20"))
(display "\n Test Case ii: let x=5 in if x then (+ x 1) else (- x 1)")
(display "\n  Expected result: 6")
(display "\n  Actual Result: ") (display (myinterpreter "let x=5 in if x then (+ x 1) else (- x 1)"))
(display "\n Test Case iii: if 1 then if 0 then 5 else 10 else 15")
(display "\n  Expected result: 10")
(display "\n  Actual Result: ") (display (myinterpreter "if 1 then if 0 then 5 else 10 else 15"))
```
Test cases for conditional expressions in myinterpreter-77617274.rkt

![[Pasted image 20250501171120.png]]
Results of testing

# Task 3
## 3.a
```
(define the-grammar
  '((program (myexpression) a-program)
    ; previously implemented code
    (myexpression ; new code
     ("func" "(" (separated-list identifier ",") ")" "{" myexpression "}")
     function-def-exp)
    (myexpression ; new code
     ("exec" myexpression "(" (separated-list myexpression ",") ")")
     function-call-exp)
   )
)
```
New coded added to sllgen-grammar-77617274.rkt to implement function expressions

```
(define-datatype function-def function-def?
  (function-closure
   (id-list (list-of symbol?))
   (func-body myexpression?)
   (env environment?)))

(define eval-function-call
  (lambda (func-closure argument-values)
    (cases function-def func-closure
      (function-closure (id-list func-body env)
      (eval-expression func-body (binding id-list argument-values env))
                        ))))

(define eval-expression
  (lambda (expr env)
    (cases myexpression expr
      ; previously implemented code
      (function-def-exp (id-list func-body) ; new code
                        (function-closure id-list func-body env))
      (function-call-exp (func-exp argument-list) ; new code
                         (let ((func-closure (eval-expression func-exp env))
                               (args-values (map (lambda(exp) (eval-expression exp env)) argument-list)))
                               (if (function-def? func-closure)
                                   (eval-function-call func-closure args-values)
                                   (eopl:error 'eval-expression "Cannot execute a non-function: ~s" func-exp)))
                           )
      )
    )
  )
```
New code added to myinterpreter-77617274.rkt to implement function expressions

## 3.b
```
; Task 3.b Testing (Function Expressions)
(display "\n\nElla Moody 77617274")
(display "\n Test Case i: exec (func(x) {let inner = func(y) {(+ x y)} in exec inner(10)})(1)")
(display "\n  Expected result: 11")
(display "\n  Actual Result: ")
(display (myinterpreter "exec func(x) {let inner = func(y) {(+ x y)} in exec inner(10)}(1)"))

(display "\n Test Case ii: let add = func(a, b) {(+ a b)} in exec add(4, 6)")
(display "\n  Expected result: 10")
(display "\n  Actual Result: ") (display (myinterpreter "let add = func(a, b) {(+ a b)} in exec add(4, 6)"))

(display "\n Test Case iii: if 1 then exec func(x) {(+ x 1)}(5) else exec func(x) {(- x 1)}(5)")
(display "\n  Expected result: 6")
(display "\n  Actual Result: ") (display (myinterpreter "if 1 then exec func(x) {(+ x 1)}(5) else exec func(x) {(- x 1)}(5)"))

(display "\n Test Case iv: exec func(a, b) {(+ a b)}(10, 5)")
(display "\n  Expected result: 15")
(display "\n  Actual Result: ") (display (myinterpreter "exec func(a, b) {(+ a b)}(10, 5)"))
```
Test cases for function expressions in myinterpreter-77617274.rkt

![[Pasted image 20250505175439.png]]
Results of testing