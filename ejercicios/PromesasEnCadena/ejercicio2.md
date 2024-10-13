# Ejercicio 2

## Convertir temperaturas

Crea una función celsiusToFahrenheit que convierta grados Celsius a Fahrenheit y devuelva una promesa. Encadena dos conversiones de Celsius a Fahrenheit.

### Respuesta 

```
function celsiusToFahrenheit(celsius) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(celsius * 9 / 5 + 32);
    }, 1000);
  });
}

// Uso
celsiusToFahrenheit(0)
  .then(fahrenheit => celsiusToFahrenheit(25))
  .then(fahrenheit25 => console.log(fahrenheit25)); // Debería imprimir 77

```

### Explicación: 

- `celsiusToFahrenheit` convierte una temperatura de Celsius a Fahrenheit y devuelve una promesa con el resultado.
- Se realiza la conversión de 0 °C, pero no se imprime porque encadenamos otra conversión para 25 °C.
- La conversión de 25 °C a Fahrenheit se completa e imprime 77 (25 * 9/5 + 32).

### Resultado 

![Texto alternativo](../../src/Ejercicio1res.png "Respuesta del codigo ejemplo")

