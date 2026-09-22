https://www.cpcjudge.com/problem/plantita

# 26P2D1. Plantita
#### Autor: Soria

## Descripción
*"Ya no es lo mismo que ayer, cuando el mundo nos vio florecer..."*

Sony, debido a la primavera, está planeando aprovechar los tiempos para hacer crecer todas las plantitas que tiene, increíblemente las plantas han logrado crecer 3 veces su tamaño. Dado el tamaño inicial por un entero $N$, ¿cuál es el tamaño final de la plantita?

## Entrada
Un entero $N$ $(1 \leq N \leq 1000)$, indicando el tamaño inicial de la plantita.

## Salida
Un entero $X$, la altura final de la plantita.

## Ejemplo

### Entrada
```
1
```
### Salida
```
3
```

### Entrada
```
50
```
### Salida
```
150
```

## Notas
En el primer caso, la plantita tiene un tamaño $1$ inicialmente, terminando con un tamaño $1 \cdot 3 = 3$.

## Temas identificados
### Programación
- Entrada y Salida

## Propuesta de solución
#### Autor: Jordan

Solo hay que multiplicar $n \times 3$.

## Implementación
```mermaid
graph TD;
A([Inicio]) --> B[/Leer n/];
B --> C[\Imprimir n * 3\];
C --> D([Fin]);
```

Leer el número $n$ y al imprimir escribimos ```n * 3```.

### C++
#### Autor: mae

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int n;
    cin >> n;
    cout << n * 3;

    return 0;
}
```
