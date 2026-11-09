# Product Backlog - TiendaOnline

## Sprint 0: Configuración Base e Investigación

- [x] Configurar la estructura de archivos y carpetas del proyecto.
- [x] Ajustar el `package.json` con scripts de compilación de Sass y arranque de servidor (`start`).
- [x] Definir e ignorar archivos compilados y variables de entorno en `.gitignore`.
- [ ] **Investigación de API para E-commerce:**
  - _Objetivo:_ Definir la API o servicios backend para gestión de productos, carrito de compras y autenticación.
  - _Opciones analizadas:_
    1. **API REST propia (Express + Base de Datos):** Creación de endpoints `/api/products`, `/api/cart`, `/api/users` estructurados con arquitectura en capas (`controllers`, `services`, `routes`).
    2. **FakestoreAPI / DummyJSON (para prototipado):** Consumo de APIs públicas de prueba para validar renderizado dinámico en cliente (`js/api/`) antes de integrar la base de datos definitiva.
  - _Resultado / Decisión:_ Desarrollar una API REST nativa con Express en el directorio `server/`, usando servicios e inyección de datos para manejar productos y órdenes.

## Sprint 1: MVP Backend & Frontend Inicial

- [ ] Implementar el servidor básico de Express en `server/index.js`.
- [ ] Crear las rutas y controladores para listar productos en `server/controllers/` y `server/routes/`.
- [ ] Diseñar el layout global responsivo con SASS y Bootstrap (`scss/layout/`, `scss/components/`).
- [ ] Implementar la vista del catálogo de productos (`public/pages/`).

## Sprint 2: Lógica de Carrito y Detalles

- [ ] Crear módulo cliente `js/api/` para peticiones `fetch`.
- [ ] Desarrollar interfaz del carrito de compras y modal interactivo.
- [ ] Configurar variables de entorno `.env` para puertos y credenciales de base de datos.
