# Bitácora de Aprendizaje - TiendaOnline

**Autor:** Edward Caicedo

En esta bitácora registro mi evolución técnica, las decisiones de arquitectura, la organización del backend y las respuestas a las preguntas de profundización del proyecto.

---

## 1. Decisiones de Arquitectura y Estructura para MongoDB

Para soportar el modelo de datos con Mongoose y mantener una arquitectura limpia y escalable en el servidor, he creado físicamente las siguientes carpetas dentro de `server/`:

- **`server/config/`**: Contiene la configuración de servicios externos, específicamente la conexión a la base de datos (`db.js`).
- **`server/models/`**: Aloja los esquemas y modelos de datos de Mongoose (`Product.model.js`, `User.model.js`).
- **`server/seeders/`**: Aloja los scripts de siembra para poblar MongoDB con productos de prueba y el usuario administrador inicial.

---

## 2. Resolución del Conflicto de Producción (Sass en Dependencias y Script `prestart`)

- **El problema:** En entornos de producción (como servicios de despliegue), comúnmente se ejecuta `npm install` omitiendo las `devDependencies`. Si `sass` hubiera estado en `devDependencies`, el despliegue habría fallado al intentar compilar los estilos.
- **La solución adoptada:** Moví la librería `sass` a las **`dependencies`** principales del `package.json` y creé un script **`prestart`** (`"prestart": "npm run sass:build"`). De este modo, cuando el servidor o un usuario ejecute `npm start`, Node.js ejecutará la compilación del SASS al vuelo de forma totalmente integrada y segura antes de levantar Express.

---

## 3. Respuestas a Preguntas Técnicas Clave

- **¿Por qué el punto de entrada (`main`) es `server/index.js`?**
  Para separar la estructura del cliente (`public`, `scss`) del backend en `server/`.

- **¿Dónde van las variables SASS personalizadas en relación con Bootstrap?**
  Van **siempre antes** de importar Bootstrap, aprovechando la directiva `!default` para sobreescribir los valores por defecto del framework.

- **¿Cómo se procesará la seguridad de las contraseñas?**
  Se cifrarán mediante el uso de **`bcrypt`** generando hashes seguros en el script de siembra y comparándolos con `bcrypt.compare()` durante el endpoint de inicio de sesión del administrador.
