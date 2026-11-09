```markdown
# Product Backlog - TiendaOnline

## Meta del Sprint 1 (Demostrable)

> Al finalizar este sprint, el cliente podrá visualizar en la interfaz web un catálogo de productos estilizado con Bootstrap y SASS, cuyos datos provienen de una base de datos MongoDB poblada mediante un script de siembra inicial, y el administrador podrá autenticarse de forma segura.

---

## Sprint 1 (Sprint Actual - MVP, Estilos y Seguridad Base)

### Tarea Técnica 01: Configuración de Infraestructura y Conexión a Base de Datos

- **Tipo:** Tarea Técnica
- **Descripción:** Configurar el servidor base de Express, establecer la conexión a MongoDB mediante Mongoose (`server/config/db.js`) y estructurar las variables de entorno con `dotenv`.
- **Criterios de Aceptación:**
  - El servidor arranca correctamente con `npm start`.
  - La conexión a la base de datos se reporta exitosa en consola.

### Tarea Técnica 02: Script de Siembra (Seeder) de Datos Iniciales

- **Tipo:** Tarea Técnica
- **Descripción:** Desarrollar un script en `server/seeders/` para poblar MongoDB con datos iniciales ejecutables por comando.
- **Criterios de Aceptación:**
  - El seeder inserta al menos 3 productos de prueba (con campos `name`, `price`, `stock`, `image`) y un usuario administrador inicial (`email`, `password` cifrada con `bcrypt`, `role: 'admin'`).

### HU-01: Visualización del Catálogo con Estilos Base

- **Como** cliente de la tienda,
- **quiero** consultar un listado de productos en una interfaz moderna y responsiva aplicando SASS y Bootstrap
- **para** poder explorar los artículos disponibles visualmente.
- **Prioridad:** Alta (1)
- **Criterios de Aceptación:**
  - Endpoint funcional `GET /api/products` que devuelva los productos almacenados en MongoDB.
  - El frontend consume el endpoint y renderiza tarjetas visuales aplicando la rejilla de diseño y componentes personalizados de Bootstrap 5 y SASS.

### HU-02: Autenticación de Administrador

- **Como** administrador del sistema,
- **quiero** iniciar sesión enviando mis credenciales
- **para** que el servidor valide la contraseña contra el hash almacenado y me otorgue un token de acceso (JWT).
- **Prioridad:** Alta (2)
- **Criterios de Aceptación:**
  - Endpoint `POST /api/auth/login` que compara la contraseña enviada con la del usuario admin en MongoDB usando `bcrypt.compare()`.
  - Retorna un token JWT válido si las credenciales son correctas.

### HU-03: Control de Acceso por Roles (Middleware de Seguridad)

- **Como** administrador autenticado,
- **quiero** que el sistema valide mi rol
- **para** asegurar que solo perfiles autorizados accedan a las funciones y rutas de gestión del panel de control.
- **Prioridad:** Alta (2)
- **Criterios de Aceptación:**
  - El middleware intercepta solicitudes a rutas protegidas, verifica el token JWT y valida estrictamente que `role === 'admin'`.

---

## Product Backlog (Futuro)

### Historias de Cliente (E-commerce)

- **HU-04:** Como cliente, quiero ver el detalle de un producto al seleccionarlo.
- **HU-05:** Como cliente, quiero agregar productos a un carrito de compras.

### Historias de Administrador (Dashboard y Ventas)

- **HU-06:** Como administrador, quiero registrar o modificar productos desde el dashboard.
- **HU-07:** Como administrador, quiero consultar el listado de pedidos o ventas registradas en la tienda para llevar el control comercial.
```
