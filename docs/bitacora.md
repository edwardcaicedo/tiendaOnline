# Bitácora del Proyecto - TiendaOnline

## Registro de Actividades

### Día 1: Configuración Inicial y Estructura del Proyecto

- **Fecha:** [Inserta la fecha de hoy]
- **Actividades realizadas:**
  - Creación de la estructura de directorios del proyecto separando el entorno de cliente (`public`, `scss`) y servidor (`server`).
  - Inicialización del gestor de paquetes de Node.js (`package.json`).
  - Instalación de las dependencias clave para el desarrollo:
    - **Express** (^5.3.0) para la creación del servidor web y manejo de rutas.
    - **Dotenv** (^18.0.10) para el manejo seguro de variables de entorno.
    - **Sass** (^1.108.1) para la compilación de estilos avanzados.
    - **Bootstrap** (^5.3.8) como framework de diseño responsivo.
  - Configuración del script `sass:watch` en el `package.json` para compilar automáticamente los archivos `.scss` ubicados en `scss/main.scss` hacia el archivo compilado `public/css/styles.css`.
  - Creación de archivos de control y configuración inicial: `.gitignore`, `.env.example`, y la documentación base (`README.md`, `backlog.md`, `bitacora.md`).

- **Observaciones / Decisiones técnicas:**
  - Se optó por una arquitectura modular tanto en los estilos (metodología SASS por carpetas) como en el backend (`controllers`, `middlewares`, `routes`, `services`) para facilitar el mantenimiento y crecimiento escalable de la tienda online.

- **Próximos pasos:**
  - Configurar las variables de entorno en el archivo `.env`.
  - Levantar el servidor básico en `server/index.js`.
