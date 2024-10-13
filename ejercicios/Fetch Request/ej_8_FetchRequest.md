# Ejercicio: Uso de Promise.all con Fetch API

En este ejercicio, utilizaremos `Promise.all` para hacer múltiples solicitudes a una API y manejar las respuestas de manera eficiente.

## Objetivo
Aprender a utilizar `Promise.all` para realizar múltiples llamadas a una API y procesar sus respuestas.


## Código
```javascript
// URLs de las APIs que vamos a consultar
const url1 = 'https://jsonplaceholder.typicode.com/posts/1';
const url2 = 'https://jsonplaceholder.typicode.com/posts/2';
const url3 = 'https://jsonplaceholder.typicode.com/posts/3';

// Función para obtener datos de las URLs
const fetchData = (url) => fetch(url).then(response => {
  if (!response.ok) {
    throw new Error(`Error en la red: ${response.status}`);
  }
  return response.json();
});

// Usando Promise.all para hacer las llamadas en paralelo
Promise.all([fetchData(url1), fetchData(url2), fetchData(url3)])
  .then((resultados) => {
    console.log("Resultados de las API:", resultados);
  })
  .catch((error) => {
    console.error("Error en alguna de las solicitudes:", error);
  });
```

## Explicación
En este ejercicio, hacemos tres solicitudes a una API que simula un conjunto de datos. La función fetchData utiliza la API Fetch para realizar la solicitud, manejando posibles errores de red. Al utilizar Promise.all, podemos realizar todas las solicitudes en paralelo. Promise.all espera a que todas las promesas se resuelvan y, si todas tienen éxito, el método then se ejecuta, proporcionando un array con los resultados de las respuestas. Si alguna de las solicitudes falla, el método catch se activa y maneja el error.


