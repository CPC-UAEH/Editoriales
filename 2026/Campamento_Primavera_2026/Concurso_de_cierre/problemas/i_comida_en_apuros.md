https://www.cpcjudge.com/problem/comidaapuros

# I. Comida en apuros
#### Autor: Empanak

## Descripción
La primavera ha llegado a nuestro lado del mundo y con ella ha empezado esa época en la que solemos ver a la naturaleza renovarse y vemos cosas maravillosas como plantas floreciendo, abejas polinizando intensamente, muchos animales empezando a criar y algunos otros despiertan de un largo descanso.
Lamentablemente, no son todo maravillas y es que la comida se echa a perder más rápido, adquiere mal sabor, mal olor, las bacterias se reproducen mucho más rápido debido al calor y hasta crece moho. Afortunadamente alguien, el señor doctor profesor Bactriperr tiene un solución para todos estos problemas! o bueno, al menos uno de ellos.

Tras observar mucho tiempo la descomposición de la comida ha descubierto un patrón en el crecimiento de las colonias de moho y ahora necesita de tu ayuda para seguir desarrollando una solución a esto.

Bactriperr ha desarrollado un compuesto casi maravilloso capaz de acabar con todo tipo de moho y las sustancias dañinas que producen al mismo tiempo, aunque por el momento sólo funciona en líquidos y al mezclarse. Es un gran avance, el único problema es que tiene que ser aplicado en dosis demasiado exactas, poca cantidad de esta sustancia podría hacer que el moho genere resistencia y un exceso podría afectar negativamente a la comida. Bactriperr te ha contado lo mucho que le cuesta seguir el crecimiento del moho y como gran amigo y programador que eres te ofreces a desarrollar una solución que le diga **cuánto ha crecido el moho** después de cierto tiempo, así que te dice los detalles del crecimiento:

1. Una colonia puede estar compuesta de esporas, hifas jóvenes e hifas maduras al mismo tiempo.
2. Siempre aparece **una sóla** hifa joven **al inicio** de la contaminación, en el primer segundo.
3. Las **esporas se vuelven hifas jovenes al pasar un segundo**.
4. Las **hifas jovenes se vuelven hifas maduras al pasar un segundo**.
5. Cada hifa madura suelta una sola espora cada segundo** (incluído el segundo en el que madura).

Podemos determinar el **tamaño de una colonia de moho al sumar la cantidad de esporas, hifas jóvenes e hifas maduras** que hay en cierto momento.

Es una pena que aún tengamos que guardar los alimentos en el refrigerador, pero dejemos al señor doctor profesor trabajar, seguro con tu ayuda pronto resolverá este problema.

## Entrada

Un sólo número $S$ $(1 \leq S \leq 90)$ que indica el segundo en el que Bactriperr quiere obtener el tamaño de la colonia.

## Salida

Un sólo número $T$ que indica el tamaño de la colonia en el momento dado.

## Ejemplos

### Entrada
```
2
```
### Salida
```
2
```

### Entrada
```
3
```
### Salida
```
3
```

### Entrada
```
43
```
### Salida
```
701408733
```

## Notas
- En el primer ejemplo el resultado es $2$ debido a que en el primer segundo habia una hifa joven, en el siguiente segundo se convirtio en hifa madura y en el mismo segundo suelta una espora, por lo que el tamaño de la colonia es de $2$, la espora y la hifa madura.
- En el segundo ejemplo el resultado es $3$ retomando el segundo $2$ del primer ejemplo, la espora se convierte en hifa joven, y la hifa madura suelta una espora, por lo que el tamaño de la colonia es de $3$, la hifa madura, la hifa joven y la nueva espora.

## Temas identificados
### Matemáticas
- Sucesiones numéricas

### Programación
- Ciclos

## Propuesta de solución
#### Autor: Jordan

Se pueden tomar dos estrategias para resolver el problema, debido a que los límites no son grandes, sino que $N$ solo llega hasta $90$, se puede resolver haciendo un simulación tal y como se describe en la descripción, cumpliendo por cada segundo con las reglas establecidas; o se pueden hacer casos de prueba de la siguiente forma:

| segundo | espora | hifa joven | hifa madura | población |
| :-----: | :----: | :--------: | :---------: | :-------: |
| 1       | 0      | 1          | 0           | 1         |
| 2       | 1      | 0          | 1           | 2         |
| 3       | 1      | 1          | 1           | 3         |
| 4       | 2      | 1          | 2           | 5         |
| 5       | 3      | 2          | 3           | 8         |
| 6       | 5      | 3          | 5           | 13        |

Y observar que la población sigue un patrón regular, la sucesión de Fibonacci, donde el siguiente número es la suma de los dos números anteriores.

## Implementación
Para ambas estrategias, basta con usar tres variables, y ya sea siguiendo las reglas de la descripción o la regla de Fibonacci se puede llegar a la solución iterando hasta $N$.

```mermaid
graph TD;
A([Inicio]) --> B(anteriorAnterior = 0
                anterior = 1
                actual = 1)
B --> C[/segundo/]
C --> D{{Desde i = 0
            Hasta i < segundo - 1
            Incremento 1}}
D --> E(anteriorAnterior = anterior
        anterior = actual
        actual = anteriorAnterior + anterior) --> D
D --> F[\actual\]
F --> G([Fin])
```

### C++
#### Autor: Jordan

Es importante tener en cuenta los límites para el tipo de variable que se va a usar, al sumar números cada vez más grandes, existe el riesgo de que se desborden las variables, por lo que se usa **long long** para poder almacenar números de hasta $10^{19}$.

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    long long int anteriorAnterior = 0;
    long long int anterior = 1;
    long long int actual = 1;

    int segundo;
    cin >> segundo;

    for (int i = 0; i < segundo - 1; i++) {
        anteriorAnterior = anterior;
        anterior = actual;
        actual = anteriorAnterior + anterior;
    }

    cout << actual;

    return 0;
}
```

```cpp
#include <bits/stdc++.h>

using namespace std;

struct segundo
{
    long long int esporas;
    long long int jovenes;
    long long int maduras;
};

segundo s[100];

int main() {
    cin.tie(0); ios::sync_with_stdio(false);
    
    int n;
    cin >> n;
    s[0].jovenes++;

    for (int i = 1; i <= n; i++) {
        s[i].maduras = s[i - 1].maduras;
        s[i].maduras += s[i - 1].jovenes;

        s[i].jovenes += s[i - 1].esporas;
        s[i].esporas += s[i].maduras;
    }

    long long int t = s[n - 1].esporas + s[n - 1].jovenes + s[n - 1].maduras;

    cout << t;

    return 0;
}
```
