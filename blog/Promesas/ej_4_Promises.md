
# Ejercicio 4: Encadenar dos promesas con tiempos diferentes

**Descripción:**
Aquí se muestra cómo encadenar promesas. La segunda promesa se ejecuta solo después de que la primera haya sido resuelta.

```javascript
let promesa1 = new Promise(resolve => setTimeout(resolve, 1000, "Promesa 1 completa"));

promesa1.then(result => {
    console.log(result);
    return new Promise(resolve => setTimeout(resolve, 2000, "Promesa 2 completa"));
}).then(result => console.log(result));
```

**Explicación:**
- La primera promesa se resuelve después de 1 segundo.
- En el `.then()` de la primera promesa, se inicia la segunda, que se resuelve después de 2 segundos.
- El encadenamiento de promesas es útil para ejecutar operaciones secuenciales.
            