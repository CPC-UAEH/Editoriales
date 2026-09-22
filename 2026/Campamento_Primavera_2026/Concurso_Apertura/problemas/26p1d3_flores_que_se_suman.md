https://www.cpcjudge.com/problem/floresquesesuman

# 26P1D3. Flores que se suman
#### Autor: MYS158

## Descripción
Durante la primavera, un pequeño jardín mágico comienza a florecer gracias a dos tipos de semillas especiales: las semillas $a$ y las semillas $b$.

El jardinero ha descubierto que la cantidad total de flores que aparecen no es simplemente la suma de las semillas, sino que sigue una regla particular. Después de muchos intentos, logró recordar la fórmula exacta que describe este comportamiento:

${f(a, b) = 2(a + b)}$ 

<p>Esto significa que cada semilla contribuye al crecimiento, pero el resultado final se duplica debido a las condiciones ideales de la primavera.</p>
<p>Tu tarea es calcular cuántas flores aparecerán en el jardín para los valores dados de $a$ y $b$.

## Entrada
Una sola línea con dos enteros $a$ y $b$ $(0 \leq a, b \leq 10^4)$.

## Salida
Imprime el valor de $f(a, b)$.

## Ejemplo

### Entrada
```
1 1
```
### Salida
```
4
```
### Entrada
```
2 2
```
### Salida
```
8
```
### Entrada
```
3 1
```
### Salida
```
8
```
## Notas
- En el primer caso, $a = 1$ y $b = 1$.
- Se calcula: $f(1,1) = 2(1 + 1) = 2 \cdot 2 = 4$

## Temas identificados
### Matemáticas
- Funciones

### Programación
- Entrada y Salida

## Propuesta de solución
#### Autor: Jordan
La respuesta es siempre la operacion ${2 \times (a+b)}$.

## Implementación
Leer $a$, $b$, para que al imprimir se haga la operación ```2 * (a + b)```.

```mermaid
graph TD;
A([Inicio]) --> B[/a, b/]
B --> C[\"2 * (a + b)"\]

C --> Z([Fin])
```

### C++
#### Autor: mae

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int a, b;
    cin >> a >> b;
    cout << 2 * (a + b);

    return 0;
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
#### Autor:

```kotlin

```
