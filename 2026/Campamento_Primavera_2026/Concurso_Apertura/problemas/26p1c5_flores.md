https://www.cpcjudge.com/problem/flores

# 26P1C5. Flores
#### Autor: Soria

## Descripción
*"Sembré una flor sin interés... yo la regaba con agua que cae del cielo"*

Honey está lista para otra gran jornada de trabajo polinizando flores y, como en cualquier trabajo, debe de cumplir con una cuota todos los días, que equivale a $X$ unidades de polen. Para lograrlo, ella dispone de $N$ flores puestas en fila.

Honey se encuentra cansada, así que cumplirá con **exactamente** esa cantidad si y solo si es posible que recolectar todo ese polen siguiendo una estrategia. Honey volará sobre flores específicas, haciendo un único recorrido desde una flor $L$ hasta la flor $R$, siendo $1 \leq L \leq R \leq N$, recolectando todo el polen dispuesto en ese intervalo.

Como te darás cuenta, el trabajo aún así es cansado, así que Honey necesitará de motivación, ayuda a Honey a saber de cuántas formas puede lograr recolectar la cantidad deseada de $X$ unidades de polen siguiendo su estrategia.


## Entrada
Dos enteros $N$ $(1 \leq N \leq 2*10^5)$ y $X$ $(1 \leq X \leq 10^9)$ , la cantidad de flores, y la cantidad de polen que necesita recolectar Honey respectivamente.
Seguido por $N$ enteros $A_1, A_2, A_3, ..., A_N$, donde $(1 \leq A_i \leq 10^9)$ indica la cantidad de polen de la flor $i$.

## Salida
Un entero, todas las formas en que Honey puede completar su estrategia.

## Ejemplo

### Entrada
```
5 7
2 4 1 2 7
```
### Salida
```
3
```
### Entrada
```
7 1
1 1 1 1 1 1 1
```
### Salida
```
7
```
### Entrada
```
10 19
2 4 10 12 15 12 8 16 12 1
```
### Salida
```
0
```

## Notas
En el primer caso, es posible tomar las flores en los rangos $[1, 3]$, $[2, 4]$ y $[5, 5]$, de forma que cumpla con **exactamente** las $7$ unidades esperadas.

En el segundo caso, tomar cualquier flor de forma individual basta para recolectar el polen requerido.

En el tercer caso, lamentablemente Honey no tiene forma de recolectar de forma exacta la cantidad necesaria.

## Temas identificados
### Matemáticas
- Subconjuntos

### Programación
- Two Pointer
- Ciclos
- Condicionales
- Arreglos

## Propuesta de solución
#### Autor: Jordan
Debemos conseguir los subarreglos donde al sumar sus elementos, el resultado sea exactamente la cantidad de polen que Honey quiere recolectar, una de las formas de recorrer todos los subarreglos que posiblemente nos interesen, es con la técnica Two Pointer, donde tenemos dos variables que nos indican los índices a recorrer.


## Implementación
En Two pointer, tenemos un índice L y otro R, que ambos comienzan en 1, y una variable acumuladora que comienza con el valor del arreglo en L, si la suma es igual a la cantidad de polen, entonces sumamos 1 a un contador de combinaciones posibles que imprimiremos al final, si la suma es menor que el polen deseado, entonces sumamos 1 a R y sumamos el valor en R a la suma, pues sabemos que todos los valores del arreglo son positivos y agregar el siguiente número siempre va a hacer que aumente la suma total, y si la suma es mayor que el polen deseado, entonces restamos el valor del arreglo en L a la suma y sumamos 1 a L.

Así sucesivamente hasta que L o R sean mayores que el número de elementos en el arreglo, en cuyo caso, ya terminamos con la búsqueda y ya se encontraron todas los subarreglos con donde la suma es exactamente la cantidad de polen requerido.

Solo queda imprimir la cantidad de subarreglos o combinaciones encontradas.

### C++
#### Autor: Jordan

```cpp
#include <bits/stdc++.h>

using namespace std;

int a[200005];

int main() {
    long long int n, polen;
    cin >> n >> polen;

    for (int i = 1; i <= n; i++) {
        cin >> a[i];
    }

    int l = 1, r = 1;
    int combinaciones = 0;
    long long int total = a[l];
    while (l <= n && r <= n) {
        if (total == polen) {
            combinaciones++;
            total -= a[l];
            l++;
        }
        if (total < polen) {
            r++;
            total += a[r];
        }
        if (total > polen) {
            total -= a[l];
            l++;
        }
    }

    cout << combinaciones;
}
```

### Java
#### Autor:

```java

```

### Python
#### Autor:

```python

```

### Kotlin


```kotlin

```
