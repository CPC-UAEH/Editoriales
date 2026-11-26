https://www.cpcjudge.com/problem/ush

# 26P1C4D. ush ush ush
#### Autor: Ignacio_benq

## Descripción
Luego de superar los obstaculos con la fuerte neblina, Maullín, en su recorrido por el bosque, se encuentra cara a cara con un lobo que lo mira con hambre.

El gato apenas conoce este lugar, así que no puede simplemente huir en cualquier dirección, debe quedarse dentro del bosque o se perdería para siempre.

El bosque se representa como una cuadrícula de tamaño ***n · m***, donde cada celda contiene cualquier cosa del bosque representado por (```*```). Como Maullín no está para ponerse estricto, atraviesa los obstáculos sin problema con tal de escapar.

Hay celdas especiales: la posición inicial de Maullín, marcada con ```M```, y las posiciones de los lobos, marcadas con ```L```.
Tanto Maullín como los lobos pueden moverse en las **4 direcciones** (arriba, abajo, izquierda y derecha), siempre que la celda destino esté dentro de los límites del bosque.

**Todos están obligados a moverse en cada turno**, ninguno puede quedarse quieto.

Cada minuto ocurre lo siguiente:

- Primero, Maullín se mueve a una de las **4** celdas vecinas de la celda donde él se encuentra.
- Después, cada lobo (viendo hacia dónde se movió el gato) se mueve a una de las **4** celdas vecinas de la celda donde ese lobo se encuentra.

Si al final del minuto algún lobo termina en la misma celda que Maullín, el gato es cazado (yiyi).

Lo sé, la primavera suele representarse con días soleados y un buen ambiente, pero los lobos cazan de noche y aun así sigue siendo primavera jeje.

Ayuda a Maullín a saber si puede huir de los lobos para siempre dentro del bosque, o si tarde o temprano será atrapado.

## Entrada
En la primera línea, dos enteros ***n*** y ***m*** $(2 \leq n, m \leq 1000)$, las dimensiones del bosque.

Las siguientes ***n*** líneas contienen ***m*** caracteres cada una, que representan el bosque. Cada celda es uno de los siguientes caracteres:

- ```*``` representa una celda transitable.
- ```M``` representa la posición inicial de Maullín.
- ```L``` representa la posición inicial de un lobo.

Se garantiza que hay exactamente una ```M``` y al menos una ```L``` en el mapa.

## Salida
Imprime ```ay maullin``` si Maullín puede escapar indefinidamente, o ```jeje``` si los lobos terminarán por atraparlo.

## Ejemplo

### Entrada
```
2 2
M L
* *
```
### Salida
```
ay maullin
```
### Entrada
```
2 2
M *
* L
```
### Salida
```
jeje
```
### Entrada
```
5 5
* * * * L
* * * * *
* * M * *
* * * * L
L * * * *
```
### Salida
```
jeje
```

## Notas
En el primer caso, Maullín tiene dos formas de sobrevivir cada minuto:

1. Moverse a la diagonal opuesta del lobo. Desde ahí, sin importar a cuál de sus dos vecinas se mueva el lobo, nunca coincidirá con la celda del gato.
2. Moverse a la propia celda del lobo. Como el lobo está obligado a abandonarla en su turno, Maullín queda solo y a salvo.

En el segundo caso, sin importar hacia dónde corra Maullín, el lobo lo atrapará en el primer movimiento ya que prácticamente sus 2 opciones son las casillas vecinas del lobo.

## Temas identificados
### Matemáticas
- Módulo

### Programación
- Ciclos
- Condicionales
- Estructuras de datos

## Propuesta de solución
#### Autor: Jordan

Este es otro ejemplo de los problemas "lo que te digo que hagas, eso no", porque no se trata de hacer una simulación entre el lobo y el gato, o de saber en cuantos segundos podría ser atrapado el gato, solamente hay dos respuestas, lo atrapa o no lo atrapa, y al tratarse de turnos, basta con hacer un par de casos en papel para darse cuenta de algunas cosas:

- Se puede ver como un tablero de ajedrez con casillas negras y blancas intercaladas, pero con números en filas y columnas.
- Si ambos números son impares o ambos números son pares, está en una casilla negra.
- Si un número es par y el otro no, entonces se encuentra en una casilla blanca.
- Si ambos, Maullin y el Lobo, se encuentran en el mismo color de casilla, Maullin siempre es cazado.
- Si Maullin y el Lobo se encuentran en casillas de distinto color, Maullin siempre escapa.

Así que solo queda averiguar en qué color de casilla se encuentra cada personaje, sin necesidad de representar la matriz, y comparar el color de la casilla en la que se encuentran.

## Implementación
Podemos saber en que color de casilla se encuentra Maullin si sabemos en qué fila y columna se encuentra, para eso podemos ir leyendo cadena por cadena para ver si es una 'M', si lo es, almacenamos las coordenadas; usamos el módulo de 2 para saber si están en una fila y columna par o si están en una fila y columna impar, que es lo mismo, luego podemos ocupar una variable booleana por cada personaje, que se vuelva verdadera si se cumplió la condición antes mencionada, si se volvió verdadera entonces está en una casilla negra, si no, entonces está en una casilla blanca.

Para los Lobos, podemos solo almacenar las coordenadas de los lobos según van apareciendo como una 'L', y se repite el procedimiento para saber en que color de casilla se encuentra cada Lobo.

Ya que sabemos en que color se encuentra cada personaje, ahora podemos hacer la comparación, si ambos se encuentran en el mismo color de casilla, entonces imprimimos "jeje", sino, imprimimos "ay maullin".

### C++
#### Autor: Jordan

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

    vector<pair<int, int>> lobos;

    int n, m, MaullinN, MaullinM;
    cin >> n >> m;

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            string s;
            cin >> s;
            if (s == "L") {
                lobos.push_back({i, j});
            }
            if (s == "M") {
                MaullinN = i;
                MaullinM = j;
            }
        }
    }

    bool negroM = false, negroL = false, blancoM = false, blancoL = false;

    if ((MaullinN % 2 == 0 && MaullinM % 2 == 0) || (MaullinN % 2 == 1 && MaullinM % 2 == 1)) {
        negroM = true;
    } else {
        blancoM = true;
    }

    for (auto [LoboN, LoboM] : lobos) {
        if ((LoboN % 2 == 0 && LoboM % 2 == 0) || (LoboN % 2 == 1 && LoboM % 2 == 1)) {
            negroL = true;
        } else {
            blancoL = true;
        }
    }

    if ((negroM && negroL) || (!negroM && !negroL) || (blancoM && blancoL) || (!blancoM && !blancoL)) {
        cout << "jeje";
    } else {
        cout << "ay maullin";
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
