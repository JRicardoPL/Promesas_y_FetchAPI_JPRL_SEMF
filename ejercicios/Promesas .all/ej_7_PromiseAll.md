
# Ejercicio 7: Promise.all

## Enunciado
Usa `Promise.all` para realizar múltiples solicitudes `fetch` a una API pública (por ejemplo, `https://jsonplaceholder.typicode.com/posts`). Extrae los títulos de los primeros 5 posts y muéstralos en la consola.

## Solución
```javascript
const fetchPosts = () => {
  const urls = [
    'https://jsonplaceholder.typicode.com/posts/1',
    'https://jsonplaceholder.typicode.com/posts/2',
    'https://jsonplaceholder.typicode.com/posts/3',
    'https://jsonplaceholder.typicode.com/posts/4',
    'https://jsonplaceholder.typicode.com/posts/5'
  ];

  const fetchPromises = urls.map((url) => fetch(url).then((response) => response.json()));

  Promise.all(fetchPromises)
    .then((posts) => {
      const titles = posts.map(post => post.title);
      console.log('Títulos de los primeros 5 posts:', titles);
    })
    .catch((error) => {
      console.error('Error al obtener los posts:', error);
    });
};

fetchPosts();
```

## Explicación
Se hace un `fetch` de 5 URLs que representan diferentes posts. `Promise.all` espera a que todas las respuestas se completen y luego extrae los títulos de cada post para mostrarlos.

**Salida esperada:**
```
Títulos de los primeros 5 posts: ["Título 1", "Título 2", "Título 3", "Título 4", "Título 5"]
```
    