# Ejercicio 8
## GET Request para Cargar Imágenes
Objetivo: Realizar una solicitud GET para cargar imágenes desde un servidor.

### Resultado

```
function loadImage(url) {
  fetch(url)
    .then(response => {
      if (!response.ok) {
        throw new Error(`Error al cargar imagen: ${response.status}`);
      }
      return response.blob();
    })
    .then(blob => {
      const img = document.createElement('img');
      img.src = URL.createObjectURL(blob);
      document.body.appendChild(img);
    })
    .catch(error => console.error('Error:', error));
}

loadImage('https://via.placeholder.com/150');
```

### Explicación:
- Aquí estamos usando `fetch` para obtener un archivo de imagen como un blob y luego creamos un objeto URL para mostrar la imagen en el DOM.

### Resultado

![Texto alternativo](../../src/Ejercicio24res.png "Respuesta del codigo ejemplo")
