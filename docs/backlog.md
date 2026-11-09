```markdown
# Product Backlog - TiendaOnline

## Meta del Sprint 1 (Demostrable)

> Al finalizar este sprint, el cliente podrá visualizar en la interfaz web un catálogo inicial de productos cargados desde la base de datos MongoDB, y el administrador podrá iniciar sesión de forma segura para validar su acceso al sistema.

---

## Sprint 1 (Sprint Actual)

### Tarea Técnica 01: Configuración del Servidor y Base de Datos

- **Tipo:** Tarea de Infraestructura
- **Descripción:** Configurar el servidor base de Express, conectar la aplicación a MongoDB usando Mongoose y estructurar las variables de entorno con `dotenv`.
- **Criterios de Aceptación:**
  - El servidor arranca correctamente con `npm start` en el puerto configurado.
  - La conexión a MongoDB se establece sin errores en la consola.

### HU-01: Visualización del Catálogo de Productos

- **Como** cliente de la tienda,
- **quiero** consultar un listado de productos disponibles en la interfaz web
- **para** poder explorar los artículos que ofrece el e-commerce.
- **Prioridad:** Alta (1)
- **Criterios de Aceptación:**
  - Endpoint funcional `GET /api/productos` que devuelva un arreglo JSON con los productos de MongoDB.
  - La base de datos cuenta con un script de siembra (_seeder_) que inserta al menos 3 productos de prueba con campos: `nombre`, `precio`, `stock` y `imagen`.
  - El frontend consume el endpoint y renderiza los productos en tarjetas visuales.

### HU-02: Autenticación de Administrador

- **Como** administrador del sistema,
- **quiero** iniciar sesión con mis credenciales
- **para** obtener un token de acceso que me permita ingresar a las rutas de gestión.
- **Prioridad:** Alta (2)
- **Criterios de Aceptación:**
  - Endpoint `POST /api/auth/login` que recibe correo y contraseña cifrada con `bcrypt`.
  - Si las credenciales son correctas, el sistema retorna un token **JWT (JSON Web Token)**.

### HU-03: Protección de Rutas por Roles

- **Como** desarrollador,
- **quiero** implementar un middleware de autorización
- **para** garantizar que solo los usuarios con rol de `admin` puedan acceder a las funciones del panel de control.
- **Prioridad:** Media (3)
- **Criterios de Aceptación:**
  - El middleware valida la existencia y validez del token JWT y comprueba que `role === 'admin'`.

---

## Product Backlog (Historias Futuras)

### Historias de Cliente (E-commerce)

- **HU-04:** Como cliente, quiero hacer clic en un producto para ver su detalle completo y descripción.
- **HU-05:** Como cliente, quiero agregar y eliminar productos de mi carrito de compras para simular un proceso de compra.

### Historias de Administrador (Dashboard)

- **HU-06:** Como administrador, quiero registrar nuevos productos o modificar el stock existente desde el panel de control.
- **HU-07:** Como administrador, quiero consultar el listado de pedidos o ventas registradas en la tienda.
```
