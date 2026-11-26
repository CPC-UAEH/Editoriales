https://www.cpcjudge.com/problem/stuartminiondislexia

# M. Stuart, el otro minion con dislexia
#### Autor: wisperfrog

## Descripción
Stuart, el hermano de Bob, empezó a ir a la misma escuela que él y aprendió a escribir textos en español. Como le dejaban la misma tarea que Bob, debía hacer varios textos sobre la primavera.

Stuart escribió el primero de sus textos y fue más inteligente que Bob, porque prefirió revisar sus textos antes de llevarlos a clase, sin embargo, resultó que Stuart escribe peor que Bob...

Stuart posee una dislexia severa, esto significa que no tiene errores mínimos, sino que reorganiza las letras de una palabra de forma aleatoria. Las palabras que Stuart escribe mal son las siguientes:

- nube
- queso
- libro
- mesa
- lapiz

Por ejemplo, si Stuart quiere escribir nube, puede escribir "nube", "unbe", "enbu", "uenb", etc... En todos esos casos, deberás corregirlo a "nube".

Así con las demás palabras que escribe mal.

Como Stuart no quiere pasar vergüenza presentando un texto mal escrito, te pidió ayuda para que corrijas su próximo texto.

Stuart tampoco ha aprendido a escribir letras mayúsculas ni acentos, entonces **todo el texto está escrito en letras minúsculas y sin acentos**.

¿Puedes ayudar a Stuart? 😈

## Entrada
En la primera línea un entero $N$ $(1 \leq N \leq 100)$, la cantidad de líneas del texto de Stuart.

En las siguientes $N$ líneas una cadena $C_i$ $(1 \leq |C_i| \leq 100)$, la $i$ - $ésima$ línea del texto registrada.

Se garantiza que las cadenas no inician ni terminan con espacios. Las palabras de una cadena están separadas por espacios.

Después de leer $N$, escribe ***cin.ignore();***.
Para leer una línea de texto (texto con espacios) utiliza ***getline(cin, tu_variable_string)***;.

## Salida
El texto de Stuart corregido.

## Ejemplos

### Entrada
```
2
bob te quiero pero
me perdiste mi lpiza
```
### Salida
```
bob te quiero pero
me perdiste mi lapiz
```

### Entrada
```
4
bob mi lapiz donde esta
quiero mi pizla por favor
tengo que contestar mi birlo
de ingles bro
```
### Salida
```
bob mi lapiz donde esta
quiero mi lapiz por favor
tengo que contestar mi libro
de ingles bro
```

### Entrada
```
4
deje el sequo sobre la sema
y mi orlib en la silla
ahora no encuentro mi ueoqs
ni mi ibrol ni mi silla
```
### Salida
```
deje el queso sobre la mesa
y mi libro en la silla
ahora no encuentro mi queso
ni mi libro ni mi silla
```

## Temas identificados
### Programación
- Ciclos
- Manejo de cadenas
- Condicionales
- Vector

## Propuesta de solución
#### Autor: Jordan

En este problema, el diccionario de palabras que pueden escribirse mal son muy pocas, y todas comparten una característica, por cada palabra, hay exactamente una vez cada letra, y cada palabra tiene letras distintas que el resto de palabras, por lo que podemos decir que para la palabra "**nube**", si hay exactamente una "**n**", una "**u**", una "**b**" y una "**e**" y la cantidad total de letras es ***4***, entonces podemos asegurar que se trata de una de las posibles combinaciones mal escritas de la palabra "nube", por lo que la podemos corregir por la palabra "**nube**", y así para el resto de palabras.


## Implementación
Se pueden tomar dos estrategias que siguen el mismo principio, una estática y una dinámica.

Al inicio tenemos que leer cada frase completa y añadirle un espacio al final para poder usar la misma condición, de forma que cada que aparezca un espacio sabemos que ya acabó una palabra.

Vamos a recorrer la frase completa, caracter por caracter. Si el caracter actual no es un espacio, registramos que apareció esa letra, lo concatenamos en una palabra que comienza vacía. Si encontramos un espacio, comparamos que hay exactamente 1 letra de cada letra de una palabra que nos interese y que tenga exactamente la cantidad de letras que necesitamos para esa palabra, solo entonces, reemplazamos la palabra posiblemente errónea por la palabra correcta.

Si la palabra es coincidió con alguno de nuestros filtros o no, vamos a concatenarla en una cadena nueva que se va armando palabra por palabra.

Al terminar con la frase la imprimimos.

### C++
#### Autor: Jordan

En este lenguaje, las variable char son interpretados como números, por lo que un char se puede usar como posición de un arreglo, esa característica puede ser usada para registrar qué letras y cuáles aparecen en la palabra

Para poder tener un bloque de entradas y un bloque de salidas, se usan las líneas:
```cpp
cin.tie(0);
ios::sync_with_stdio(false);
```

