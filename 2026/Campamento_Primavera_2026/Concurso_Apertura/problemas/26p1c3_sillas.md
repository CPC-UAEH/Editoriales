https://www.cpcjudge.com/problem/sillas

# 26P1C3. Sillas
#### Autor: Mafuyu_137
## Descripción
Al momento de organizar un evento masivo, un aspecto crucial es acomodar los asientos de las personas. Para ello, los organizadores crearon una regla que debe cumplirse sin excepción:

- No se puede sentar a ninguna persona junto a otra.

Esto se debe a que las personas son tan platicadoras que terminan arruinando por completo el evento, quitándole todo el sentido.

Inicialmente, los organizadores habían distribuido invitaciones considerando cierta capacidad. Sin embargo, debido a un recorte presupuestal inesperado, ahora necesitan **reducir la cantidad total de asistentes**.

Dado este recorte, tu tarea es determinar, para cada fila, cuál es la **mínima** cantidad de personas que debes sentar (incluyendo las ya sentadas) cumpliendo que:

1. No haya personas en sillas consecutivas.
2. No sea posible agregar una persona más sin romper la regla.
   
Cabe mencionar que cada fila se analiza de manera independiente.

## Entrada
En la primera línea un entero $F$ $(1 \leq F \leq 10^4)$, indicando el número de filas de sillas en el evento.
Para cada $i$ - $ésima$ fila:

Un entero $N_i$ $(1 \leq N_i \leq 2 \cdot 10^5)$, la cantidad de sillas en la $i$ - $ésima$ fila.
En la siguiente línea una cadena $C_i$ $(1 \leq |C_i| \leq 2 \cdot 10^5)$, donde:

- **0** representa un lugar disponible.
- **1** representa un lugar ya ocupado.

Se garantiza que la suma total de sillas no excede $2 \cdot 10^5$ y que no existe ningún par consecutivo de sillas ocupadas; es decir, ningún par rompe la regla mencionada.

## Salida
Por cada fila, imprimir un único entero: la **mínima** cantidad de personas que debes sentar para que sea imposible sentar a más gente.

## Ejemplo

### Entrada
```
4
3
000
4
0000
5
01000
8
01010101
```
### Salida
```
1
2
2
4
```

## Notas
Para la primera fila, el único acomodo válido es **010** porque ya no permite que se sienten más personas. El acomodo **101** tampoco permite que se sienten más personas, sin embargo, no es la cantidad mínima. Por lo tanto, la respuesta es **1**.

Para la segunda fila, un acomodo válido es **0101**. Se puede demostrar que no existe un acomodo con menos personas, por lo que la respuesta es **2**.
Para la cuarta fila, no existe lugar disponible, por lo que la respuesta es **4**.

## Temas identificados

### Programación
- Ciclos
- Manejo de cadenas
- Acumuladores
- Contadores

## Propuesta de solución
#### Autor: Jordan

Lo primero que podemos formalizar es que cada 3 asientos vacios, es posible colocar a una persona, se puede representar con una pirámide según la cantidad de sillas y la cantidad mínima de personas que podemos sentar:

	1			1
	1		   0 1
	1		  0 1 0
	2		 0 1 0 1
	2		0 1 0 0 1
	2	   0 1 0 0 1 0
	3	  0 1 0 0 1 0 1

Y así sucesivamente, por lo que siempre que haya 3 asientos vacíos, ahí cabe una persona y para asegurarnos de que sea la menor cantidad posble, lo ponemos en el tercer asiento:

	00000000

	00100100

Y claro que aún cabe una persona más en primera y última silla.

	10100101

Pero no es la solución más óptima, para esa cantidad de sillas, el mejor acomodo es de 3 personas y se ve así

	01001001

Por lo que, para empezar, la posición más óptima de la primera persona que vamos a sentar es en la segunda silla de la fila, después de ahí ya se pueden sentar cada 3 sillas vacías.

Suponiendo que ya hubiera dos personas sentadas en la fila de la siguiente forma:

	00100010

Y seguimos estrictamente la regla de sentar a alguien en la segunda silla al inicio si las primeras dos sillas están vacías y luego sentar gente cada 3 sillas vacías

	01100110

Donde a simple vista parece que incumplimos la regla de sentar gente junta, sin embargo, esa forma es totalmente equivalente a

	10101010

Entonces sí se cumplen las reglas.

## Implementación
Para poder hacer todo en una sola condición sin tomar casos especiales para la cadena, lo primero que hay que hacer, es agregar caracteres '0' al inicio y al final de la cadena ingresada, en esta cadena ya se encuentran todas las sillas libres y ocupadas, de forma que tenemos:

	 000010010
	 
	00000100100

Y así ya podemos siempre cumplir la condición de encontrar tres ceros y poner un 1 en el tercer espacio, realmente no es necesario modificar la cadena, solo debemos hacer un conteo de $0's$ y un conteo de $1's$ que vamos viendo o añadiendo.

Cada que veamos un '0', sumamos 1 a la variable de ceros, si la variable ceros llega a ser 3, entonces la reseteamos ceros a 0 y sumamos 1 al total de personas, si vemos un '1', entonces sumamos 1 al total de personas y reseteamos la variable ceros a 0.

Finalmente imprimimos el total de personas, y así con cada fila.

```mermaid
graph TD;
A([Inicio]) --> B[/q/]
B --> C{{Desde j = 0
		Hasta j < q
		Incremento 1}}
C --> D[/n, fila/]
D --> E(fila = '0' + fila + '0')
E --> F(t = 0, ceros = 0)
F --> G{{Desde i = 0
		Hasta i < n + 2
		Incremento 1}}
G --> H{"fila[i] == '0'"}
H --V--> I(ceros++)
H --F--> J((" "))
I --> J
J --> K{"fila[i] == '1' ||
		ceros == 3"}
K --V--> L(t++)
L --> M(ceros = 0)
K --F--> N((" "))
M --> N
N --> G
G --> O[\t\]
O --> C
C --> P([Fin])
```

### C++
#### Autor: Jordan

Usamos las siguientes líneas para tener un bloque claro de entradas y otro bloque de salidas
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```

```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
   cin.tie(0); ios::sync_with_stdio(false);

	int q;
	cin >> q;
	for (int j = 0; j < q; j++) {
	    int n;
	    cin >> n;
	    string fila;
	    cin >> fila;
        fila = '0' + fila + '0';
	    int t = 0, ceros = 0;
	    for (int i = 0; i < n + 2; i++) {
            if (fila[i] == '0') {
                ceros++;
            }
            if (fila[i] == '1' || ceros == 3) {
                t++;
                ceros = 0;
            }
	    }
	    cout << t << '\n';
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
