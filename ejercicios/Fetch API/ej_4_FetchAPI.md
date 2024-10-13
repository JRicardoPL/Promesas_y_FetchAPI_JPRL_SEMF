# Ejercicio 4: Fetch API - Solicitud POST para Crear un Recurso

## Descripción
En este ejercicio, aprenderás a utilizar la Fetch API para realizar una solicitud POST y crear un nuevo recurso en una API. Usaremos una API pública para enviar datos de un nuevo usuario.

## Código
```javascript
// URL de la API para crear un nuevo usuario
const url = 'https://jsonplaceholder.typicode.com/users';

// Datos del nuevo usuario que se enviarán
const newUser = {
  name: 'Juan Pérez',
  email: 'juan.perez@example.com',
  phone: '123-456-7890'
};

// Hacer una solicitud POST a la API
fetch(url, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json', // Indicar que el contenido es JSON
  },
  body: JSON.stringify(newUser) // Convertir el objeto a JSON
})
  .then(response => {
    // Comprobar si la respuesta es exitosa (código 201)
    if (!response.ok) {
      throw new Error('Error en la solicitud: ' + response.status);
    }
    return response.json(); // Convertir la respuesta a JSON
  })
  .then(data => {
    // Mostrar la información del nuevo usuario creado en la consola
    console.log('Nuevo Usuario Creado:', data);
  })
  .catch(error => {
    // Manejar errores
    console.error('Error:', error);
  });
```

Explicación
Definición de la URL: Se establece la URL de la API donde se enviarán los datos para crear un nuevo usuario.

Definición de los Datos: Se crea un objeto newUser con la información del nuevo usuario que se desea enviar.

Uso de Fetch con POST: Se realiza una solicitud POST utilizando fetch(url, `{ method: 'POST', ... })`.

Configuración de Headers: Se especifica el encabezado Content-Type para indicar que el cuerpo de la solicitud contiene datos en formato JSON.

Conversión de Datos: Se utiliza JSON.stringify(newUser) para convertir el objeto en una cadena JSON que se enviará en el cuerpo de la solicitud.

Verificación de la Respuesta: Se comprueba si la respuesta es exitosa (response.ok). Si no lo es, se lanza un error.

Conversión a JSON: Si la respuesta es exitosa, se convierte a formato JSON.

Manejo de los Datos: Se muestra en la consola la información del nuevo usuario creado, que incluye un ID asignado por la API.

Manejo de Errores: Se captura cualquier error que ocurra durante la solicitud o la conversión de datos, mostrando un mensaje en la consola.