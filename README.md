# 📱 Kaffecito – App móvil para gestión de pedidos

**Kaffecito** es una aplicación móvil desarrollada con **Ionic React** y **TypeScript** para gestionar los pedidos en una cafetería.  
Está orientada al uso por parte de los **meseros**, quienes pueden iniciar sesión, ver productos, añadirlos a un carrito y enviar pedidos al backend, además de consultar y actualizar su estado.

---

## ✨ Características principales

- 🔐 **Autenticación de usuarios**
  - Login con cédula y contraseña.
  - Solo permite acceso a usuarios con rol **`mesero`**.
  - Manejo de errores de autenticación (credenciales incorrectas, token inválido, etc.).

- 🏠 **Pantalla de inicio (Home)**
  - Listado de **categorías de productos** desde la API.
  - Buscador por nombre/descripcion de categoría.
  - Menú lateral con opciones:
    - Inicio
    - Pedidos
    - Carrito
    - Cerrar sesión

- 🍽️ **Productos por categoría**
  - Visualización de productos de la categoría seleccionada.
  - Detalle de nombre, precio, descripción y stock.
  - Posibilidad de añadir productos al **carrito** con cantidad.

- 🛒 **Carrito de compras**
  - Gestión global del carrito con **Context API** (`CarritoContext`).
  - Modificar cantidades, eliminar productos.
  - Cálculo automático del total del pedido.
  - Envío del pedido al backend y limpieza del carrito al finalizar.

- 📋 **Gestión de pedidos**
  - Listado de pedidos desde la API.
  - Filtros por estado: `pendiente`, `en_proceso`, `completado`, `cancelado`, `todos`.
  - Orden: primero los pendientes y luego por fecha de creación.
  - Actualización del estado del pedido con mensajes de éxito/error.
  - Pull-to-refresh para recargar pedidos.

- 🎨 **Interfaz moderna**
  - Uso de componentes de **Ionic** con estilos adicionales en **TailwindCSS**.
  - Diseño adaptado a móviles (Android/iOS) y PWA.

---

## 🧰 Tecnologías utilizadas

- **Framework/UI:** Ionic React (`@ionic/react`)
- **Lenguaje:** TypeScript
- **Bundler:** Vite
- **Ruteo:** `react-router-dom`
- **Estado global:** Context API (`CarritoContext`)
- **Estilos:** TailwindCSS + tema de Ionic
- **HTTP Client:** Axios (servicio API con manejo de token)
- **Mobile:** Capacitor (para compilar a Android/iOS)
- **Testing (si se utiliza):** Vitest / Cypress

---

## 📁 Estructura principal del proyecto

```text
src/
├── pages/
│   ├── Login/         # Pantalla de autenticación
│   ├── Home/          # Listado de categorías + menú
│   ├── Productos/     # Productos por categoría
│   ├── Carrito/       # Carrito y confirmación de pedido
│   └── Pedidos/       # Gestión de pedidos y cambio de estado
├── services/
│   ├── api.service.ts       # Configuración base de Axios, tipos y utilidades
│   ├── auth.service.ts      # Login, manejo de token
│   ├── producto.service.ts  # Operaciones sobre productos
│   ├── categoria.service.ts # Operaciones sobre categorías
│   └── pedido.service.ts    # CRUD de pedidos
├── context/
│   └── CarritoContext.tsx   # Estado global del carrito
├── config.ts                # URL base de la API y helpers
├── App.tsx                  # Rutas principales
└── main.tsx                 # Punto de entrada de la app
