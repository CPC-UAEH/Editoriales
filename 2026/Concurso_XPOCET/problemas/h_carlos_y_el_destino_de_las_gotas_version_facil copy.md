# H. Carlos y el destino de las gotas (Versión fácil)

**Autor:** Kaarlarax

**Link:** [Carlos y el destino de las gotas (Versión fácil)](https://cpcjudge.com/problem/carloslluviafacil)

**Tiempo límite:** 1.0 s

**Memoria límite:** 256M

## Descripción

Carlos observa una ventana formada por una cuadrícula de $N$ filas y $M$ columnas. Cada casilla contiene:

- `o`: una gota adherida a la ventana.
- `.`: una casilla vacía.

Puede lanzar $X$ gotas móviles desde la primera fila, eligiendo libremente la columna inicial de cada una.

Las gotas solo se desplazan verticalmente. Por lo tanto, una gota que comienza en una determinada columna recogerá todas las gotas adheridas que se encuentren en esa misma columna.

Si se colocan varias gotas móviles en una misma columna, no se obtiene ningún beneficio adicional, ya que todas recorren exactamente el mismo camino.

Por lo tanto, el objetivo consiste en elegir hasta $X$ columnas distintas que contengan la mayor cantidad posible de gotas adheridas.

## Entrada

La primera línea contiene un entero $T$, el número de casos de prueba.

Para cada caso de prueba:

La primera línea contiene tres enteros:

$N, M, X$

donde $N$ y $M$ representan las dimensiones de la ventana y $X$ es la cantidad de gotas móviles disponibles.

Las siguientes $N$ líneas contienen una cadena de longitud $M$ formada únicamente por `o` y `.`.

## Salida

Para cada caso de prueba, imprime un entero que represente la máxima cantidad de gotas adheridas que pueden terminar formando parte del charco.

## Ejemplos

### Ejemplo 1

#### Entrada

```text
4 5 2
.o.o.
oo.oo
.o.o.
..o..
```

#### Salida

```text
6
```

### Ejemplo 2

#### Entrada

```text
3 3 1
o.o
.oo
ooo
```

#### Salida

```text
3
```

### Ejemplo 3

#### Entrada

```text
2 2 4
oo
oo
```

#### Salida

```text
4
```

### Ejemplo 4

#### Entrada

```text
3 1 5
o
o
o
```

#### Salida

```text
3
```

### Ejemplo 5

#### Entrada

```text
3 4 0
oooo
o..o
.oo.
```

#### Salida

```text
0
```

## Notas

En el primer caso, la cantidad de gotas en cada columna es:

$
[1,\ 3,\ 1,\ 3,\ 1]
$

Como $X=2$, se pueden elegir las dos columnas con mayor cantidad de gotas:

$
3+3=6
$

En el tercer caso hay únicamente $2$ columnas. Aunque se tienen $4$ gotas móviles, colocar más de una en la misma columna no permite recoger gotas adicionales. Por eso se toman como máximo las $2$ mejores columnas.

## Temas identificados

### Programación

- Arreglos
- Ordenamiento
- Conteo
- Greedy

### Matemáticas

- Suma de cantidades por columna
- Maximización

## Propuesta de solución

**Autor de la propuesta:** Jordan

La trayectoria de una gota móvil queda completamente determinada por la columna desde la que comienza.

Por lo tanto, para cada columna $j$ podemos calcular cuántas gotas adheridas contiene:

$
c_j=\sum_{i=0}^{N-1}[mat_{i,j}=\texttt{'o'}]
$

donde $(mat_{i,j}=\texttt{'o'})$ vale $1$ si la casilla contiene una gota y $0$ en caso contrario.

Una vez obtenida la cantidad de gotas de cada columna, basta con ordenar estas cantidades de mayor a menor.

Las mejores decisiones son seleccionar las columnas con mayor cantidad de gotas. Como no tiene sentido colocar dos gotas móviles en la misma columna, se pueden aprovechar como máximo $M$ columnas distintas.

Por ello, la cantidad de columnas que se seleccionan es:

$
\min(X,M)
$

Finalmente, se suman las primeras $\min(X,M)$ cantidades después del ordenamiento.

## Observaciones

- Todas las gotas móviles que comienzan en una misma columna recorren el mismo camino.
- Colocar más de una gota móvil en una columna no aumenta la cantidad de gotas recogidas.
- Solo importa la cantidad de `o` que existe en cada columna.
- Si $X=0$, no se selecciona ninguna columna y la respuesta es $0$.
- Si $X\geq M$, se pueden seleccionar todas las columnas.

## Restricciones

$
1\leq T\leq 10^4
$

$
1\leq N,M\leq 2\cdot10^5
$

$
0\leq X\leq10^9
$

$
1\leq N\cdot M\leq2\cdot10^5
$

Además, la suma de $N\cdot M$ entre todos los casos de prueba no supera:

$
10^6
$

## Estados o estructura de la solución

Se utiliza:

- Una matriz `mat` para almacenar la ventana.
- Un arreglo `candidates` de tamaño $M$.
- `candidates[j]` representa la cantidad de gotas adheridas en la columna $j$.

## Casos base

No existe un caso base recursivo, ya que la solución es completamente iterativa.

Los casos particulares relevantes son:

- $X=0$: la respuesta es $0$.
- $M=1$: solo existe una columna que puede ser seleccionada.
- $X>M$: únicamente pueden aprovecharse $M$ columnas diferentes.

## Transiciones o algoritmo

1. Leer $N$, $M$ y $X$.
2. Leer la matriz de la ventana.
3. Para cada columna, recorrer todas sus filas y contar las casillas que contienen `o`.
4. Guardar la cantidad obtenida para cada columna.
5. Ordenar las cantidades de mayor a menor.
6. Tomar las primeras $\min(X,M)$ posiciones.
7. Sumar sus cantidades.
8. Imprimir la suma.

```mermaid id="72841"
flowchart LR
    A[Inicio] --> B[Leer N, M y X]
    B --> C[Leer la matriz]
    C --> D[Contar gotas de cada columna]
    D --> E[Ordenar cantidades de mayor a menor]
    E --> F["Tomar min(X, M) columnas"]
    F --> G[Sumar sus cantidades]
    G --> H[Imprimir respuesta]
```

## Correctitud

Para cada columna $j$, el valor $c_j$ representa exactamente la cantidad de gotas adheridas que puede recoger una gota móvil que comienza en esa columna, ya que su trayectoria es únicamente vertical.

Una vez calculados todos los valores $c_j$, seleccionar una columna con mayor cantidad de gotas siempre es al menos tan bueno como seleccionar una columna con menor cantidad.

Por lo tanto, para maximizar la cantidad total recogida, se deben seleccionar las $\min(X,M)$ columnas con los valores $c_j$ más grandes.

El algoritmo ordena estos valores de mayor a menor y suma exactamente esas cantidades. Por lo tanto, la suma obtenida es la máxima cantidad de gotas que pueden terminar en el charco.

## Complejidad computacional

Para contar las gotas se recorren todas las casillas de la matriz:

$
O(NM)
$

Ordenar las $M$ cantidades requiere:

$
O(M\log M)
$

Por lo tanto, la complejidad total es:

$
O(NM+M\log M)
$

La matriz utiliza:

$
O(NM)
$

memoria y el arreglo de cantidades utiliza:

$
O(M)
$

por lo que la complejidad espacial total es:

$
O(NM+M)
$

## Implementación

### C++

**Autor de la implementación:** Soria

```cpp
#include <bits/stdc++.h>
using namespace std;

#define sz(x) int((x).size())
#define pb push_back
#define nl "\n"

typedef vector<int> vi;
typedef pair<int, int> ii;

void solve() {
    int n, m, x;
    cin >> n >> m >> x;

    vector<vector<char>> mat(n, vector<char>(m));
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> mat[i][j];
        }
    }

    vector<int> candidates(m);
    for (int j = 0; j < m; ++j) {
        for (int i = 0; i < n; ++i) {
            candidates[j] += mat[i][j] == 'o';
        }
    }

    sort(rbegin(candidates), rend(candidates));

    int sol = 0;
    for (int i = 0; i < min(x, m); ++i) {
        sol += candidates[i];
    }

    cout << sol << nl;
}

int main() {
    ios_base::sync_with_stdio(0);
    cin.tie(0);

    int t = 1;
    cin >> t;

    while (t--) solve();

    return 0;
}
```

## Casos límite

- $X=0$: no se puede recoger ninguna gota.
- $X=1$: únicamente se selecciona la columna con más gotas.
- $X>M$: solo se pueden utilizar $M$ columnas distintas.
- Una columna puede contener cero gotas.
- Todas las gotas pueden estar concentradas en una sola columna.
- Todas las columnas pueden tener la misma cantidad de gotas.
- $N=M=1$: la respuesta depende únicamente de si la única casilla contiene `o`.