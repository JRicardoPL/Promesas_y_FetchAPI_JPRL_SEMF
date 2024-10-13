# Promise.all 

`Promise.all` es un método estático de la clase Promise en JavaScript que permite manejar múltiples promesas de forma concurrente. Es una herramienta poderosa para trabajar con operaciones asíncronas que pueden ejecutarse en paralelo.

`Promise.all` toma un iterable (generalmente un array) de promesas como entrada y devuelve una nueva promesa. Esta promesa resultante se resuelve cuando todas las promesas en el iterable se han resuelto, o se rechaza si alguna de las promesas en el iterable se rechaza.

## Sintaxis

La sintaxis básica de Promise.all es la siguiente:

```javascript
Promise.all(iterable)
```

Donde `iterable` es típicamente un array de promesas.

## Comportamiento de resolución

Cuando todas las promesas en el iterable se resuelven con éxito, `Promise.all` se resuelve con un array que contiene los valores de resolución de todas las promesas, en el mismo orden en que fueron proporcionadas.

```javascript
const promesa1 = Promise.resolve(3);
const promesa2 = 42;
const promesa3 = new Promise((resolve) => setTimeout(resolve, 100, 'foo'));

Promise.all([promesa1, promesa2, promesa3])
  .then((valores) => {
    console.log(valores); // [3, 42, 'foo']
  });
```

## Manejo de errores

Si alguna de las promesas en el iterable se rechaza, `Promise.all` se rechaza inmediatamente con la razón de la primera promesa que se rechazó, sin esperar a que se resuelvan o rechacen las demás promesas.

```javascript
const p1 = Promise.resolve(3);
const p2 = new Promise((resolve, reject) => setTimeout(reject, 100, 'error'));
const p3 = 42;

Promise.all([p1, p2, p3])
  .then(valores => console.log(valores))
  .catch(error => console.error(error)); // Imprime: 'error'
```

## Casos de uso comunes

- Realizar múltiples solicitudes HTTP en paralelo y esperar a que todas se completen.
- Cargar varios recursos (como imágenes o archivos) simultáneamente.
- Ejecutar varias operaciones de base de datos independientes y procesar los resultados juntos.

## Ejemplo práctico: Carga de múltiples recursos

```javascript
const urls = [
  'https://api.ejemplo.com/datos1',
  'https://api.ejemplo.com/datos2',
  'https://api.ejemplo.com/datos3'
];

const promesasDeCarga = urls.map(url => fetch(url).then(resp => resp.json()));

Promise.all(promesasDeCarga)
  .then(resultados => {
    console.log('Todos los datos cargados:', resultados);
  })
  .catch(error => {
    console.error('Error al cargar los datos:', error);
  });
```

## Comportamiento con valores no-Promise

`Promise.all` también acepta valores no-Promise en el iterable. Estos valores se tratan como promesas ya resueltas.

```javascript
Promise.all([1, 2, Promise.resolve(3), Promise.resolve(4)])
  .then(valores => console.log(valores)); // [1, 2, 3, 4]
```

## Promise.all vs. bucles secuenciales

`Promise.all` es más eficiente que ejecutar promesas en un bucle secuencial cuando las operaciones son independientes entre sí, ya que permite que se ejecuten en paralelo.

## Limitaciones y consideraciones

- Si necesitas que todas las promesas se completen incluso si alguna falla, `Promise.all` no es adecuado. En su lugar, podrías usar `Promise.allSettled`.
- Para conjuntos muy grandes de promesas, considera dividirlas en grupos más pequeños para evitar sobrecargar los recursos del sistema.

## Alternativas a Promise.all

- `Promise.allSettled`: Similar a `Promise.all`, pero espera a que todas las promesas se resuelvan o rechacen, proporcionando el resultado de cada una.
- `Promise.race`: Se resuelve o rechaza tan pronto como una de las promesas en el iterable se resuelve o rechaza.
- `Promise.any`: Se resuelve tan pronto como una de las promesas en el iterable se resuelve, o se rechaza si todas las promesas se rechazan.


`Promise.all` Permite ejecutar tareas en paralelo y recopilar sus resultados de forma ordenada, mejorando significativamente el rendimiento en escenarios donde se requieren múltiples operaciones asíncronas independientes.