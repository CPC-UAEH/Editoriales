https://www.cpcjudge.com/problem/plato

# 26P1D4. Plato
#### Autor: Soria

## Descripción
*"Tiempo, cielo lo perdí..."*

Coco está participando en el Concurso Primaveral de la FAOCE para perros, el objetivo es, obviamente, comer un plato lleno de croquetas en el menor tiempo posible. Como no es novedad, Coco ha ganado la final de la competencia. Pero, para su mala suerte, el juez activó el cronómetro muy tarde; sin embargo, aun con este problema, es más que evidente la victoria de esta chihuahua. Para recalcarlo necesita que muestres la diferencia de tiempo entre su contrincante y el suyo.

## Entrada
Dos números con 2 decimales $A$ y $B$, donde $(0.01 \leq A &lt; B \leq 999.99)$, indicando los tiempos marcados por los cronómetros de Coco y su contricante.

## Salida
Un número $X$ con 2 decimales, la diferencia de tiempo entre $A$ y $B$.

Para imprimir la respuesta con 2 decimales, debes:

- Agregar la librería ```<iomanip>```
- Imprimir la respuesta así ```cout << fixed << setprecision(2) << respuesta;```

## Ejemplo

### Entrada
```
1.00 4.00
```
### Salida
```
3.00
```

### Entrada
```
100.50 439.96
```
### Salida
```
339.46
```

## Notas
En el primer caso Coco terminó en 1 segundo después de que el juez activara el cronómetro, mientras que su contrincante en 4 segundos, dejando una diferencia de 3 segundos.

## Temas identificados
### Programación
- Entrada y Salida

## Propuesta de solución
#### Autor: Jordan
La respuesta siempre es imprimir $b - a$.

## Implementación
Leer a y b, para imprimir $b - a$, pero la instrucción de impresión debe mantener dos decimales.

```mermaid
graph TD;
A([Inicio]) --> B[/a, b/]
B --> C[\b - a\]
C --> D([Fin])
```
### C++
#### Autor: Jordan

```cpp
#include <bits/stdc++.h>
#include <iomanip>

using namespace std;

int main() {
    double a, b;
    cin >> a >> b;
    cout << fixed << setprecision(2) << b - a;
}
```
