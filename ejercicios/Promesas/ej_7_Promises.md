
# Ejercicio 7: Ejecutar operaciones asíncronas y manejar errores

**Descripción:**
Este ejercicio muestra cómo manejar múltiples operaciones asíncronas y gestionar los errores que puedan ocurrir en cualquiera de ellas.

```javascript
function operacion1() {
    return new Promise((resolve, reject) => {
        setTimeout(() => resolve("Operación 1 exitosa"), 1000);
    });
}

function operacion2() {
    return new Promise((resolve, reject) => {
        setTimeout(() => reject("Operación 2 fallida"), 2000);
    });
}

operacion1()
    .then(result => {
        console.log(result);
        return operacion2();
    })
    .catch(error => console.error(error));
```

**Explicación:**
- La primera operación es exitosa y la segunda falla.
- Si ocurre un error en cualquiera de las promesas, se captura en el `.catch()`.
            