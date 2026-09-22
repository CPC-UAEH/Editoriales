https://www.cpcjudge.com/problem/aguitadelimonvs67

# 26P1D5. Agüita de limón vs sixseven sixseven
#### Autor: wisperfrog

## Descripción
El calor nos está matando de sed y, a pesar de que todo el mundo carga su botella de agua, ésta no dura más de $5$ minutos.
Tú quieres aprovechar la situación y comienzas a vender agüita de limón a $X$ pesos el vaso para así probar suerte y hacerte millonario.

Un día, el meme sixseveeeeeen sixseveeeeeen se hizo tan viral que comenzaste a odiar todo lo que tuviera que ver con un $6$ o un $7$.

Es tanto tu odio que si atiendes un grupo de $C_i$ personas y $C_i$ es divisible entre $6$ o $7$, prefieres no venderles.

En caso contrario, les venderás $C_i$ vasos de agüita de limón.

Desgraciadamente, mientras vendías agüita de limón, te dio un golpe de calor y no recuerdas cuánto dinero ganaste, pero si recuerdas a los $N$ grupos que atendiste.

Como eres programador, escribirás un programa que calcule tu ganancia total.

## Entrada
En la primera línea dos enteros $N$ $(1 \leq N \leq 1000)$ y $X$ $(1 \leq X \leq 100)$, la cantidad de grupos y el precio por vaso, respectivamente.

En las siguientes $N$ líneas un entero $C_i$ $(1 \leq C_i \leq 100)$, la cantidad de personas del $i$ - $ésimo$ grupo.

## Salida
Tu ganancia total.


## Ejemplos

### Entrada
```
3 10
5 6 7
```
### Salida
```
50
```
### Entrada
```
6 2
10 11 12 10 14 42
```
### Salida
```
62
```
### Entrada
```
5 100
42 18 21 84 36
```
### Salida
```
0
```

## Notas
En el primer caso, la ganancia se calcula de la siguiente forma:

- Tu ganancia = $0$
- Llegó un grupo de $5$ personas, y $5$ no es divisible entre $6$ ni $7$, por lo tanto vendes $5$ vasos
ganaste $5 \cdot 10 = 50$ pesos, ganancia = 50
- Llegó un grupo de $6$ personas, y $6$ es divisible entre $6$, no vendes nada
- Llegó un grupo de $7$ personas, y $7$ es divisible entre $7$, no vendes nada Tu ganancia total es de $50$ pesos.

En el segundo caso, únicamente le vendes a los grupos de $10$, $11$ y $10$ personas.
Tu ganancia total es de ${(10 \cdot 2)+(11 \cdot 2)+(10 \cdot 2) = 20+22+20 = 62}$ pesos.

## Temas identificados
### Matemáticas
- Módulo

### Programación
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Solamente si el grupo de personas no es divisible entre 6 y tampoco es divisible entre 7, entonces sí se contabilizan las ganancias. 

## Implementación
Dicho de otra manera, si $C_i$ módulo 6 es diferente de 0 y $C_i$ módulo 7 es diferente de 0, entonces acumulamos la cantidad de personas de ese grupo en una suma, después haber leído los $N$ grupos, imprimimos la multiplicación $X \cdot suma$.

```mermaid
graph TD;
A([Inicio]) --> B[/n, x/]
B --> C(sum = 0)
C --> D{{Desde i = 0
        Hasta i < n
        Incremento 1}}
D --> E[/grupo/]
E --> F{"grupo % 6 == 0 ||
        grupo % 7 == 0"}
F --F--> G(sum = sum + grupo)
F --V--> H((" "))
G --> H
H --> D
D --> I[\sum * x\]
I --> Z([Fin])
```

### C++
#### Autor: mae

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int n;
    int x;
    int sum = 0;
    cin >> n >> x;

    for (int i = 0; i < n; i++){
        int grupo;
        cin >> grupo;

        if (grupo % 6 == 0 || grupo % 7 == 0) {

        } else {
            sum = sum + grupo;
        }
    }
    cout << sum * x;
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
