
# Ejercicio 1: Crear una promesa que se resuelve después de 2 segundos

**Descripción:**
Este ejercicio introduce el concepto básico de una promesa que se resuelve después de un cierto tiempo, en este caso 2 segundos. Es una excelente manera de entender el flujo de las promesas.

```javascript
let promesa = new Promise(resolve => {
    setTimeout(() => {
        resolve("Operación exitosa");
    }, 2000);
});

promesa.then(result => console.log(result));
```

**Explicación:**
- `Promise` es una función que toma dos argumentos: `resolve` y `reject`.
- En este caso, la promesa se resuelve (`resolve`) después de 2 segundos.
- El método `.then()` se usa para ejecutar código una vez que la promesa ha sido resuelta.
            