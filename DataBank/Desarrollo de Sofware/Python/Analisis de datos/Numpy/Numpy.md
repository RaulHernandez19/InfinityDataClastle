NumPy es una biblioteca de Python que proporciona soporte para arreglos multidimensionales y matrices, junto con una amplia colección de funciones matemáticas de alto nivel para operar en estos arreglos. NumPy es fundamental para la computación científica en Python.

---

# Array y Matriz

Se puede jugar con la cantidad de [ ] dentro de la matriz para alcanzar diferentes dimensiones, y con **ndim** se puede ver la dimension de un array.

```python
import numpy as np

array=np.array([1,2,3])
matriz2d=np.array([[3,4,5],[2,3,4]])
matriz3d=np.array([[[2,3,4],[3,4,5]],[[2,3,4],[3,4,5]]])
    
print(array.ndim)
print(matriz2d.ndim)
print(matriz3d.ndim)
---
1
2
3
```

## Shape

Hace referente a la forma del array, por ejemplo, en array 3D primero tiene 2 dimensiones, que dentro tienen dos listas y dentro de esas listas tienen 3 elementos.

```python
print(np.shape(array))
print(np.shape(matriz2d))
print(np.shape(matriz3d))

--- 
(3,)
(2, 3)
(2, 2, 3)
```

## Recorrer array

### For

```python
array=np.array([1,2,3])
matriz2d=np.array([[3,4,5],[2,3,4]])
matriz3d=np.array([[[2,3,4],[3,4,5]],[[2,3,4],[3,4,5]]])

for fila in matriz2d:
    print(fila)
    
print("Matriz 3D: \\n")

for matriz in matriz3d:
   
    for fila in matriz:
        print(fila)
    print("-")
---
[3 4 5]
[2 3 4]
Matriz 3D: 
[2 3 4]
[3 4 5]
-
[2 3 4]
[3 4 5]

```

```python
for matriz in matriz3d:
    for fila in matriz:
        for elemento in fila:
            print(elemento)
    print("-")

---
2
3
4
3
4
5
-
2
3
4
3
4
5
-
```

## Where

Busca los elementos y busca las posiciones en forma de array.

```python
posx,posy=np.where(matriz1==2)
print(posx,posy)
--
[1] [0]
```

## Visualizar elementos

```python
print(matriz3d[0,1,0]) #Forma con comillas
---
3

print(matriz3d[0,0:2]) #Con doble punto
---
[[2 3 4]
 [3 4 5]]
```

## Reshape

Con esto podemos cambiar la forma de un array respetando la cantidad de filas y columnas existentes

```python
matriz2d=np.array([[3,4,5],[2,3,4]])

print("Primera figura: \\n",matriz2d)
print(np.shape(matriz2d))

nuevo2d=matriz2d.reshape(3,2)#Restructuramos el array

print("Primera figura: \\n",nuevo2d)
print(np.shape(nuevo2d))
---
Primera figura: 
 [[3 4 5]
 [2 3 4]]
(2, 3)
Primera figura: 
 [[3 4]
 [5 2]
 [3 4]]
(3, 2)
```

## Concatenate

```python
matriz1=np.array([[3,4,5],[2,3,4]])
matriz2=np.array([[10,3,500],[2,3,4]])
matriz3=np.concatenate([matriz1,matriz2])
matriz3
---
array([[  3,   4,   5],
       [  2,   3,   4],
       [ 10,   3, 500],
       [  2,   3,   4]])
```

<aside> 💡 axis indica en que dimension queremos que se contatene, 0 siendo la primera dimension.

</aside>

```python
matriz3=np.concatenate((matriz1,matriz2),axis=0)
print(matriz3)
---
[[  3   4   5]
 [  2   3   4]
 [ 10   3 500]
 [  2   3   4]]
```

```python
matriz3=np.concatenate((matriz1,matriz2),axis=1)
print(matriz3)
---
[[  3   4   5  10   3 500]
 [  2   3   4   2   3   4]]
```

## Split

```python
matriz3,matriz4=np.split(matriz1,2)
print(matriz3)
print(matriz4)
--
[[3 4 5]]
[[2 3 4]]
```

# Random

## Randit

```python
#Genera un numero aleatorio en el 
#rango de numeros dado.

from numpy import random as rd

numero = rd.randint(5,10)

print(numero)
--
6
```

## Rand

```python

#Numero aleatorio flotante 
#entre el 0,1

numero = rd.rand()
print(round(numero,2))
--
0.36
```

# Creacion automatica de arrays

## Zero

```python
nuevoArray=np.zeros((3,4))
print(nuevoArray)
--
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

## Ones

```python
nuevoArray=np.ones((3,4))
print(nuevoArray)
--
[[1. 1. 1. 1.]
 [1. 1. 1. 1.]
 [1. 1. 1. 1.]]
```

## Eye

```python
nuevoArray=np.eye((4))
print(nuevoArray)
---
[[1. 0. 0. 0.]
 [0. 1. 0. 0.]
 [0. 0. 1. 0.]
 [0. 0. 0. 1.]]
```

---

## **Crear una matriz con un tamano dado en un rango de numeros**

### Int

```python
numero = rd.randint(10,size=(2,20))

print(numero)
---
[[3 0 8 5 2 7 1 9 2 3 5 3 4 1 3 8 2 9 6 8]
 [6 7 4 0 5 4 8 0 9 6 6 6 6 2 4 4 5 8 1 5]]

```

### Float

```python
numero = rd.rand(2,5)

print(numero)
---
[[0.97839466 0.17656925 0.86662766 0.16786117 0.06115527]
 [0.09964441 0.37924983 0.48470466 0.65658825 0.54571191]]
```

# Seleccion aleatorio

```python
from numpy import random as rd

lista_nombre=["Pepe","Maria","Eduardo","Marco","Sofia","Juana"]

ganador=rd.choice(lista_nombre,size=3)

print(ganador)
---
['Maria' 'Sofia' 'Eduardo']
```

```python
from numpy import random as rd

lista_nombre=["Pepe","Maria","Eduardo","Marco","Sofia","Juana"]

ganador=rd.choice(lista_nombre,size=(2,3))

print(ganador)
---
[['Marco' 'Marco' 'Pepe']
 ['Eduardo' 'Eduardo' 'Maria']]
```

#languageComplement 