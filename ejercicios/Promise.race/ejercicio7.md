# Ejercicio 7
## Carrera de promesas con rechazo y éxito
Objetivo: Comparar un caso donde hay múltiples promesas y una es rechazada.

### Respuesta
```
const promise1 = new Promise((resolve) => setTimeout(() => resolve('Promesa 1'), 2000));
const promise2 = new Promise((resolve) => setTimeout(() => resolve('Promesa 2'), 1000));
const failingPromise = new Promise((_, reject) => setTimeout(() => reject('Falló'), 1500));

Promise.race([promise1, promise2, failingPromise])
.then(result => console.log(result))
.catch(error => console.log(error)); 
```
### Resultado 

![Texto alternativo](../../src/Ejercicio15res.png "Respuesta del codigo ejemplo")

### Explicación:

- Aquí tenemos tres promesas: dos que se resuelven y una que se rechaza.
- La segunda promesa se resuelve primero, por lo que el error de la promesa fallida no se ejecuta.
