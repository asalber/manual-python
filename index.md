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
Autor: Alfredo Sánchez Alberca ([asalber@ceu.es](mailto:asalber@ceu.es))  
http://aprendeconalf.es  
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
>>> print("Hola ", name)
Hola Alf
```

--

### Interpretado en fichero

Se leen y se ejecutan una a una todas las instrucciones del fichero.

```python
# Fichero hola.py
name = "Alf"
print("Hola ", name)
```

```sh
> python hola.py
Hola Alf
```

También se puede hacer el fichero ejecutable indicando en la primera línea la ruta hasta el intérprete de Python.

```{python}
#!/usr/bin/python3
name = "Alf"
print("Hola", name)
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
- **Tuplas** (tuples). Colecciones de objetos que representan secuencias ordenadas de objetos de distintos tipos. A diferencia de las listas son inmutables, es decir, que no cambian durante la ejecución. Se representan mediante paréntesis y los elementos se separan por comas.  
**Ejemplo**. (1, 'dos', 3)
- **Diccionarios** (dictionaries): Colecciones de objetos con una clave asociada. Se representan con llaves, los pares separados por comas y cada par contiene una clave y un objeto asociado separados por dos puntos.  
**Ejemplo**. {'pi':3.1416, 'e':2.718}.

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
**Ejemplo**. `int('12')` <i class="fa fa-arrow-right"></i> `12`  
`int(True)` <i class="fa fa-arrow-right"></i> `1`   
`int('c')` <i class="fa fa-arrow-right"></i> Error
- `float()` convierte a real.  
**Ejemplo**. `float('3.14')` <i class="fa fa-arrow-right"></i> `3.14`  
`float(True)` <i class="fa fa-arrow-right"></i> `1.0`  
`float('III')` <i class="fa fa-arrow-right"></i> Error
- `str()` convierte a cadena.  
**Ejemplo**. `str(3.14)` <i class="fa fa-arrow-right"></i> `'3.14'`  
`str(True)` <i class="fa fa-arrow-right"></i> `'True'`  
- `bool()` convierte a lógico.  
**Ejemplo**. `bool('0')` <i class="fa fa-arrow-right"></i> `False`  
`bool('3.14')` <i class="fa fa-arrow-right"></i> `True`  
`bool('')` <i class="fa fa-arrow-right"></i> `False`   
`bool('Hola')` <i class="fa fa-arrow-right"></i> `True`

---

## Variables

Una variable es un identificador ligado a algún valor.

Reglas para nombrarlas:

- Comienzan siempre por una letra, seguida de otras letras o números.
- No se pueden utilizarse palabras reservadas del lenguaje.

A diferencia de otros lenguajes no tienen asociado un tipo y no es necesario declararlas antes de usarlas (tipado dinámico).

