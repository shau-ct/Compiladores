<p  align="center">
  <img  width="200"  src="https://www.fciencias.unam.mx/sites/default/files/logoFC_2.png"  alt="">  <br>Compiladores  2026-1 <br>
  Práctica 1: Analizadores léxicos con Lex (Flex) <br> Alumno: Morales Aguilar Marcos
</p>

## Análisis léxico con Flex
### Ejercicios:
#### Primer programa en lex
1. ¿Qué ocurre si en la primera sección se quitan las llaves al nombre de la macro letra? (0.5 pts)

Si se quitan las llaves a la macro ```letra```, quedaría definida como: 
```C++
letra [a-zA-Z]

```

Lo que provocaría un error de compilación, ya que Flex no reconocería ```letra``` como una macro válida al intentar usarla en las expresiones regulares. Las llaves ```{}``` son necesarias para delimitar el nombre de la macro.

2. ¿Qué ocurre si en la segunda sección se quitan las llaves a las macros? (0.5 pts)

Si se quitan las llaves en la segunda sección, Flex no reconocería que se está haciendo referencia a la macro definida, en su lugar, trataría de interpretar literalmente los caracteres de la macro. Esto resultaría en un comportamiento incorrecto del analizador léxico.

3. ¿Cómo se escribe un comentario en flex? (0.5 pts)

En Flex se pueden escribir comentarios de varias formas: 
* En la sección de declaraciones (dentro de ```%{ %}```). Se puede usar comentarios de C++ ```//``` o C ```/* */```
* Dentro de las reglas (entre ```%%``` y ```%%```). Flex no reconoce ```//``` estilo C++; solo ```/* ... */```

4. ¿Qué se guarda en yytext? (0.5 pts)

La variable ```yytext``` guarda la cadena de caracteres que coincidió con la expresión regular actual. Es un puntero a char que apunta al texto que fue reconocido por la regla léxica que se está ejecutando.

5. ¿Qué pasa al ejecutar el programa e introducir cadenas de caracteres y de dígitos por la consola? (0.5 pts)

Al ejecutar el programa:
* Si se introducen dígitos, por ejemplo: "123", se mostrará: "Encontré un número: 123"
* Si se introducen palabras, como "hola", mostrará: "Encontré una palabra: hola"
* Los espacios, tabs y saltos de línea son ignorados

6. ¿Qué ocurre si introducimos caracteres como "\*" en la consola? (0.5 pts)

Los caracteres que no coincidan con ninguna regla definida (espacios, dígitos o palabras) serán manejados por la regla implícita de Flex, la cual los imprime tal como son o genera un error léxico.

7. Modificar al código anterior en un archivo nuevo, de tal manera que reconozca lo siguiente: (2 pts)
    1. La expresión regular para los hexadecimales en lenguaje C++.
    2. 5 palabras reservadas del lenguaje C++.
    3. Los identificadores válidos del lenguaje C++, con longitud máxima de 32 caracteres (**Sugerencia**: use el operador {m,n}).
    4. Los espacios en blanco.
  
Se encuentra en el archivo.

---

## Analizador léxico para el lenguaje C_1

8. Describir el conjunto de terminales y la expresión regular que reconoce a cada uno  en _lexer.ll_. (2 pts)

| Token | Valor | Descripción | Expresión Regular |
|-------|-------|-------------|-------------------|
| MAS | 1 | Operador suma | `\+` |
| MENOS | 2 | Operador resta | `-` |
| MUL | 3 | Operador multiplicación | `\*` |
| DIV | 4 | Operador división | `/` |
| ASIG | 5 | Operador asignación | `=` |
| LPAR | 6 | Paréntesis izquierdo | `\(` |
| RPAR | 7 | Paréntesis derecho | `\)` |
| COMA | 8 | Coma | `,` |
| PYC | 9 | Punto y coma | `;` |
| ID | 10 | Identificador | `[a-zA-Z_][a-zA-Z0-9_]*` |
| IF | 11 | Palabra reservada if | `if` |
| INT | 12 | Palabra reservada int | `int` |
| WHILE | 13 | Palabra reservada while | `while` |
| ELSE | 14 | Palabra reservada else | `else` |
| FLOAT | 15 | Palabra reservada float | `float` |
| NUMERO | 16 | Número entero o real | `[0-9]+(\.[0-9]*)?([eE][+-]?[0-9]+)?` |
| ESP | 17 | Espacios en blanco | `[ \t\n\r]+` |

9. Generar acciones léxicas para cada terminal de nuestro lenguaje en _Lexer.cpp_, de modo que se muestre en pantalla la salida esperada con el archivo _prueba_. (2 pts)

Se encuentra en el archivo.

10. Crear un _Makefile_. (1 pt)

Se encuentra en la carpeta C_1.

---
#### Extras

11. Documentar el código. (0.25pts)
12. Proponer 4 archivos de prueba nuevos, 2 válidos y 2 inválidos. (0.25pts)





