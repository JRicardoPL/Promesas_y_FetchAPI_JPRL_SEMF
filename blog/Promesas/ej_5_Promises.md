
# Ejercicio 5: Simular inicio de sesión con promesas

**Descripción:**
Este ejercicio introduce una promesa que simula un sistema de autenticación. Si el usuario y la contraseña son correctos, la promesa se resuelve; de lo contrario, se rechaza.

```javascript
function iniciarSesion(usuario, contraseña) {
    return new Promise((resolve, reject) => {
        if (usuario === "admin" && contraseña === "1234") {
            resolve("Inicio de sesión exitoso");
        } else {
            reject("Usuario o contraseña incorrectos");
        }
    });
}

iniciarSesion("admin", "1234")
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

**Explicación:**
- Se valida el usuario y contraseña dentro de la promesa.
- Si las credenciales son correctas, se resuelve la promesa; de lo contrario, se rechaza.
            