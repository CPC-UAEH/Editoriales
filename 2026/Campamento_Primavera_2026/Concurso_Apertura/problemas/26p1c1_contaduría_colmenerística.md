https://www.cpcjudge.com/problem/contadorabeja

# 26P1C1. Contaduría colmenerística
#### Autor: Empanak

## Descripción
Desde que empezó la primavera las abejas han andado de aquí para allá, hay mucho trabajo por hacer y casi no hay tiempo para descansar, pero están bien con eso. Sin embargo hay una de ellas que no está del todo a gusto, la abeja reina. Hay tanta miel en la colmena que ya no hay espacio para las abejas e incluso se fuga de los contenedores donde se guarda y es necesario ampliar el espacio o construir una nueva colmena para expandir sus capacidades de almacenamiento.

Claro que no todo es tan fácil, aunque es la reina, el mundo ha empezado a cambiar y las abejas han formado un concejo que representa la opinión de todas las abejas, y no sólo eso, ahora votan en conjunto para aprobar o rechazar las decisiones de la reina, incluida la decisión sobre mover la miel excedente a un nuevo lugar, por lo que tiene que esperar a su aprobación. Ahora el concejo solicita una auditoría contable para contar la miel que ha ingresado a los almacenes y la miel con la que se cuenta antes de su traslado y así evitar malentendidos. Por ello, la abeja contadora está en apuros, ayúdale a ver que todo esté en orden!

Honey es la abeja encargada de esta auditoría y, aunque es muy lista, esta tarea la rebasa. Necesita darle resultados al concejo antes de que la miel siga aumentando y toda la colmena esté inundada en ella. Además, entre tanto alboroto y tanta miel, es probable que alguien haya robado parte de las reservas del reino, o incluso que se haya ingresado miel sin reportar, por lo que tiene que saber si falta miel, sobra, o todo está en orden. Afortunadamente Honey cuenta con los registros de la miel que ha sido ingresada a los almacenes y la cantidad de ésta, pero aún falta comprobar la coherencia de lo registrado con la miel que se tiene.

## Entrada
En la primera línea un número flotante $C$ $(0 \lt C \leq 10^5)$ que indica la cantidad de miel almacenada.

En la segunda línea un número entero $N$ $(1 \leq N \leq 10^6)$ que indica la cantidad de registros de ingreso de miel.

En la tercera línea $N$ números flotantes $a_i$ $(0 \lt a_i \leq 10^5)$ separados por un espacio que indican la cantidad de miel ingresada en esa ocasión.

## Salida
Imprime un número $F$ que indique la diferencia entre los registros de miel y la cantidad de miel existente.

La respuesta será considerada correcta si su error absoluto o relativo no excede $10^{-6}$

Para imprimir la respuesta con $6$ decimales, debes:

- Agregar la librería ```<iomanip>```
- Imprimir la respuesta así ```cout << fixed << setprecision(6) << respuesta;```

## Ejemplo

### Entrada
```
10.65
2
6.7 4
```
### Salida
```
0.05
```
### Entrada
```
190.345
8
6 25 32 12 27 0.4 19.6 8
```
### Salida
```
-60.345
```
### Entrada
```
53.123456
2
0.123456 53
```
### Salida
```
0.0
```

## Temas identificados
### Programación
- Ciclos
- Acumuladores

## Propuesta de solución
#### Autor: Jordan

No dicen que debemos encontrar la diferencia entre la miel que sabemos que tenemos y los registros que se tienen. Simplemente hay que restar la cantidad de miel que se sabe que tenemos con la total de miel que mencionan los registros.

## Implementación

Realmente no necesitamos el arreglo de los registros, basta con acumular en una variable double los registros, luego restar del total de registros el total de miel almacenada que recibimos al inicio.

```mermaid
graph TD;
A([Inicio]) --> B[/c, n/]
B --> C(Total = 0)
C --> D{{Desde i = 0
		Hasta i < n
		Incremento 1}}
D --> E[/aux/]
E --> F(total = total + aux)
F --> D
D --> G[\total - c\]
G --> H([Fin])
```

### C++
#### Autor: Jordan

Como menciona la descripción, es necesario:
- Agregar la librería ```<iomanip>```
- Imprimir la respuesta así ```cout << fixed << setprecision(6) << respuesta;```

```cpp
#include <bits/stdc++.h>
#include <iomanip>

using namespace std;

int main() {
	double c;
	int n;
	cin >> c >> n;
	double total = 0;
	for (int i = 0; i < n; i++) {
	    double aux;
	    cin >> aux;
	    total += aux;
	}
	cout << fixed << setprecision(6) << total - c;
}
```

### Java
#### Autor

```java

```

### Python
#### Autor

```python

```

### Kotlin
#### Autor

```kotlin

```
