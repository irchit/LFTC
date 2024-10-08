# Lab 1
 ## 1.) Specificarea minilimbajului de programare (MLP). <br>
 ### MLP creat din limbajul C.
 #### Tipuri de date:<br> 
   &emsp;1.) int -> int<br>
   &emsp;2.) float -> float<br>
   &emsp;2.) string -> string<br>

 #### Instructiuni:<br>
 &emsp;1.) instructiune atribuire 
```
   variabila = expresie;
```
&emsp;2.) instructiune in/out
```c
   in: 
      scanf(string, variabila);
   out:
      printf(string);
      printf(string, variabila);
      printf(string, variabila, variabila);
```
&emsp;3.) instructiune selectie
 ```c++
   if(condition){
      ...
    } 
 ```
&emsp;4.) instructiune ciclare
 ```c++
   while(condition){
      ...
    } 
 ```

 #### Reguli Lexicale:<br>

&emsp;1.) Simboluri

&emsp;&emsp; a.) Operatori:

&emsp;&emsp;&emsp; - aritmetici: +, -, *, /, %

&emsp;&emsp;&emsp; - atribuire: =

&emsp;&emsp;&emsp; - egalitate: ==, !=

&emsp;&emsp;&emsp; - comparare: >, <, >=, <=

&emsp;&emsp;&emsp; - secventare: ,

&emsp;&emsp; b.) Separatori: {, }, (, ), ;

&emsp;&emsp; c.) Cuvinte cheie:

&emsp;&emsp;&emsp; - int: numar intreg

&emsp;&emsp;&emsp; - float: numar zecimal

&emsp;&emsp;&emsp; - string: sir de caractere

&emsp;&emsp;&emsp; - if: conditie

&emsp;&emsp;&emsp; - while: ciclare

&emsp;&emsp;&emsp; - scanf: citire

&emsp;&emsp;&emsp; - printf: afisare

&emsp;&emsp;&emsp; - return: returnare

&emsp;&emsp;&emsp; - " : marcare inceput si final sir de caractere

&emsp;2.) Identificatori:

&emsp;&emsp; - ID = ^[a-zA-Z_][a-zA-Z0-9_]*$

#### Tabela Codificare:

| ATOM   | COD |
|--------|-----|
|  ID    | 0   |
| CONST  | 1   |
|  int   | 2   |
| float  | 3   |
| string | 4   |
|    (   | 5   |
|    )   | 6   |
|    ;   | 7   |
|    {   | 8   |
|    }   | 9   |
|    +   | 10  |
|    -   | 11  |
|    *   | 12  |
|    %   | 13  |
|    /   | 14  |
|    >   | 15  |
|    <   | 16  |
|    <=  | 17  |
|    >=  | 18  |
|     =  | 19  |
|    ==  | 20  |
|    !=  | 21  |
|     ,  | 22  |
|    if  | 23  |
| while              | 24  |
| return | 25  |
|  scanf             | 26  |
| printf             | 27  |
|  main              | 28  |
| #include<stdio.h>  | 29  |
| "  | 29  |

#### Gramatica specificata in BNF

```html

<program> ::= <antet><functie_main>
<antet> ::= #include<stdio.h>(\n)*
<functie_main> ::= int main(){<sectiune_cod> return 0;}
<sectiune_cod> ::= <sectiune_declarativa><sectiune_instructiuni>
<sectiune_declarativa> ::= <tip> ID; | <tip> ID; <sectiune_declarativa>
<tip> ::= int | float | string
<sectiune_cod> ::= <instructiune> | <instructiune> <sectiune_cod>
<instructiune> ::= <atribuire> | <ciclare> | <conditie> | <intrare> | <iesire> | (\n)* | (\n)* <instructiune>
<atribuire> ::= <expresie>; <instructiune>
<intrare> ::= scanf("<tip_data_citita>", &ID); <instructiune>
<iesire> ::= printf("^[a-zA-Z0-9:, \]*$<tip_data_citita>^[a-zA-Z0-9:, \]*$", ID); <instructiune> | printf("^[a-zA-Z0-9:, \]*$<tip_data_citita>^[a-zA-Z0-9:, \]*$<tip_data_citita>^[a-zA-Z0-9:, \]*$", ID, ID); <instructiune> | printf("^[a-zA-Z0-9:, \]*$"); <instructiune>
<tip_data_citita> ::= %d | %f | %s
<conditie> ::= if(<expresie_conditionala>){ <instructiune> }
<ciclare> ::= while(<expresie_conditionala>){ <instructiune> }
<expresie_conditionala> ::= ID <evaluator> ID | ID
<evaluator> ::= < | > | <= | >= | != | ==


```

 ## 2.) Se cer textele sursa a 3 mini-programe. <br>
 ```c++
#include <stdio.h>

int main(){
   float r;
   float pi;
   float perimetru;
   float arie;
   printf("Calculator arie si perimetru cerc, introduceti raza: ");
   scanf("%f", &a);
   pi = 3.14;
   perimetru = 2 * pi * r;
   arie = pi * r * r;
   printf("Aria: %f\nPerimetru: %f", arie, perimetru);
   return 0;
}
 ```
 ```c++
#include <stdio.h>

int main(){
   int a;
   int b;
   int r;
   printf("Calculator CMMDC, introduceti 2 numere: ");
   scanf("%d", &a);
   scanf("%d", &b);
   while(b != 0){
      r = a % b;
      a = b;
      b = r;
   }
   printf("Cmmdc-ul numerelor este: %d", a);
   return 0;
} 
 ``` 
 ```c++
#include <stdio.h>

int main(){
   int n;
   float x;
   float s;
   s = 0;
   scanf("%d", &n);
   while (n != 0)
   {
      scanf("%f", x);
      s = s + x;
      n = n - 1;
   }
   printf("Suma celor n numere este: %f", s);
   return 0;   
} 
 ```
 ## 3.)  Se cer textele sursa a doua programe care contin erori conform MLP-ului definit:
  ```c++
#include <stdio.h>

int main(){
   int n;
   float x;
   float s;
   s = 0;
   scanf("%d", n); //eroare, n trebuie sa fie pointer
   while (n > 1)
   {
      scanf("numar nou = %f", x); //eroare, stringul din scanf trebuie sa contina numai %d, %f, ... ce definesc tipuri de date, alte caractere produc eroare
      s = s + x;
      n = n - 1;
   }
   printf("Suma celor n numere este: %f", s);
   return 0;   
} 
 ```  
 ```c++
#include <stdio.h>

int main(){
   int n;
   float x;
   float s;
   s = 0;
   scanf("%d", &n);
   while (n != 0)
   {
      scanf("%f", x);
      s = s + x, n = n - 1; //eroare, nu este definita secventarea instructiunilor de atribuire cu ,
   }
   printf("Suma celor n numere este: %f %f %f", s, s, s); //eroare, nu este printf definit cu multiple afisari de variabila (max 2)
   return 0;   
} 
 ```
