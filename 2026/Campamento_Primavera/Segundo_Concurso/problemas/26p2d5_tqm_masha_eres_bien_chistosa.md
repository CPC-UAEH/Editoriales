https://www.cpcjudge.com/problem/masha

# 26P2D5. Tqm Masha, eres bien chistosa
#### Autor: wisperfrog

## Descripción
Oso tuvo una visión. Él cree que si planta demasiados árboles, cuando estos crezcan, albergarán muchos panales de abejas y así tendrá miel casi infinita. Así entonces, Oso fue a la ciudad y compró muchísimas semillas de árbol. Llegó a casa y cuando estaba por entrar resbaló con uno de los juguetes de Masha y las semillas estaban regadas por todas partes.

Masha estaba durmiendo, pero la caída de Oso fue tan aparatosa que la despertó. Masha salió y, al ver todo el desastre que había provocado uno de sus juguetes, quiso ayudar a Oso solo por $N$ segundos porque quería seguir durmiendo, pero había un problema: **Masha seguía encamorrada**.
  
En un segundo, Masha recogió $X$ semillas, pero al siguiente segundo, Masha se durmió y tiró $X$ semillas; un segundo después, recogió $X$ semillas nuevamente, después tiró $X$ semillas y así sucesivamente por $N$ segundos.

Mientras Oso se recupera de la caída, tu tarea es indicar cuántas semillas recogió Masha al final de los \(N\) segundos.

## Entrada
En la primera línea un entero $T$ $(1 \leq T \leq 1000)$, la cantidad de casos.

En las siguientes $T$ líneas, dos enteros $X$ y $N$ $(1 \leq X, N \leq 10^6)$, la cantidad de semillas que recoge/tira y los segundos que ayudará Masha, respectivamente.

Cada caso es independiente.

## Salida
Para cada caso, imprimir la cantidad de semillas que recogió Masha.

## Ejemplo

### Entrada
```
4
2 3
1 4
3 6
4 7
```
### Salida
```
2
0
0
4
```

## Notas
En el primer caso, ocurre lo siguiente:
- Segundo $1$: Masha recoge $2$ semillas, lleva $2$
- Segundo $2$: Masha cabecea y tira $2$ semillas, lleva $0$
- Segundo $3$: Masha recoge $2$ semillas, lleva $2$

Masha recogió $2$ semillas en total.

## Temas identificados
### Matemáticas
- Módulo

### Programación
- Ciclos
- Condicionales

## Propuesta de solución
#### Autor: Jordan

Este es un clásico problema de "lo que te describimos, eso no es", porque realmente, no nos importa lo que pasa en cada segundo, porque cada operación se cancela con la siguiente, como se menciona en la descripción, la respuesta oscila entre $0$ y $x$. Solo hay que notar que en los segundos impares lleva $x$ semillas, y en los segundos pares lleva $0$ semillas.

La respuesta depende de si el ultimo segundo es par o impar.

## Implementación
Por cada caso podemos leer las semillas y los segundos, comprobar si el último segundo es par o impar con el módulo de $2$; si segundos es impar la respuesta es $x$, si segundos es impar, la respuesta es $0$.

```mermaid
graph TD;
A([Inicio]) --> B[/casos/]
B --> C{{Desde i = 0
        Hasta i < casos
        Incremento 1}}
C --> D[/semillas, segundos/]
D --> E{segundos % 2 == 1}
E --V--> F[\semillas\]
E --F--> G[\0\]
F --> X((" "))
G --> X
X --> C
C --> Z([Fin])
```

### C++

#### Autor: mae
```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    int casos;
    cin >> casos;
    for (int i = 0; i < casos; i++) {
        int semillas, segundos;
        cin >> semillas >> segundos;

        if (segundos % 2 == 1) {
            cout << semillas << '\n';
        } else {
            cout << 0 << '\n';
        }
    }
    
    return 0;
}
```
