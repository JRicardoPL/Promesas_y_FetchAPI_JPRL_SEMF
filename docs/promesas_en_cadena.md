# Promesas en cadena

Una Promise (promesa en castellano) es un objeto que representa la terminación o el fracaso de una operación asíncrona. Dado que la mayoría de las personas consumen promises ya creadas, esta guía explicará primero cómo consumirlas, y luego cómo crearlas.

Esencialmente, una promesa es un objeto devuelto al cual se adjuntan funciones callback, en lugar de pasar callbacks a una función.

Encadenamiento
Una necesidad común es el ejecutar dos o más operaciones asíncronas seguidas, donde cada operación posterior se inicia cuando la operación previa tiene éxito, con el resultado del paso previo. Logramos esto creando una cadena de objetos promises.

Aquí está la magia: la función then() devuelve una promesa nueva, diferente de la original:

``` JS ```

``` 
    const promesa = hazAlgo(); 
    const promesa2 = promesa.then(exitoCallback, falloCallback); 
```

O

``` 
let promesa2 = hazAlgo().then(exitoCallback, falloCallback); 
```

Esta segunda promesa (promesa2) representa no sólo la terminación de hazAlgo(), sino también de exitoCallback o falloCallback que pasaste, las cuales pueden ser otras funciones asíncronas devolviendo una promesa. Cuando ese es el caso, cualquier función callback añadida a promesa2 se queda en cola detrás de la promesa devuelta por exitoCallback o falloCallback.

Básicamente, cada promesa representa la terminación de otro paso (asíncrono on no) en la cadena.

En el pasado, hacer varias operaciones asíncronas en fila conduciría a la clásica pirámide de funciones callback:

``` JS ```

```hazAlgo(function(resultado) {

-  hazAlgoMas(resultado, function(nuevoResultado) {

    hazLaTerceraCosa(nuevoResultado, function(resultadoFinal) {
      console.log('Obtenido el resultado final: ' + resultadoFinal

    }, falloCallback);

  }, falloCallback);

}, falloCallback);
```
Con las funciones modernas, adjuntamos nuestras functiones callback a las promesas devueltas, formando una cadena de promesa:
```
JS
hazAlgo()
  .then(function (resultado) {
    return hazAlgoMas(resultado);
  })
  .then(function (nuevoResultado) {
    return hazLaTerceraCosa(nuevoResultado);
  })
  .then(function (resultadoFinal) {
    console.log("Obtenido el resultado final: " + resultadoFinal);
  })
  .catch(falloCallback);
```

Los argumentos a then son opcionales, y catch(falloCallBack) es un atajo para then(null, falloCallBack). Es posible que veas esto expresado con funciones de flecha :

````
hazAlgo()
  .then((resultado) => hazAlgoMas(resultado))
  .then((nuevoResultado) => hazLaTerceraCosa(nuevoResultado))
  .then((resultadoFinal) => {
    console.log(`Obtenido el resultado final: ${resultadoFinal}`);
  })
  .catch(falloCallback);
```



# Referencias 

https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Using_promises