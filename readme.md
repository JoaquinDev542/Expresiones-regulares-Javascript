# Expresiones regulares: #
Son una secuencia de caracteres que forma un patrón de búsqueda, principalmente utilizada para la búsqueda de patrones de cadena de caracteres u operaciones de sustituciones.

Se suele utilizar a la hora de validar formularios, ya sea que el email tenga ciertas cosas, que la contraseña tenga ciertos items, etc.

[Página para hacer test sobre las expresiones regulares] (https://regex101.com/)


# Sintaxis #
`/patron/letraBandera`

## Formas de escribir Expresiones Regulares ##

1. ``const regEx = /lorem/gi;``
2. ``const regEx = new RegExp('lorem' , 'gi');``
3. ``const regEx = new RegExp('/lorem/' , 'gi');`` 

Cabe destacar que la más utilizada es el caso 1.

# Banderas #
Las expresiones regulares pueden usar banderas que afectan la búsqueda. Podemos encontrar 6 banderas en JavaScript:

- i
- g
- m 
- s 
- u 
- y


### i ###
Con esta bandera, la búsqueda no distingue entre mayúsculas y minúsculas. 


### g ###
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


# Delimitadores #
- ˆ (shif + altGr + l) Antes de este símbolo, no puede haber nada.
-  $ Después de este símbolo no puede haber nada.

Ejemplo:

``ˆhola$``

## Llaves: ##
Lo que está antes tiene que aparecer la cantidad exacta de veces. Hay tres combinaciones posibles.
### ###
- {n} Se tiene que repetir "n" veces.
- {n,m} Se tiene que repetir entre "n" y "m" veces, ambas incluidas.
- {n,} Se tiene que repetir como mínimo "n" veces y sin máximo.

Ejemplo:

``ˆ[a-zA-Z]{1,3}@{1}$``


## Asterisco: ##
Lo que está antes del asterisco puede estar, puede no estar y se puede repetir.

Ejemplo:

``.*@.*\..*``


## Interrogación ##
Lo que está antes de la interrogación puede no estar, pero si está solo puede aparecer una vez. 

Ejemplo:

``ˆ[œ]?$``


## Operador más; ##
Lo que está antes del + tiene que estar una vez como mínimo.

Ejemplo:

``A-[0-9]+``
