# Tienda Virtual - MugSolutions SAS 🛒

Plataforma de comercio electrónico avanzada desarrollada como un monolito robusto por los socios de **MugSolutions SAS** en **Villavicencio, Meta, Colombia (2026)**. Este sistema está diseñado bajo estrictos estándares de arquitectura de software, seguridad informática y control transaccional para garantizar una operación comercial altamente confiable y resistente a fallos.

---

## 🏗️ Stack Tecnológico (Monolito Next.js)

* **Framework Full-Stack:** [Next.js](https://nextjs.org/) (App Router, Server Actions, API Routes)
* **Lenguaje:** TypeScript
* **Estilos:** Tailwind CSS
* **Base de Datos Principal:** PostgreSQL (Consistencia transaccional ACID)
* **Caché y Control de Concurrencia:** Redis (Bloqueos temporales e Idempotencia)
* **ORM / Query Builder:** Prisma o Drizzle ORM

---

## 🏛️ Arquitectura y Componentes del Sistema

### 1. Gestión de Inventarios y Bloqueo de Stock
* **Bloqueo Temporal:** Mecanismo de reserva de stock en Redis durante el proceso de pago para prevenir *race conditions* (sobreventa) cuando múltiples usuarios compran la última unidad disponible.
* **Control en Tiempo Real:** Actualización automatizada de existencias tras confirmar o cancelar una orden.
* **Alertas de Stock Bajo:** Notificaciones automáticas al panel de administración al alcanzar los umbrales mínimos.

### 2. Transaccionalidad y Confiabilidad (Idempotencia)
* **Idempotencia en la Compra:** Uso de *Idempotency Keys* en las peticiones de pago para asegurar que duplicidades por fallos de red o reintentos del cliente ejecuten el cargo una sola vez.
* **Control Transaccional (ACID):** Bloques atómicos en PostgreSQL donde el pago, la creación de la orden y el descuento de inventario ocurren de forma íntegra (reversión total ante cualquier fallo).

### 3. Seguridad y Metodologías Seguras
* **Secure SDLC:** Prácticas basadas en OWASP Top 10 desde la fase de diseño.
* **Autenticación Robusta:** JWT (Access Token / Refresh Token) con contraseñas cifradas mediante Argon2 o bcrypt.
* **Protección Integral:** Prevención contra Inyección SQL, XSS, CSRF y limitación de tasas (*Rate Limiting*) en endpoints críticos.

### 4. Roles y Control de Acceso (RBAC)
* **Cliente / Comprador:** Perfil, historial, seguimiento de envíos y carrito.
* **Administrador de Inventario:** Gestión de productos, categorías, precios y stock.
* **Administrador de Ventas / Operaciones:** Órdenes, estados de entrega y devoluciones.
* **Super Administrador:** Control total, usuarios, roles, permisos y configuraciones globales.

### 5. Carrito de Compras
* **Persistencia Híbrida:** Soporte para carritos en sesiones anónimas (LocalStorage/Cookies) con migración automática al iniciar sesión.
* **Cálculos Dinámicos:** Subtotales, cupones de descuento, impuestos y costos de envío geolocalizados.

### 6. Control, Auditoría y Monitoreo
* **Logs de Auditoría:** Registro detallado de acciones críticas administrativas y eventos del sistema.
* **Métricas:** Control de rendimiento de la API y detección de errores en tiempo real.

### 7. Sistema de Notificaciones
* **Canales Multiplataforma (Email / SMS / WhatsApp):** Confirmaciones de registro, recibos de compra con clave de idempotencia y actualizaciones de envíos.
* **Alertas Internas:** Avisos operacionales ante fallos de pasarela o caídas de inventario.

---

## 🚀 Guía de Configuración e Instalación

### Prerrequisitos
* Node.js (versión 18 o superior recomendada)
* Docker y Docker Compose (para levantar PostgreSQL y Redis localmente)

### 1. Clonar el repositorio y configurar variables de entorno
```bash
git clone [https://github.com/MugSolutions-SAS/MugShop.git](https://github.com/MugSolutions-SAS/MugShop.git)
cd MugShop
cp .env.example .env



### 2. Reglas de ORO 

FEAT: Feature, para todo lo referente a nuevas funcionalidades, modulos o secciones
FIX: Reparación, arreglos, mantenimientos de funcionalidades, modulos o secciones

##Notación 

FEAT/FIX[Seccion, modulo] : Descripción corta acción realizada


## Ramas

Main 

__Por definir notación de otras