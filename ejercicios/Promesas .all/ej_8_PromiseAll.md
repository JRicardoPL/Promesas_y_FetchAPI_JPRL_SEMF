
# Ejercicio 8: Promise.all

## Enunciado
Crea una función que acepte una lista de URLs y realice un `fetch` de cada una. Cada `fetch` debe resolverse solo si la respuesta tiene un código de estado 200. Si alguna de las solicitudes falla, `Promise.all` debe capturar el error. Usa un `timeout` para que si alguna solicitud toma más de 3 segundos, se rechace automáticamente y el resto de las solicitudes se cancelen.

## Solución
```javascript
const fetchWithTimeout = (url, timeout = 3000) => {
  return new Promise((resolve, reject) => {
    const timer = setTimeout(() => {
      reject(`Timeout de ${timeout} ms superado para ${url}`);
    }, timeout);

    fetch(url)
      .then((response) => {
        clearTimeout(timer);
        if (response.ok) {
          resolve(response.json());
        } else {
          reject(`Error ${response.status} en ${url}`);
        }
      })
      .catch((error) => reject(`Error de red en ${url}: ${error}`));
  });
};

const fetchMultipleUrls = (urls) => {
  const fetchPromises = urls.map((url) => fetchWithTimeout(url));

  Promise.all(fetchPromises)
    .then((results) => {
      console.log('Resultados de todas las solicitudes:', results);
    })
    .catch((error) => {
      console.error('Error en alguna de las solicitudes:', error);
    });
};

// Ejemplo de uso
const urls = [
  'https://jsonplaceholder.typicode.com/posts/1',
  'https://jsonplaceholder.typicode.com/posts/2',
  'https://jsonplaceholder.typicode.com/posts/3'
];
fetchMultipleUrls(urls);
```

## Explicación
La función `fetchWithTimeout` combina una solicitud `fetch` con un temporizador para manejar tiempos de espera. `Promise.all` espera que todas las solicitudes se completen, pero cualquier error en una de ellas es capturado por el bloque `catch`.

**Salida esperada:**
```
Resultados de todas las solicitudes: [{...}, {...}, {...}]
```
    