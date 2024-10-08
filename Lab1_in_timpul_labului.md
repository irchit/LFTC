### MLP Robert Buda

```py
program ::= include_statement namespace_block main_function ; //block ul programului
include_statement ::= "#include <iostream>" ;    //libraria necesara
namespace_block ::= "using" "namespace" "std" ;	 /
main_function ::= type "main()" "{" statement_block "return" "0;" "}" ; //block-ul main-ului
user_defined_struct ::= "struct" identifier "{" variable_declaration_list "};" ;	//tip-ul definit de catre utilizator

statement_block ::= { statement } ;			//instructiune din functie
statement ::= io_operation ";" | variable_declaration ";" | assignment_operation ";" | conditional_statement | loop_statement ; //procedurile acceptate ca si instructiune

io_operation ::= input_operation | output_operation ;		//read write operations
input_operation ::= "cin" ">>" variable { ">>" variable } ;
output_operation ::= "cout" "<<" " "|"cout" "<<" expression { "<<" expression } ;

variable_declaration ::= type variable {"," variable } ; //declarare de variabile
assignment_operation ::= variable "=" expression ; // assignare
expression ::= constant | variable | expression arithmetic_operator expression ;			

conditional_statement ::= "if" "(" condition ")" "{" statement_block "}" ;			//block-ul conditional
condition ::= boolean_expression { logical_operator boolean_expression } ;
boolean_expression ::= variable | constant relational_operator variable | constant ;

loop_statement ::= "while" "(" condition ")" "{" statement_block "}" ;//block-ul iterativ

type ::= "int" | "char" | "float" | "void" ;
variable ::= identifier ;
constant ::= numeric_constant | binary_constant | octal_constant | hex_constant ;
numeric_constant ::= digit_sequence ;
binary_constant ::= "0b" binary_digit { binary_digit } ;
octal_constant ::= "0" octal_digit { octal_digit } ;
hex_constant ::= "0x" hex_digit { hex_digit } ;

arithmetic_operator ::= "+" | "-" | "*" | "/" | "%" |;
relational_operator ::= "<=" | ">=" | "==" | "!=" | "<" | ">" ;
logical_operator ::= "&&" | "||" ;

digit_sequence ::= digit | digit digit_sequence ; 
binary_digit ::= "0" | "1" ;
octal_digit ::= "0" | "1" | ... | "7" ;
hex_digit ::= "0" | "1" | ... | "9" | "A" | "B" | ... | "F" ;

identifier ::= letter | letter identifier ;       
letter ::= "a" | "b" | "c" | ... | "z" | "A" | "B" | "C" | ... | "Z"  ;
digit ::= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9" ;

```


### Cod corect in MLP si limbaj initial

```c++
#include <iostream>
using namespace std;

int main(){
    int x;
    cin >> x;
    while(x < 5)
    {
        x = x + 1;
    }
    cout << x;
    return 0;
}
```

### Cod gresit MLP, functional in C++

```c++
#include <iostream>
#include <stdio.h> // absent din gramatica
using namespace std;

int main(){
    int x;
    cin >> x;
    while(x < 5) // absente acolade
        x ++; // incrementare ++ nedefinita
    cout << x;
    return 0;
}
```
