https://www.cpcjudge.com/problem/serie

# H. Serie
#### Autor: Soria

## Descripción
*"Fue todo, ¿no es así?"*
Después de mucho esfuerzo, Felipe por fin está a punto de terminar su semestre, pero existe un pequeño detalle que aún debe resolver: el proyecto final de su clase "Fundamentos Electrónicos".
Debido a esto él crea un pequeño circuito usando el módulo amplificador LM358, el cual duplica el voltaje que recibe. Felipe decide realizar una pequeña prueba primero, por lo que crea un circuito donde conecta las señales de 10 de estos amplificadores y una señal inicial de $1V$ que llega desde el úlitmo al primero, sumando el voltaje de ciertos módulos. Dada una cadena conformada de $1$ y $0$ significando que Felipe toma o no el voltaje del amplificador $i$ determinar la suma final del voltaje.

## Entrada
Una cadena $S$ $(|S| = 10)$ conformada por $1$ o $0$ donde, si el caracter $S_i$ es igual a $1$ significa Felipe suma el voltaje del modulo $i$

## Salida

Un entero $X$ la suma total del voltaje.

## Ejemplo

### Entrada
```
0000000011
```
### Salida
```
3
```

### Entrada
```
0110011110
```
### Salida
```
414
```

### Entrada
```
0000010011
```
### Salida
```
19
```
### Entrada
```
1111111111
```
### Salida
```
1023
```

## Notas
- En el primer caso, el voltaje del último módulo es de $1V$ el penúltimo, entonces, otorga $2 * 1V = 2V$, siendo la suma final de $3V$.
- En el tercer caso, la suma de todos los voltajes son $512 + 256 + 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1 = 1023$ siendo la suma del último al primer módulo.

## Temas identificados
### Matemáticas
- Sistemas numéricos
- Potencias

### Programación
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Si los números empiezan a duplicarse de derecha a izquierda empezando en $1$, es un clásico conversor de binario a decimal. 

## Implementación
Comenzando desde $0$ de derecha a izquierda, si el contenido de la cadena en una posición $i$ es igual a $1$, entonces sumamos el resultado de elevar $2^i$ a un total. 

```mermaid
graph TD;
A([Inicio]) --> B[/s/]
B --> C(total = 0)
C --> D{{Desde i = 9, j = 0
        Hasta i >= 0
        Decremento en i de 1
        Incremento en j de 1}}
D --> E{"s[i] == '1'"}
E --V--> F("pow(2, j)") --> D
D --> G[\total\]
G --> H([Fin])
```

### C++
#### Autor: Jordan

El total puede ser una variable int donde se acumule el resultado de la operación de potencia se puede hacer con la función **pow()** que está contenida en la librería **cmath**, contenida a su vez en la librería **bits/stdc++.h**, dando como parámetros $2$ e $i$:

```cpp
pow(2, i);
```

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    string s;
    cin >> s;

    int total = 0;

    for (int i = 9, j = 0; i >= 0; i--, j++) {
        if (s[i] == '1') {
            total += pow(2, j);
        }
    }

    cout << total;

    return 0;
}
```
