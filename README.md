# Last.fm Recent Tracks Visualizer

Este proyecto es una visualización web moderna y responsiva que muestra las últimas 10 canciones escuchadas por el usuario `camoril` en Last.fm.

## Funcionalidad

- **Grid Visual**: Muestra una cuadrícula dinámica (adaptable a móvil/desktop) con las imágenes de los artistas recientes.
- **Actualización en Tiempo Real**: La página consulta la API de Last.fm cada 15 segundos para mantener la lista actualizada.
- **Prioridad de Imagen de Artista**:
  - A diferencia de implementaciones estándar, este visualizador **ignora las portadas de álbumes** (que suelen ser inconsistentes o de baja calidad en la API) y busca siempre la imagen oficial del artista.
  - Utiliza un sistema de caché en memoria para minimizar las llamadas a la API de `artist.getinfo`.
- **Indicador "Now Playing"**: Muestra un badge animado con un ecualizador visual sobre la canción que se está reproduciendo actualmente.
- **Indicador "Loved Track"**: Visualización de canciones favoritas con un icono de corazón animado.
- **Configuración de Usuario**: Permite cambiar el usuario de Last.fm a visualizar mediante un botón de configuración flotante. La preferencia se guarda localmente.
- **Interactivo**: Las tarjetas son enlaces directos a la página de la canción en Last.fm.

## Cómo funciona

El proyecto consta de un único archivo `index.html` optimizado, sin dependencias de compilación ni frameworks pesados.

1.  **API de Last.fm**:
    - `user.getrecenttracks`: Obtiene el historial de escucha.
    - `artist.getinfo`: Se llama para cada pista única para obtener una imagen de alta calidad del artista.
2.  **JavaScript Moderno**:
    - Uso extensivo de `async/await` y `Promise.all` para la carga paralela de metadatos.
    - Manejo robusto de errores con *Optional Chaining* (`?.`) para prevenir caídas por respuestas API incompletas.
3.  **Diseño**:
    - CSS Grid para el layout.
    - Tipografía 'Montserrat'.
    - Diseño totalmente responsivo (Móvil: 2 columnas, Tablet: 3, Desktop: 5).

## Instalación y Uso

Simplemente abre el archivo `index.html` en un navegador moderno. No requiere servidor backend (aunque se recomienda usar un servidor local como Live Server para evitar restricciones de CORS en algunos navegadores, aunque la API de Last.fm suele permitirlo).

Para cambiar el usuario a visualizar, haz clic en el botón flotante rojo en la esquina inferior derecha e ingresa el nombre de usuario de Last.fm deseado.
