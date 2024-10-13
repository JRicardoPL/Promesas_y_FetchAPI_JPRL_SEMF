
# Ejercicio 8: Simular procesamiento de pedidos con promesas encadenadas

**Descripción:**
En este ejercicio, cada paso de un proceso de compra (validación de stock, procesamiento de pago, y envío de producto) es una promesa que se encadena.

```javascript
function validarStock() {
    return new Promise(resolve => setTimeout(resolve, 1000, "Stock validado"));
}

function procesarPago() {
    return new Promise(resolve => setTimeout(resolve, 2000, "Pago procesado"));
}

function enviarProducto() {
    return new Promise(resolve => setTimeout(resolve, 3000, "Producto enviado"));
}

validarStock()
    .then(result => {
        console.log(result);
        return procesarPago();
    })
    .then(result => {
        console.log(result);
        return enviarProducto();
    })
    .then(result => console.log(result));
```

**Explicación:**
- La función `validarStock` simula la validación del stock.
- Luego se procesa el pago y finalmente se simula el envío del producto.
- Cada paso es una promesa que se encadena usando `.then()`.
            