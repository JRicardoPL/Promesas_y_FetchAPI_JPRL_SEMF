# Ejercicio 1: Fetch API - Solicitud GET a un Recurso

## Descripción
En este ejercicio, aprenderás a utilizar la Fetch API para realizar una solicitud GET a un recurso y manejar la respuesta. Utilizaremos una API pública para obtener información sobre un usuario.

## Código
```javascript
// URL de la API
const url = 'https://jsonplaceholder.typicode.com/users/1';

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
    // Mostrar la información del usuario en la consola
    console.log('Información del Usuario:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```

Explicación
Definición de la URL: Se establece la URL de la API para obtener información sobre un usuario específico (en este caso, el usuario con ID 1).

Uso de Fetch: Se realiza una solicitud GET utilizando fetch(url). Este método devuelve una promesa que se resuelve cuando se recibe la respuesta.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (response.ok). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte la respuesta a formato JSON con response.json().

Manejo de los Datos: Una vez que se obtiene la información, se muestra en la consola.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.