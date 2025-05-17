# Proyecto_Auditoria

# Plataforma de Registro Inicial para Atención en Salud

---

## Introducción

Este sistema permite la gestión de usuarios de diferente rol, inventario y asignación citas médicas, diseñado con niveles de acceso diferenciados para garantizar la seguridad y control administrativo.

---

## 1. Configuración Inicial

### Creación del archivo de conexión a la base de datos

Para iniciar, debe crear el archivo `conexion.php` en la raíz del proyecto, configurando la conexión a su base de datos PostgreSQL. 
 

## 2. Importación de la base de datos

El proyecto incluye un archivo llamado `tablas.sql` que contiene las sentencias SQL necesarias para crear las tablas y relaciones del sistema.

Debe importar estas consultas en su base de datos PostgreSQL para crear las siguientes estructuras fundamentales:

- Tabla `usuarios`
- Tabla `citas`
- Tabla `inventario`

Este paso es imprescindible para que el sistema funcione correctamente.

## 3. Flujo de Usuario y Funcionalidades

### 3.1. Primer acceso: Creación del Superusuario

En la pantalla de login encontrará un botón en la parte superior para crear el primer usuario de tipo superusuario.

Este usuario tendrá privilegios para gestionar el sistema.

Una vez creado, deberá iniciar sesión utilizando su usuario o correo electrónico y la contraseña configurada.

### 3.2. Panel de Superusuario

Al ingresar, el superusuario dispondrá de dos opciones principales:

**a) Crear Usuarios**

Puede crear usuarios de dos tipos:

- Superusuario  
- Digitador

Los datos requeridos para cada usuario corresponden a la tabla `usuarios`.

**b) Gestionar Usuarios**

Permite actualizar la información de cualquier usuario con rol doctor, paciente o digitador.

No es posible modificar usuarios con rol superusuario para preservar los niveles de acceso.

### 3.3. Panel de Digitador

Una vez creado un usuario digitador, podrá iniciar sesión con su usuario o correo y contraseña. En su panel encontrará tres opciones:

**a) Actualizar Contraseña**

El digitador podrá cambiar su contraseña. Al hacerlo, el sistema cerrará sesión automáticamente para que ingrese nuevamente con la nueva contraseña, garantizando seguridad.

**b) Agendar Citas**

El digitador podrá agendar citas médicas para pacientes.

Primero, buscará al paciente mediante su número de identificación.

Si el paciente existe, el formulario se autocompletara con su nombre y se podra llenar con sus datos para la cita que se desea agendar.

Las citas se almacenan en la tabla `citas`.

**c) Gestión de Inventario**

El digitador dispone de tres funcionalidades para el inventario:

- **Visualizar Inventario**  
  Muestra el inventario actual si existen registros; en caso contrario, muestra un mensaje indicando que no hay registros.

- **Subir Inventario vía Archivo CSV**  
  Permite importar registros desde un archivo CSV.  
  *Nota importante:* Para que la importación funcione correctamente, los `id` en el archivo CSV deben existir previamente en la base de datos; de lo contrario, se marcarán como error.

- **Agregar Elementos Manualmente**  
  Permite registrar manualmente nuevos elementos mediante formulario.

Los elementos del inventario se almacenan en la tabla inventario.

## 4. Seguridad y Validaciones

- Se utiliza `htmlspecialchars()` para el escapado de salida HTML, previniendo vulnerabilidades XSS.  
- Validación estricta de todos los campos de entrada para garantizar la integridad de datos.  
- Contraseñas almacenadas utilizando `password_hash()`, garantizando cifrado seguro.  
- Solo usuarios autorizados pueden acceder a funciones sensibles, reforzando control de acceso.

## 5. Requisitos del Sistema

- PHP 7.4 o superior  
- PostgreSQL como sistema de gestión de base de datos  
- Servidor web compatible, como Apache (puede usarse XAMPP para desarrollo local)  
- Navegador moderno para interfaz de usuario

## 6. Notas Finales

Este sistema está diseñado con altos estándares de seguridad y usabilidad para asegurar un manejo eficiente de la información sensible, facilitando el trabajo de superusuarios y digitadores.

