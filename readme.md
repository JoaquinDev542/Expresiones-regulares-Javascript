# Expresiones regulares: #
Son una secuencia de caracteres que forma un patrón de búsqueda, principalmente utilizada para la búsqueda de patrones de cadena de caracteres u operaciones de sustituciones.

Se suele utilizar a la hora de validar formularios, ya sea que el email tenga ciertas cosas, que la contraseña tenga ciertos items, etc.

[Página para hacer test sobre las expresiones Regulares] (https://regex101.com/)

[Página para generar Expresiones Regulares] (https://ihateregex.io/?q=)


# Sintaxis #
`/patron/letraBandera`

## Formas de escribir Expresiones Regulares ##

1. const regEx = /lorem/gi;
2. const regEx = new RegExp('lorem' , 'gi');
3. const regEx = new RegExp('/lorem/' , 'gi');

Cabe destacar que la más utilizada es el caso 1.


# Banderas #
Las expresiones regulares pueden usar banderas que afectan la búsqueda. Podemos encontrar 6 banderas en JavaScript:

- i
- g
- m 
- s 
- u 
- y


### i (ignore) ###
Con esta bandera, la búsqueda no distingue entre mayúsculas y minúsculas. 


### g (global) ###
Con esta bandera, la búsqueda encuentra todas las coincidencias, sin ella, solo se devuelve la primera coincidencia.


### m ###
Modo multilínea.


### s ###
Habilita el modo "dotall", que permite un punto (.) coincida con el carácter de línea nueva \n


### u ###
Permite el soporte completo de Unicode. La bandera permite el procesamiento correcto de pares sustitutos.


### y ###
Modo "adhesivo": Búsqueda en la posición exacta del texto.

Cabe destacar, que las más comúnes y utilizadas son las banderas i y g.

``/ig``


# Método test #
El método test() ejecuta la búsqueda de una ocurriencia entre una expresión regular y una cadena de texto especificada. El valor devuelto será **true** **false**

Su sintaxis es:

```
const regEx = /l/gi;
console.log(regEx.test(variableATestear));
// Si la cadena tiene una "l", devuelve true, de lo contrario devuelve false.
```

Ejemplo:

```
let cadena = "Hello World";
let regEx = /e/gi;
console.log(regEx.test(cadena));
// true
```

Esto se debe a que la cadena de texto, tiene el caracter "e".


# Comodines #


## Sustitución ##
Su símbolo es un punto (.)

Define un comodín dentro del patrón. Es decir, cada punto equivale a un caracter y lo utilizamos cuando no sabemos algunas letras=.

Ejemplo:

La palabra *ipsum* no sabemos las letras de en medio, podemos hacer lo siguiente:

``/i..um/g``


## Listado de caracteres válidos ##
Su símbolo es entre corchetes ([])

Se pone una lista de los caracteres válidos. 

Un ejemplo sería: ``[aeiou]`` 

De esta manera, agarraríamos todas las vocales y permitiriamos que sean SOLO ESOS, los caracteres válidos. 


## Rangos ##
Su símbolo al igual que el listado de caracteres válidos se pone entre corchetes ([]). La diferencia reside en que a su vez utilizamos un guión.

Un ejemplo sería: ``[a-z]``

Lo que estamos diciendo acá es que queremos establecer un rango de la letra "a" hasta la letra "z" , es decir, todo el abcedario.

Para saber bien que rangos elegir, tenemos la página ASCII, la cual nos da por código escrito los números del código.

[código ASCII] (https://ascii.cl/es/)


## Mezcla entre rangos y listas ##
Es importante recalcar, que podemos unir los dos anteriores casos en uno solo. Mezclar tanto rangos como listas. 

Un ejemplo sería: ``[0-5ou]``

En este caso, estamos seleccionando los números del 0 al 5 y las letras "o" y "u".


## Cadenas completas ##
Por último, para establecer una cadena completa, se debe ir entre paréntesis, si queremos más palabras, irán separadas por un pipe. 

Un ejemplo sería: ``(lorem|amet)``

En este caso, estamos seleccionando tanto la palabra "lorem" como la palabra "amet".


# Operador de Delimitadores #
Estos son los más utilizados, aunque hay más.

- ^ (Acento Circunflejo) Antes de este símbolo, no puede haber nada.
-  $ Después de este símbolo no puede haber nada.

Ejemplo:

``^hola$``

Es decir, encontrará match solo cuando el mensaje solo sea "hola", ya que DELIMITAMOS el contenido que tiene que haber.

 
# Operador de Cantidad #

## Llaves: ##
Lo que está antes tiene que aparecer la cantidad exacta de veces. Hay tres combinaciones posibles.

- {n} Se tiene que repetir "n" veces.
- {n,m} Se tiene que repetir entre "n" y "m" veces, ambas incluidas. Es decir, el mínimo y el máximo.
- {n,} Se tiene que repetir como mínimo "n" veces y sin máximo.

Ejemplo:

``^[a-zA-Z]{1,3}@{1}$``


## Asterisco: ##
Lo que está antes del asterisco puede estar, puede no estar y se puede repetir.

Ejemplo:

``.*@.*\..*``


## Interrogación ##
Lo que está antes de la interrogación puede no estar, pero si está solo puede aparecer una vez. 

Ejemplo:

``^[ae]?$``


## Operador más (+) ##
Lo que está antes del + tiene que estar una vez como mínimo, no tiene límite.

Ejemplo:

``A-[0-9]+``


# Caracteres #
Nos sirve para ahorrar código, ya que funciona como si una letra agrupara diferentes caracteres, dependiendo cada comodín (\s \d , etc).

## \s: ##
Coincide con un caracter de espacio, entre ellos incluidos espacio, tab, salto de página, salto de línea y retorno de carro.

Ejemplo:

``^[a-zA-Z]+\s[a-zA-Z]+$``


## \S: ## 
Coincide con todo menos caracteres de espacio.

Ejemplo:

``^\S{5}$``


## \d (digito) ## 
Coincide con un caracter de número. Equivalente a [0-9]

Ejemplo:

``^\d{5}$``


## \D ##
Coincide con cualquier caracter no numérico. Equivalente a [^0-9]

Ejemplo:

``^\D{5}$``


## \w ##
Coincide con cualquier caracter alfanumérico, incluyendo el guión bajo. Equivalente a [A-Za-z0-9_] 

Ejemplo:

``^\w+@$``


## \W ##
Coincide con todo menos caracteres de palabras.

Ejemplo:

``^\W+$``


# Métodos que usan Expresiones Regulares #

## test() ##
Prueba una coincidencia en una cadena. El valor devuelto será **true** o **false**.

Su sintaxis es:

``regexObj.test(cadena);``


## exec() ##
Ejecuta una búsqueda por una coincidencia en una cadena. El valor devuelto será **un arreglo de información o null en una discrepancia**.

Su sintaxis es:

``regexObj.exec(cadena);``


## match() ##
Devuelve un **arreglo que contiene toda las coincidencias, incluidos los grupos de captura, o null si no se encuentra ninguna coincidencia**.

Su sintaxis es:

``regexObj.match(expresionRegular);``

* expresionRegular: Un objeto de expresión regular. 


## matchAll() ##
Devuelve **un iterador que contiene todas las coincidencias, incluido los grupos de caputura.**

Su sintaxis es:

``regexObj.matchAll(expresionRegular);``


## search() ##
Prueba una coincidencia en una cadena. El valor devuelto será **el índice de la coincidencia o -1 si la busqueda falla.**

Su sintaxis es:

``regexObj.search(expresionRegular);``


## replace() ##
Ejecuta una búsqueda por una coincidencia en una cadena y reemplaza la subcadena coincidente con una subcadena de reemplazo.

## replaceAll() ##
Ejecuta una búsqueda de todas las coincidencias en una cadena y reemplaza las subcadenas coincidentes con una subcadena de reemplazo.

## split() ##
Utiliza una expresión regular o una cadena fija para dividir una cadena en un arreglo de subcadenas.

Su sintaxis es:

``regexObj.split([separador] , [limite]);``

* separador: Especifica el carácter a usar para la separación de la cadena. Es tratado como una cadena o como una expresión regular. Si se **OMITE** el array devuelto contendrá sólo un elemento con la cadena completa.

* limite: Opcional. Entero que especifica un límite sobre el número de divisiones a realizar.
