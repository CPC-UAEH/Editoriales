https://www.cpcjudge.com/problem/noloentenderias

# 26P2D3. no lo entenderias, es aesthetic
#### Autor: xenredda

## Descripción
Melisa, es una estudiante de artes visuales que está preparando a contrareloj su nueva exposición inspirada en la primavera. Para inspirarse y entrar en un verdadero trance artístico, le encanta pintar su lienzo primaveral mientras escucha música a todo volumen. Curiosamente, las flores y mariposas le quedan mucho mejor cuando tiene en repetición a Fiona Apple, Bjork o un poco de Kanye West.

Toda esta mezcla musical la pone tan eufórica que, al invitar a sus amigos a la galería por mensaje de texto, su intensidad artística se sale de control. Cuando escribe la palabra "FLOR" en el chat, le gusta alargar la letra "O" para demostrar gráficamente cuánta emoción (y cuánta música) lleva encima. Su nivel de intensidad musical se mide con un número entero $E$, que equivale a la cantidad de canciones que escuchó mientras pintaba.

Tu tarea es ayudar a Melisa a generar su mensaje de spam creando la palabra "**FLOR**", pero repitiendo la letra "**O**" exactamente $E$ veces.

## Entrada
La entrada consiste en una sola línea con un número entero $E$ $(1 \le E \le 100)$, que representa el nivel de intensidad musical de Melisa (el número de canciones que escuchó).

## Salida
Imprime la cadena de texto comenzando con "FL", seguida de exactamente $E$ letras "**O**" mayúsculas, y terminando con la letra "R". Todo debe estar en una sola línea y sin espacios.

Melisa Mendoza — **Práctica 8**, 2026.
      Acrílico sobre MDF, 20 × 30 cm.
      Obra realizada por Melisa durante su etapa de máxima intensidad musical.

## Ejemplo

### Entrada
```
1
```
### Salida
```
FLOR
```

### Entrada
```
5
```
### Salida
```
FLOOOOOR
```

### Entrada
```
10
```
### Salida
```
FLOOOOOOOOOOR
```

## Notas
- En el primer ejemplo, la intensidad es 1, así que solo se imprime una "O", que es la forma ortográficamente correcta.
- En el segundo ejemplo, la intensidad es 5 tras un buen rato de inspiración musical, así que debes imprimir 5 letras "O" seguidas justo antes de la "R".

## Temas identificados
### Matemáticas
- Ninguno

### Programación
- Ciclos
- Cadenas de texto
- Entrada y salida estándar

## Propuesta de solución
#### Autor: mae
El problema nos pide construir una palabra a partir de un número entero $E$.

La palabra siempre debe comenzar con "FL" y terminar con "R", pero la cantidad de letras "O" que aparecen entre ambas partes depende del valor de $E$.

Por ejemplo:
- E = 1  -> FLOR
- E = 3  -> FLOOOR
- E = 5  -> FLOOOOOR

La forma más sencilla de resolverlo es crear una cadena inicial con el texto "FL" y después agregar una letra "O" exactamente $E$ veces mediante un ciclo.
Una vez agregadas todas las letras necesarias, solo queda imprimir la cadena seguida de la letra "R".

## Implementación
Se utiliza una variable de tipo string para almacenar el resultado.

Primero se inicializa la cadena con "FL". Después, mediante un ciclo for, se agrega una letra "O" en cada iteración hasta completar la cantidad indicada por $E$.

Finalmente, se imprime la cadena construida y se agrega la letra "R" al final.

```mermaid
graph TD;
A([Inicio]) --> B[/e/]
B --> C(s = &quot;FL&quot;)
C --> D{{Desde i = 0
            Hasta i < e
            Incremento 1}}
D --> E(s = s + &quot;O&quot;)
E --> D
D --> F[\s + &quot;R&quot;\]
F --> Z([Fin])
```

### C++
#### Autor: mae

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    string s = "FL";
    int e;
    cin >> e;

    for (int i = 0; i < e; i++){
        s += "O";
    }
    cout << s << "R";

    return 0;
}

```
