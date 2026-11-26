https://omegaup.com/arena/problem/ofmi-2026-constelaciones/

# Constelaciones
#### Autor: Alondra Valdivia Sánchez

## Descripción

La Organización Federal de Misiones Interplanetarias (OFMI) mantiene un gigantesco archivo con información sobre constelaciones observadas en distintos sistemas estelares. En estos registros, cada estrella está conectada con otras estrellas mediante líneas imaginarias que las astrónomas utilizan para identificar patrones.

Recientemente, un observatorio espacial descubrió un nuevo sistema estelar conformado por $n$ estrellas, las cuales identificó con índices del $1$ al $n$. Durante la transmisión de datos proveniente del observatorio, parte de la información sobre las constelaciones de este sistema se perdió debido a una interferencia cósmica. El mapa exacto de conexiones entre estrellas desapareció, pero afortunadamente algunos datos lograron recuperarse.

Para cada estrella se conoce cuántas conexiones tenía originalmente con otras estrellas dentro del sistema estelar. Cada conexión une exactamente dos estrellas distintas y las conexiones son **bidireccionales**. Es decir, si la estrella $U$ está conectada con la estrella $V$, entonces $V$ también está conectada con $U$.

Además, no puede haber más de una conexión entre el mismo par de estrellas. En otras palabras, cualquier par de estrellas tiene a lo más una conexión entre ellas.

La última tarea que te ha asignado la división de cómputo y análisis de la OFMI es ayudarles a reconstruir el archivo de constelaciones del nuevo sistema estelar utilizando la información que pudo recuperarse.

## Problema

Dado el número de estrellas y el número de conexiones que tenía cada una de ellas, debes reconstruir un posible conjunto de conexiones que sea consistente con la información recuperada.

Las conexiones deben cumplir que:

- Cada estrella tiene exactamente el número de conexiones especificado.
- No existen conexiones entre una estrella y sí misma.
- No existen conexiones repetidas entre el mismo par de estrellas.

Se garantiza que siempre existe al menos una solución válida.

## Entrada

La primera línea contiene un entero $n$, representando el número de estrellas.

La segunda línea contiene $n$ enteros, donde el $i$-ésimo entero representa el número de conexiones $D_i$ que tenía la estrella $i$.

## Salida

En la primera línea imprime un entero $m$, representando el número de conexiones del sistema.

En las siguientes $m$ líneas imprime dos enteros $U_j$ y $V_j$, indicando que existe una conexión entre las estrellas $U_j$ y $V_j$.

Si existen varias respuestas válidas, puedes imprimir cualquiera.

## Límites

- $1 \le n \le 10^5$
- $0 \le D_i \le n-1$
- $\sum D_i \le 5 \times 10^5$

## Ejemplo

### Entrada
```text
4
2 1 1 2
```

### Salida
```text
3
4 1
4 3
2 1
```

### Entrada
```text
5
1 3 1 1 0
```

### Salida
```text
3
2 4
2 3
2 1
```

## Notas

### Primer ejemplo

Una posible reconstrucción es:

- La estrella $1$ se conecta con las estrellas $2$ y $4$.
- La estrella $2$ se conecta con la estrella $1$.
- La estrella $3$ se conecta con la estrella $4$.
- La estrella $4$ se conecta con las estrellas $1$ y $3$.

Cada estrella tiene exactamente el número de conexiones indicado.

### Segundo ejemplo

Una posible reconstrucción es:

- La estrella $2$ se conecta con las estrellas $1$, $3$ y $4$.
- Las estrellas $1$, $3$ y $4$ tienen exactamente una conexión.
- La estrella $5$ no tiene conexiones.

## Temas identificados

### Programación

-

## Propuesta de solución
#### Autor:

## Implementación

```mermaid

```

### C++
#### Autor: Jordan


Respuesta correcta solo para el 14% de los casos, entra en tiempo, veredicto WA
```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    int n;
    cin >> n;
    vector<pair<int,int>> a;
    list<pair<int,int>> conexiones;
    int c = 0;

    for (int i = 0; i < n; i++) {
        int aux;
        cin >> aux;
        a.emplace_back(aux, i);
    }
    sort(a.begin(), a.end());
    reverse(a.begin(), a.end());

    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (a[i].first > 0) {
                if (a[j].first > 0) {
                    c++;
                    conexiones.push_back({a[i].second + 1, a[j].second + 1});
                    a[i].first--;
                    a[j].first--;
                }
            } else {
                break;
            }
        }
    }

    cout << c << '\n';
    for (auto [f, s] : conexiones) {
        cout << f << " " << s << '\n';
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
