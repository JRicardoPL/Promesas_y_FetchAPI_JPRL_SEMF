
# Ejercicio 3: Promesa que se resuelve o rechaza según un número aleatorio

**Descripción:**
Este ejercicio introduce la lógica condicional dentro de una promesa. Según el valor de un número aleatorio, la promesa se resuelve o se rechaza.

```javascript
function numeroAleatorio() {
    return new Promise((resolve, reject) => {
        let numero = Math.random();
        if (numero > 0.5) {
            resolve("Éxito, número mayor a 0.5");
        } else {
            reject("Error, número menor a 0.5");
        }
    });
}

numeroAleatorio()
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

**Explicación:**
- La función `Math.random()` genera un número entre 0 y 1.
- Si el número es mayor que 0.5, la promesa se resuelve; de lo contrario, se rechaza.
- Usamos `.then()` para manejar el éxito y `.catch()` para manejar el error.
            