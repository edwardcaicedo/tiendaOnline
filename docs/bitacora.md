# Bitácora de Aprendizaje - TiendaOnline

**Autor:** Edward Caicedo

En esta bitácora registro mi evolución técnica, las decisiones de arquitectura, la organización del backend y las respuestas a las preguntas de profundización del proyecto.

---

## 1. Decisiones de Arquitectura y Estructura para MongoDB

Para soportar el modelo de datos con Mongoose y mantener una arquitectura limpia y escalable en el servidor, he definido las siguientes carpetas dentro de `server/`:

- **`server/config/`**: Contiene la configuración de servicios externos, específicamente la conexión a la base de datos (`db.js` para la lógica de conexión con Mongoose).
- **`server/models/`**: Contiene los esquemas y modelos de datos de Mongoose (por ejemplo, `Product.model.js`, `User.model.js`), definiendo la estructura y tipos de las colecciones de MongoDB.
- **`server/seeders/`**: Aloja los scripts de siembra de datos (_seeders_), encargados de poblar la base de datos vacía con productos de prueba y el usuario administrador inicial.
- _Nota aclaratoria sobre `services/`:_ La lógica de conexión a la base de datos no es lógica de negocio, por lo que no va en `services/`. La carpeta `server/services/` se reservará exclusivamente para operaciones de negocio puras (como calcular totales de un carrito o procesar filtros complejos de búsqueda).

---

## 2. Resolución del Conflicto de Producción (Compilación de CSS y Script `prestart`)

- **El dilema:** Si la carpeta `public/css/` está ignorada en Git y `sass` vive en `devDependencies`, ¿cómo se genera el CSS en un servidor de producción que solo hace `npm install` y `npm start`?
- **La solución técnica:** Para solucionar esto de forma automatizada, utilizaré un script **`prestart`** en el `package.json`. Cuando ejecute `npm start`, Node.js ejecutará automáticamente primero el comando de compilación de Sass.

  ```json
  "scripts": {
    "prestart": "npm run sass:build",
    "start": "node server/index.js"
  }
  ```
