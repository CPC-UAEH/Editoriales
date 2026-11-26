https://www.cpcjudge.com/problem/pacascolmena

# E. Pacas en la colmena
#### Empanak

## Descripción

Últimamente Honey ha notado que en su colmena hay un gran desorden de recursos, especialmente hay un gran desorden en la bodega donde hay unidades de ***cera*** y ***propóleo***, dos de los principales materiales de construcción de las abejas obreras, la organización de las abejas las ha llevado a formar una fila de materiales conforme fueron llegando a la bodega, sin embargo Honey ha concluido que una forma más conveniente de guardar estos recursos es colocándolos en pacas a su vez.

Cada paca debe tener exactamente dos unidades de algún recurso, para lograr llevar un control sobre el almacenamiento Honey decidió que cada paca debe tener un sólo tipo de material guardado y para hacer más rápido el proceso de guardado ha planeado que un grupo de abejas le ayude a completar esta labor.

Honey quiere calcular cuántas pacas de ambos materiales podría empacar una abeja al ponerla en algún segmento de la fila de materiales y usar estos datos para planear mejor su estrategia de acomodado.

## Entrada
Un número $N$ $(2 \leq N \leq 10^6)$ que representa la cantidad de materiales que salieron por la banda y un número $Q$ $(1 \leq Q \leq 10^6)$ que representa la cantidad de segmentos en los que Honey quiere calcular.

Una línea con $N$ numeros $a_i$ $(a_i \in {1, 2})$ donde $a_i$ representa el tipo de material. $1$ ***para cera*** y 2 ***para propóleo***.

$Q$ líneas, cada una con dos números $l$ y $r$ $(1 \leq l &lt; r \leq N)$  que representan la posicion en que empieza el segmento y la posición en la que termina.

## Salida

$Q$ líneas, cada una con un número que represente la cantidad de pacas armadas en total en el rango especificado.

## Ejemplos

#### Entrada
```
10 3
2 1 1 2 2 1 2 1 2 2 
1 10
3 6
8 9
```
### Salida
```
5
2
0
```

### Entrada
```
5 2
1 2 1 2 1
1 2
3 4
```
### Salida
```
0
0
```

## Notas
En el primer caso:
- En la primer prueba se consideró toda la secuencia de materiales con un total de $5$ pacas armadas ($2$ de cera y $3$ de propóleo)
- En la segunda prueba se consideró la secuencia {1, 2, 2, 1} por lo que se armó un total de $2$ pacas ($1$ de cera y $1$ de propóleo)
- En la tercera prueba se consideró la secuencia {1, 2} por lo que no se armó ninguna paca al no poder completar alguna.

## Temas identificados
### Matemáticas
- Intervalos

### Programación
- Arreglos
- Prefix
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Se hacen dos arreglos de frecuencia acumulada, uno para cada material, representados como $1$ y $2$.

Para el caso de entrada $2$ $1$ $1$ $2$ $2$ $1$ $2$ $1$ $2$ $2$, se obtendran dos arreglos:

Para $1$: { $0, 1, 2, 2, 2, 3, 3, 4, 4, 4$ }

Para $2$: { $1, 1, 1, 2, 3, 3, 4, 4, 5, 6$ }

Si no se hacen estos arreglos, el algoritmo no entra en tiempo y será rechazado, siendo que son $10^6$ cantidad de tareas y en el peor de los casos, por cada tarea recorreriamos $10^6$ posiciones del arreglo, daría $10^{12}$ operaciones y tardaría demasiado.

Pero, de esta forma podemos entrar en tiempo al no recorrer todo el arreglo inicial por cada tarea posterior, y solo hacer la operación $x[R] - x[L - 1]$, donde obtenemos, para ambos arreglos, la cantidad total de material que hay hasta la posición $R$ y le restamos la cantidad de material que había hasta antes de la posición $L$, así solo nos quedamos con la cantidad de material que hay desde la posición $L$ hasta $R$.

Ahora que tenemos la cantidad de material hay que dividir entre dos y redondear hacia abajo, para obtener la cantidad total de pacas que se pueden hacer por cada tipo de material, si hubiera $4$ ***cera***, al dividir entre dos resulta $2$ pacas, si hubiera $9$ ***propóleo***, resulta $4$ pacas.

Solo queda sumar la cantidad de pacas para ambos materiales e imprimir el resultado por cada tarea.

## Implementación

### C++
#### Autor: Jordan

Particularmente C++ tiene el problema de que al declarar un arreglo dentro de main, no tiene valores inicializados, cada posición del arreglo tiene valores basura de la RAM, por lo que para que todos los valores sean inicializados en $0$, lo declaramos fuera de main y le damos el tamaño correspondiente a los límites del problema, que en este caso fue $10^6$ más unas cuantas posiciones más para asegurar que no habrá intentos de acceso de memoria a espacios que no nos corresponden.

Además, al tener variables enteras y dividirlas por un número que nos da un resultado decimal, C++ se encarga de cortar los decimales, si el resultado es $0.5$, dentro de la variable entera el valor será $0$, si el resultado en $5.99999$, la variable entera valdrá $5$.

Normalmente, al ingresar las entradas notamos que para las $Q$ tareas se leen dos valores y se imprime un valor sucesivamente por cada tarea, pero el juez virtual tomará el resultado como erróneo pues no hay un bloque de salidas preciso, sino que están mezcladas las entradas con las salidas. Para solucionar este problema, se usan las líneas: 

```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```

Así pausamos las salidas hasta que todas las entradas se hagan y permitimos que haya un bloque de entradas y un bloque de salidas que el juez virtual sí puede identificar y marcar como correcto.

```cpp
#include <bits/stdc++.h>

using namespace std;

int uno[10000005];
int dos[10000005];

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

    int n, q;
    cin >> n >> q;

    for (int i = 1; i <= n; i++) {
        int a;
        cin >> a;
        if (a == 1) {
            uno[i] = uno[i-1] + 1;
            dos[i] = dos[i-1];
        } else {
            uno[i] = uno[i-1];
            dos[i] = dos[i-1] + 1;
        }
    }

    for (int i = 0; i < q; i++) {
        int l, r;
        cin >> l >> r;
        cout << ((uno[r] - uno[l-1]) / 2) + ((dos[r] - dos[l-1]) / 2) << '\n';
    }

    return 0;
}
```
