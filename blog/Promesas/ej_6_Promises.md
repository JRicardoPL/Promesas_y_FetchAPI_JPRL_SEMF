
# Ejercicio 6: Simular la búsqueda de datos con promesas

**Descripción:**
Este ejercicio simula la búsqueda de datos, donde la operación tarda 3 segundos y la promesa se resuelve con un objeto que representa los datos encontrados.

```javascript
function buscarDatos() {
    return new Promise(resolve => {
        setTimeout(() => {
            resolve({ id: 1, nombre: "Producto" });
        }, 3000);
    });
}

buscarDatos().then(datos => console.log(datos));
```

**Explicación:**
- La función `buscarDatos` retorna una promesa que se resuelve con un objeto de datos.
- Después de 3 segundos, los datos se muestran en la consola.
            