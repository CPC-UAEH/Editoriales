https://www.cpcjudge.com/problem/carlosysandroprimave

# 26P2C4. El Misterio de la Carta Primaveral
### Autor: Kaarlarax

## Descripción
Durante las cálidas tardes de primavera, Sandro y Carlos aprovechan el clima para entrenar al aire libre. Sus días comienzan con horas de algoritmos y código, por lo que pronto terminan exhaustos. Para darle un descanso a sus mentes y disfrutar de la brisa primaveral bajo los árboles, les gusta jugar a las cartas en sus ratos libres.

El juego de cartas que inventaron funciona de la siguiente manera:

El valor de una carta se define por su primer carácter. Si muestra un dígito entre el $2$ y el $9$, ese es su valor. De lo contrario (cartas cuyo primer carácter es T, J, Q, K, A), su valor es $10$. Inicialmente, se tiene un mazo de $52$ cartas boca abajo.

- Toman las $25$ cartas superiores del mazo y las guardan en su mano.
- Establecen una variable $Y = 0$.
- Luego, ejecutan el siguiente proceso exactamente tres veces:
  - Toman la carta superior del mazo restante y determinan su valor. Sea $X$ el valor de esta carta.
  - Suman $X$ a $Y$.
  - Descartan esta carta junto con las siguientes $(10 - X)$ cartas de la parte superior del mazo.
- Finalmente, toman las $25$ cartas que tenían guardadas en la mano y las vuelven a colocar en la parte superior del mazo.

El objetivo del juego es determinar cuál es la $Y-ésima$ carta del mazo, contando desde abajo hacia arriba.

Sandro y Carlos conocen el orden inicial de las cartas antes de empezar, por lo que asumen que pueden deducir mentalmente cuál es la $Y-ésima$ carta sin mirar el mazo. Sin embargo, con el cansancio de la primavera, a menudo se equivocan. ¡Tu tarea es escribir un programa que encuentre la carta correcta por ellos!

## Entrada
En la primera línea un entero $Q$ $(1 \le Q \le 1000)$, el número de casos de prueba.

Cada caso de prueba consta de $52$ cartas separadas por espacios, representando el orden inicial del mazo **desde la parte inferior hasta la parte superior**.

El formato de cada carta es una cadena de $2$ caracteres: el primer carácter indica el valor ($2-9$, T, J, Q, K, A) y el segundo carácter indica el palo (C, D, H, S).

## Salida
Para cada caso de prueba, imprime la carta objetivo (la $Y-ésima$ carta desde la parte inferior).

## Ejemplo

### Entrada
```
2
AC KC QC JC TC 9C 8C 7C 6C 5C 4C 3C 2C AD KD QD JD TD 9D 8D 7D 6D 5D 4D 3D 2D AH KH QH JH TH 9H 8H 7H 6H 5H 4H 3H 2H AS KS QS JS TS 9S 8S 7S 6S 5S 4S 3S 2S
AC KC QC JC TC 9C 8C 7C 6C 5C 4C 3C 2C AD KD QD JD TD 9D 8D 7D 6D 5D 4D 3D 2D AH KH QH JH TH 9H 8H 7H 6H 5H 4H 3H 2H AS KS QS JS TS 9S 8S 7S 6S 5S 4S 3S 2S

```
### Salida
```
8H
8H
```

## Temas identificados
### Matemáticas
- Simplificación
- Sustitución
- Álgebra
- Adhoc

### Programación
- Ciclos
- Condicionales
- Estructuras de datos

## Propuesta de solución
### Autor: Jordan

Se pueden tomar dos estrategias, la primera, más difícil de programar pero más fácil de entender es seguir los pasos de la descripción, debido a que por caso son $52$ cartas siempre, y solo se llega hasta 1000 casos, hacer una simulación entra en tiempo perfectamente.

La segunda estrategia requiere identificar y desarrollar algebraicamente la abstracción matemática del problema como se describe a continuación:

- Primero se toman las 52 cartas, y se retiran las 25 cartas superiores, por lo que haremos nuestro proceso con las primeras 27 cartas, donde la primera que entró es la que se encuentra abajo en el mazo.
- Se toma la carta superior y se lee el número, si es $A$, $T$, $Q$, $K$, $J$, equivale a $10$, y se le denomina $x_i$. Este paso se hace $3$ veces, por lo que al final de la operación tenemos $x_1$, $x_2$ y $x_3$.
- El proceso requiere sumar los tres números obtenidos en una variable $Y$ que comienza con valor $0$. Al final de este proceso, $Y$ equivale a ($x_1 + x_2 + x_3$).
- Este mismo proceso requiere que por cada iteración se haga la operación ($10 - x_i$), y el resultado es la cantidad de cartas que vamos a descartar de la parte superior del mazo, además de descartar la carta consultada.

