# Ejercicio 7: Fetch API - Solicitud PUT para Actualizar un Recurso

## Descripción
En este ejercicio, aprenderás a utilizar la Fetch API para realizar una solicitud PUT y actualizar un recurso existente en una API. Usaremos una API pública para modificar los datos de un usuario.

## Código
```javascript
// URL de la API para actualizar un usuario específico
const url = 'https://jsonplaceholder.typicode.com/users/1'; // Cambia el ID según sea necesario

// Datos actualizados del usuario
const updatedUser = {
  name: 'Juan Pérez Actualizado',
  email: 'juan.perez.actualizado@example.com',
  phone: '123-456-7890',
};

// Hacer una solicitud PUT a la API
fetch(url, {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json', // Indicar que el contenido es JSON
  },
  body: JSON.stringify(updatedUser), // Convertir el objeto a una cadena JSON
})
  .then(response => {
    // Comprobar si la respuesta es exitosa (código 200)
    if (!response.ok) {
      throw new Error('Error en la solicitud: ' + response.status);
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then(data => {
    // Mostrar la información del usuario actualizado en la consola
    console.log('Usuario Actualizado:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```
Explicación
Definición de la URL: Se establece la URL de la API para actualizar un usuario específico, utilizando su ID en la URL.

Datos Actualizados: Se define un objeto updatedUser que contiene la información actualizada del usuario.

Uso de Fetch con PUT: Se realiza una solicitud PUT utilizando fetch(url, { method: 'PUT', ... }).

Cabeceras de la Solicitud: Se indican las cabeceras necesarias, especificando que el contenido de la solicitud es de tipo JSON.

Envío de los Datos Actualizados: Los datos actualizados del usuario se convierten a una cadena JSON utilizando JSON.stringify(updatedUser) y se envían como cuerpo de la solicitud.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (código 200). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte a formato JSON.

Manejo de los Datos: Se muestra en la consola la información del usuario actualizado, que incluye los detalles modificados.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.