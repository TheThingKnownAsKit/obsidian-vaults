CSCE-322, Programming Language Concepts
Dr. Hoang-Dung Tran
Ella Moody
emoody4@huskers.unl.edu

# Task 1
## 1.a
```Racket
; Task 1.a
(define-datatype bintree bintree?
  (leaf-node
   (datum number?)
   )
  (interior-node
   (key symbol?)
   (left bintree?)
   (right bintree?)
   )
  )
```
The implementation of Task 1.a

## 1.b
```Racket
; Task 1.b
(display "Ella Moody 77617274")
(define happytree
  (interior-node 'a
                 (interior-node 'b 
                               (leaf-node 1) 
                               (leaf-node 2))
                 (interior-node 'c
                               (interior-node 'd 
                                             (leaf-node 3) 
                                             (leaf-node 4))
                               (interior-node 'e
                                             (leaf-node 5) 
                                             (leaf-node 6)))))
(define sadtree
  (interior-node 'x
                 (interior-node 'y
                               (interior-node 'z
                                             (leaf-node 10)
                                             (leaf-node 20))
                               (interior-node 'w
                                             (leaf-node 30)
                                             (leaf-node 40)))
                 (leaf-node 50)))
(display "\n is happy tree, a balanced binary tree, valid?: ")
(display (bintree? happytree))
(display "\n is sadtree, an unbalanced binary tree, valid?: ")
(display (bintree? sadtree))
```
This is the test code for Task 1.b

![[Pasted image 20250413204725.png]]
Output for the test code in Task 1.b

## 1.c
```Racket
; Task 1.c Code
(define leaf-sum
  (lambda (tree)
    (cases bintree tree
      (leaf-node (datum) datum)
      (interior-node (key left right)
                     (+ (leaf-sum left)
                        (leaf-sum right))))))
```
Code for the implementation of Task 1.c

```Racket
; Task 1.c Tests
(display "\nElla Moody 77617274")
(display "\n The leaf sum for happytree: ")
(display (leaf-sum happytree))
(display "\n The leaf sum for sadtree: ")
(display (leaf-sum sadtree))
```
The code for the tests for Task 1.c

![[Pasted image 20250413205528.png]]
The test output for Task 1.c

## 1.d
```Racket
; Task 1.d Code
(define-datatype expression expression?
  (variable-expression (identifier symbol?))
  (lambda-expression
   (identifier symbol?)
   (body expression?))
  (application-expression
   (operator expression?)
   (operand expression?)))
```
The code implementation for Task 1.d

```Racket
; Task 1.d Test
; ((lambda (a) (a b)) c)
(define lamb-calc-test
  (application-expression
    (lambda-expression 'a
      (application-expression
        (variable-expression 'a)
        (variable-expression 'b)))
    (variable-expression 'c)))

(display "\nElla Moody 77617274")
(display "\n Is this a valid lambda calculus expression?: ") (display (expression? lamb-calc-test))
```
The code for the test for Task 1.d

![[Pasted image 20250413210454.png]]
Output for the test for Task 1.d

# Task 2
## 2.a
```Racket
; Task 2.a Code
(define parse-expression
  (lambda (expr)
    (cond
      ((symbol? expr)
       (variable-expression expr))
      ((pair? expr)
       (cond 
         ((eqv? (car expr) 'lambda)
          (lambda-expression (caadr expr) (parse-expression (caddr expr))))
         (else
          (application-expression (parse-expression (car expr))
                                  (parse-expression (cadr expr))))))
      (else (eopl:error  parse-expression "~s is not a valid expression" expr))
      )))  ;; cond <- lambda <- define
```
The code implementation for Task 2.a

```Racket
; Task 2.a Tests
(define test-var (parse-expression 'x))
(define test-lambda (parse-expression '(lambda (y) y)))
(define test-app (parse-expression '((lambda (x) x) z)))

(display "\nElla Moody 77617274")
(display "\n Is this a valid variable expression?: ") (display (expression? test-var))
(display "\n Is this a valid lambda expression?: ") (display (expression? test-lambda))
(display "\n Is this a valid application expression?: ") (display (expression? test-app))
```
The code for Task 2.a tests