Para asignar un valor a una variable se utiliza el operador `=` y para borrar una variable se utiliza la instrucción `del`.

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
# Valor no definido
x = None
del x
```

---

## Entrada por terminal
#### `input()`

Para asignar a una variable un valor introducido por el usuario en la consola se utiliza la instrucción

>`input(mensaje)`  

donde `mensaje` es un mensaje que se muestra al usuario solicitándole que introduzca un valor.

<i class="far fa-exclamation-triangle"></i> _El valor obtenido siempre es una cadena, incluso si el usuario introduce un dato numérico._

```python
>>> language = input('¿Cuál es tu lenguaje favorito? ')
¿Cuál es tu lenguaje favorito? Python
>>> language
'Python'
>>> age = input('¿Cuál es tu edad? ')
¿Cuál es tu edad? 20
>>> age
'20'
```

---

### Salida por terminal
#### `print()`

Para mostrar un dato por la terminal se utiliza la instrucción 

> `print(dato1, ..., sep=' ', end='\n', file=sys.stdout`)

donde

- `dato1, ...` son los datos a imprimir y pueden indicarse tantos como se quieran separados por comas.
- `sep` establece el separador entre los datos, que por defecto es un espacio en blanco `' '`.
- `end` indica la cadena final de la impresión, que por defecto es un cambio de línea `\n`.
- `file` indica la dirección del flujo de salida, que por defecto es la salida estándar `sys.stdout`.

--

### Salida por terminal
#### `print()`

```python
>>> print('Hola')
Hola
>>> name = 'Alf'
>>> print('Hola', name)
Hola Alf
>>> print('El valor de pi es', 3.1415)
El valor de pi es 3.1415
>>> print('Hola', name, sep='')
HolaAlf
>>> print('Hola', name, end='!\n')
Hola Alf!
```

---

## Listas

Una **lista** es una secuencias ordenadas de objetos de distintos tipos.

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

Se utilizan los mismos operadores de acceso que para cadenas de caracteres.

- `l[i]` devuelve el elemento de la lista `l` con el índice `i`.

<i class="far fa-exclamation-triangle"></i> _El índice del primer elemento de la lista es 0._

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

### Sublistas

- `l[i:j:k]`: Devuelve la sublista desde el elemento de `l` con el índice `i` hasta el elemento anterior al índice `j`, tomando elementos cada `k`.

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

### Operaciones que no modifican una lista

- `len(l)`: Devuelve el número de elementos de la lista `l`.
- `min(l)`: Devuelve el mínimo elemento de la lista `l` siempre que los datos sean comparables.
- `max(l)`: Devuelve el máximo elemento de la lista `l` siempre que los datos sean comparables.
- `sum(l)`: Devuelve la suma de los elementos de la lista `l`, siempre que los datos se puedan sumar.
- `dato in l`: Devuelve `True` si el dato `dato` pertenece a la lista `l` y `False` en caso contrario.
- `l.index(dato)`: Devuelve la posición que ocupa en la lista `l` el primer elemento con valor `dato`.
- `l.count(dato)`: Devuelve el número de veces que el valor `dato` está contenido en la lista `l`.
- `all(l)`: Devuelve `True` si todos los elementos de la lista `l` son `True` y `False` en caso contrario.
- `any(l)`: Devuelve `True` si algún elemento de la lista `l` es `True` y `False` en caso contrario.

--

### Operaciones que no modifican una lista

```python
>>> a = [1, 2, 2, 3]
>>> len(a)
4
>>> min(a)
1
>>> max(a)
3
>>> sum(a)
8
>>> 3 in a
True
>>> a.index(2)
1
>>> a.count(2)
2
>>> all(a)
True
>>> any([0, False, 3<2])
False
```

--

### Operaciones que modifican una lista

- `l1 + l2`: Crea una nueva lista concatenan los elementos de la listas `l1` y `l2`.
- `l.append(dato)`: Añade `dato` al final de la lista `l`. 
- `l.extend(sequencia)`: Añade los datos de `sequencia` al final de la lista `l`.
- `l.insert(índice, dato)`: Inserta `dato` en la posición `índice` de la lista `l` y desplaza los elementos una posición a partir de la posición `índice`.
- `l.remove(dato)`: Elimina el primer elemento con valor `dato` en la lista `l` y desplaza los que están por detrás de él una posición hacia delante.
- `l.pop([índice])`: Devuelve el dato en la posición `índice` y lo elimina de la lista `l`, desplazando los elementos por detrás de él una posición hacia delante.
- `l.sort()`: Ordena los elementos de la lista `l` de acuerdo al orden predefinido, siempre que los elementos sean comparables.
- `l.reverse()`: invierte el orden de los elementos de la lista `l`.

--

### Operaciones que modifican una lista

```python
>>> a = [1, 3]
>>> b = [2 , 4, 6]
>>> a.append(5)
>>> a
[1, 3, 5]
>>> a.remove(3)
>>> a
[1, 5]
>>> a.insert(1, 3)
>>> a
[1, 3, 5]
>>> b.pop()
6
>>> c = a + b
>>> c
[1, 3, 5, 2, 4]
>>> c.sort()
>>> c
[1, 2, 3, 4, 5]
>>> c.reverse()
>>> c
[5, 4, 3, 2, 1]
```

---

## Tuplas

Una **tupla** es una secuencias ordenadas de objetos de distintos tipos.

Se construyen poniendo los elementos entre corchetes `(`  `)` separados por comas.

Se caracterizan por:

- Tienen orden.
- Pueden contener elementos de distintos tipos.
- Son inmutables, es decir, no pueden alterarse durante la ejecución de un programa.

Se usan habitualmente para representar colecciones de datos una determinada estructura semántica, como por ejemplo un vector o una matriz.

```python
# Tupla vacía
[]
# Tupla con elementos de distintos tipos
(1, "dos", True)
# Vector
(1, 2, 3)
# Matriz
((1, 2, 3), (4, 5, 6))
```

--

### Operaciones con tuplas

El acceso a los elementos de una tupla se realiza del mismo modo que en las listas.
También se pueden obtener subtuplas de la misma manera que las sublistas.

Las operaciones de listas que no modifican la lista también son aplicables a las tuplas.

```python
>>> a = (1, 2, 3)
>>> a[1]
2
>>> len(a)
3
>>> a.index(3)
2
>>> 0 in a
False
>>> b = ((1, 2, 3), (4, 5, 6))
>>> b[1]
(4, 5, 6)
>>> b[1][2]
6
```

---

## Diccionarios

Un diccionario es una colección de pares formados por una _clave_ y un _valor_ asociado a la clave.

Se construyen poniendo los pares entre llaves `{` y `}` separados por comas, y separando la clave del valor con dos puntos `:`.

Se caracterizan por:

- No tienen orden.
- Pueden contener elementos de distintos tipos.
- Son mutables, es decir, pueden alterarse durante la ejecución de un programa.

```python
# Diccionario vacío
{}
# Diccionario con elementos de distintos tipos
{'nombre':'Alfredo', 'despacho': 218, 'email':'asalber@ceu.es'}
# Diccionarios anidados
{'nombre_completo':{'nombre': 'Alfredo', 'Apellidos': 'Sánchez Alberca'}}
```

--

### Acceso a los elementos de un diccionario

- `d[clave]` devuelve el valor del diccionario `d` asociado a la clave `clave`. Si en el diccionario no existe esa clave devuelve un error.
- `d.get(clave, valor)` devuelve el valor del diccionario `d` asociado a la clave `clave`. Si en el diccionario no existe esa clave devuelve `valor`, y si no se especifica un valor por defecto devuelve `None`.

```python
>>> a = {'nombre':'Alfredo', 'despacho': 218, 'email':'asalber@ceu.es'}
>>> a['nombre']
'Alfredo'
>>> a['despacho'] = 210
>>> a
{'nombre':'Alfredo', 'despacho': 218, 'email':'asalber@ceu.es'}
>>> a.get('email')
'asalber@ceu.es'
>>> a.get('universidad', 'CEU')
'CEU'
```

--

### Operaciones que no modifican un diccionario

- `len(d)`: Devuelve el número de elementos del diccionario `d`.
- `min(d)`: Devuelve la mínima clave del diccionario `d` siempre que las claves sean comparables.
- `max(d)`: Devuelve la máxima clave del diccionario `d` siempre que las claves sean comparables.
- `sum(d)`: Devuelve la suma de las claves del diccionario `d`, siempre que las claves se puedan sumar.
- `clave in d`: Devuelve `True` si la clave `clave` pertenece al diccionario `d` y `False` en caso contrario.
- `d.keys()`: Devuelve un iterador sobre las claves de un diccionario.
- `d.values()`: Devuelve un iterador sobre los valores de un diccionario.
- `d.items()`: Devuelve un iterador sobre los pares clave-valor de un diccionario.

--

### Operaciones que no modifican un diccionario

```python
>>> a = {'nombre':'Alfredo', 'despacho': 218, 'email':'asalber@ceu.es'}
>>> len(a)
3
>>> min(a)
'despacho'
>>> 'email' in a
True
>>> a.keys()
dict_keys(['nombre', 'despacho', 'email'])
>>> a.values()
dict_values(['Alfredo', 218, 'asalber@ceu.es'])
>>> a.items()
dict_items([('nombre', 'Alfredo'), ('despacho', 218), ('email', 'asalber@ceu.es')])
```

--

### Operaciones que modifican un diccionario

- `d[clave] = valor`: Añade al diccionario `d` el par formado por la clave `clave` y el valor `valor`.
- `d.update(d2)`. Añade los pares del diccionario `d2` al diccionario `d`. 
- `d.pop(clave, alternativo)`: Devuelve del valor asociado a la clave `clave` del diccionario `d` y si la clave no está devuelve el valor `alternativo`.
- `d.popitem()`: Devuelve la tupla formada por la clave y el valor del último par añadido al diccionario `d`.
- `del d[clave]`: Elimina del diccionario `d` el par con la clave `clave`.
- `d.clear()`: Elimina todos los pares del diccionario `d` de manera que se queda vacío.

--

### Operaciones que modifican un diccionario

```python
>>> a = {'nombre':'Alfredo', 'despacho': 218, 'email':'asalber@ceu.es'}
>>> a['universidad'] = 'CEU'
>>> a
{'nombre': 'Alfredo', 'despacho': 218, 'email': 'asalber@ceu.es', 'universidad': 'CEU'}
>>> a.pop('despacho')
218
>>> a
{'nombre': 'Alfredo', 'email': 'asalber@ceu.es', 'universidad': 'CEU'}
>>> a.popitem()
('universidad', 'CEU')
>>> a
{'nombre': 'Alfredo', 'email': 'asalber@ceu.es'}
>>> del a['email']
>>> a
{'nombre': 'Alfredo'}
>>> a.clear()
>>> a
{}
```

---

## Referencias

- [Python](https://www.python.org/) Sitio web de Python.
- [Python tutor] Sitio web que permite visualizar la ejecución el código Python.
- [Tutorial de Python](https://www.tutorialpython.com/) Tutoría rápido de python.
- [Python para todos](http://mundogeek.net/tutorial-python/) Libro de introducción a Python con muchos ejemplos. Es de licencia libre.
- [Python para principiantes](https://www.safecreative.org/work/1207302042960-curso-python-para-principiantes) Libro de introducción Python que abarca orientación a objetos. Es de licencia libre.
- [Python crash course](https://ehmatthes.github.io/pcc/) Libro de introducción a Python gratuito.
- [Think python 2e](http://greenteapress.com/wp/think-python-2e/). Libro de introducción a Python que abarca también algoritmos, estructuras de datos y gráficos. Es de licencia libre.
- [Learning Python](http://shop.oreilly.com/product/0636920028154.do) Libro de introducción a Python con enfoque de programación orientada a objetos.