En resumen, hasta este punto ya podemos hacer el desarrollo con las expresiones encontradas que son:

- El índice del mazo que vamos a consultar después de añadir las 25 cartas que habiamos apartado: $Y=x_1+x_2+x_3$
- La cantidad de cartas que se descartaron durante el proceso: ${[(10-x_1)+1]+[(10-x_2)+1]+[(10-x_3)+1]}$

Podemos simplificar la cantidad de cartas descartadas a ${(11-x_1)+(11-x_2)+(11-x_3)}$, luego a ${33-(x_1+x_2+x_3)}$, donde observamos que es posible sustituir la variable $Y$ en la cantidad de cartas descartadas, de la siguiente forma:

$33-Y$

Ahora, sabemos que tenemos un mazo de $27$ cartas de donde vamos a descartar $33-Y$ cartas, y se puede representar como:

${27-(33-Y)=Y-6}$

Donde ahora sabemos que el índice a consultar después de descartar $33-Y$ cartas está en la posición $Y-6$, por lo tanto, tras añadir las 25 cartas que habiamos apartado, el índice que queremos imprimir será $Y$ tras haber restado la cantidad de cartas descartadas, que es $Y-6$.

${Y-(Y-6)=6}$

Por lo que ahora sabemos que la posición $6$ del mazo de 25 cartas es la solución al problema, así que de un total de 52 cartas, el índice que nos da la respuesta es $27+6=33$.

Finalmente vemos que, la posición 33 de cualquier caso nos da la solución correcta.

## Implementación
Para la simulación, se requiere usar varios ciclos for, pero al ser solo 52 cartas, y solo 1000 tareas, además de que las operaciones son finitas, incluso los ciclos anidados tres veces no suponen un riesgo de rendimiento. La idea es que para evitar hacer acciones repetitivas, solamente se lean las primeras 27 cadenas, se haga el proceso, se acumulen las $x_i$ en una variable $Y$, luego se lean el resto de cadenas en frente de la lista ya procesada, y se imprima finalmente el índice $Y$.

Para el desarrollo algebraico solo hay que imprmir la posición $33$.

```mermaid
graph TD;
A([Inicio]) --> B[/q/]
B --> M{{Desde i = 0
		Hasta i < q
		Incremento 1}}
M --> C{{Desde j = 0
		Hasta j < 52
		Incremento 1}}
C --> D[/carta/]
D --> E{j == 33}
E --V--> F[\carta\]
E --F--> G((" "))
F --> G
G --> C
C --> M
B --> Z([Fin])
```

### C++
Para mantener un bloque claro de entradas y un bloque de salidas, se utilizan las siguientes instrucciones, que pausan la salida hasta que se hacen todas las entradas:
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```

Estrategia de la simulación:
```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

	int q;
	cin >> q;

	for (int i = 0; i < q; i++) {
        int y = 0;
        vector<string> mazo;
        for (int j = 1; j <= 27; j++) {
            string s;
            cin >> s;
            mazo.push_back(s);
        }
        for (int j = 0; j < 3; j++) {
            int num = mazo.back()[0] == 'A' ||
                           mazo.back()[0] == 'J' ||
                           mazo.back()[0] == 'K' ||
                           mazo.back()[0] == 'Q' ||
                           mazo.back()[0] == 'T'? 10 : mazo.back()[0] - '0';
            for (int k = 1; k <= 11 - num; k++) {
                mazo.pop_back();
            }
            y += num;
        }
        for (int j = 1; j <= 25; j++) {
            string s;
            cin >> s;
            mazo.push_back(s);
        }
        cout << mazo[y - 1] << '\n';
	}
}
```

Estrategia de desarrollo algebraico:
```cpp
#include <bits/stdc++.h>

using namespace std;

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

	int q;
	cin >> q;

	for (int i = 0; i < q; i++) {
        for (int i = 1; i <= 52; i++) {
            string carta;
            cin >> carta;
            if (i == 33) {
                cout << carta << '\n';
            }
        }
	}
}
```
