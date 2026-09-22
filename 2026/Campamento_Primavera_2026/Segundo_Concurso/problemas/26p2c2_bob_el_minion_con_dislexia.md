https://www.cpcjudge.com/problem/bobminiondislexia

# 26P2C2. Bob, el minion con dislexia
#### Autor: wisperfrog

## Descripción
Bob, el pequeño minion, empezó a ir a la escuela con Agnes y aprendió a escribir textos en español. Escribe sobre perros, sobre zapatos, sobre árboles, sobre la Segunda Guerra Mundial, etc. Y un día, en la escuela le encomendaron hacer varios textos sobre la primavera, los cuales iba a presentar en cada una de sus clases.

Bob escribió el primero de sus textos y lo llevó a clase pero, cuando lo estaba leyendo (no habla español solo lo escribe), se dio cuenta que escribió mal varias palabras debido a la dislexia. Las palabras que escribió mal fueron:

- cilma por clima
- birsa por brisa
- calro por calor
- homirga por hormiga
- abrol por arbol

Como Bob no quiere pasar vergüenza de nuevo con un texto mal escrito, te pidió ayuda para que corrijas su próximo texto. Para corregir el texto de Bob, si una palabra coincide **exactamente** con alguna de las ya descritas, ésta deberá ser corregida.

Bob aún no aprende a escribir letras mayúsculas ni acentos, entonces **todo el texto está escrito en letras minúsculas y sin acentos**.

¿Puedes ayudar a Bob?

## Entrada
En la primera línea un entero $N$ $(1 \leq N \leq 100)$, la cantidad de líneas del texto de Bob.

En las siguientes $N$ líneas una cadena $C_i$ $(1 \leq |C_i| \leq 100)$, la $i-ésima$ línea del texto registrada.

Se garantiza que las cadenas no inician ni terminan con espacios. Las palabras de una cadena están separadas por espacios.

Después de leer $N$, escribe ```cin.ignore();```.

Para leer una línea de texto (texto con espacios) utiliza ```getline(cin, tu_variable_string);```.

## Salida
El texto de Bob corregido.

## Ejemplo

### Entrada
```
3
la homirga oh la homirgaa la quiero mucho
no se como le hace para soportar este calro
lo bueno es que puede vivir bajo un abrol
```
### Salida
```
la hormiga oh la homirgaa la quiero mucho
no se como le hace para soportar este calor
lo bueno es que puede vivir bajo un arbol
```

### Entrada
```
4
en mi casa hay un abrol grande
y una vez vi una ardilla en el
y cuando me acerque
se cayo
```
### Salida
```
en mi casa hay un arbol grande
y una vez vi una ardilla en el
y cuando me acerque
se cayo
```

### Entrada
```
3
las flores son bonitas
pero me gustan mas
los dorilocos con cueritos uf papoi
```
### Salida
```
las flores son bonitas
pero me gustan mas
los dorilocos con cueritos uf papoi
```

## Temas identificados
### Programación
- Ciclos
- Condicionales
- Manejo de cadenas

## Propuesta de solución
#### Autor: Jordan

Observamos que hay un diccionario especifico de palabras mal escritas que hay que corregir, por lo que solo necesitamos separar las palabras de cada frase, reconocer que se encuentra en nuestro diccionario y reemplazarla, para separar las palabras lo idea sería que no hubiera signos de puntuación como comas, puntos, punto y coma, signos de interrogación o admiración, como lo es en este caso, por lo que basta con separar las palabras por espacios.

## Implementación
Si ya tenemos la frase completa en una cadena, debemos agregar un espacio al final, para después recorrer caracter por caracter, si es una caracter cualquiera lo concatenamos en una variable string, que comienza vacía, que nos va a servir para generar cada palabra caracter por caracter, en caso de que el caracter actual sea un espacio, entonces podemos identificar si la palabra hasta el momento es igual que alguna de las de nuestro diccionario, si lo es, sobreescribimos la variable palabra, si no, la variable palabra se queda tal cual está y se concatena en una variable de respuesta que nos va a servir para generar la frase completa corregida, concatenamos un espacio después de cada palabra y reseteamos la variable palabra. 

Finalmente, cuando se acaben los caracteres en la cadena original, tendremos la frase corregida completa y la imprimimos con un salto de línea al final.

### C++
#### Autor: Jordan

Después de obtener la cantidad de frases es necesario escribir la instrucción ```cin.ignore```.

Podemos leer la frase completa con ```getline(cin, tu_variable_string)``` que puede leer toda la frase en una sola cadena, incluyendo los espacios, solo se detiene cuando hay un salto de línea, contrario a usar solo ```cin``` porque separa las entradas según los espacios.

En C++, los strings son vectores, por lo que podemos ocupar métodos como ```push_back()```, además podemos comparar cada posición con un ```char``` y recorrer todos los caracteres de la cadena con un ciclo for each sin necesidad de saber cuantos caracteres tenemos.

Para poder tener un bloque de entradas y un bloque de salidas, se usan las líneas:
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```

```cpp
#include <bits/stdc++.h>

using namespace std;

int main()
{
    cin.tie(0); ios::sync_with_stdio(false);

    int n;
    cin >> n;
    cin.ignore();
    for (int i = 0; i < n; i++) {
        string r;
        string s;
        getline(cin, s);
        s.push_back(' ');
        string p;
        for (auto c : s) {
            if (c == ' ') {
                if (p == "cilma") {
                    p = "clima";
                }
                if (p == "birsa") {
                    p = "brisa";
                }
                if (p == "calro") {
                    p = "calor";
                }
                if (p == "homirga") {
                    p = "hormiga";
                }
                if (p == "abrol") {
                    p = "arbol";
                }
                for (auto cc : p) {
                    r.push_back(cc);
                }
                r.push_back(' ');
                p = "";
            } else {
                p.push_back(c);
            }    
        }
        cout << r << '\n';   
    }

    return 0;
}
```
