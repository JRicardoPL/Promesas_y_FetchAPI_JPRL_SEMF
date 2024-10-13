# Fetch de Blobs

Un objeto Blob representa un objeto tipo fichero de datos planos inmutables. Los Blobs representan datos que no necesariamente se encuentran en un formato nativo de JavaScript. La interfaz File se encuentra basada en un Blob, heredando y expendiendo la funcionalidad de un Blob para soportar archivos en el sistema del usuario.

Una forma fácil de construir un Blob es invocando el constructor Blob().
# Blob()
El constructor Blob() retorna un nuevo objeto Blob . El contenido del blob consiste en la concatenación de los valores obtenidos en el parrametro array.

# Constructor
Blob()
Regresa un nuevo objeto Blob creado cuyo contenido consiste en la concatenación de un arreglo de valores establecidos en el parámetro de la función.

# Propiedades
Blob.size 
El tamaño, en bytes, de los datos contenidos en el objeto Blob

Blob.type 
Una cadena (String) indicando el tipo MIME de los datos contenidos en el Blob. Si el tipo es desconocido, esta cadena será vacía.

# Métodos
Blob.slice()
Regresa un nuevo objeto Blob conteniendo los datos de un rango específico de bytes del origen del Blob.

# Ejemplos
## Ejemplo de uso de un constructor de Blob
El siguiente código:

```
var aFileParts = ['<a id="a"><b id="b">hey!</b></a>'];
var oMyBlob = new Blob(aFileParts, { type: "text/html" }); // the blob
```

es equivalente a:

```
var oBuilder = new BlobBuilder();
var aFileParts = ['<a id="a"><b id="b">hey!</b></a>'];
oBuilder.append(aFileParts[0]);
var oMyBlob = oBuilder.getBlob("text/xml"); // the blob
```

# Ejemplo para crear una URL en un arreglo tipado utilizando un blob
El siguiente código:

```
var typedArray = GetTheTypedArraySomehow();
var blob = new Blob([typedArray], { type: "application/octet-binary" }); // pass a useful mime type here
var url = URL.createObjectURL(blob);
// url will be something like: blob:d3958f5c-0777-0845-9dcf-2cb28783acaf
// now you can use the url in any context that regular URLs can be used in, for example img.src, etc.
```

# Ejemplo para extraer datos de un Blob
La única manera de leer contenido de un Blob es utilizando un FileReader. El siguiente código lee el contenido de un Blob como un arreglo tipado.

```
var reader = new FileReader();
reader.addEventListener("loadend", function () {
  // reader.result contains the contents of blob as a typed array
});
reader.readAsArrayBuffer(blob);
```

Al utilizar otros métodos de FileReader, es posible leer los contenidos del Blob como una cadena o una URL de datos.

# Referencias 

https://developer.mozilla.org/es/docs/Web/API/Blob