# Guía de uso de recursos

Esta carpeta está destinada a almacenar imágenes, diagramas y otros recursos visuales que complementen las editoriales de los problemas.

## Recomendación: Usar URLs externas

**Se recomienda encarecidamente usar URLs externas** en lugar de almacenar imágenes directamente en este repositorio.

### Ventajas de URLs externas

- **Sin límite de tamaño**: GitHub tiene un límite de 100 MB por archivo y recomienda mantener el repositorio bajo 1 GB
- **Carga más rápida**: Las imágenes se sirven desde CDNs optimizados
- **Más fácil mantenimiento**: No necesitas hacer commit para actualizar imágenes
- **Mejor colaboración**: Los contribuidores no necesitan clonar archivos binarios grandes

## Cómo usar URLs externas

En tu archivo `problema.md`, usa la sintaxis estándar de Markdown:

```markdown
![Descripción de la imagen](https://i.imgur.com/abc123.png)
```

O con HTML para mayor control:

```html
<img src="https://i.imgur.com/abc123.png" alt="Descripción" width="400">
```

## Cuándo usar archivos locales

Solo almacena imágenes localmente si:

1. La imagen es crítica y podría eliminarse del servicio externo
2. Necesitas versionar la imagen (cambios frecuentes)
3. La imagen es muy pequeña (< 100 KB)

## Convenciones de nomenclatura

Si decides usar archivos locales, sigue estas convenciones:

- **Formato**: minúsculas con guiones
- **Nombre**: `problema-[letra]-[descripcion].png`
- **Ejemplos**:
  - `problema-a-diagrama-flujo.png`
  - `problema-b-grafico-estado.png`
  - `problema-c-ejemplo-visual.jpeg`

## Estructura de archivos locales

```text
recursos/
├── problema-a-diagrama.png
├── problema-b-grafico.png
└── problema-c-ejemplo.jpeg
```

## Referencia en editoriales

Desde `problema.md`, referencia las imágenes locales así:

```markdown
![Diagrama del problema A](./recursos/problema-a-diagrama.png)
```

## Compresión de imágenes

Si usas archivos locales, comprime las imágenes antes de subirlas:

- **PNG**: Usa [TinyPNG](https://tinypng.com/) o `pngquant`
- **JPEG**: Usa [TinyJPG](https://tinyjpg.com/) o `jpegoptim`
- **WebP**: Considera este formato para mejor compresión

## Ejemplo completo

```markdown
## Estados o estructura de la solución

![Diagrama de estados](https://i.imgur.com/abc123.png)

El diagrama muestra las transiciones entre estados A, B y C...
```

## Más información

- [GitHub: Working with large files](https://docs.github.com/en/repositories/working-with-files/managing-large-files)
- [Markdown: Images](https://www.markdownguide.org/basic-syntax/#images)
