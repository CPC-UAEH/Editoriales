https://omegaup.com/arena/problem/ofmi-2026-asteroides/

# Destruyendo asteroides
#### Autor: Ethan Jiménez

## Descripción

La Organización Federal de Misiones Interplanetarias (OFMI) ha detectado un cinturón de asteroides que representa un riesgo para futuras misiones en la zona. Para garantizar la seguridad de los drones que navegan por ahí, la OFMI ha desplegado una nave equipada con un cañón de antimateria para destruir todos los asteroides.

Existen $n$ asteroides en el cinturón, convenientemente numerados del $1$ al $n$. Para destruir el $i$-ésimo asteroide con masa de $M_i$ toneladas, el cañón debe tener una carga de antimateria de al menos $M_i$ toneladas. Después de destruirlo, la nave recolecta su materia y la carga del cañón de antimateria aumenta en $M_i$ toneladas.

Por ejemplo, si el cañón tiene una carga de antimateria de $10$ toneladas, puede destruir un asteroide de $7$ o $10$ toneladas, pero no uno de $11$. Si en este mismo ejemplo, el cañón de $10$ toneladas destruyera un asteroide de $7$ toneladas, la carga de antimateria incrementaría a $17$ toneladas.

Antes de comenzar la misión, la nave debe cargar antimateria. La división de suministros de la OFMI tarda exactamente una hora en cargar una tonelada de antimateria a la nave. Afortunadamente, todos los asteroides se encuentran dentro del campo de visión de la nave, por lo que **es posible decidir el orden en que serán destruidos**.

## Problema

Dado el número de asteroides y la lista de sus masas, determina la **menor carga inicial de antimateria** necesaria para destruirlos a todos.

## Entrada

La primera línea contiene un entero $n$, representando el número de asteroides.

La segunda línea contiene $n$ enteros, donde el $i$-ésimo entero representa la masa $M_i$ del $i$-ésimo asteroide.

## Salida

Imprime un solo entero representando la menor cantidad de antimateria inicial necesaria para destruir todos los asteroides.

## Límites

- $1 \le n \le 10^5$
- $1 \le M_i \le 10^9$
- $\sum M_i \le 10^9$

## Ejemplo

### Entrada
```text
2
10 8
```

### Salida
```text
8
```

### Entrada
```text
5
1 16 6 3 30
```

### Salida
```text
6
```

## Notas

### Primer ejemplo

Hay dos asteroides con masas $10$ y $8$.

Si la nave comienza con $8$ toneladas de antimateria, puede destruir primero el asteroide de masa $8$, aumentando su carga a $16$, suficiente para destruir el de masa $10$.

### Segundo ejemplo

Los asteroides tienen masas $1$, $16$, $6$, $3$ y $30$.

Con una carga inicial de $5$ toneladas es posible destruir los asteroides de masas $1$, $6$ y $3$, alcanzando una carga de $15$, insuficiente para destruir el asteroide de masa $16$.

Sin embargo, con una carga inicial de $6$ toneladas, después de destruir esos mismos tres asteroides se alcanza una carga de $16$, permitiendo destruir el resto.

## Temas identificados

### Programación
- Ordenamiento
- Búsqueda binaria sobre la respuesta
- Simulación
- Greedy

## Propuesta de solución
#### Autor: Jordan

Necesitamos encontrar la carga mínima posible pero que sea capaz de destruir todos los asteroides, para eso necesitamos elegir un número, y recorrer la lista de asteroides identificando si la suma de la carga inicial más el elemento actual es mayor o igual que el siguiente elemento, si es mayor o igual significa que si lo podemos destruir el siguiente asteroide y continuamos con la simulación, si en algun punto es falso, significa que el número elegido fue muy pequeño, y si se pude completar toda la simulación sin fallas, puede significar que el número escogido fue demasiado grande.

Para escoger un número podemos usar una búsqueda binaria sobre resultado, donde buscamos la frontera entre que sí se pudo destruir todo y que no fue suficiente carga para destruir todo.

## Implementación

Primero leemos y almacenamos los asteroides en un arreglo, ordenamos el arreglo de menor a mayor, y ajustamos los límites de la búsqueda binaria a ser L igual al primer elemento, R igual al último elemento, pues sabemos que siempre el mínimo necesario será el primer elemento, sino, nunca podríamos destruir ningún asteroide, y el máximo posible será menor que el último elemento.

Podemos ocupar una variable booleana para marcar si se logró acabar toda la simulación o falló en algún momento, en base a eso recortamos los límites.

### C++

#### Autor: Jordan
```cpp
#include <bits/stdc++.h>

using namespace std;

int a[100005];

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    int n;
    cin >> n;

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    sort(a, a + n);

    int l = a[0], r = a[n - 1], m, anti;
    bool b;

    while (l <= r) {
        m = (l + r) / 2;
        b = true;
        int carga = m;
        for (int i = 0; i < n - 1; i++) {
            carga += a[i];
            if (carga < a[i + 1]) {
                b = false;
                break;
            }
        }
        if (b) {
            anti = m;
            r = m - 1;
        } else {
            l = m + 1;
        }
    }

    cout << anti;
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
