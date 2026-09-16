# Plantilla de editoriales

Esta carpeta sirve como base para crear las editoriales de cualquier año,
evento y concurso. No se debe editar directamente: copia su contenido dentro de
la carpeta del año correspondiente.

## Estructura

### Eventos con múltiples concursos

```text
periodo-academico/
└── evento/
    ├── evento.md                    # Descripción general del evento
    └── concurso/
        ├── concurso.md              # Índice del concurso con lista de problemas
        └── problemas/
            ├── problema.md          # Plantilla de editorial individual
            └── recursos/
                └── ejemplo.md       # Guía de uso de imágenes y recursos
```

### Eventos con un solo concurso

Cuando un evento tiene un único concurso, se elimina la carpeta del concurso y los archivos `concurso.md` y `problemas/` van directamente en la raíz del evento:

```text
periodo-academico/
└── evento/
    ├── evento.md                    # Descripción general del evento
    ├── concurso.md                  # Índice del concurso con lista de problemas
    └── problemas/
        ├── problema.md              # Plantilla de editorial individual
        └── recursos/
            └── ejemplo.md           # Guía de uso de imágenes y recursos
```

## Archivos de la plantilla

### evento.md

Contiene la descripción general del evento (campamento, olimpiada, etc.),
fecha, plataforma y lista de concursos que lo componen.

### concurso.md

Es el índice del concurso. Contiene:
- Descripción breve del concurso
- Tabla con todos los problemas y enlaces a sus editoriales
- Temas identificados y observaciones generales

### problema.md

Es la plantilla para la editorial de cada problema individual. Incluye:
- Descripción, entrada, salida y ejemplos
- Análisis de complejidad y propuestas de solución
- Implementaciones en C++, Java, Kotlin, Python

### recursos/

Carpeta para imágenes y recursos visuales. Se recomienda usar URLs externas
en lugar de archivos locales. Consulta `recursos/ejemplo.md` para más detalles.

## Cómo usarla

### Para eventos con múltiples concursos

1. Copia `periodo-academico` dentro de la carpeta del año, por ejemplo `2027/`.
2. Renombra `evento` con el nombre del evento en minúsculas y guiones: `campamento-primavera-2027/`.
3. Completa `evento.md` con la información general del evento.
4. Renombra `concurso` con el nombre del concurso: `concurso-apertura/`.
5. Completa `concurso.md` como índice del concurso.
6. Agrega una editorial por problema dentro de `problemas/` usando el formato de `problema.md`.
7. Actualiza el README principal con los enlaces del nuevo material.
8. Consulta las [reglas para contribuir](../.github/CONTRIBUTING.md) para convenciones de commits, ramas y contenido.

### Para eventos con un solo concurso

1. Copia `periodo-academico` dentro de la carpeta del año.
2. Renombra `evento` con el nombre del evento en minúsculas y guiones.
3. Completa `evento.md` con la información general del evento.
4. **Elimina la carpeta `concurso/`** y mueve `concurso.md` y `problemas/` directamente a la raíz del evento.
5. Completa `concurso.md` como índice del concurso.
6. Agrega una editorial por problema dentro de `problemas/` usando el formato de `problema.md`.
7. Actualiza el README principal con los enlaces del nuevo material.

## Convenciones

- Usa nombres de carpetas en minúsculas con guiones: `campamento-otono-2025/`.
- Usa guiones para nombres de archivo: `concurso-de-cierre.md`.
- Nombra los problemas con letra y nombre: `a-suma-simple.md`.
- Escribe las complejidades como `$O(...)$` e indica tiempo y memoria.
- Usa URLs externas para imágenes cuando sea posible.
- Revisa los enlaces antes de publicar el material.

## Ejemplo de estructura completa

### Evento con múltiples concursos

```text
2027/
└── campamento-primavera-2027/
    ├── evento.md
    ├── concurso-apertura/
    │   ├── concurso.md
    │   └── problemas/
    │       ├── a-saludando.md
    │       ├── b-suma-de-dos.md
    │       └── recursos/
    │           └── b-diagrama.png
    └── concurso-cierre/
        ├── concurso.md
        └── problemas/
            ├── a-grafos.md
            └── b-dp-mochila.md
```

### Evento con un solo concurso

```text
2026/
└── ofmi-2026/
    ├── ofmi-2026.md
    ├── concurso.md
    └── problemas/
        ├── a-constelaciones.md
        ├── b-destruyendo-asteroides.md
        └── recursos/
            └── a-diagrama.png
```
