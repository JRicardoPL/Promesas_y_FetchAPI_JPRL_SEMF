# Ejercicio 6: Fetch API - Solicitud POST para Crear un Recurso

## Descripción
En este ejercicio, aprenderás a utilizar la Fetch API para realizar una solicitud POST y crear un nuevo recurso en una API. Usaremos una API pública para agregar un nuevo usuario.

## Código
```javascript
// URL de la API para crear un nuevo usuario
const url = 'https://jsonplaceholder.typicode.com/users';

// Datos del nuevo usuario a crear
const newUser = {
  name: 'Juan Pérez',
  email: 'juan.perez@example.com',
  phone: '123-456-7890',
};

// Hacer una solicitud POST a la API
fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json', // Indicar que el contenido es JSON
  },
  body: JSON.stringify(newUser), // Convertir el objeto a una cadena JSON
})
  .then(response => {
    // Comprobar si la respuesta es exitosa (código 201)
    if (!response.ok) {
      throw new Error('Error en la solicitud: ' + response.status);
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then(data => {
    // Mostrar la información del nuevo usuario en la consola
    console.log('Nuevo Usuario Creado:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```
Explicación
Definición de la URL: Se establece la URL de la API donde se enviarán los datos del nuevo usuario.

Datos del Nuevo Usuario: Se define un objeto newUser que contiene la información del nuevo usuario a crear.

Uso de Fetch con POST: Se realiza una solicitud POST utilizando fetch(url, { method: 'POST', ... }).

Cabeceras de la Solicitud: Se indican las cabeceras necesarias, especificando que el contenido de la solicitud es de tipo JSON.

Envío de los Datos: Los datos del nuevo usuario se convierten a una cadena JSON utilizando JSON.stringify(newUser) y se envían como cuerpo de la solicitud.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (código 201). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte a formato JSON.

Manejo de los Datos: Se muestra en la consola la información del nuevo usuario creado, que incluye el ID asignado por la API y los detalles proporcionados.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.

