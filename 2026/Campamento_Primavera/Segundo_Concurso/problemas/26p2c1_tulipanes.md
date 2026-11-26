https://www.cpcjudge.com/problem/tulipanes

# 26P2C1. Tulipanes
#### Autor: wisperfrog

## Descripción
Hoy es $27$ de mayo y una rana profundamente enamorada cumple un mes más de noviazgo con su querida novia. Esta rana no tiene dinero, pero está dispuesta a hacer lo que sea por conseguir un detalle para celebrar este día.

Mientras iba de camino a la Universidad de las Ranas, se topó un invernadero cuya puerta estaba abierta...

La rana entró silenciosamente y analizó el perímetro, NO HABÍA NADIE!

Amapolas, Girasoles, Anturios, y más flores/plantas se encontraban en este enorme invernadero de $N$ filas por $M$ columnas, pero había una de interés especial para la rana, el Tulipán.

Su intención era **robar la mayor cantidad de Tulipanes** para regalar a su novia pero, a pesar de lo solitario de este lugar, era probable que pronto volviera un encargado, por lo que la rana debía darse prisa.

Para no demorar mucho, la rana decidió robar únicamente los Tulipanes de una columna, así que te pidió ayuda para que le indiques hacia que columna correr para robar **solo los Tulipanes** y después escapar.

## Entrada
En la primera línea dos enteros $N$ y $M$ $(1 \leq N, M \leq 100)$, la cantidad de filas y columnas respectivamente.

En las siguientes $N$ líneas, $M$ carácteres, donde:

- indica una flor
- indica una planta
- indica un tulipán
- indica un espacio vacío

## Salida
En caso de que no haya ningún Tulipán, deberás imprimir "Bro..." (sin comillas).

En caso contrario, imprimir dos enteros $C$ y $T$, la columna a la que debe ir y la cantidad de tulipanes que puede robar en dicha columna, respectivamente.
  
Si hay varias soluciones, imprimir la menor columna.

## Ejemplo

### Entrada
```
5 5
FFP..
T..T.
T...T
T.PPP
T.F..
```
### Salida
```
1 4
```

### Entrada
```
6 4
.P.T
...T
F.T.
PP..
..T.
FFPF
```
### Salida
```
3 2
```

### Entrada
```
3 7
FFP...F
P..F..F
....PPF
```
### Salida
```
Bro...
```

## Notas
En el primer caso, la rana debe robar los tulipanes de la primera columna, así conseguirá robar $4$ tulipanes.

Si la rana optara por la cuarta o quinta columna, solo robaría un tulipán.


En el segundo caso, la rana puede robar tanto en la tercera como en la cuarta columna, así conseguirá robar $2$ tulipanes en ambas.

Dadas las restricciones de la salida, la rana debe robar en la tercera columna.

## Temas identificados
### Programación
- Arreglos de frecuencia
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Se debe buscar la columna en la que más tulipanes haya, si solo queremos la cantidad, no necesitamos almacenar toda la matriz, solo la frecuencia con la que aparecen los tulipanes segun la columna en la que se encuentran, por lo que podemos generar un arreglo de frecuencia (cubetas) donde en la posición de la columna sumemos 1 por cada tulipan que encontremos en la matriz de entrada.

Una vez que tenemos el arreglo de frecuencias completo, podemos buscar el número mayor dentro de ese arreglo, la posición del número mayor y la posición del número mayor es la respuesta, si todos son 0, el resultado será "Bro...".

## Implementación
Creamos un arreglo, para que durante la entrada hagamos dos ciclos for anidados, de forma que un for nos de las filas y el otro las columnas, solo nos interesa sumar 1 a la posición de la columna donde se encontró un tulipan.

```
5 5
FFP..
T..T.
T...T
T.PPP
T.F..
```

Con esa entrada obtendremos un arreglo 1-indexado ${4, 0, 0, 1, 1}$, donde solo debemos encontrar la posición del número mayor, que en este caso es $1$, y se encontraron $4$ Tulipanes en esta columna.

Podemos usar una variable que empiece en 0 para encontrar el número mayor que solo se actualice que encuentra un número mayor que 0, de esta forma, si no encuentra ningún número mayor que 0, signfica que no hubo tulipanes en ninguna columna, por lo que el resultado será "Bro...".

### C++
#### Autor: Jordan

Para leer la matriz y comparar caracter por caracter, podemos leer variables char, sin necesidad de que haya un espacio entre los caracteres ya se leen en variables distintas.

Al declarar el arreglo de enteros fuera de main, forzamos a que se cree un arreglo con valores default, en este caso para int es $0$, de esta forma sí podemos sumar dentro del arreglo.

```cpp
#include <bits/stdc++.h>

using namespace std;

int a[1000005];

int main()
{
    int n, m;
    cin >> n >> m;
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= m; j++) {
            char c;
            cin >> c;
            if (c == 'T') {
                a[j]++;
            }
        }
    }

    int c = 1;
    int mayor = 0;
    for (int i = 1; i <= m; i++) {
        if (a[i] > mayor) {
            mayor = a[i];
            c = i;
        }
    }

    if (mayor == 0) {
        cout << "Bro...";
    } else {
        cout << c << " " << mayor;
    }

    return 0;
}
```