![[Pasted image 20250413211135.png]]
The output for Task 2.a tests

## 2.b
```Racket
; Task 2.b Code
(define unparse-expression
  (lambda (expr)
    (cases expression expr
      (variable-expression (id) id); case of variable
      (lambda-expression (id body)
                         ; case of lambda expression, e.g., (lambda (id) (body))
                         (list 'lambda (list id) (unparse-expression body)))
      (application-expression (operator operand)
                              ; case of application expression, e.g., (f x)
                              (list (unparse-expression operator)
                                    (unparse-expression operand)))
      )))
```
The code implementation for Task 2.b

```Racket
; Task 2.b Tests
(define test-unparse-var
  (unparse-expression (variable-expression 'x)))
(define test-unparse-lambda  
  (unparse-expression  
    (lambda-expression 'y (variable-expression 'y))))
(define test-unparse-app  
  (unparse-expression  
    (application-expression  
      (lambda-expression 'z (variable-expression 'z))  
      (variable-expression 'w))))

(display "\nElla Moody 77617274")
(display "\n The expected outcome for unparsing the var is: x\n  Output: ")
(display test-unparse-var)
(display "\n The expected outcome for unparsing the lambda is: (lambda (y) y)\n  Output: ")
(display test-unparse-lambda)
(display "\n The expected outcome for unparsing the application expression is: ((lambda (z) z) w)\n  Output: ")
(display test-unparse-app)
```
The code for testing Task 2.b

![[Pasted image 20250413211822.png]]
The output for testing Task 2.b

# Task 3
```Racket
(define-datatype program program?
  (a-program (exp myexpression?)))

(define-datatype myexpression myexpression?
  (lit-exp (datum number?))
  (primapp-exp
   (prim primitive?) (exp1 myexpression?) (exp2 myexpression?)))

(define-datatype primitive primitive?
  (add-prim)
  (subtract-prim))

(define myparser
  (lambda (sourceprogram)
    (a-program (parse-myexpression sourceprogram))
    )
  )

(define parse-myexpression
  (lambda (expr)
    (cond
      ((number? expr) (lit-exp expr))
      ((pair? expr)
       (cond
         ((not (null? (cdddr expr)))
          (eopl:error `parse-myexpression "~s is not a sentence. Only two arguments are accepted for primapp-exp" expr)
          )
         ((eqv? (car expr) '+)
          (primapp-exp (add-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr)) )
          )
         ((eqv? (car expr) '-)
          (primapp-exp (subtract-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr)) )
          )
         (else
          (eopl:error `parse-myexpression "~s is not a sentence" expr)
          )
         )
       )
      (else (eopl:error `parse-myepression "~s is not a sentence" expr))
      )
    )
  )
```
The abstract parser implementation for Task 3, including necessary code from the lectures

## 3.a.
```Racket
; Task 3.a Tests
(define prog1
  (a-program 
    (primapp-exp 
      (subtract-prim) 
      (lit-exp 5) 
      (lit-exp 2))))
(define prog2 
  (a-program 
    (primapp-exp 
      (add-prim) 
      (lit-exp 1) 
      (primapp-exp (add-prim) (lit-exp 2) (lit-exp 3)))))

(display "\nElla Moody 77617274")
(display "\n Test 1 (Abstract Syntax - Subtraction)")
(display "\n  Program: (a-program (primapp-exp (subtract-prim) (lit-exp 5) (lit-exp 2)))")
(display "\n  Expected result: 3")
(display "\n  Result: ")(display (eval-program prog1))
(display "\n Test 2 (Parsed-Like Nested Addition):")
(display "\n  Program: (a-program (primapp-exp (add-prim) (lit-exp 1) (primapp-exp (add-prim) (lit-exp 2) (lit-exp 3))))")
(display "\n  Expected result: 6")
(display "\n  Result: ") (display (eval-program prog2))
```
The tests for Task 3.a

![[Pasted image 20250413213316.png]]
The output of the tests for Task 3.a

## 3.b
```Racket
; Task 3.b Code
(define myinterpreter
  (lambda (source-program)
    (let ((program-AST (myparser source-program))
          )
      (eval-program program-AST))
    )
  )
