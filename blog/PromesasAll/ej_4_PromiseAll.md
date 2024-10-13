
# Ejercicio 4: Promise.all

## Enunciado
Crea dos promesas, una que se resuelva y otra que se rechace. Utiliza `Promise.all` para manejarlas y captura el error utilizando `.catch` para mostrar un mensaje cuando alguna de las promesas falla.

## Solución
```javascript
const promise1 = new Promise((resolve) => setTimeout(() => resolve('Promesa 1 resuelta'), 2000));
const promise2 = new Promise((_, reject) => setTimeout(() => reject('Promesa 2 rechazada'), 3000));

Promise.all([promise1, promise2])
  .then((results) => {
    console.log('Todas las promesas resueltas:', results);
  })
  .catch((error) => {
    console.error('Una de las promesas falló:', error);
  });
```

## Explicación
En este ejercicio, `Promise.all` se rechaza si cualquiera de las promesas es rechazada. La promesa `promise2` se rechaza después de 3 segundos, lo que provoca que se ejecute el bloque `catch`.

**Salida esperada después de 3 segundos:**
```
Una de las promesas falló: Promesa 2 rechazada
```
    