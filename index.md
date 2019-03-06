---
title: Manual de Python
separator: '^\r?\n---\r?\n$'
verticalSeparator: '^\r?\n--\r?\n$'
author: Alfredo Sánchez Alberca
theme: black
customTheme : custom
css: custom.css
highlightTheme: monokai
revealOptions:
    transition: convex
    center: true
logoImg: "/img/logo-python.png"
---

<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.2/css/all.css" integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" crossorigin="anonymous">

# Manual de introducción a Python


<div style="text-align:center">
Autor: [Alfredo Sánchez Alberca](http://aprendeconalf.es) ([asalber@ceu.es](mailto:asalber@ceu.es))
<br>
<img data-src="img/logo-python.png" alt="Logo de Python">
</div>

---

## ¿Qué es Python?

[Python](https://www.python.org/) es un lenguaje de programación de alto nivel multiparadigma que permite:
- Programación imperativa
- Programación funcional
- Programación orientada a objetos

Fue creado por Guido van Rossum en 1990 aunque actualmente es desarrollado y mantenido por la [Python Software Foundation](https://www.python.org/psf-landing/)

---

## Principales ventajas de Python

- Es de código abierto (certificado por la OSI).
- Es interpretable y compilable.
- Es fácil de aprender gracias a que su sintaxis es bastante legible para los humanos.
- Es un lenguaje maduro (29 años).
- Es fácilmente extensible e integrable en otros lenguajes (C, java).
- Esta mantenido por una gran comunidad de desarrolladores y hay multitud de recursos para su aprendizaje.

---

## Tipos de ejecución

### Interpretado en la consola de Python

Se ejecuta cada instrucción que introduce el usuario de manera interactiva.

```sh
> python
>>> name = "Alf"
>>> print("Hola " + name)
Hola Alf
```

--

### Interpretado en fichero

Se leen y se ejecutan una a una todas las instrucciones del fichero.

```python
# Fichero hola.py
name = "Alf"
print("Hola " + name)
```

```sh
> python hola.py
Hola Alf
```

También se puede hacer el fichero ejecutable indicando en la primera línea la ruta hasta el intérprete de Python.

```{python}
#!/usr/bin/python3
name = "Alf"
print("Hola " + name)
```

```sh
> chmod +x hola.py
> ./hola.py
Hola Alf
```

--

### Compilado a bytecode

```python
# Fichero hola.py
name = "Alf"
print("Hola " + name)
```

```sh
> python -O -m py_compile hola.py
> python __pycache__/hola.cpython-37.pyc
Hola Alf
```

### Compilado a ejecutable del sistema

Hay distintos paquetes que permiten compilar a un ejecutable del sistema operativo usado, por ejemplo `pyinstaller`.

```sh
> conda install pyinstaller
> pyinstaller hola.py
> ./dist/hola/hola
Hola Alf
```

---

## Tipos de datos primitivos simples

- **Números** (numbers): Cadenas de dígitos (pueden incluir el - para negativos y el . para decimales) que representan números.  
**Ejemplo**. 0, -1, 3.1415.
- **Cadenas** (strings): Cadenas de caracteres alfanuméricos que representan texto. Se representan entre comillas simples o dobles.  
**Ejemplo**. 'Hola', "Adiós".
- **Booleanos** (boolean): Contiene únicamente dos elementos `True` y `False` que representan los valores lógicos verdadero y falso respectivamente.

Estos datos son inmutables, es decir, su valor es constante y no puede cambiar.

--

## Tipos de datos primitivos compuestos (contenedores)

- **Listas** (lists): Colecciones de objetos que representan secuencias ordenadas de objetos de distintos tipos. Se representan con corchetes y los elementos se separan por comas.  
**Ejemplo**. [1, "dos", [3, 4], True].
- **Diccionarios** (dictionaries): Colecciones de objetos con una clave asociada. Se representan con llaves, los pares separados por comas y cada par contiene una clave y un objeto asociado separados por dos puntos.  
**Ejemplo**. {'pi':3.1416, 'e':2.718}.
- **Tuplas** (tuples). Colecciones de objetos que representan secuencias ordenadas de objetos de distintos tipos. A diferencia de las listas son inmutables, es decir, que no cambian durante la ejecución. Se representan mediante paréntesis y los elementos se separan por comas.  
**Ejemplo**. (1, 'dos', 3)

--

## Clase de un dato
#### `type()`

La clase a la que pertenece un dato se obtiene con el comando `type()`

```python
>>> type(1)
<class 'int'>
>>> type("Hola")
<class 'str'>
>>> type([1, "dos", [3, 4], True])
<class 'list'>
>>>type({'pi':3.1416, 'e':2.718})
<class 'dict'>
>>>type((1, 'dos', 3))
<class 'tuple'>
```

---

## Números (clases `int` y `float`)

Pueden ser enteros (`int`) o reales (`float`).

```python
>>> type(1)
<class 'int'>
>>> type(2.3)
<class 'float'>
```

- Operadores aritméticos: `+` (suma), `-` (resta), `*` (producto), `/` (cociente), `//` (cociente división entera), `%` (resto división entera).
- Operadores lógicos: `==` (igual que), `>` (mayor que), `<` (menor que), `>=` (mayor o igual que), `<=` (menor o igual que), `!=` (distinto de).

```python
>>> 2+3
5
>>> 5*2
10
>>> 5/2
2.5
>>> 5//2
2
>>> 3==3
True
>>> 4<=3
False
```

---

## Cadenas (clase `str`)

Se representan entre comillas sencillas ' o dobles ".

- Operadores de cadenas: `s[i]` (carácter i+1-ésimo), `s[i:j]` (subcadena de la posición i+1 a la j), `+` (concatenación), `*` (copias concatenadas), `in` pertenencia, `not in` no pertenencia.
- Operadores lógicos:  `==` (igual que), `>` (sucede), `<` (antecede), `>=` (sucede o igual que), `<=` (antecede o igual que), `!=` (distinto de). Utilizan el orden establecido en el código ASCII.
- Funciones: `len` (longitud de la cadena), `min` (carácter menor), `max` (carácter mayor).

```python
>>> 'Python'[1]
'y'
>>> 'Me gusta ' + 'Python'
'Me gusta Python'
>>> 'Python' * 3 
'PythonPythonPython'
>>> 'Python' < 'python'
True
>>> len('Python')
6
>>> max('Python')
'y'
```

---

## Datos lógicos o booleanos (clase `bool`)

Contiene únicamente dos elementos `True` y `False` que representan los valores lógicos verdadero y falso respectivamente.

`False` tiene asociado el valor 0 y `True` tiene asociado el valor 1.

- Operadores lógicos:  `==` (igual que), `>` (mayor), `<` (menor), `>=` (mayor o igual que), `<=` (menor o igual que), `!=` (distinto de), `not` (negación), `and` (conjunción), `or` (disyunción).


```python
>>> True == False
False
>>> True != False
True
>>> True < False
False
>>> False <= True
True
```

--

### Tabla de verdad

|   `x`   |   `y`   | `not x` | `x and y` | `x or y` |
| :-----: | :-----: | :-----: | :-------: | :------: |
| `False` | `False` | `True`  |  `False`  | `False`  |
| `False` | `True`  | `True`  |  `False`  |  `True`  |
| `True`  | `False` | `False` |  `False`  |  `True`  |
| `True`  | `True`  | `False` |  `True`   |  `True`  |


```python
>>> not True
False
>>> False or True
True
>>> True and False
False
>>> True and True
True
```

---

## Conversión de datos primitivos simples

Las siguientes funciones convierten un dato de un tipo en otro, siempre y cuando la conversión sea posible.

- `int()` convierte a entero.  
**Ejemplo**. `int('12')` <i class="fas fa-arrow-right"></i> `12`  
`int(True)` <i class="fas fa-arrow-right"></i> `1`   
`int('c')` <i class="fas fa-arrow-right"></i> Error
- `float()` convierte a real.  
**Ejemplo**. `float('3.14')` <i class="fas fa-arrow-right"></i> `3.14`  
`float(True)` <i class="fas fa-arrow-right"></i> `1.0`  
`float('III')` <i class="fas fa-arrow-right"></i> Error
- `str()` convierte a cadena.  
**Ejemplo**. `str(3.14)` <i class="fas fa-arrow-right"></i> `'3.14'`  
`str(True)` <i class="fas fa-arrow-right"></i> `'True'`  
- `bool()` convierte a lógico.  
**Ejemplo**. `bool('0')` <i class="fas fa-arrow-right"></i> `False`  
`bool('3.14')` <i class="fas fa-arrow-right"></i> `True`  
`bool('')` <i class="fas fa-arrow-right"></i> `False`   
`bool('Hola')` <i class="fas fa-arrow-right"></i> `True`

---

## Variables

Una variable es un identificador ligado a algún valor.

Reglas para nombrarlas: 

- Comienzan siempre por una letra, seguida de otras letras o números.
- No se pueden utilizarse palabras reservadas del lenguaje.

A diferencia de otros lenguajes no tienen asociado un tipo y no es necesario declararlas antes de usarlas (tipado dinámico).

Para asignar un valor a una variable se utiliza el operador `=`.


```python
lenguaje = 'Python'
x = 3.14
y = 3 + 2
# Asignación múltiple
a1, a2 = 1, 2
# Intercambio de valores
a, b = b, a
# Incremento (equivale a x = x + 2)
x += 2
# Decremento (equivale a x = x - 1)
x -= 1
```

--

### Entrada por consola

Para asignar a una variable un valor introducido por el usuario en la consola se utiliza la instrucción `input(mensaje)`  donde `mensaje` es un mensaje que se muestra al usuario solicitándole que introduzca un valor.

```python
>>> lenguaje = input('¿Cuál es tu lenguaje favorito? ')
¿Cuál es tu lenguaje favorito? Python
>>> lenguaje
'Python'
```

---

## Listas

Secuencias ordenadas de objetos de distintos tipos.

Se construyen poniendo los elementos entre corchetes `[`  `]` separados por comas.

Se caracterizan por:

- Tienen orden.
- Pueden contener elementos de distintos tipos.
- Son mutables, es decir, pueden alterarse durante la ejecución de un programa.

```python
# Lista vacía
[]
# Lista con elementos de distintos tipos
[1, "dos", True]
# Listas anidadas
[1, [2, 3], 4]
```

--

### Acceso a los elementos de una lista

Se accede a los elementos de una lista mediante un índice que indica la posición de cada elemento entre corchetes. Se utilizan los mismos operadores de acceso que para cadenas de caracteres.

**¡Ojo!** El índice del primer elemento de la lista es 0. 

|      Lista      | `'P'` | `'y'` | `'t'` | `'h'` | `'o'` | `'n'` |
| :-------------: | :---: | :---: | :---: | :---: | :---: | :---: |
| Índice positivo |   0   |   1   |   2   |   3   |   4   |   5   |
| Índice negativo |  -6   |  -5   |  -4   |  -3   |  -2   |  -1   |

```python
>>> a = ['P', 'y', 't', 'h', 'o', 'n']
>>> a[0]
'P'
>>> a[5]
'n'
>>> a[6]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
>>> a[-1]
'n'
```

--

### Operaciones con listas

- **Sublistas**: `l[i:j:k]` sublista desde el elemento de `l` con el índice `i` hasta el elemento anterior al índice `j`, tomando elementos cada `k`.

```python
>>> a = ['P', 'y', 't', 'h', 'o', 'n']
>>> a[1:4]
['y', 't', 'h']
>>> a[1:1]
[]
>>> a[:-3]
['y', 't', 'h']
>>> a[:]
['P', 'y', 't', 'h', 'o', 'n']
>>> a[0,6,2]
['P', 't', 'o']
```

--

### Operaciones con listas

- **Concatenación de listas**: `l1 + l2`

---

## Referencias

- [Python](https://www.python.org/) Sitio web de Python.
- 