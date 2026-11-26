https://omegaup.com/arena/problem/ofmi-2026-defensa/

# Sistema de defensa
#### Autor: Ethan Jiménez

## Descripción

La Organización Federal de Misiones Interplanetarias (OFMI) quiere desarrollar un sistema de defensa contra la inclemente radiación cósmica para su nueva estación espacial.

La estación está dividida en $n$ sectores contiguos, numerados del $1$ al $n$. Para proteger cada sector, la OFMI desplegará $k$ drones especializados. Cada dron activa una red de defensa que cubre un rango continuo de sectores.

El $i$-ésimo dron protege todos los sectores desde $L_i$ hasta $R_i$, otorgando $E_i$ unidades de energía de protección a cada uno de ellos.

Un mismo sector puede estar cubierto por varios drones. En ese caso, su protección total será la suma de las energías aportadas por todas las redes que lo cubren.

Después de activar todas las redes de defensa, las ingenieras de la OFMI desean responder múltiples consultas sobre el estado final de la estación.

## Problema

Dada la información de todos los drones y múltiples valores $X_i$, determina cuántos sectores de la estación quedaron protegidos con **al menos** $X_i$ unidades de energía total.

## Entrada

La primera línea contiene dos enteros $n$ y $k$, representando el número de sectores y el número de drones.

Las siguientes $k$ líneas contienen tres enteros $L_i$, $R_i$ y $E_i$, indicando que el $i$-ésimo dron protege todos los sectores del intervalo $[L_i,R_i]$ con $E_i$ unidades de energía.

La siguiente línea contiene un entero $q$, representando el número de consultas.

Las siguientes $q$ líneas contienen un entero $X_i$.

## Salida

Imprime $q$ líneas.

En la $i$-ésima línea imprime cuántos sectores tienen al menos $X_i$ unidades de energía total.

## Límites

- $1 \le n \le 10^9$
- $1 \le k \le 10^5$
- $1 \le L_i \le R_i \le n$
- $1 \le E_i \le 10^9$
- $\sum E_i \le 10^9$
- $1 \le q \le 10^5$
- $1 \le X_i \le 10^9$

## Ejemplo

### Entrada
```text
5 2
3 5 1
1 4 1
3
5
1
2
```

### Salida
```text
0
5
2
```

### Entrada
```text
1000000000 2
5 50000000 1
7000000 700000000 1
1
2
```

### Salida
```text
43000001
```

### Entrada
```text
5 4
3 3 1
2 2 1
5 5 1
3 3 1
2
1
2
```

### Salida
```text
3
1
```

## Notas

### Primer ejemplo

Después de activar ambos drones, la energía de los sectores es:

$$1,\;1,\;2,\;2,\;1$$

- Ningún sector tiene al menos $5$ unidades de energía.
- Los cinco sectores tienen al menos $1$ unidad.
- Solo los sectores $3$ y $4$ tienen al menos $2$ unidades.

### Segundo ejemplo

Los dos intervalos de cobertura se traslapan desde el sector $7\,000\,000$ hasta el sector $50\,000\,000$.

Ese intervalo contiene:

$$50\,000\,000-7\,000\,000+1=43\,000\,001$$

sectores, por lo que esa es la respuesta.

### Tercer ejemplo

Cada dron protege un único sector.

- El sector $2$ recibe una unidad de energía.
- El sector $3$ recibe dos unidades.
- El sector $5$ recibe una unidad.

Por ello, hay $3$ sectores con al menos una unidad de energía y únicamente $1$ sector con al menos dos unidades.

## Temas identificados

### Programación

-

## Propuesta de solución
#### Autor:

## Implementación

```mermaid

```

### C++
#### Autor:

```cpp

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
