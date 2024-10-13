
# Ejercicio 6: Promise.all

## Enunciado
Dada una lista de números, crea una función que devuelva un array de promesas que resuelvan cada número al cuadrado después de 1 segundo. Usa `Promise.all` para obtener todos los resultados y mostrarlos en la consola.

## Solución
```javascript
const squareNumbers = (numbers) => {
  const promises = numbers.map((num) => {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(num * num);
      }, 1000);
    });
  });

  Promise.all(promises)
    .then((squared) => {
      console.log('Cuadrados de los números:', squared);
    })
    .catch((error) => {
      console.error('Error al calcular cuadrados:', error);
    });
};

// Ejemplo de uso
squareNumbers([1, 2, 3, 4, 5]);
```

## Explicación
La función `squareNumbers` toma un array de números y devuelve promesas que se resuelven con el cuadrado de cada número después de 1 segundo. `Promise.all` se utiliza para esperar a que todas las promesas se resuelvan antes de mostrar los resultados.

**Salida esperada después de 1 segundo:**
```
Cuadrados de los números: [1, 4, 9, 16, 25]
```
    