https://www.cpcjudge.com/problem/abejas

# 26P2C5. Abejas
#### Autor: Soria

## Descripción
*"Si el sol está solificándose y la luna vive lunizándose..."*

Honey, entre una de sus mil labores, debe monitorear al pelotón polinizador de la colmena escogido por la abeja reina. Para esto, se dispone de $N$ abejas con sus respectivos *rangos polinizadores*. El rango polinizador indica el desempeño de una abeja. También existen rangos negativos porque algunas abejas no están tan experimentadas para las misiones del día de hoy, por lo que tenerlas en el pelotón puede significar una carga porque deben ser capacitadas para las flores encargadas.

Existirán $Q$ misiones, para las cuales el pelotón escogido por la reina serán las abejas dentro del intervalo *[L, R]*. Para Honey es importante tener una gran eficacia a la hora de polinizar, por lo que ella filtrará el pelotón polinizador realizando dos tipos de operaciones sobre él:
-Remover a la abeja colocada al principio del pelotón.
-Remover a la abeja colocada al final del pelotón.

Honey puede realizar las operaciones la cantidad de veces que sea necesaria para **maximizar** la suma de los rangos del pelotón actual, incluso si esto significa dejar al pelotón vacío, haciendo que ella se encargue sola de la misión. Después de que el pelotón realice su trabajo, todas las abejas vuelven a sus posiciones preparadas para la siguiente misión.

Por cada una de las misiones, responde cuál es la suma de los rangos del pelotón después de que Honey realice el filtrado.

## Entrada
Dos enteros $N$ y $Q$ $(1 \leq N, Q \leq 2*10^5)$, la cantidad de abejas, y la cantidad de misiones respectivamente.

Seguido por $N$ enteros $A_1, A_2, A_3, ..., A_N$, donde $(-10^9 \leq A_i \leq 10^9)$ indica el rango de la abeja $i$.

Seguido por $Q$ líneas conformadas por dos enteros $L$ y $R$, donde $(1 \leq L \leq R \leq N)$ indica el intervalo escogido por la abeja reina.</p>

## Salida
$Q$ enteros, la suma de los rangos después del filtrado.

## Ejemplo

### Entrada
```
8 4
2 5 1 -2 3 -1 -7 1
2 4
2 5
6 7
4 8
```
### Salida
```
6
7
0
3
```

## Notas
En la primera misión, Honey puede eligir quitar a la abeja del final del pelotón, dejando una suma de $5 + 1 = 6$.

En la segunda misión, Honey deja el pelotón tal cual como fue elegido.

En la tercera misión, Honey vacía el pelotón, haciendo que la suma sea de $0$.

## Temas identificados
### Matemáticas
- 

### Programación
- 

## Propuesta de solución
#### Autor: 


## Implementación


### C++
#### Autor: 

```cpp

```