```
The code implementation for Task 3.b

```Racket
; Task 3.b Program Tests
(display "\nElla Moody 77617274")
(display "\n Test case 1: (+ (- 10 (* 2 3)) (/ 8 2))")
(display "\n  Expected result: 8")
(display "\n  Actual result: ") (display (myinterpreter '(+ (- 10 6) 4)))
(display "\n Test case 2: (- (- (- 20 5) 3) 2)")
(display "\n  Expected result: 10")
(display "\n  Actual result: ") (display (myinterpreter '(- (- (- 20 5) 3) 2)))
(display "\n Test case 3: (+ (* 2 (+ 3 1)) (- 10 (/ 8 2)))")
(display "\n  Expected result: 12")
(display "\n  Actual result: ") (display (myinterpreter '(+ (+ 2 4) (- 10 4))))
```
The tests for Task 3.b

![[Pasted image 20250413222915.png]]
The output for the tests for Task 3.b

# Task 4 (Bonus)
## 4.a
```Racket
; Updated for 4.a
(define-datatype primitive primitive?
  (add-prim)
  (subtract-prim)
  (multiply-prim)
  (divide-prim))
```
Updated abstract syntax for the bonus question

## 4.b
```Racket
; Updated for 4.a
(define parse-myexpression
  (lambda (expr)
    (cond
      ((number? expr) (lit-exp expr))
      ((pair? expr)
       (cond
         ((not (null? (cdddr expr)))
          (eopl:error `parse-myexpression "~s is not a sentence. Only two arguments are accepted for primapp-exp" expr))
         ((eqv? (car expr) '+)
          (primapp-exp (add-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr))))
         ((eqv? (car expr) '-)
          (primapp-exp (subtract-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr))))
         ((eqv? (car expr) '*)       ; Added case for multiplication
          (primapp-exp (multiply-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr))))
         ((eqv? (car expr) '/)       ; Added case for division
          (primapp-exp (divide-prim) (parse-myexpression (cadr expr)) (parse-myexpression (caddr expr))))
         (else
          (eopl:error `parse-myexpression "~s is not a sentence" expr))))
      (else (eopl:error `parse-myexpression "~s is not a sentence" expr)))))
```
Updated myparser code for the bonus question

```Racket
; Updated for 4.a
(define eval-primapp
  (lambda (prim exp1 exp2)
    (cases primitive prim
      (add-prim ()
                (+ (eval-expression exp1)
                   (eval-expression exp2)))
      (subtract-prim ()
                     (- (eval-expression exp1)
                        (eval-expression exp2)))
      (multiply-prim ()
                     (* (eval-expression exp1)
                        (eval-expression exp2)))
      (divide-prim ()
                   (let ((denominator (eval-expression exp2)))
                     (if (zero? denominator)
                         (eopl:error 'eval-primapp "Division by zero")
                         (/ (eval-expression exp1) denominator)))))))
```
Updated eval-primapp for the bonus question

## 4.c
```Racket
; Task 4.c Test Cases
(define bonus-test1 '(+ (* 3 4) (- 10 (/ 8 2))))
(define bonus-test2 '(/ (* (+ 1 2) (- 5 1)) 2))
(define bonus-test3 '(- (* (+ 2 (/ 6 2)) 3) 5))

(display "\nElla Moody 77617274")
(display "\n Bonus Test 1: (+ (* 3 4) (- 10 (/ 8 2)))")
(display "\n  Expected result: 18)")
(display "\n  Actual result: ") (display (myinterpreter bonus-test1))
(display "\n Bonus Test 2: (/ (* (+ 1 2) (- 5 1)) 2)")
(display "\n  Expected result: 6")
(display "\n  Actual result: ") (display (myinterpreter bonus-test2))
(display "\n Bonus Test 3: (- (* (+ 2 (/ 6 2)) 3) 5)")
(display "\n  Expected result: 10")
(display "\n  Actual result: ") (display (myinterpreter bonus-test3))
```
The new tests for Task 4

![[Pasted image 20250413225018.png]]
The output for Task 4 tests