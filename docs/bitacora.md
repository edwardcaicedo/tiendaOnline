# Bitácora de Aprendizaje - TiendaOnline

**Autor:** Edward Caicedo

En esta bitácora registro mi evolución técnica, las decisiones de arquitectura que tomo y las respuestas a las preguntas de profundización del proyecto.

---

## 1. Decisiones Técnicas y Respuestas a Preguntas Clave

- **¿Por qué el punto de entrada (`main`) cambió a `server/index.js`?**
  Porque quise mantener una separación limpia entre la estructura del cliente (`public`, `scss`) y el backend. Al estar todo el código del servidor en la carpeta `server/`, el archivo que inicializa Express debe ser `server/index.js`.

- **¿Por qué `sass` está en `devDependencies`?**
  Porque Sass es un compilador que solo utilizo en la fase de desarrollo para transformar mis archivos `.scss` en un archivo CSS final (`public/css/styles.css`). En producción, Node.js no necesita compilar estilos; solo sirve el CSS estático ya generado.

- **¿Por qué la carpeta `public/css/` se ignora en Git?**
  Para evitar subir archivos generados automáticamente (artefactos derivados). Si los subiera, cada vez que modifique un `.scss` y lo compile se generarían conflictos molestos en Git (_merge conflicts_). Es mejor que cada entorno compile su propio CSS.

- **¿Tus variables van antes o después de importar Bootstrap?**
  Mis variables personalizadas de SASS van **siempre antes** de importar Bootstrap. Esto funciona porque Bootstrap utiliza la directiva `!default` en sus variables, lo que le permite aceptar mis valores personalizados si ya fueron declarados previamente.

- **¿Cuál es la diferencia entre `server/services/` (backend) y `public/js/api/` (frontend)?**
  - `server/services/` vive en el backend y contiene la lógica de negocio pura (por ejemplo, conectarse a MongoDB, hacer consultas con Mongoose o procesar cálculos de datos).
  - `public/js/api/` vive en el cliente (navegador) y contiene funciones con `fetch()` encargadas exclusivamente de hacer peticiones HTTP hacia los endpoints expuestos por mi API.

- **Si alguien clona tu repo y corre `npm start`, ¿qué verá y por qué?**
  Si clonan el repositorio y ejecutan `npm start` de inmediato, el servidor Express arrancará y responderá a la API, pero la interfaz web **se verá sin estilos (sin diseño CSS)**. Esto ocurre porque la carpeta `public/css/` está ignorada en el `.gitignore` y los archivos compilados no viajan en el repositorio. Para solucionarlo, el usuario debe ejecutar primero `npm run sass:build` para generar el archivo `styles.css`.

- **¿Cómo se almacenarán las contraseñas de manera segura?**
  Las contraseñas de los usuarios nunca se guardarán en texto plano. Utilizaré la librería **`bcrypt`** para aplicar un hash con sal (_salt_) a la contraseña antes de guardarla en MongoDB, y al momento del login compararé el hash almacenado con la contraseña ingresada.
