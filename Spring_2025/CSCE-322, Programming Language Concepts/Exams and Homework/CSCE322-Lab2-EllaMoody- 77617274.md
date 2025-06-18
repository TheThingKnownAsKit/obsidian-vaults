# Task 1
## 1.a
**Test Cases:**
![[Pasted image 20250326230230.png]]
## 1.b
**var.l Code:**
```
cons [b-df-hj-np-tv-z]
%%
{cons}*a{cons}*e{cons}*i{cons}*o{cons}*u{cons}* {printf("Token: <VALID_WORD>; Lexeme:%s\n", yytext);}
[0-9]+(\.[0-9]+)? {printf("Token: <INT>; Lexeme:%s\n", yytext);}
.
%%

int yywrap(void) {
 return 1;
}

int main (void) {
 yylex();
 return 0;
}
```

**Test Cases:**
![[Pasted image 20250326230520.png]]

# Task 2
## 2.a
**scanner.l Code:**
```
%%
[0-9]+  {printf("<NUMBER,%s>", yytext);}
[-]     {printf("<MINUS>");}
[+]     {printf("<PLUS>");}
[ \t\n] {}
.       {printf("<UNKNOWN-TOKEN,%s>", yytext);}
%%

int yywrap(void) {
 return 1;
}

int main (void) {
 yylex();
 return 0;
}
```

**Test Cases:**
![[Pasted image 20250326230824.png]]

## 2.b
**cal.y Code:**
```
%{
  #include <stdio.h>
  #include "cal.tab.h"
  void yyerror(char *);
  int yylex(void);
%}

%token NUMBER PLUS MINUS
%left PLUS MINUS

%%
program:
        expr '\n'     {printf("Valid syntax\n");}
        |
        ;

expr:
    NUMBER
    | expr PLUS expr      { ;}
    | expr MINUS expr     { ;}
    ;
%%

int main(void) {
  yyparse();
  return 0;
}
```

**scanner.l Code:**
```
%{
  #include "cal.tab.h"
  extern void yyerror(char *s);
%}

%%
[0-9]+  {printf("<NUMBER,%s>\n", yytext); return NUMBER; }
[-]     {printf("<MINUS>\n"); return MINUS; }
[+]     {printf("<PLUS>\n"); return PLUS; }
[\n]    {return '\n';}
[ \t] {}
.       {yyerror("Unknown token");}
%%

int yywrap(void) {
  return 1;
}

void yyerror(char *s) {
  fprintf(stderr, "%s\n",s);
}
```

**Test Cases:**
![[Pasted image 20250326231602.png]]

## 2.c
**Test Cases:**
![[Pasted image 20250326231854.png]]

# Task 3
## 3.a
![[Pasted image 20250326233359.png]]

**Short Answer:**
This grammar is ambiguous because it does not have the proper operator precedence. A plus is treated with the same priority as multiplication, when ideally it should follow PEMDAS.

## 3.b
**Revised Grammar:**
```
%{
  #include <stdio.h>
  #include "cal.tab.h"
  void yyerror(char *);
  int yylex(void);
%}

%union {
  int num;
}

%token <num> NUMBER
%token MINUS PLUS MULTIPLICATION DIVISION

%type <num> expr
%type <num> program

%left PLUS MINUS
%left MULTIPLICATION DIVISION

%%
program:
        expr '\n'     { printf("Valid syntax. Solution: %d\n", $1); $$ = $1; }

        ;

expr:
    NUMBER                      { printf("<NUMBER, %d>\n", $1); $$ = $1; }
    | expr MULTIPLICATION expr  { printf("<MULTIPLICATION>"); $$ = $1 * $3; }
    | expr DIVISION expr        { printf("<DIVISION>"); $$ = $1 / $3;}
    | expr PLUS expr            { printf("<PLUS>"); $$ = $1 + $3; }
    | expr MINUS expr           { printf("<MINUS>"); $$ = $1 - $3; }
    ;
%%

void yyerror(char *s) {
  fprintf(stderr, "%s\n",s);
}

int main(void) {
  yyparse();
  return 0;
}
```

**Test Cases:**
![[Pasted image 20250326233704.png]]