```cpp
#include <bits/stdc++.h>

using namespace std;

int abc[30];

int main() {
    cin.tie(0); ios::sync_with_stdio(false);

	int q;
	cin >> q;
    cin.ignore();

	for (int i = 0; i < q; i++) {
        string frase;
        getline(cin, frase);

        frase.push_back(' ');

        fill(begin(abc), end(abc), 0);

        string palabra = "";
        string resultado = "";

        for (auto c : frase) {
            if (c == ' ') {
                if (abc['n' - 'a'] == 1 &&
                    abc['u' - 'a'] == 1 &&
                    abc['b' - 'a'] == 1 &&
                    abc['e' - 'a'] == 1 &&
                    palabra.length() == 4) {
                    palabra = "nube";
                }
                if (abc['q' - 'a'] == 1 &&
                    abc['u' - 'a'] == 1 &&
                    abc['e' - 'a'] == 1 &&
                    abc['s' - 'a'] == 1 &&
                    abc['o' - 'a'] == 1 &&
                    palabra.length() == 5) {
                    palabra = "queso";
                }
                if (abc['l' - 'a'] == 1 &&
                    abc['i' - 'a'] == 1 &&
                    abc['b' - 'a'] == 1 &&
                    abc['r' - 'a'] == 1 &&
                    abc['o' - 'a'] == 1 &&
                    palabra.length() == 5) {
                    palabra = "libro";
                }
                if (abc['m' - 'a'] == 1 &&
                    abc['e' - 'a'] == 1 &&
                    abc['s' - 'a'] == 1 &&
                    abc['a' - 'a'] == 1 &&
                    palabra.length() == 4) {
                    palabra = "mesa";
                }
                if (abc['l' - 'a'] == 1 &&
                    abc['a' - 'a'] == 1 &&
                    abc['p' - 'a'] == 1 &&
                    abc['i' - 'a'] == 1 &&
                    abc['z' - 'a'] == 1 &&
                    palabra.length() == 5) {
                    palabra = "lapiz";
                }
                resultado += palabra + " ";

                fill(begin(abc), end(abc), 0);
                palabra = "";
            } else {
                abc[c - 'a']++;
                palabra.push_back(c);
            }
        }
        cout << resultado << '\n';
	}
}

```

```cpp
#include <iostream>
#include <bits/stdc++.h>

using namespace std;

int main() {
    cin.tie(0); ios::sync_with_stdio(false);
    
    int num;
    cin >> num;
    cin.ignore();

    for (int k = 0; k < num; k++) {
        string frase;
        getline(cin, frase);
        frase.push_back(' ');
        string resultado = "";
        string palabra = "";

        int n = 0, u = 0, b = 0, e = 0, q = 0, s = 0, o = 0, l = 0, i = 0, r = 0, m = 0, a = 0, p = 0, z = 0;

        for (char c : frase) {
            switch(c) {
                case ' ':
                    if (n == 1 && u == 1 && b == 1 && e == 1 && palabra.length() == 4) {
                        palabra = "nube";
                    }
                    if (q == 1 && u == 1 && e == 1 && s == 1 && o == 1 && palabra.length() == 5) {
                        palabra = "queso";
                    }
                    if (l == 1 && i == 1 && b == 1 && r == 1 && o == 1 && palabra.length() == 5) {
                        palabra = "libro";
                    }
                    if (m == 1 && e == 1 && s == 1 && a == 1 && palabra.length() == 4) {
                        palabra = "mesa";
                    }
                    if (l == 1 && a == 1 && p == 1 && i == 1 && z == 1 && palabra.length() == 5) {
                        palabra = "lapiz";
                    }
                    resultado += palabra + " ";
                    
                    n = 0, u = 0, b = 0, e = 0, q = 0, s = 0, o = 0, l = 0, i = 0, r = 0, m = 0, a = 0, p = 0, z = 0;
                    palabra = "";
                    break;
                case 'n':
                    palabra.push_back(c);
                    n++;
                    break;
                case 'u':
                    palabra.push_back(c);
                    u++;
                    break;
                case 'b':
                    palabra.push_back(c);
                    b++;
                    break;
                case 'e':
                    palabra.push_back(c);
                    e++;
                    break;
                case 'q':
                    palabra.push_back(c);
                    q++;
                    break;
                case 's':
                    palabra.push_back(c);
                    s++;
                    break;
                case 'o':
                    palabra.push_back(c);
                    o++;
                    break;
                case 'l':
                    palabra.push_back(c);
                    l++;
                    break;
                case 'i':
                    palabra.push_back(c);
                    i++;
                    break;
                case 'r':
                    palabra.push_back(c);
                    r++;
                    break;
                case 'm':
                    palabra.push_back(c);
                    m++;
                    break;
                case 'a':
                    palabra.push_back(c);
                    a++;
                    break;
                case 'p':
                    palabra.push_back(c);
                    p++;
                    break;
                case 'z':
                    palabra.push_back(c);
                    z++;
                    break;
                default:
                    palabra.push_back(c);
                    break;
            }
        }
        cout << resultado << '\n';
    }

    return 0;
}
```
