```markdown
# Product Backlog - TiendaOnline

## Meta del Sprint 1 (Demostrable)

> Al finalizar este sprint, el cliente podrá visualizar en la interfaz web un catálogo de productos estilizado con Bootstrap y SASS, cuyos datos provienen de una base de datos MongoDB poblada mediante un script de siembra inicial.

---

## Sprint 1 (Sprint Actual - MVP Catálogo y Estilos)

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
  - El seeder inserta al menos 3 productos de prueba (con campos `name`, `price`, `stock`, `image`) y un usuario administrador por defecto (con contraseña cifrada mediante `bcrypt`).

### HU-01: Visualización del Catálogo con Estilos Base

- **Como** cliente de la tienda,
- **quiero** consultar un listado de productos en una interfaz moderna y responsiva
- **para** poder explorar los artículos disponibles visualmente.
- **Prioridad:** Alta (1)
- **Criterios de Aceptación:**
  - Endpoint funcional `GET /api/products` que devuelva los productos almacenados en MongoDB.
  - El frontend consume el endpoint y renderiza tarjetas visuales aplicando la rejilla de diseño y componentes personalizados de Bootstrap 5 y SASS.

---

## Sprint 2 (Siguientes Iteraciones - Autenticación y Admin)

### HU-02: Autenticación de Administrador

- **Como** administrador del sistema,
- **quiero** iniciar sesión enviando mis credenciales en texto plano
- **para** que el servidor valide la contraseña contra el hash almacenado y me otorgue un token de acceso (JWT).
- **Prioridad:** Media (2)
- **Criterios de Aceptación:**
  - Endpoint `POST /api/auth/login` que compara la contraseña enviada con la del usuario admin en MongoDB usando `bcrypt.compare()`.
  - Retorna un token JWT válido si las credenciales son correctas.

### HU-03: Control de Acceso por Roles (Middleware)

- **Como** desarrollador,
- **quiero** implementar un middleware de autorización
- **para** proteger las rutas del panel de control permitiendo el acceso únicamente a usuarios con el rol `admin`.
- **Prioridad:** Baja (3)
- **Criterios de Aceptación:**
  - El middleware intercepta solicitudes, verifica el token JWT y valida que `role === 'admin'`.

---

## Product Backlog (Futuro)

- **HU-04:** Como cliente, quiero ver el detalle de un producto al seleccionarlo.
- **HU-05:** Como cliente, quiero agregar productos a un carrito de compras.
- **HU-06:** Como administrador, quiero registrar o modificar productos desde el dashboard.
```
