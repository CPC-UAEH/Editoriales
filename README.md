<div align="center">
  <img src="https://raw.githubusercontent.com/CPC-UAEH/Editoriales/main/Recursos/logoCPC.png" alt="Logo del Club de Programación Competitiva de la UAEH" width="180">

# Editoriales CPC · UAEH

  **Análisis detallado y soluciones de problemas de programación competitiva.**

  <p>
    <a href="https://cpcjudge.com/"><img src="https://img.shields.io/badge/CPC%20Judge-practica-111827?style=for-the-badge" alt="CPC Judge"></a>
    <a href="https://github.com/CPC-UAEH/Editoriales"><img src="https://img.shields.io/github/last-commit/CPC-UAEH/Editoriales?style=for-the-badge&label=actualizado" alt="Última actualización"></a>
    <a href="https://github.com/CPC-UAEH/Editoriales/issues"><img src="https://img.shields.io/github/issues/CPC-UAEH/Editoriales?style=for-the-badge&label=issues" alt="Issues abiertas"></a>
    <a href="https://github.com/CPC-UAEH/Editoriales/graphs/contributors"><img src="https://img.shields.io/github/contributors/CPC-UAEH/Editoriales?style=for-the-badge&label=contribuidores" alt="Contribuidores"></a>
    <a href="./LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey?style=for-the-badge" alt="Licencia"></a>
  </p>

  <p>
    <a href="#contenido">Contenido</a> ·
    <a href="#cómo-aprender-con-este-material">Cómo aprender</a> ·
    <a href="#contribuir">Contribuir</a> ·
    <a href="#autoría-y-mantenimiento">Autoría</a>
  </p>
</div>

## Sobre el proyecto

Este repositorio reúne editoriales, análisis de complejidad, propuestas de solución e implementaciones de referencia para problemas de programación competitiva resueltos por el **Club de Programación Competitiva de la UAEH**.

El objetivo es construir una colección de material técnico en español que acompañe a los alumnos durante las sesiones de entrenamiento y la preparación para competencias. El contenido prioriza el razonamiento detrás de los algoritmos sobre la memorización de soluciones.

> **Recomendación:** intenta resolver cada problema antes de consultar su editorial.

## Contenido

El material se organiza por año y evento.

### 2025

- [Campamento Otoño 2025](./2025/Campamento_Otonio_2025/campamento-otono-2025.md)

### 2026

- [Campamento Primavera 2026](./2026/Campamento_Primavera_2026/campamento-primavera-2026.md)
- [OFMI 2026](./2026/OFMI_2026/ofmi-2026.md)

Para crear material de un nuevo evento, consulta la [plantilla de editoriales](./template/README.md).

## Cómo aprender con este material

Las editoriales siguen este proceso:

```text
Problema → Observaciones → Restricciones → Idea → Algoritmo → Complejidad → Implementación
```

Las editoriales no muestran únicamente una solución. Documentan las observaciones y decisiones que permiten llegar a ella.

### Contenido de una editorial

Cada editorial incluye:

- **Descripción:** enunciado con variables matemáticas en formato LaTeX
- **Entrada/Salida:** formato y restricciones
- **Ejemplos:** casos de prueba
- **Temas identificados:** técnicas de programación y conceptos matemáticos
- **Propuesta de solución:** modelado y estrategia general
- **Restricciones:** análisis de límites y complejidad requerida
- **Estados/Estructura:** definición de estados DP o estructuras de datos
- **Casos base:** casos iniciales y justificación
- **Transiciones:** algoritmo paso a paso con diagramas Mermaid
- **Correctitud:** argumento de por qué el algoritmo es correcto
- **Complejidad:** análisis de tiempo y memoria
- **Implementación:** código fuente en C++, Java, Kotlin, Python
- **Casos límite:** edge cases y resultados esperados

Para practicar los problemas, visita [CPC Judge](https://cpcjudge.com/).

## Contribuir

Las contribuciones son bienvenidas. Puedes ayudar con:

- correcciones de errores o de redacción;
- nuevas editoriales de problemas;
- ejemplos adicionales o implementaciones en otros lenguajes;
- propuestas de problemas o concursos;
- revisión de Pull Requests existentes.

Consulta las [reglas para contribuir](./.github/CONTRIBUTING.md) y el
[Código de Conducta](./.github/CODE_OF_CONDUCT.md) antes de participar.

### Flujo recomendado

1. Revisa los [issues abiertos](https://github.com/CPC-UAEH/Editoriales/issues) o crea uno nuevo.
2. Haz un fork del repositorio y crea una rama descriptiva:

   ```bash
   git checkout -b editorial/nombre-problema
   ```

3. Copia la plantilla y realiza tus cambios:

   ```bash
   cp -r template/periodo-academico año/nombre-evento/
   ```

4. Usa commits claros, por ejemplo:

   ```text
   docs: agregar editorial del problema X
   docs: mejorar análisis de complejidad
   fix: corregir implementación en C++
   ```

5. Abre un Pull Request explicando qué cambiaste y por qué.

Para cambios pequeños de documentación, también puedes abrir directamente un Pull Request desde GitHub.

## Autoría y mantenimiento

Este proyecto es mantenido de forma colaborativa por **KaarLarax**, el [Club de Programación Competitiva de la UAEH](https://github.com/CPC-UAEH) y todas las personas que han contribuido al repositorio.

- **Mantenimiento:** [KaarLarax](https://github.com/KaarLarax), en coordinación con el [Club de Programación Competitiva de la UAEH](https://github.com/CPC-UAEH)
- **Contribuciones:** todas las personas que han aportado contenido, correcciones, ideas o revisiones
- **Práctica de problemas:** [CPC Judge](https://cpcjudge.com/)
- **Canal de YouTube:** [Year Zero](https://www.youtube.com/@yearzero4486)

## Contribuidores

Gracias a todas las personas que ayudan a mejorar este material.

<div align="center">
  <a href="https://github.com/CPC-UAEH/Editoriales/graphs/contributors">
    <img src="https://contrib.rocks/image?repo=CPC-UAEH/Editoriales" alt="Contribuidores del repositorio">
  </a>
</div>

La imagen se actualiza automáticamente con los contribuidores registrados en GitHub. También puedes consultar la [lista completa de contribuidores](https://github.com/CPC-UAEH/Editoriales/graphs/contributors).

## Licencia

Este repositorio está bajo la licencia [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](./LICENSE). Puedes reutilizar, adaptar y compartir el material siempre que otorgues atribución y distribuyas las obras derivadas bajo la misma licencia.

## Reconocimientos

Material desarrollado como apoyo para las actividades del **Club de Programación Competitiva de la UAEH**.


