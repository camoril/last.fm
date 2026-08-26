# Registro de Cambios (Changelog)

Todos los cambios notables en el proyecto "Last.fm Visualizer" serán documentados en este archivo.

## [2026-08-25] - Corrección de Bugs y Mejoras de Accesibilidad

### Corregido
- **Intervalo de actualización**: Corregida la discrepancia en la documentación. El código actualiza cada 10 segundos (no 15 como decía el README).
- **Tiempos relativos desactualizados**: Los badges de tiempo ("2m", "1h") ahora se actualizan automáticamente cada 30 segundos mediante un intervalo independiente, sin esperar a que cambie la canción.
- **Usuario inexistente**: Ahora se valida que el usuario exista en Last.fm antes de guardar. Si no existe, se muestra un mensaje de error en el modal.
- **Manejo de errores de red**: Errores de conexión ahora se muestran visualmente con un toast de error en lugar de solo console.error.
- **Caché de artistas no persistente**: El caché de imágenes de artistas ahora se guarda en localStorage, evitando llamadas repetidas a la API al recargar la página.

### Añadido
- **Indicador de carga**: Spinner visible durante la carga inicial y actualizaciones.
- **Indicador de estado**: Badge en esquina inferior izquierda muestra estado de conexión (Conectado/Error).
- **Toast de errores**: Notificaciones visuales no intrusivas para errores de API.
- **Validación de usuario**: Feedback visual durante la validación del usuario en el modal.
- **Cierre de modal con Escape**: El modal ahora se puede cerrar con la tecla Escape.
- **Atributos de accesibilidad**: 
  - `aria-label` en botones y contenedores de tracks
  - `role="dialog"` y `aria-modal="true"` en el modal
  - `aria-live="polite"` en toasts y mensajes de error
  - `alt` text dinámico en imágenes de artistas
  - `aria-hidden="true"` en iconos decorativos

### Cambiado
- **Documentación**: README actualizado para reflejar el intervalo real de 10 segundos y la actualización independiente de tiempos cada 30 segundos.

## [2025-12-22] - Mejoras de UI y Funcionalidad

### Añadido
- **Información de Álbum**: Se muestra el nombre del álbum debajo del artista para mayor contexto.
- **Tiempo Relativo**: Badge que indica hace cuánto tiempo se escuchó la canción (ej. "2m", "1h"). Se oculta automáticamente si la canción se está reproduciendo.
- **Indicador de "Loved Track"**: Se muestra un icono de corazón animado en las canciones marcadas como favoritas en Last.fm.
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
