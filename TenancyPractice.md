# Sistema Multi-CRUDilino con Laravel Tenancy

## Objetivo general
Construir un proyecto en Laravel con arquitectura multi-inquilino (multi-tenant) usando Laravel Tenancy, donde exista:
* Un dominio central (admin) para la gestión de tenants y usuarios.
* Varios tenants independientes, cada uno con su propio inventario de productos.
* Un catálogo público (landing page) y un panel de administración por tenant.

## Contexto del proyecto
La empresa MultiStore ofrece una plataforma donde diferentes negocios pueden tener su propia tienda online, totalmente aislada de las demás, pero administrada desde un dominio central.

Cada negocio (tenant) tiene:
* Su propio dominio o subdominio.
* Su propio inventario de productos.
* Un catálogo público.
* Un panel de administración privado.

## Arquitectura requerida
* Framework: Laravel (versión 10+ sugerida).
* Arquitectura: Multi-tenant con el paquete laravel-tenancy (stancl/tenancy).
* Base de datos: MySQL.
* Separación clara entre:
    * Dominio central.
    * Dominios de tenants.

## Dominio central (Admin principal)
Funcionalidades obligatorias:

### 1. Gestión de Tenants
CRUD completo de tenants que incluya:
* Crear, actualizar, eliminar e inhabilitar tenants.
* Atributos: Nombre, Dominio o subdominio, Tipo de negocio, Estado (activo / inactivo).

### 2. Gestión de administradores del dominio central
* Crear, listar, editar y eliminar administradores del dominio central.
* Autenticación independiente del tenant.

### 3. Gestión de administradores por tenant
Desde el dominio central se debe permitir:
* Listar los tenants creados.
* Ver los administradores asociados a cada tenant.
* CRUD de administradores de tenant.
* Asignar administradores a un tenant específico.

## Tenants (Tiendas)
Se deben crear 5 tenants diferentes para la entrega, por ejemplo:
1. Productos de cocina.
2. Ferretería.
3. Joyería.
4. Productos gamer.
5. Papelería (o tema libre).

## Módulo de Inventario (por tenant)
Cada tenant debe contar con un inventario independiente.
* Campos mínimos del producto: Imagen, Nombre, Descripción, Precio.
* Reglas: Los productos de un tenant no deben ser visibles en otro; cada tenant gestiona solo su propio inventario.

## Landing Page pública (por tenant)
Cada tenant debe tener una página de inicio accesible sin autenticación:
* Vista tipo catálogo de productos.
* Personalización básica: Nombre del negocio y elementos visuales simples (banner o colores).
* Ejemplo de acceso: cocina.tienda.com o ferreteria.tienda.com.

## Panel de Administración del Tenant
Cada tenant debe tener un panel privado para:
* Login de administrador del tenant.
* CRUD de productos (incluyendo subida de imágenes).
* Visualización del catálogo interno.

## Reglas técnicas
* Uso correcto de middleware de tenancy para la identificación de inquilinos.
* Separación de rutas: Archivos independientes para Central y Tenant.
* Uso de migraciones (centralizadas y de tenant).
* Buen uso de controladores y modelos.
* Código organizado y legible.

## Entregables
* Repositorio en GitHub.
* docker-compose
* Archivo README con:
    * Explicación del proyecto.
    * Pasos de instalación.
    * Cómo crear tenants y acceder a cada dominio.
* Evidencia de:
    * 5 tenants creados con inventario funcional.
    * Landing page pública por cada uno.

## Reto adicional (opcional)
* Implementación de Roles y Permisos.
* Cache por tenant.

---

by: crudzaso - "mas que solo crud"

![Eche](https://images.canal1.com.co/uploads/2018/04/silvestre.png)
