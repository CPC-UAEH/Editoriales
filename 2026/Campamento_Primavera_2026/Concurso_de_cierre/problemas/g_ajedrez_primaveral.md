https://www.cpcjudge.com/problem/chesscarlosyangelica

# G. Ajedrez Primaveral
#### Autor: Kaarlarax

## Descripción
Durante las cálidas tardes de primavera, Carlos y Angélica aprovechan el clima soleado para disfrutar su tiempo de ocio al aire libre. Después de pasar horas estudiando programación y algoritmos, deciden darle un descanso a sus mentes y relajarse bajo un árbol florecido jugando al ajedrez. Inspirados por la frescura de la temporada, deciden inventar un nuevo reto basado en un problema clásico.
Casi todo el mundo conoce el dilema de colocar ocho reinas en un tablero de ajedrez de $8 \times 8$ de manera que ninguna reina pueda capturar a otra. Sin embargo, Carlos y Angélica quieren ir más allá: desean saber el número máximo de piezas de ajedrez de un solo tipo que se pueden colocar en un tablero de dimensiones $m \times n$ de tal forma que ninguna pieza ataque a otra.

Como es bastante difícil calcular la solución a mano mientras intentan disfrutar de su tarde primaveral, te han pedido ayuda para programar la solución. No necesitan saber la respuesta para todas las piezas del juego. Los peones les parecen bastante aburridos y, de todas formas, Angélica perdió los alfiles entre las flores del jardín. Solo quieren saber cuántas Torres, Caballos, Reinas o Reyes se pueden colocar en el tablero sin que se ataquen entre sí.


## Entrada
La primera línea de entrada contiene un entero $T$, el número de casos de prueba.

Cada caso de prueba consiste en una línea que contiene un carácter del conjunto { $r$, $k$, $Q$, $K$ }, que representan respectivamente las piezas Torre (Rook), Caballo (Knight), Reina (Queen) o Rey (King). El carácter es seguido por los enteros $m$ $(4 \le m \le 10)$ y $n$ $(4 \le n \le 10)$, que indican el número de filas y el número de columnas del tablero de ajedrez.

La casilla inferior izquierda es $(1, 1)$.

## Salida
Para cada caso de prueba, imprime el número máximo de piezas **de ese tipo** que se pueden poner en un tablero con las dimensiones dadas, de modo que no estén en posición de atacar a ninguna otra pieza.

## Ejemplo

### Entrada
```
2
r 6 7 
k 8 8
```
### Salida
```
6
32
```

## Temas identificados
### Matemáticas
- Adhoc

### Programación
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Solo se piden 4 piezas distintas, por cada una de las piezas se puede hacer una simulación con el tablero dado o se pueden aplicar fórmulas para calcular la cantidad de piezas que caben en el tablero dado. Para explicar las posiciones de las piezas, voy a poner un ejemplo con un tablero de $5 \times 6$, con la solución para todas las piezas:

- Para torres ```r```:

```
r . . . .
. r . . .
. . r . .
. . . r .
. . . . r
. . . . .
```

- Para reinas ```Q```:

```
. . . Q .
Q . . . .
. . Q . .
. . . . Q
. Q . . .
. . . . .
```

- Para reyes ```K```:

```
K . K . K
. . . . .
K . K . K
. . . . .
K . K . K
. . . . .
```

- Para caballos ```k```:

```
k . k . k
. k . k .
k . k . k
. k . k .
k . k . k
. k . k .
```

## Implementación

Voy a tomar el mismo tablero de antes para explicar las fórmulas encontradas para cada pieza.

- Para torres ```r```:

Observamos que para maximizar el número de piezas lo mejor es colocarlas en diagonal desde un borde hasta el otro, por lo que la diagonal va a ser tan grande como el lado más corto.

La fórmula encontrada es $\min${ $n,m$ }.

- Para reinas ```Q```:

Observamos que las reinas tienen un acomodo parecido a los movimientos de un caballo, pero si hacemos casos, no daremos cuenta que pueden caber tantas reinas como torres, debido a su naturaleza ortogonal, por lo que de igual forma, caben tantas reinas como el lado más corto.

La fórmula encontrada es $\min${ $n,m$ }.

- Para reyes ```K```:

Observamos que los reyes se acomodan en una cuadrícula, pues cada uno puede atacar a sus 8 casillas adyacentes, se puede dejar solo un espacio entre cada uno, por lo que caben tantos reyes como la mitad del lado $n$, multiplicado por la mitad del lado $m$, pero hay que notar que si el lado es par, la división es correcta, pero si el lado es impar, el resultado de la división se desvía por 0.5 de la cantidad real,  por lo que hay que sumar una unidad a $m$ y a $n$, para luego dividir y redondear hacia abajo.

La fórmula encontrada es $\left(\frac{n+1}{2}\right)\left(\frac{m+1}{2}\right)$.

- Para caballos ```k```:

Observamos que los caballos siempre atacan a una casilla del color contrario al que están, por lo que podemos acomodar caballos en todas las casillas de un solo color sin que se ataquen, cabrán tantos caballos como la cantidad de casillas dividido entre $2$, pero si uno de los lados es impar se desvía en 0.5 de la cantidad real, por lo que hay que sumar una unidad al resultado de la multiplicación, dividir y redondear hacia abajo.

La fórmula encontrada es $\frac{n \cdot m + 1}{2}$.

```mermaid
graph TD;
A([Inicio]) --> B[/leer t/]
B --> C{{Desde i = 0
Hasta i < t
Incremento 1}}
C --> D[/Leer pieza, n, m/]
D --> E{pieza}
E --> F{caso 'r'}
F --> G[\"Imprimir min(n, m)"\]
E --> H{caso 'Q'}
H --> I[\"Imprimir min(n, m)"\]
E --> J{caso 'K'}
J --> K[\"Imprimir ((n + 1) / 2) * ((m + 1) / 2)"\]
E --> L{caso 'k'}
L --> M[\"Imprimir ((n * m) + 1) / 2"\]
N((" ")) --> C
G --> N
I--> N
K --> N
M --> N
C --> Z([Fin])
```

### C++
#### Autor: Jordan

Cuando hacemos una división a un número que se encuentra en una variable entera, y el resultado tiene decimales, C++ se encarga de cortar los decimales, por lo que en lugar de redondear hacia abajo, simplemente lo dejamos como esta, si el resultado da 6.5, C++ va a cortar los decimales y queda solo el entero.

La función switch es C++ solo recibe como parámetro números enteros, por lo que solo puede recibir char e int y sus variantes, por esa razón se usó char en lugar de string.

Al tener tareas, debemos tener un bloque claro de entradas y un bloque de salidas, para eso ocupamos las instrucciones:
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```
Así evitamos tener las entradas y salidas mezcladas, para que el juez pueda valorar correctamente.

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

  	int t;
  	cin >> t;
  
  	for (int i = 0; i < t; i++) {
        char pieza;
        int n, m;
        cin >> pieza >> n >> m;

        switch(pieza) {
            case 'r':
                cout << min(n, m) << '\n';
                break;
            case 'Q':
                cout << min(n, m) << '\n';
                break;
            case 'K':
                cout << ((n + 1) / 2) * ((m + 1) / 2) << '\n';
                break;
            case 'k':
                cout << ((n * m) + 1) / 2 << '\n';
                break;
        }
  	}
}
```
