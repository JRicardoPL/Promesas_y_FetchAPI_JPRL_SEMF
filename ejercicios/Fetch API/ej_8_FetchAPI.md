# Ejercicio 8: Fetch API - Manejo de Errores en Solicitudes

## Descripción
En este ejercicio, aprenderás a manejar errores que pueden ocurrir durante las solicitudes realizadas con la Fetch API. Esto es importante para mejorar la experiencia del usuario y para depurar problemas de red.

## Código
```javascript
// URL de una API que podría no existir para simular un error
const url = 'https://jsonplaceholder.typicode.com/invalid-endpoint';

// Hacer una solicitud GET a la API
fetch(url)
  .then(response => {
    // Comprobar si la respuesta es exitosa (código 200)
    if (!response.ok) {
      throw new Error('Error en la solicitud: ' + response.status); // Lanza un error si la respuesta no es exitosa
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then(data => {
    // Mostrar los datos en la consola
    console.log('Datos recibidos:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error capturado:', error.message);
    // Mostrar un mensaje al usuario en la interfaz (si aplica)
    alert('Ocurrió un error al realizar la solicitud: ' + error.message);
  });
```
Explicación
Definición de la URL: Se establece una URL de API que no existe (invalid-endpoint) para simular un error durante la solicitud.

Uso de Fetch: Se realiza una solicitud GET utilizando fetch(url).

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (código 200). Si la respuesta no es exitosa, se lanza un error con un mensaje que incluye el estado de la respuesta.

Conversión a JSON: Si la respuesta es exitosa, se convierte a formato JSON.

Manejo de los Datos: Se muestra en la consola los datos recibidos.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos. En el bloque catch, se muestra un mensaje en la consola y se notifica al usuario mediante un alert.