https://www.cpcjudge.com/problem/caeronocaer

# D12O25. Caer o no caer
#### Autor: wisperfrog

## Descripción
"¿Por qué una hoja se dejaría caer desde lo más alto de un árbol? Estando a salvo en las ramas, sosteniéndose contra el viento, ¿será que el árbol empuja a las hojas? ¿y qué hay de las hojas que no caen nunca? Seguramente se secan, pero las que volaron también. Qué dilema, si yo fuera una hoja, creo que preferiría..."


 - Entonces ranita, ¿cuántas hojas quedan en el árbol?
 - Ah si, quedan...


Ayuda a la ranita a saber cuántas hojas quedan en el árbol.

## Entrada
Dos enteros $A$ y $S$, donde 1 ≤ <i>S</i> ≤ <i>A</i> ≤ 10<sup>9</sup>, que representan la cantidad de hojas que había en el árbol y la cantidad de hojas que hay en el suelo, respectivamente.

## Salida
Un entero $R$, la cantidad de hojas que hay en el árbol.

## Ejemplo

### Entrada
```
5 2
```
### Salida
```
3
```
### Entrada
```
10000 10000
```
### Salida
```
0
```
### Entrada
```
20 5
```
### Salida
```
15
```

## Temas identificados
### Matemáticas
- Resta de números enteros.
- Operaciones aritméticas básicas.

### Programación
- Declaración y uso de variables de tipo int.
- Entrada y salida de datos.
- Operador de resta (-).

## Propuesta de solución
#### Autor: mae
Crear dos variables de tipo int para almacenar la cantidad de hojas que había en el árbol y la cantidad de hojas que se encuentran en el suelo. Posteriormente, restar la cantidad de hojas del suelo a la cantidad de hojas iniciales para obtener cuántas hojas quedan en el árbol.

## Implementación
Se declaran las variables $a$ y $s$ de tipo int y se leen los dos valores mediante cin. Después, se realiza la operación $a$ - $s$ y se imprime el resultado directamente mediante cout.

### C++

#### Autor: 
```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int a, s;
    cin >> a >> s;

    cout << a - s;

return 0;
}
```
