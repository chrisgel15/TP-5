# tp-ssl-2015-individual

# Trabajo Práctico Integrador

## ¿Compila? - ¿Ejecuta? - ¿Por Qué?

### Consigna
![alt text][logo]

[logo]: https://raw.githubusercontent.com/chrisgel15/TP-5/master/consignaTP-SSL.png "Consigna TP"

- Análisis Léxico
    - Investigue sobre _digraphs_ y _trigraphs_.
    
        Los _digrafos_ y _trigrafos_ son secuencias que permiten la representacion de otros simbolos que no se encuentran en algunos sets de caracteres. 

    - Responda: ¿Cuándo se reemplazan los _trigraphs_? ¿Y los _digraphs_?
    
        Los _trigrafos_ se reemplazan durante el **preprocesamiento** por su equivalente de un carácter antes de hacer cualquier otro proceso. A diferencia de los _trígrafos_, los _dígrafos_ son procesados durante el **tokenizado**.
        
    - Escriba la secuencia de lexemas a partir de la secuencia de caracteres.
    
    ```c
    int printf(const char *, ...);
    int main (void) {
        int _ [] = { -!.0, };
        printf("%d%d", sizeof _ - sizeof _[0], sizeof(char) + 0[_]);
    }
    ```
    
    - "Tokenize" a partir de la secuencia de lexemas.
    
    | Número de linea | Lexema | Token|
    |:------|:--------|:--------|
    | 1 | int | palabra reservada |
    | 1 | printf | identificador |
    | 1 | ( | caracter puntuación |
    | 1 | const | palabra reservada |
    | 1 | char | palabra reservada |
    | 1 | * | operador|
    | 1 | , | operador |
    | 1 | ... | Declaracion de numero y tipo de argumentos variables |
    | 1 | ) | caracter puntuación |
    | 1 | ; | caracter puntuación |
    | 2 | int | palabra reservada |
    | 2 | main | identificador |
    | 2 | ( | caracter puntuación |
    | 2 | void | palabra reservada |
    | 2 | ) | caracter puntuación |
    | 2 | { | caracter puntuación |
    | 3 | int | palabra reservada  |
    | 3 | _ | identificador |
    | 3 | [] | Caracter corchete de apertura y cierre |
    | 3 | = | operador |
    | 3 | { | caracter puntuacion |
    | 3 | - | operador |
    | 3 | ! | operador |
    | 3 | .0 | constante flotante |
    | 3 | , | operador |
    | 3 | } | caracter puntuacion |
    | 3 | ; | caracter puntuacion |
    | 4 | printf  | identificador |
    | 4 | ( | caracter puntuacion |
    | 4 | "%d%d" | literal cadena |
    | 4 | , | operador |
    | 4 | sizeof | operador  |
    | 4 | _ | identificador |
    | 4 | - | operador |
    | 4 | sizeof | operador |
    | 4 | _ | identificador |
    | 4 | [] | operador |
    | 4 | 0 | constante entera |
    | 4 | , | operador |
    | 4 | sizeof | operador |
    | 4 | ( | caracter puntuacion |
    | 4 | char | palabra reservada |
    | 4 | ) | caracter puntuacion |
    | 4 | + | operador |
    | 4 | 0 | constante entera |
    | 4 | [] | operador |
    | 4 | _ | identificador |
    | 4 | ) | caracter puntuacion |
    | 4 | ; | caracter puntuacion |
    | 5 | } | caracter puntuacion |
    
    - Indique si la UT es lexicamente correcta
    
        La UT es lexicametne correcta.
        
- Analisis sintactico
    - Arme el arbol de derivacion.
    
    El arbol de derivacion se encuentra subido en el repositorio, en el archivo **Arbol_De_Derivacion.xslx**.

    - Indique si la UT es sintacticamente correcta.
    
    La UT es sintacticamente correcta.

- Analisis semantico

    - Indique si la UT es lexicamente correcta. ¿Viola alguna restriccion semantica?
    
    La UT es lexicamente correcta y no viola ninguna restriccion semantica.
    
    - Indique que hace el programa
    
    Primeramente el programa declara una funcion llamada **printf** y luego dentro de la funcion **main**, inicializa un arreglo de enterors e imprime por pantalla el resultado de 2 expresiones en cuyos operandos estan involucrados el arreglo y la la funcion sizeof.
    
    - Si es semanticamente correcto, indique la salida. Justifique.
    
    La salida imprime los caracteres **00**. 
    En el arreglo inicializado, se encuentra almacenado el valor entero **-1**.
    El primer **0** es resultado de resolver la expresion ```sizeof _ - sizeof _[0]```, ya que **sizeof _** da como resultado la cantidad de bytes en el arreglo (4), y **sizeof _[0]** el resultado es la cantidad de bytes para almacenar un entero (4).
    El segundo **0** es resultado de resolver la expresion ```sizeof(char) + 0[_]```, ya que **sizeof(char)** da como resultado 1, y el valor almacenado en **0[_]** es -1.

