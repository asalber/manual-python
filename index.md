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

# Manual de introducción a Python

Autor: [Alfredo Sánchez Alberca](http://aprendeconalf.es) (asalber@ceu.es)

<img data-src="img/logo-python.png" alt="Logo de Python">

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
- **Booleanos** (boolean): Contiene únicamente dos elementos que representan los valores lógicos `True` (veradero) y `False` (falso).

--

## Tipos de datos primitivos compuestos

- **Listas** (lists): Listas de objetos que representan secuencias ordenadas de objetos de distintos tipos. Se representan con corchetes y los elementos se separan por comas.  
**Ejemplo**. [1, "dos", [3, 4], True].
- **Diccionarios** (dictionaries): Colección de objetos con una clave asociada. Se representan con llaves, los pares separados por comas y cada par contiene una clave y un objeto asociado separados por dos puntos.  
**Ejemplo**. {'pi':3.1416, 'e':2.718}.
- **Tuplas** (tuples). Representan secuencias ordenadas de objetos de distintos tipos. A diferencia de las listas son inmutables, es decir, que no cambian durante la ejecución. Se representan mediante paréntesis y los elementos se separan por comas.  
**Ejemplo**. (1, 'dos', 3)

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
```

---

## Referencias

- [Python](https://www.python.org/) Sitio web de Python.
- 