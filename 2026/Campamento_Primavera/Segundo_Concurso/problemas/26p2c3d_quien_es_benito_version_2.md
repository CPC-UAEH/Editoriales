https://www.cpcjudge.com/problem/quienesbenitov2

# 26P2C3D. ¿Quién es benito? 👀 (versión 2)
#### Autor: Ignacio_benq

## Descripción
Benito es un gato que lleva un buen rato jugando ajedrez. Ya van varias partidas y se le están acumulando los pendientes.

A Benito le gusta empezar a hacer otras cosas cuando el momento sea "múltiplo de tres".

Entonces se le ocurrió sumar todos los segundos desde que empezó a jugar hasta el segundo en el que está ahora.

Si esa suma es múltiplo de tres, deja el tablero y se va a sus pendientes. Si no, juega otro ratito de ajedrez.

Es decir si la suma de todos los enteros en el rango $[a, b]$ (incluyendo ambos extremos) es **múltiplo de tres** o no.

## Entrada
Una línea con dos enteros $a$ y $b$  $(1 \leq a \leq b \leq 10^{18})$, el segundo en el que Benito empezó a jugar y el segundo actual.

## Salida
Imprime ```ya estuvo``` si la suma del rango es múltiplo de tres, o ```otro ratito``` si no lo es.

## Ejemplo

### Entrada
```
1 3
```
### Salida
```
ya estuvo
```

### Entrada
```
2 3
```
### Salida
```
otro ratito
```

## Notas
En el primer caso sumamos $1 + 2 + 3 = 6$, que es múltiplo de tres. Benito se levanta y se va a hacer sus cosas.

En el segundo caso la suma es $2 + 3 = 5$, no es múltiplo de tres. Le toca seguir moviendo piezas otro rato.

## Temas identificados
### Matemáticas
- Módulo
- Suma de Gauss
- Jerarquía de operaciones
- Leyes de exponentes

### Programación
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Se pide sumar todos los números entre un intervalo dado, el intervalo puede ser 1 a 3, pero también puede ser 1 a 1000000000000000000, por lo que desde el principio se descarta abordar el problema con un ciclo, no dará tiempo

Lo que sí podemos hacer es aplicar fórmulas para convertir un proceso lineal en uno constante, la **Suma de Gauss** es una fórmula muy usada, de la que me voy a saltar su deducción matemática, pero nos servirá para sumar todos los números entre $1$ y el número que especifiquemos:

${\frac{n(n+1)}{2}}$

De esta forma podemos encontrar la sumatoria desde $1$ hasta $a$ y también desde $1$ hasta $b$, pero lo que necesitamos en la sumatoria entre $a$ y $b$, la forma de resolver este intervalo es sencilla, solo hay que restar la sumatoria de Gauss donde $n$ es igual a $a-1$ a la sumatoria de Gauss donde $n$ es igual a $b$, de forma que se incluyan los extremos del intervalo en la sumatoria.

    1----------------a
    1------------------------------------------------------------b
                     a-------------------------------------------b

Luego de encontrar la sumatoria en el intervalo con esta sencilla resta, solo queda ver si el número es divisible entre $3$.


## Implementación
La fórmula de Gauss se puede implementar como una operación en una misma línea o como un método, solo hay que recordar la jerarquía de operaciones.

Para ver si un número es divisible entre cualquier número, necesitamos ver si el módulo de la división es igual a 0, para este caso, si el resultado divido por $3$ tiene un módulo (residuo) igual a $0$, significa que el resultado es divisible entre $3$, los otros dos valores posibles para el módulo son $1$ y $2$, en cualquiera de esos dos casos, no es divisible entre $3$. El símbolo de módulo en programación es %.

```mermaid
graph TD;
A([Inicio]) --> B[/a, b/]
B --> C(a = a % 3
        b = b % 3)
C --> D("s = (b * (b + 1)) / 2 - ((a - 1) * (a)) / 2")
D --> E{s % 3 == 0}
E --V--> F[\ya estuvo\]
E --F--> G[\otro ratito\]
F --> Z([Fin])
G --> Z([Fin])
```

### C++
#### Autor: Jordan

Hay un gran problema, la fórmula de Gauss requiere multiplicar $n$ por $n$, si multiplicamos $100$ por $100$, no hay problema, pero si multiplicamos $10^{18}$ por $10^{18}$, el resultado será $10^{36}$, en C++ no existe una variable que pueda almacenar un valor más grande de $10^{19}$ sin desbordarse. Para solucionar esto, debemos hacer más pequeños los valores antes de que se haga la suma de gauss, una forma para hacer esto es aplicar el módulo de $3$ a $a$ y $b$ antes de hacer la sumatoria, sabiendo que el objetivo final es saber si es divisible entre $3$.

```cpp
#include <iostream>
#include <bits/stdc++.h>

using namespace std;

long long int gauss(long long int n);

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    long long int a, b;
    cin >> a >> b;
    
    a %= 3;
    b %= 3;
    
    long long int s = gauss(b) - gauss(a - 1);
    if (s % 3 == 0) {
        cout << "ya estuvo";
    } else {
        cout << "otro ratito";
    }

    return 0;
}

long long int gauss(long long int n) {
    long long int gaus = (n * (n + 1)) / 2;
    return gaus;
}
```
