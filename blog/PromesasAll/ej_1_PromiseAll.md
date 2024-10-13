
# Ejercicio 1: Promise.all

## Enunciado
Crea dos promesas que se resuelvan después de 2 y 4 segundos respectivamente. Utiliza `Promise.all` para esperar a que ambas se resuelvan e imprime el resultado combinado en la consola.

## Solución
```javascript
const promise1 = new Promise((resolve) => setTimeout(() => resolve('Promesa 1 resuelta'), 2000));
const promise2 = new Promise((resolve) => setTimeout(() => resolve('Promesa 2 resuelta'), 4000));

Promise.all([promise1, promise2])
  .then((results) => {
    console.log('Todas las promesas resueltas:', results);
  })
  .catch((error) => {
    console.error('Una promesa falló:', error);
  });
```

## Explicación
Se crean dos promesas, cada una con diferentes tiempos de resolución. `Promise.all` espera a que ambas promesas se resuelvan antes de ejecutar el `then` y combinar sus resultados en un array.

**Salida esperada después de 4 segundos:**
```
Todas las promesas resueltas: ["Promesa 1 resuelta", "Promesa 2 resuelta"]
```
    