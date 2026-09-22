https://www.cpcjudge.com/problem/serie2

# B. Serie 2
#### Autor: Soria

## Descripción
*"¿No es así? Eso fue todo"*

Después de mucho esfuerzo, Felipe por fin está a punto de terminar su semestre, pero existe un pequeño detalle que aún debe resolver: el proyecto final de su clase "Fundamentos Electrónicos". Debido a esto él crea un pequeño circuito usando el módulo amplificador LM358, el cual duplica el voltaje que recibe.

Después de realizar las pruebas, Felipe comienza a trabajar con la versión final de su proyecto. Ahora construye **$N$** circuitos distintos, cada uno compuesto por señales de **$30$** módulos amplificadores, donde cada uno recibe ***1V*** desde el último al primero.

Para comprobar el funcionamiento, Felipe conecta varios circuitos a un bus de sincronización. Cada posición del bus corresponde a uno de los módulos del circuito, por lo que múltiples señales pueden llegar simultáneamente a la misma posición.

Por lo tanto:

- Si una posición recibe una cantidad impar de señales, el bus encenderá el módulo de esta posición.
- Si una posición recibe una cantidad par de señales, el bus apagará el módulo de esta posición.

Felipe hará $Q$ pruebas sobre el uso de este bus. En cada una seleccionará todos los circuitos en el rango de $L$ y $R$, conectándolos al bus. Él debe verificar sus resultados, ayúdalo a conocer cuánto será el voltaje final producido por el bus en cada prueba.

## Entrada
Dos enteros $N$ y $Q$ $(1 \leq N, Q \leq 2*10^5)$, la cantidad de circuitos y las pruebas a realizar.
Seguido por $N$ cadenas $S_1, S_2, S_3, ..., S_N$, donde $(|A_i| = 30)$, indica los módulos encendidos en el circuito $i$. Si el carácter $A_{ij}$ es $1$, significa que el amplificador $j$ del circuito $i$ está encendido.
Después $Q$ líneas, donde cada una se conforma por $2$ enteros $L$ y $R$, donde $(1 \leq L \leq R \leq N)$, indica una prueba que se realiza desde el circuito $L$ hasta el $R$.

## Salida
$Q$ enteros, el voltaje que tendrá el bus de sincronización en cada prueba.

## Ejemplo

### Entrada
```
5 1
001111101011001100011001001001
110100001011101110001100101111
111101100010011010001111001111
010011110000010001111110110000
010101110010101001100100001010
1 5
```
### Salida
```
19
```

## Notas
En el caso de ejemplo, la única consulta da como resultado 19, puesto que las posiciones $30$, $29$ y $26$ reciben una cantidad de $3$, $3$ y $1$ señales respectivamente, siendo las únicas impares, dando como resultado $1V + 2V + 16V = 19V$.

## Temas identificados
### Matemáticas
- Módulo
- Potencias
- Sistemas numéricos

### Programación
- Ciclos
- Condicionales
- Arreglos
- Suma de acumulados
- Prefix

## Propuesta de solución
#### Autor: Jordan

Dada una matriz de dimensiones $30 \times N$, donde cada fila $N$ se compone por $0's$ y $1's$, lo primero que pensaríamos sería en la cantidad de bits encendidos por cada cadena, pero hay 3 frases importantes en la descripción:
- Felipe conecta varios circuitos a un bus de sincronización.
- Múltiples señales pueden llegar simultáneamente a la misma posición.
- Si una posición recibe una cantidad impar de señales, el bus encenderá el módulo de esta posición.

Pondré un caso simple:

Entrada
```
2 1
111111111111111111111111111111
111111111111111111111111110000
1 2
```

Salida
```
15
```

El bus de sincronización se refiere a que, si bien los circuitos son horizontales, al **sincronizar** se miden todos a la vez, por lo que es un corte vertical. En este ejemplo, contando los $1's$ por cada columna, es fácil notar que en la posición $0$, $1$, $2$, $3$ (de derecha a izquierda) hay una cantidad impar de $1's$, mientras que en el resto de posiciones hay una cantidad par de $1's$. La regla impuesta es que si una posición recibe una cantidad impar de $1's$, se considerará esa posición en el cálculo de voltaje total.

Hay que sumar $2^i$, donde la cantidad de $1's$ de la columna en la posición $i$ debe ser impar. Lo que en este pequeño caso se traduce a:

$1+2+4+8$ $=$ $15$

## Implementación
Lo primero será leer las entradas, para lo que necesitamos un arreglo bidimensional de tamaño $30 \times N$ de tipo *char*. Sabemos que nos van a pedir $Q$ tareas, cada una con un rango de circuitos en el que haremos un conteo vertical de $1's$.

Si hacemos el conteo cada vez, contaremos intervalos repetidos, y en el peor de los casos habría $10^5$ circuitos, con $10^5$ tareas, y por cada tarea se recorre del circuito $1$ hasta el $10^5$, lo que da $10^{15}$ operaciones y ya se sale de tiempo por mucho.

Una de las estrategias para optimizar el tiempo de las consultas es crear un **prefix**, que se refiere a crear un arreglo de frecuencias que nos diga cuántas veces aparece un $1$ según la posición consultada. Un prefix para el caso propuesto quedaría así:
```
111111111111111111111111111111
222222222222222222222222221111
```
Así podemos hacer las consultas en el rango $arr[i][b] - arr[i][a - 1]$, donde $i$ representa una de las 30 posiciones de la cadena, así podemos saber cuántos $1's$ hay en el intervalo $[a, b]$ según la columna en la que encuentre; logramos que cualquier consulta, sin importar la longitud del rango, se haga en complejidad O(1) en vez de O(N).

Si dentro del rango dado, hay una cantidad impar de $1's$, se puede calcular con el módulo de 2, en caso de ser impar, tomamos la posición en la que se encuentra, hacemos la potencia $2^i$ y lo sumamos en una varible, que va acumulando el total de voltaje.

### C++
Hay que tener cuidado con los límites del problema, porque son $2 \times 10^5$ y si tomamos el primer índice como $1$, debemos tener posiciones extra para evitar errores de acceso de memoria.

Para poder tener un bloque de entradas y un bloque de salidas, se usan las líneas:
```
cin.tie(0);
ios::sync_with_stdio(false);
```

#### Autor: Jordan
```cpp
#include <bits/stdc++.h>

using namespace std;

int unos[35][200005];

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    int n, q;
    cin >> n >> q;

    for (int i = 1; i <= n; i++) {
        for (int j = 30; j >= 1; j--) {
            char c;
            cin >> c;

            if (c == '1') {
                unos[j][i] = unos[j][i - 1] + 1;
            } else {
                unos[j][i] = unos[j][i - 1];
            }
        }
    }

    for (int i = 0; i < q; i++) {
        long long int voltajeTotal = 0;
        int a, b;
        cin >> a >> b;

        for (int j = 1; j <= 30; j++) {
            if ((unos[j][b] - unos[j][a - 1]) % 2 == 1) {
                voltajeTotal += pow(2, j - 1);
            }
        }
        cout << voltajeTotal << '\n';
    }

    return 0;
}
```
