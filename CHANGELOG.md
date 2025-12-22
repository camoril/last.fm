# Registro de Cambios (Changelog)

Todos los cambios notables en el proyecto "Last.fm Visualizer" serán documentados en este archivo.

## [2025-12-22] - Configuración de Usuario

### Añadido
- **Cambio de Usuario en UI**: Se implementó un botón flotante (FAB) y una ventana modal que permite cambiar el usuario de Last.fm directamente desde la interfaz.
- **Persistencia**: El nombre de usuario configurado se guarda en `localStorage`, manteniendo la preferencia entre sesiones.
- **Feedback Visual**: La cuadrícula se limpia y recarga automáticamente al guardar un nuevo usuario.

## [2025-12-16] - Estabilidad y Consistencia Visual

### Cambiado
- **Lógica de Imágenes**: Se modificó el algoritmo de selección de imágenes para **ignorar siempre** la portada del álbum proporcionada por `recenttracks`. Ahora se fuerza la búsqueda de la imagen del artista (`artist.getinfo`) para todas las pistas. Esto soluciona la inconsistencia visual donde algunas pistas tenían portadas de baja calidad o faltantes.

### Corregido
- **Manejo de Errores API**: Se implementó *Optional Chaining* (`?.`) en el procesamiento de la respuesta JSON. Esto corrige un error crítico donde la aplicación dejaba de actualizarse si la API de Last.fm devolvía un array de imágenes vacío o malformado para una canción específica.

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
- **Fallback de Imágenes**: Lógica original para buscar imagen de artista solo si faltaba la del álbum.
- **Caché Local**: Sistema simple para almacenar URLs de imágenes de artistas.
