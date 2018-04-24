# 4 Un programa de Chistes

![Matraz de Erlenmeyer](https://inventwithpython.com/invent4thed/images/00016.jpeg "Matraz de Erlenmeyer")

Este capítulo le cuenta algunas bromas a las personas usuarias y les demuestra algunas maneras avanzadas de utilizar cadenas utilizando la función print(). La mayoría de los juegos en este libro tendrán un texto simple de entrada y salida. La entrada es digitada por la usuaria utilizando el teclado y la salida es el texto desplegado en la pantalla.


***
Temas cubiertos en este capítulo:
* Caracteres de escape
* Uso de comillas simples y dobles para manejo de cadenas
* Utilizando el argumento palabra clave "end" de la función print() para evitar nuevas lineas
***

Ya aprendiste cómo desplegar una salida de texto simple utilizando la función print(). Ahora vamos a profundizar y veremos cómo las cadenas y `print()` funcionan en Python.

## Ejemplo de ejecución del programa Chistes

Esto es lo que la usuaria ve cuando ejecuta el programa Chistes:

<pre>
¿Qué sale de la cruza entre un mono y un pato?
¡Un monopatín!

¿Porqué vuelan los pájaros pa'l sur?
¡Porque caminando tardarían muchísimo!

¿En qué se parecen una familia, un bombero y un barco?
No sé... ¿en qué se parecen?
En que el bombero y el barco tienen casco.
¿Y la familia? -Bien, gracias.
</pre>

Si obtienes errores después de escribir este código, compáralo con el código del libro con la herramienta diff en línea en http://invpy.com/es/diff/chistes.

<pre>
<b>¡NOTA IMPORTANTE!:</b> Los programas de este libro sólo podrán ejecutarse sobre Python 3, no Python 2. Al iniciar la ventana IDLE, dirá algo como “Python 3.4.2” en la parte superior. Si tienes Python 2 instalado, es posible instalar también Python 3 a la vez. Para descargar Python 3, dirígete a https://python.org/download/.
</pre>

![Python 3](https://inventwithpython.com/invent4thed/images/00060.jpeg "Python3")

<pre>
<b>chistes.py</b>

 1. print('¿Qué sale de la cruza entre un mono y un pato?')
 2. input()
 3. print('¡Un monopatín!')
 4. print()
 5. print('¿Porqué vuelan los pájaros pa\'l sur?')
 6. input()
 7. print('¡Porque caminando tardarían muchísimo!')
 8. print()
 9. print('¿En qué se parecen una familia, un bombero y un barco?')
10. input()
11. print("No sé... ¿en qué se parecen?")
12. input()
13. print('En que el bombero y el barco tienen casco.')
14. input()
15. print('¿Y la familia?', end='')
16. print(' -Bien, gracias.')
</pre>

## ¿Cómo funciona el código?
Empecemos por ver las primeras cuatro líneas de código:
<pre>
 1. print('¿Qué sale de la cruza entre un mono y un pato?')
 2. input()
 3. print('¡Un monopatín!')
 4. print()
</pre>

Las líneas de la 1 a la 3 tienen llamadas a la función `print()` que se utiliza para preguntar y responder al chiste. No se quiere que la jugadora lea de inmediato la respuesta del chiste, por lo que se utiliza una llamada a la función `input()` después del primer `print()`. De esta manera la jugadora puede leer la primer línea, presionar la tecla INTRO, y después leer el respuesta del chiste.

La persona usuaria podría escribir una cadena y pulsar INTRO, pero esa cadena no estará siendo almacenada en ninguna variable. El programa tan solo la olvidará y se moverá a la siguiente línea de código.

La última llamada a la función `print()` no tiene argumento de cadena. Esto le indica al programa que solamente despliegue una línea en blanco. Las líneas en blanco pueden ser útiles para evitar que el texto quede unido.

## Caracteres de escape

Las líneas de la 5 a la 8 imprimen la pregunta y la respuesta del siguiente chiste:
<pre>
 5. print('¿Porqué vuelan los pájaros pa\'l sur?')
 6. input()
 7. print('¡Porque caminando tardarían muchísimo!')
 8. print()
</pre>

En la línea 5 hay una barra invertida justo antes de la comilla simple (note que es una barra invertida y no una barra inclinada). Esta barra invertida indica que la letra que se encuentra justo después es un **caracter de escape**. Un **caracter de escape** te permite imprimir caracteres especiales que son difíciles o imposibles de ingresar al código fuente, como una comilla simple en una cadena que empieza y termina con comillas simples.
En este caso el caracter de escape es un signo de pregunta. Si este caso, si no se incluía la barra invertida, en `¿Porqué` el signo de pregunta hubiera sido mal interpretado y habría generado un error de parseo en lugar de ser incluido en la cadena. La comilla simple de escape le indica a Python que debe incluir el caracter especial en la cadena. 

Ahora, ¿cómo se podría imprimir una barra invertida?. Si se ejecuta la siguiente línea de código desde una terminal, no funcionaría:

<pre>
>>> print('Él se fue volando en un helicóptero verde\turquesa.')
Él se fue volando en un helicóptero verde    urquesa.
</pre>

Esto es porque la "t" en "turquesa" fue vista como un **caracter de escape** debido a que estaba después de una barra invertida. El caracter de escape `t` simula la pulsación de la tecla TAB de tu teclado. Hay caracteres de escape para que las cadenas puedan tener caracteres que no se pueden escribir.

En lugar de eso, prueba con esta línea:

<pre>
>>> print('Él se fue volando en un helicóptero verde\\turquesa.')
Él se fue volando en un helicóptero verde\turquesa.
</pre>

De esta manera el `\\` es un caracter de barra invertida en lugar de un `\t` que es interpretado por Python como un TAB.


La tabla **4-1** podremos encontrar una lista de caracteres de escape en Python.

**Tabla 4-1: Caracteres de Escape**

|Caracter de Escape | Lo Que Imprime |
|---------|----------------|
| `\\`     | Barra invertida (\)           |
| `\'`     | Comilla simple (')          |
| `\"`     | Comilla doble (") |
| `\n`     | Salto de línea       |
| `\t`     | Tabulador       |

Existen más caracteres de escape en Python, pero estos son los caracteres que más probablemente va a necesitar durante la creación de juegos.

## Comillas Simples y Dobles
Mientras todavía estamos en una terminal interactiva, veamos un poco más a fondo a las comillas. Las cadenas no siempre tienen que estar entre comillas simples en Python. También se pueden poner entre comillas dobles. Estas dos líneas a continuación van a imprimir la misma cosa:
<pre>
>>> print('Hola Mundo')
Hola Mundo
>>> print("Hola Mundo")
Hola Mundo
</pre>

Pero no se pueden mezclar las comillas simples con las dobles. Esta siguiente línea va a retornar un error porque utiliza ambas comillas al mismo tiempo:

<pre>
>>> print('Hola mundo")
SyntaxError: EOL while scanning single-quoted string
</pre>

Personalmente prefiero utilizar comillas simples para no tener que mantener presionada la tecla SHIFT para escribirlas. Son mucho más fáciles de escribir y a Python no le importa cuál de las dos utilicemos.

Tenga en cuenta que al igual que necesita la barra invertida (`\'`), para tener una comilla simple en una cadena encerrada entre comillas simples, también va a necesitar la barra invertida (`\"`) para poder tener comillas dobles en una cadena encerrada por comillas dobles. Veamos los ejemplos a continuación:

<pre>
>>> print('Le pedí prestado el carro a Pedro pa\'ir al pueblo. Él dijo, "Seguro."')
Le pedí prestado el carro a Pedro pa'ir al pueblo. Él dijo, "Seguro."
>>> print("Él dijo, \"No puedo creer que lo dejaste llevarse el carro pa'l pueblo\"")
Él dijo, "No puedo creer que lo dejaste llevarse el carro pa'l pueblo"
</pre>

En las cadenas de comillas simples no necesitas escapar las comillas dobles, y en las cadenas de comillas dobles no necesitas escapar las comillas simples. El intérprete de Python tiene inteligencia suficiente para saber que si una cadena comienza con un tipo de comillas, el otro tipo de comillas no significa que la cadena está terminada.

## El parámetro de palabra clave `end` de la función print()

Ahora regresemos al archivo chistes.py y observemos las líneas de la 9 a las 6:

<pre>
 9. print('¿En qué se parecen una familia, un bombero y un barco?')
10. input()
11. print("No sé... ¿en qué se parecen?")
12. input()
13. print('En que el bombero y el barco tienen casco.')
14. input()
15. print('¿Y la familia?', end='')
16. print(' -Bien, gracias.')
</pre>

¿Te diste cuenta del segundo parámetro en el print de la línea 15?. Normalmente, `print()` añade un salto de línea al final de la cadena que imprime. Por esta razón, una función `print()` en blanco tan solo imprimirá una nueva línea. Pero la función `print()` tiene la opción de un segundo parámetro (que tiene nombre “end” (fin)).

Recordemos que un argumento es un valor que se le pasa a una llamada de función. La cadena en blanco qus se le pasa a la función `print()` se llama **argumento** de palabra clave. El `end` que se encuentra en el `end=''` se llama **parámetro** de palabra clave. Para pasar un argumento de palabra clave a este parámetro de palabra clave, debe digitar la palabra `end=` al antes del argumento.
Cuando ejecutamos esta sección de código, la salida sería:

<pre>
¿En qué se parecen una familia, un bombero y un barco?
No sé... ¿en qué se parecen?
En que el bombero y el barco tienen casco.
¿Y la familia? -Bien, gracias.
</pre>

Pasando una cadena en blanco usando `end`, la función `print()` no añadirá un salto de linea al final de la cadena, en lugar de esto añadirá una cadena en blanco. Por esta razón ' -Bien, gracias.' aparece junto a la línea anterior, en lugar de sobre una nueva línea. No hubo salto de línea después de la cadena '¿Y la familia?'.

## Resumen

Este capítulo explora las diferentes formas en las que se puede utilizar la función `print()`. Los caracteres de escape se utilizan para los caracteres que son difíciles o imposibles de introducir al código usando el teclado. Si quiere utilizar caracteres especiales como parte de una cadena, debe utilizar una barra invertida (`\`) seguida de una sola letra para el carácter de escape. Por ejemplo, `\n` sería un salto de línea. Para incluir una barra invertida en una cadena, deberás utilizar el carácter de escape `\\`.

La función `print()` añade automáticamente un carácter de salto de línea al final de la cadena que se pasa para imprimr en pantalla. La mayor parte del tiempo, es un atajo útil. Pero a veces no quieres un carácter de salto de línea al final. Para cambiar esto, puedes pasar el argumento de palabra clave `end` con una cadena en blanco. Por ejemplo, para imprimir “spam” en la pantalla sin un carácter de salto de línea, podrías hacer el llamado `print('spam', end='')`.

Al añadir este nivel de control sobre el texto que mostraremos en la pantalla, puedes tener formas más flexibles para hacerlo.

[Previo: Capítulo 3: Adivine el número](capitulo3.md) | [Siguiente: Capítulo 5: Reino de Dragones](capitulo5.md)
