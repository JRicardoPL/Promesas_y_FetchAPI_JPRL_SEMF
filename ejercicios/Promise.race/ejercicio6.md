# Ejercicio 6
## Carrera entre promesa resuelta y rechazada
Objetivo: Mostrar cómo se comporta Promise.race cuando una promesa se resuelve y otra se rechaza.

### Respuesta
```
const resolvedPromise = new Promise((resolve) => setTimeout(() => resolve('Resuelto'), 1000));
const rejectedPromise = new Promise((_, reject) => setTimeout(() => reject('Rechazado'), 500));

Promise.race([resolvedPromise, rejectedPromise])
.then(result => console.log(result))
.catch(error => console.log(error)); 
```
### Resultado

![Texto alternativo](../../src/Ejercicio14res.png "Respuesta del codigo ejemplo")

### Explicación:

- Tenemos una promesa que se resuelve después de 1 segundo y otra que se rechaza después de 500 ms.
- `Promise.race` rechazará la carrera cuando la promesa rechazada se complete primero.
