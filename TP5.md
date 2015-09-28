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
    | 1 | ... |  |
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
    | 3 | [] |  |
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

        unidad-de-traduccion:
            
            declaracion-externa
        
        declaracion-externa:
            
            definicion-de-funcion
        definicion-de-funcion:
            
            especificadores-de-declaracion(opt) declarador lista-de-declaraciones(opt)
            
        especificadores-de-declaracion:
        
            especificador-de-tipo especificadores-de-declaracion(opt)
        
        especificador-de-tipo: ```int```
            
        declarador:
        
            declarador-directo
        
        declarador-directo:
        
            declarador-directo (lista-tipos-de-parametro)
        
        declarador-directo:
        
            identificador
            
        identificador: ```printf```
        
        lista-tipos-de-parametro:
        
            lista-de-parametros , ...
        
        lista-de-parametros:
        
            declaracion-parametro
            
        declaracion-parametro:
        
            especificadores-de-declaracion declarador-abstracto(opt)
            
        especificadores-de-declaracion:
        
            calificador-de-tipo especificadores-de-declaracion(opt)
            
        calificador-de-tipo: ```const```
        
        especificadores-de-declaracion:
        
            especificador-de-tipo
            
        especificador-de-tipo: ```char```
        
        declarador-abstracto:
        
            apuntador
            
        apuntador: ```*```