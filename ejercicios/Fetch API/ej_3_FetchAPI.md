# Ejercicio 3: Fetch API - Obtener Datos de un Usuario

## Descripción
En este ejercicio, utilizaremos la Fetch API para obtener información de un usuario específico desde una API pública. Haremos una solicitud GET para recuperar los datos y los mostraremos en la consola.

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
    // Mostrar los datos del usuario en la consola
    console.log('Datos del Usuario:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```

Memoria actualizada
Aquí tienes el ejercicio 3 sobre Fetch API:

markdown
Copiar código
# Ejercicio 3: Fetch API - Obtener Datos de un Usuario

## Descripción
En este ejercicio, utilizaremos la Fetch API para obtener información de un usuario específico desde una API pública. Haremos una solicitud GET para recuperar los datos y los mostraremos en la consola.

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
    // Mostrar los datos del usuario en la consola
    console.log('Datos del Usuario:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });

  ```
Explicación
Definición de la URL: Se establece la URL de la API de la que se quiere obtener información.

Uso de Fetch: Se realiza una solicitud GET utilizando fetch(url). Este método devuelve una promesa que se resuelve cuando se recibe la respuesta.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (response.ok). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte la respuesta a formato JSON con response.json().

Manejo de los Datos: Una vez que se obtiene la información, se muestra en la consola.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.