https://www.cpcjudge.com/problem/diosnoshaabandonado

# 26P1D2. dios nos ha abandonado
#### Autor: xenredda

## Descripción
Se supone que ya es primavera. en todo el mundo esto significa flores, pajaritos cantando y calorcito rico, pero tú estudias en el Instituto de Artes (IDA) en Real del Monte y aquí la primavera es un mito como los finales felices. mientras en el resto de México ya sacaron los shorts, aqui la neblina es tan espesa que a veces saludas a un árbol pensando que es tu coordinador.

Según los antiguos pergaminos de facebook y los memes de piolín, el cuerpo humano está compuesto por 70% agua, pero el hidalguense promedio está compuesto por 70% resistencia al frío y 30% pastes de papa. sin embargo, la "primavera" de montaña tiene un límite. en cuanto la temperatura baja del umbral crítico de los **8 grados**, nuestro sistema operativo colapsa: el sudor se vuelve escarcha, la silla se te congela al cuerpo y el cerebro solo puede procesar una frase existencial mientras intentas no morir de hipotermia.

Dada la temperatura actual $T$, determina si todavía podemos fingir que somos bohemios o si ya nos cargó el payaso.

## Entrada
Un único entero $T$ $(-50 \le T \le 100)$, que representa la temperatura en los pasillos fríos del IDA.

## Salida
Imprime exactamente una línea con el mensaje correspondiente:
- Si $T &lt; 8$, imprime: "dios nos ha abandonado"
- Si $T \ge 8$, imprime: "todo bien, un paste de papa y se me quita"

![Imagen](Recursos/IDA.png)

*Fotografía tomada durante un soleado día primaveral en IDA (8 grados).*

## Ejemplo

### Entrada
```
5
```
### Salida
```
dios nos ha abandonado
```

### Entrada
```
26
```
### Salida
```
todo bien, un paste de papa y se me quita
```

## Notas
- En el primer ejemplo (**5**) el valor de temperatura es menor a 8, por lo tanto se imprime "dios nos ha abandonado"
- En el segundo ejemplo (**6**) el valor de temperatura es mayor a 8, por lo tanto se imprime "todo bien, un paste de papa y se me quita"

## Temas identificados
### Programación
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Si el número $t$ es menor que 8, la solución es "dios nos ha abandonado", si $t$ es mayor o igual que 8, entonces la solución es "todo bien, un paste de papa y se me quita".

## Implementación
Leer la variable $t$, hacer una condición ```t < 8```, si es verdadero imprimir "todo bien, un paste de papa y se me quita", si no, imprimir "dios nos ha abandonado".

```mermaid
graph TD;
A([Inicio]) --> B[/t/]
B --> C{t < 8}
C --V--> D[\&quot;dios nos ha abandonado&quot;\]
C --F--> E[\&quot;todo bien, un paste de papa y se me quita&quot;\]
D --> G((" "))
E --> G
G --> H([Fin])

```

### C++
#### Autor: mae

```cpp
#include <iostream>

using namespace std;

int main() {
    int t;
    cin >> t;
    if (t < 8) {
        cout << "dios nos ha abandonado";
    } else {
        cout << "todo bien, un paste de papa y se me quita";
    }
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
