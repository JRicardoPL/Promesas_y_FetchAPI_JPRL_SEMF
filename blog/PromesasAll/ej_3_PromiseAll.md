
# Ejercicio 3: Promise.all

## Enunciado
Crea una función que reciba un array de URLs y realice un `fetch` de cada una utilizando `Promise.all`. Imprime en la consola la respuesta de todas las solicitudes.

## Solución
```javascript
const fetchUrls = (urls) => {
  const fetchPromises = urls.map((url) => fetch(url).then((response) => response.json()));
  
  Promise.all(fetchPromises)
    .then((data) => {
      console.log('Respuestas de todas las solicitudes:', data);
    })
    .catch((error) => {
      console.error('Error al realizar las solicitudes:', error);
    });
};

// Ejemplo de uso
const urls = [
  'https://jsonplaceholder.typicode.com/posts/1',
  'https://jsonplaceholder.typicode.com/posts/2',
  'https://jsonplaceholder.typicode.com/posts/3'
];
fetchUrls(urls);
```

## Explicación
La función `fetchUrls` recibe un array de URLs y utiliza `map` para crear un array de promesas de `fetch`. Con `Promise.all`, se espera a que todas las solicitudes se completen para mostrar las respuestas.

**Salida esperada:**
```
Respuestas de todas las solicitudes: [{...}, {...}, {...}]
```
    