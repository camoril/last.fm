# Registro de Cambios (Changelog)

Todos los cambios notables en el proyecto "Last.fm Visualizer" serán documentados en este archivo.

## [2025-12-02] - Rediseño Visual y Funcionalidad

### Añadido
- **Diseño Responsivo**: Implementación de CSS Grid que se adapta a diferentes tamaños de pantalla (Móvil: 2 columnas, Tablet: 3, Desktop: 5).
- **Tipografía**: Integración de la fuente 'Montserrat' de Google Fonts.
- **Indicador "Now Playing"**: Badge animado con ecualizador visual para la canción que se está reproduciendo actualmente.
- **Enlaces Activos**: Las portadas ahora son enlaces que abren la página de la canción en Last.fm en una nueva pestaña.
- **Efectos Visuales**: Zoom suave al pasar el mouse y degradados en los textos para mejorar la legibilidad.

### Cambiado
- **Optimización de Renderizado**: Se reescribió la lógica de actualización del DOM para modificar solo los elementos que cambian, eliminando parpadeos y mejorando el rendimiento.
- **Estructura HTML**: Cambio de contenedores `div` a `a` para semántica y funcionalidad de enlaces.

## [2025-12-02] - Versión Inicial

### Añadido
- **Visualización Básica**: Grid de 10 últimas canciones escuchadas.
- **Integración API**: Conexión con la API de Last.fm (`user.getrecenttracks`).
- **Fallback de Imágenes**: Lógica para buscar la imagen del artista (`artist.getinfo`) si la canción no tiene portada de álbum.
- **Caché Local**: Sistema simple para almacenar URLs de imágenes de artistas y reducir llamadas a la API.
