https://www.cpcjudge.com/problem/salida

# T26P1C2. Salida
#### Autor: Soria

## Descripción
*"Espero alegre la salida y espero no volver jamás."*

Debido al clima de la primavera, Felipe se encuentra en medio la inundación de la UACH (Universidad Autónoma para Capibaras de Hidalgo). Él necesita salir lo más rápido posible, así que necesita buscar la puerta entre tantas que diga el texto *"SALIDA"* Existen $N$ puertas dispuestas en fila, cada una con un texto conformado por letras mayúsculas desde la $A$ a la $Z$.

## Entrada
Un entero $N$ $(1 \leq N \leq 1000)$ representando el número de puertas que hay.
En las siguientes $N$ lineas una cadena $A_i$, el texto de la $i$ - $ésima$ puerta.
Se garantiza que la suma de los tamaños de todas las cadenas no supera $10^3$ y que una sola cadena tiene el texto *"SALIDA"*.
  
## Salida
Un entero $i$, indicando que $i$ - $ésima$ puerta es la de la salida.

## Ejemplo

### Entrada
```
5
ENTRADA
SALON
SALIDA
LABORATORIO
PAPELERIA
```
### Salida
```
3
```
### Entrada
```
1
SALIDA
```
### Salida
```
1
```

## Notas
En el primer caso, el texto en la posición *3* es el que cuenta con la salida.

En el segundo caso, existe una única puerta, la cuál es la salida.

## Temas identificados
### Programación
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan
Se nos da una lista de palabras, y se asegura que una de ellas dice "SALIDA", por lo que solo tenemos que encontrar en que número de palabra apareció la salida.

## Implementación
Durante la lectura de las palabras podemos comparar si la palabra recién leída dice "SALIDA", si es verdadero, lo imprimimos, si no, no hacemos nada.

```mermaid
graph TD;
A([Inicio]) --> B[/n/]
B --> C{{Desde i = 1
        Hasta i <= n
        Incremento 1}}
C --> D[/s/]
D --> E{s == &quot;SALIDA&quot;}
E --V--> F[/i/]
E --F--> G((" "))
F --> G
G --> C
C --> H([Fin]) 
```

### C++
#### Autor: mae
Es necesario pausar la salida de la consola con las líneas:
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```
Para leer todas las palabras y que la impresión del número donde apareció la salida sea al final.

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    int n;
    string s;

    cin >> n;

    for (int i = 1; i <= n; i++){
        cin >> s;
        if (s == "SALIDA"){
            cout << i;
        }
    }
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
