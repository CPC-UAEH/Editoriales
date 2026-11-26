https://www.cpcjudge.com/problem/eltamanio 

# D32O25. El tamaño

#### Autores: Tourist, Ignacio_benq

## Descripción
Maullin encontró un montón de números, así que te los quiere enseñar. Como solo son números sin sentido, simplemente devuélvele lo mismo.

## Entrada
En la primera línea, un número $A$ (${1 \leq A \leq 10^{100}}$).

## Salida
Imprimir el mismo número.

## Ejemplo


### Entrada 
```
10
```
### Salida
```
10
```
### Entrada 
```
999999999999999999999999999999
```
### Salida
```
999999999999999999999999999999
```

## Pista
Por los límites, tienes un número de hasta cien dígitos. ¿Qué tipo de variable crees conveniente usar para poder leerlo e imprimirlo correctamente?



## Temas identificados

### Programación
- Flujo de salida

## Propuesta de solución
#### Autor: mae y Jordan
La salida siempre será el mismo numero de la entrada.

## Implementación
Leer por teclado una cadena de caracteres e imprimir la misma cadena leída.

### C++
#### Autor: mae y Jordan
No existe, en este lenguaje, ninguna variable capaz de almacenar un número de $10^{100}$, y como realmente no vamos a hacer ninguna operación con el número que nos dan, podemos simplemente almacenarlo como una cadena de caracteres, en ese caso, 100 caracteres son pocos y la computadora los puede manejar perfectamente, al leer y al imprimir.
```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
    string n;
    cin >> n;
    cout << n;
}
```
