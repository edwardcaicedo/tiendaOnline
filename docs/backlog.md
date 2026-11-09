# Product Backlog - TiendaOnline

## Meta del Sprint 1

Configurar el entorno base del proyecto, estructurar la arquitectura modular de la API REST en Express y establecer las bases visuales del e-commerce para clientes y administradores.

---

## Sprint 1: Configuración, API Base y Estructuras

### HU-01: Estructura del Servidor Base

- **Como** desarrollador backend,
- **quiero** configurar un servidor con Express y variables de entorno
- **para** garantizar la comunicación inicial y la seguridad de las credenciales del sistema.
- **Prioridad:** Alta (1)
- **Criterios de Aceptación:**
  - El servidor arranca correctamente usando `npm start` apuntando a `server/index.js`.
  - Se utiliza `dotenv` para leer un archivo `.env` local sin exponer datos sensibles.
  - La estructura de carpetas incluye `controllers`, `routes`, `services` y `middlewares`.

### HU-02: Gestión del Catálogo de Productos (API)

- **Como** cliente de la tienda,
- **quiero** consultar un listado de productos disponibles a través de una API REST
- **para** poder visualizarlos en la interfaz web de la tienda.
- **Prioridad:** Alta (2)
- **Criterios de Aceptación:**
  - Endpoint funcional `GET /api/products` que retorne un JSON con la lista de productos.
  - Los productos incluyen campos estructurados: `id`, `nombre`, `precio`, `stock`, `categoria` e `imagen`.
  - Si la base de datos o el almacenamiento local está vacío temporalmente, se pueden sembrar datos iniciales (usando datos base adaptados de fuentes como DummyJSON).

### HU-03: Panel de Administración de Usuarios y Roles

- **Como** administrador de la tienda,
- **quiero** gestionar el acceso mediante roles específicos
- **para** proteger las rutas de administración del dashboard.
- **Prioridad:** Media (3)
- **Criterios de Aceptación:**
  - Existen diferenciaciones de usuario entre `cliente` y `admin`.
  - Middleware de autenticación y control de acceso por roles implementado en el backend.
