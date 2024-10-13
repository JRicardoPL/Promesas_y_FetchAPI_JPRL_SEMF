# Ejercicio 2: Fetch API - Obtener Lista de Publicaciones

## Descripción
En este ejercicio, utilizaremos la Fetch API para obtener una lista de publicaciones desde una API pública. Haremos una solicitud GET para recuperar los datos y los mostraremos en la consola.

## Código
```javascript
// URL de la API
const url = 'https://jsonplaceholder.typicode.com/posts';

// Hacer una solicitud GET a la API
fetch(url)
  .then(response => {
    // Comprobar si la respuesta es exitosa (código 200)
    if (!response.ok) {
      throw new Error('Error en la solicitud: ' + response.status);
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then(data => {
    // Mostrar los datos de las publicaciones en la consola
    console.log('Lista de Publicaciones:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```

Explicación
Definición de la URL: Se establece la URL de la API de la que se quiere obtener la lista de publicaciones.

Uso de Fetch: Se realiza una solicitud GET utilizando fetch(url). Este método devuelve una promesa que se resuelve cuando se recibe la respuesta.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (response.ok). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte la respuesta a formato JSON con response.json().

Manejo de los Datos: Una vez que se obtiene la información, se muestra en la consola.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola