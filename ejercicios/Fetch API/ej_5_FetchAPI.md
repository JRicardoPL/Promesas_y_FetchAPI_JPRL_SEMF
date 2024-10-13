# Ejercicio 5: Fetch API - Solicitud GET para Obtener un Recurso

## Descripción
En este ejercicio, aprenderás a utilizar la Fetch API para realizar una solicitud GET y obtener un recurso de una API. Usaremos una API pública para recuperar información sobre un usuario específico.

## Código
```javascript
// URL de la API para obtener información de un usuario específico
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
Definición de la URL: Se establece la URL de la API desde donde se obtendrá la información del usuario específico (en este caso, el usuario con ID 1).

Uso de Fetch con GET: Se realiza una solicitud GET utilizando fetch(url).

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (response.ok). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte a formato JSON.

Manejo de los Datos: Se muestra en la consola la información del usuario recuperada, que incluye el nombre, email, teléfono, y otros detalles.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.si