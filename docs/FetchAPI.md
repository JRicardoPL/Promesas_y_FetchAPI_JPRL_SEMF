# Fetch API 

La Fetch API proporciona una interfaz JavaScript para acceder y manipular partes del canal HTTP, como peticiones y respuestas. Es una alternativa moderna y más potente a XMLHttpRequest para realizar solicitudes de red asíncronas.

Utiliza el método global `fetch()` para realizar solicitudes de red. Este método devuelve una Promise que se resuelve con un objeto Response, permitiendo un manejo más fluido de las operaciones asíncronas.

## Sintaxis básica

La sintaxis más simple de fetch es:

```javascript
fetch(url)
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## Objetos clave

- **Request**: Representa una solicitud de recurso.
- **Response**: Representa la respuesta a una solicitud.
- **Headers**: Permite manipular los encabezados de la solicitud y la respuesta.

## Realizar una solicitud GET

```javascript
fetch('https://api.ejemplo.com/datos')
  .then(response => {
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('Fetch error:', error));
```

## Realizar una solicitud POST

```javascript
fetch('https://api.ejemplo.com/datos', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    nombre: 'Juan',
    edad: 30
  })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

## Manejo de respuestas

El objeto Response proporciona varios métodos para manejar el cuerpo de la respuesta:

- `response.json()`: Interpreta la respuesta como JSON.
- `response.text()`: Devuelve la respuesta como texto.
- `response.blob()`: Devuelve la respuesta como un objeto Blob.
- `response.formData()`: Interpreta la respuesta como un objeto FormData.
- `response.arrayBuffer()`: Devuelve la respuesta como un ArrayBuffer.

## Configuración de solicitudes

Fetch permite configurar varios aspectos de la solicitud:

```javascript
fetch(url, {
  method: 'GET', // *GET, POST, PUT, DELETE, etc.
  mode: 'cors', // no-cors, *cors, same-origin
  cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
  credentials: 'same-origin', // include, *same-origin, omit
  headers: {
    'Content-Type': 'application/json'
  },
  redirect: 'follow', // manual, *follow, error
  referrerPolicy: 'no-referrer', // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
  body: JSON.stringify(data) // body data type must match "Content-Type" header
})
```

## Manejo de errores

Fetch considera como error solo los fallos de red. Errores HTTP (como 404 o 500) no causan el rechazo de la promesa. Es importante verificar `response.ok` o `response.status`.

```javascript
fetch(url)
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return response.json();
  })
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

## Cancelación de solicitudes

Fetch no proporciona una forma directa de cancelar una solicitud. Sin embargo, se puede usar AbortController para lograr esto:

```javascript
const controller = new AbortController();
const signal = controller.signal;

fetch(url, { signal })
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Fetch aborted');
    } else {
      console.error('Error:', error);
    }
  });

// Cancelar la solicitud
controller.abort();
```

## Uso con async/await

Fetch se puede usar de manera más limpia con async/await:

```javascript
async function obtenerDatos() {
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  }
}
```

## Ventajas de Fetch API

- Sintaxis más simple y moderna que XMLHttpRequest.
- Basada en Promesas, lo que facilita el encadenamiento de operaciones y el manejo de errores.
- Mejor integración con otras APIs modernas de JavaScript.
- Más flexible y potente para configurar solicitudes.

## Limitaciones

- No soportada en navegadores muy antiguos (aunque hay polyfills disponibles).
- No tiene progreso de carga incorporado (aunque se puede implementar con otras APIs).
- El manejo de timeouts requiere implementación adicional.

Ofrece una interfaz más limpia y basada en Promesas en comparación con las alternativas más antiguas, lo que la hace ideal para aplicaciones web modernas que requieren comunicación eficiente con servidores.