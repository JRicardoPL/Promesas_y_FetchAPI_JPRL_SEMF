
# Ejercicio 5: Promise.all

## Enunciado
Simula una operación de descarga de archivos usando `Promise.all` con tres promesas, cada una representando un archivo con diferentes tiempos de descarga. Muestra un mensaje cuando todas las descargas hayan finalizado.

## Solución
```javascript
const downloadFile = (fileName, time) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(`Descarga de ${fileName} completada`);
    }, time);
  });
};

const file1 = downloadFile('Archivo1', 2000);
const file2 = downloadFile('Archivo2', 3000);
const file3 = downloadFile('Archivo3', 1000);

Promise.all([file1, file2, file3])
  .then((results) => {
    console.log('Todas las descargas completadas:', results);
  })
  .catch((error) => {
    console.error('Error en la descarga de archivos:', error);
  });
```

## Explicación
Cada promesa simula la descarga de un archivo con diferentes tiempos. `Promise.all` se asegura de que el mensaje de finalización solo se muestre cuando todos los archivos se hayan descargado.

**Salida esperada después de 3 segundos:**
```
Todas las descargas completadas: ["Descarga de Archivo1 completada", "Descarga de Archivo2 completada", "Descarga de Archivo3 completada"]
```
    