# Ejercicio 6

Mostrar un video descargado

### Respuesta

```javascript
async function fetchVideo() {
  try {
    const response = await fetch('https://www.w3schools.com/html/mov_bbb.mp4');
    const blob = await response.blob();
    const video = document.createElement('video');
    video.controls = true;
    video.src = URL.createObjectURL(blob);
    document.body.appendChild(video);
  } catch (error) {
    console.error('Error al cargar el video:', error);
  }
}

fetchVideo();
```

### Explicación:

- fetch('https://www.w3schools.com/html/mov_bbb.mp4'): Solicita un archivo de video.
- response.blob(): Convierte la respuesta en un objeto Blob.
- document.createElement('video'): Crea un elemento de video `(<video>)`.
- video.controls = true: Habilita los controles del video.
- video.src = URL.createObjectURL(blob): Establece la URL del blob como la fuente del video.
- document.body.appendChild(video): Agrega el video al cuerpo del documento.

### Resultado

![Texto alternativo](../../src/Ejercicio30res.png "Respuesta del codigo ejemplo")
