
# Ejercicio 2: Promise.all

## Enunciado
Realiza tres promesas que simulen la carga de datos desde tres APIs distintas (usando `setTimeout` para simular el tiempo de respuesta). Usa `Promise.all` para mostrar un mensaje cuando todas las promesas se hayan completado.

## Solución
```javascript
const apiCall1 = new Promise((resolve) => setTimeout(() => resolve('API 1 completada'), 3000));
const apiCall2 = new Promise((resolve) => setTimeout(() => resolve('API 2 completada'), 2000));
const apiCall3 = new Promise((resolve) => setTimeout(() => resolve('API 3 completada'), 1000));

Promise.all([apiCall1, apiCall2, apiCall3])
  .then((responses) => {
    console.log('Todas las API completadas:', responses);
  })
  .catch((error) => {
    console.error('Error en una de las APIs:', error);
  });
```

## Explicación
Cada promesa simula una llamada a una API usando `setTimeout`. `Promise.all` se asegura de que todas las llamadas estén completadas antes de ejecutar el `then` y muestra los resultados combinados.

**Salida esperada después de 3 segundos:**
```
Todas las API completadas: ["API 1 completada", "API 2 completada", "API 3 completada"]
```
    