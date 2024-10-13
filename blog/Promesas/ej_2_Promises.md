
# Ejercicio 2: Crear una promesa que se rechaza después de 3 segundos

**Descripción:**
Este ejercicio introduce el concepto de rechazar promesas. Aquí, la promesa se rechaza después de 3 segundos, simulando un error en la operación.

```javascript
let promesa = new Promise((resolve, reject) => {
    setTimeout(() => {
        reject("Ocurrió un error");
    }, 3000);
});

promesa.catch(error => console.error(error));
```

**Explicación:**
- En este ejemplo, la promesa se rechaza (`reject`) después de 3 segundos.
- El método `.catch()` es utilizado para manejar errores en promesas rechazadas.
            