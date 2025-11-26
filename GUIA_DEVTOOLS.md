# 📘 Guía Completa de Laravel DevTools

## 📖 Introducción

### ¿Qué es DevTools?

**Laravel DevTools** es un panel de desarrollo visual que te permite ejecutar comandos de Laravel y gestionar tu proyecto desde una interfaz web intuitiva, sin necesidad de usar la terminal.

### ¿Para quién es esta guía?

Esta guía está diseñada para:
- Desarrolladores que están aprendiendo Laravel
- Personas que prefieren interfaces visuales en lugar de comandos de terminal
- Equipos que buscan agilizar tareas repetitivas de desarrollo

### Requisitos previos

Antes de usar DevTools, debes tener:
- Laravel 11+ instalado
- PHP 8.2 o superior
- Conocimientos básicos de Laravel (modelos, controladores, migraciones)
- El paquete `zamyr/laravel-devtools` instalado en tu proyecto

### Acceso

Una vez instalado, accede al panel en:
```
http://localhost:8000/devtools
```

---

## 1. 🏠 Dashboard Principal

El Dashboard es la página de inicio de DevTools. Aquí encontrarás información general de tu proyecto y accesos rápidos a todas las herramientas.

### Secciones del Dashboard

#### 📊 Información del Sistema

En la parte superior verás 4 tarjetas con información técnica:

**1. LARAVEL**
- **Versión del Framework**: Muestra la versión de Laravel que estás usando
- **Ejemplo**: `12.38.1`
- **Utilidad**: Verificar compatibilidad con paquetes

**2. PHP**
- **Versión de PHP**: Runtime actual del servidor
- **Ejemplo**: `8.4.14`
- **Utilidad**: Confirmar que cumples los requisitos de Laravel

**3. ENVIRONMENT**
- **Modo de Entorno**: Configuración actual (`local`, `production`, `staging`)
- **Ejemplo**: `Local`
- **⚠️ Advertencia**: NUNCA uses DevTools en producción

**4. DOCKER**
- **Estado del Contenedor**: Si usas Laravel Sail, muestra si Docker está activo
- **Ejemplo**: `Active`
- **Utilidad**: Confirmar que tus servicios están corriendo

---

#### 🚀 Quick Actions (Acciones Rápidas)

Esta es la sección más importante. Contiene 13 accesos directos a las herramientas principales:

##### **Generadores (Generators)**

1. **Create Controller**
   - **Descripción**: Genera un nuevo controlador
   - **Tipos**: Plain, Resource, API, Singleton, Invokable
   - **Ruta**: `/devtools/generators/controller`

2. **Create Model**
   - **Descripción**: Genera un modelo Eloquent
   - **Incluye**: Migration, Factory, Seeder, Controller, Policy
   - **Ruta**: `/devtools/generators/model`

3. **Create Migration**
   - **Descripción**: Genera un archivo de migración
   - **Tipos**: Crear tabla, Modificar tabla
   - **Ruta**: `/devtools/generators/migration`

##### **Visualizadores (Viewers)**

4. **View Routes**
   - **Descripción**: Explora todas las rutas de tu aplicación
   - **Muestra**: Método HTTP, URI, Nombre, Acción, Middleware
   - **Equivalente**: `php artisan route:list`

5. **View Controllers**
   - **Descripción**: Lista todos los controladores del proyecto
   - **Muestra**: Nombre, Ubicación, Métodos
   - **Utilidad**: Inspeccionar código sin abrir archivos

##### **Administradores (Managers)**

6. **Artisan Commands**
   - **Descripción**: Ejecuta cualquier comando de Artisan desde la UI
   - **Ejemplos**: `cache:clear`, `migrate`, `queue:work`
   - **Ruta**: `/devtools/artisan`

7. **Composer Packages**
   - **Descripción**: Gestiona dependencias de Composer
   - **Acciones**: Instalar, Actualizar, Eliminar paquetes
   - **Equivalente**: `composer require`, `composer update`

8. **Sail Manager**
   - **Descripción**: Controla contenedores Docker (Laravel Sail)
   - **Acciones**: Iniciar, Detener, Reiniciar servicios
   - **Equivalente**: `./vendor/bin/sail up`, `sail down`

9. **Database Manager**
   - **Descripción**: Explorador visual de tu base de datos
   - **Funciones**: Ver tablas, Ejecutar consultas SQL, Exportar datos
   - **⚠️ Advertencia**: Ten cuidado con consultas DELETE

10. **Log Viewer**
    - **Descripción**: Visualiza los logs de Laravel en tiempo real
    - **Ubicación de logs**: `storage/logs/laravel.log`
    - **Útil para**: Debugging, Monitorear errores

11. **Cache Manager**
    - **Descripción**: Limpia y gestiona el caché de la aplicación
    - **Acciones**: Limpiar caché, Limpiar vistas, Limpiar rutas
    - **Comandos equivalentes**:
      ```bash
      php artisan cache:clear
      php artisan view:clear
      php artisan route:clear
      php artisan config:clear
      ```

12. **Queue Monitor**
    - **Descripción**: Monitorea trabajos en cola (jobs)
    - **Muestra**: Jobs pendientes, Fallos, Estadísticas
    - **Equivalente**: `php artisan queue:work`

13. **Config Editor**
    - **Descripción**: Edita variables de entorno (archivo `.env`)
    - **Variables comunes**: `APP_NAME`, `DB_DATABASE`, `MAIL_MAILER`
    - **⚠️ Advertencia**: Cambios requieren reiniciar el servidor

---

#### 📋 Project Information (Información del Proyecto)

Panel lateral con datos de tu proyecto:

- **NAME**: Nombre de tu aplicación (definido en `config/app.php` o `.env`)
- **URL**: Dirección base de tu proyecto (`http://localhost`)
- **LARAVEL VERSION**: Versión del framework (`12.38.1`)
- **PHP VERSION**: Versión de PHP (`8.4.14`)

**¿Para qué sirve?**
- Verificar configuración rápidamente
- Confirmar versiones antes de instalar paquetes
- Documentar tu entorno de desarrollo

---

### Navegación

En la parte superior encontrarás:

- **Logo DevTools**: Click para volver al Dashboard
- **Selector de idioma**: Cambiar entre EN/ES
- **Selector de proyecto**: Si tienes múltiples proyectos
- **Botón "Back to project"**: Vuelve a tu aplicación Laravel

---

## 📌 Próximos Pasos

Ahora que conoces el Dashboard, exploraremos cada herramienta en detalle:

1. **Controller Generator** - Crear controladores visualmente
2. **Model Generator** - Generar modelos completos
3. **Migration Generator** - Crear migraciones de base de datos
4. **Database Manager** - Explorar y consultar tu BD
5. **Artisan Commands** - Ejecutar comandos desde la UI
6. Y más...

---

## 2. 🎮 Generadores (Generators)

Los generadores son herramientas visuales para crear archivos de Laravel sin escribir comandos. Son ideales para acelerar el desarrollo.

---

## 2.1 📝 Controller Generator

**Ruta**: `http://localhost:8000/devtools/generators/controller`

### ¿Qué hace?

Crea controladores personalizados con diferentes tipos y opciones, equivalente a ejecutar `php artisan make:controller` pero con una interfaz visual.

---

### Campos del Formulario

#### 1. **Controller Name*** (Requerido)

Campo de texto para el nombre del controlador.

**Reglas:**
- Debe terminar en `Controller` (ej: `UserController`, `PostController`)
- Usa PascalCase (primera letra de cada palabra en mayúscula)
- Sin espacios ni caracteres especiales

**Ejemplos válidos:**
```
UserController
PostController
BlogPostController
API\AuthController
Admin\DashboardController
```

**Ubicación del archivo generado:**
```
app/Http/Controllers/TuControlador.php
```

---

### 2. **Controller Type*** (Requerido)

Selecciona uno de los 5 tipos de controlador disponibles:

#### 🔹 **Plain** (Controlador Vacío)
- **Descripción**: Controlador sin métodos predefinidos
- **Cuándo usarlo**: Cuando necesitas crear tus propios métodos personalizados
- **Color en UI**: Índigo

**Ejemplo de código generado:**
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class ExampleController extends Controller
{
    // Aquí agregas tus métodos personalizados
}
```

**Comando equivalente:**
```bash
php artisan make:controller ExampleController
```

---

#### 🔹 **Resource** (Métodos CRUD)
- **Descripción**: Controlador con 7 métodos para operaciones CRUD completas
- **Cuándo usarlo**: Para gestionar recursos con crear, leer, actualizar y eliminar
- **Color en UI**: Verde
- **Campo adicional**: Aparece campo "Model Name" para vincular con un modelo

**Métodos generados:**
```php
public function index()    // Listar todos los registros (GET /posts)
public function create()   // Mostrar formulario de creación (GET /posts/create)
public function store()    // Guardar nuevo registro (POST /posts)
public function show($id)  // Mostrar un registro (GET /posts/{id})
public function edit($id)  // Mostrar formulario de edición (GET /posts/{id}/edit)
public function update($id) // Actualizar registro (PUT/PATCH /posts/{id})
public function destroy($id) // Eliminar registro (DELETE /posts/{id})
```

**Comando equivalente:**
```bash
php artisan make:controller PostController --resource
```

**Con modelo vinculado:**
```bash
php artisan make:controller PostController --resource --model=Post
```

**Ejemplo de uso:**
Si creas `PostController` tipo Resource con modelo `Post`, los métodos recibirán instancias del modelo automáticamente:
```php
public function show(Post $post)
{
    return view('posts.show', compact('post'));
}
```

---

#### 🔹 **API** (Recurso para API)
- **Descripción**: Similar a Resource pero SIN los métodos `create()` y `edit()`
- **Cuándo usarlo**: Para crear APIs RESTful (sin vistas HTML)
- **Color en UI**: Azul
- **Campo adicional**: Aparece campo "Model Name"

**Métodos generados:**
```php
public function index()    // Listar recursos (GET /api/posts)
public function store()    // Crear recurso (POST /api/posts)
public function show($id)  // Mostrar recurso (GET /api/posts/{id})
public function update($id) // Actualizar recurso (PUT /api/posts/{id})
public function destroy($id) // Eliminar recurso (DELETE /api/posts/{id})
```

**Comando equivalente:**
```bash
php artisan make:controller API/PostController --api
```

**Con modelo:**
```bash
php artisan make:controller API/PostController --api --model=Post
```

**¿Por qué no tiene create/edit?**
Las APIs no necesitan formularios HTML. Los clientes (apps móviles, frontends) envían JSON directamente.

---

#### 🔹 **Singleton** (Recurso Único)
- **Descripción**: Controlador para gestionar UN SOLO recurso sin ID en la URL
- **Cuándo usarlo**: Perfil del usuario, configuración de cuenta, dashboard personal
- **Color en UI**: Naranja
- **Campo adicional**: Aparece "Model Name" y checkbox "Creatable singleton"

**Métodos generados (sin creatable):**
```php
public function show()   // Ver el recurso único (GET /profile)
public function edit()   // Editar el recurso (GET /profile/edit)
public function update() // Actualizar el recurso (PUT /profile)
```

**Métodos con creatable activado:**
```php
public function create() // Formulario de creación (GET /profile/create)
public function store()  // Guardar el recurso (POST /profile)
public function show()   // Ver el recurso único (GET /profile)
public function edit()   // Editar el recurso (GET /profile/edit)
public function update() // Actualizar el recurso (PUT /profile)
```

**Comando equivalente:**
```bash
php artisan make:controller ProfileController --singleton --model=User
```

**Con creatable:**
```bash
php artisan make:controller ProfileController --singleton --creatable --model=User
```

**Ejemplo de uso real:**
```php
// ProfileController.php
public function show()
{
    // El recurso es el usuario autenticado
    $user = auth()->user();
    return view('profile.show', compact('user'));
}

public function update(Request $request)
{
    $request->user()->update($validated);
    return redirect()->route('profile.show');
}
```

**Rutas generadas:**
```php
Route::singleton('profile', ProfileController::class);
// GET    /profile      → show()
// GET    /profile/edit → edit()
// PUT    /profile      → update()
```

---

#### 🔹 **Invokable** (Acción Única)
- **Descripción**: Controlador con UN SOLO método `__invoke()`
- **Cuándo usarlo**: Para acciones específicas que no necesitan múltiples métodos
- **Color en UI**: Púrpura

**Código generado:**
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class SendNewsletterController extends Controller
{
    public function __invoke(Request $request)
    {
        // Lógica de la acción única
    }
}
```

**Comando equivalente:**
```bash
php artisan make:controller SendNewsletterController --invokable
```

**Ejemplo de uso:**
```php
// routes/web.php
Route::post('/newsletter/send', SendNewsletterController::class);

// No necesitas especificar el método, __invoke se llama automáticamente
```

**Casos de uso comunes:**
- Enviar emails
- Procesar pagos
- Generar reportes
- Exportar datos

---

### 3. **Model Name** (Opcional - Aparece con Resource, API y Singleton)

Campo de texto con autocompletado que lista los modelos existentes en tu proyecto.

**¿Para qué sirve?**
Vincula el controlador con un modelo específico para:
- Usar type-hinting en los métodos
- Inyección automática de modelos (Route Model Binding)

**Ejemplo:**
Si creas `PostController` con modelo `Post`:
```php
// Sin modelo
public function show($id)
{
    $post = Post::findOrFail($id);
    return view('posts.show', compact('post'));
}

// Con modelo vinculado
public function show(Post $post)
{
    // Laravel automáticamente busca el Post por ID
    return view('posts.show', compact('post'));
}
```

---

### 4. **Additional Options** (Opciones Adicionales)

Checkboxes para funcionalidades extras:

#### ☑️ **Parent resource controller**
Crea un controlador para recursos anidados (nested resources).

**Ejemplo de uso:**
```
Controlador: CommentController
Modelo: Comment
Parent: activado
```

**Métodos generados:**
```php
public function index(Post $post)    // GET /posts/{post}/comments
public function store(Post $post)    // POST /posts/{post}/comments
public function show(Post $post, Comment $comment)  // GET /posts/{post}/comments/{comment}
public function update(Post $post, Comment $comment) // PUT /posts/{post}/comments/{comment}
public function destroy(Post $post, Comment $comment) // DELETE /posts/{post}/comments/{comment}
```

**Comando equivalente:**
```bash
php artisan make:controller CommentController --resource --model=Comment --parent=Post
```

**Rutas correspondientes:**
```php
Route::resource('posts.comments', CommentController::class);
```

---

#### ☑️ **Generate form request classes**
Crea clases separadas para validación de formularios.

**Archivos generados:**
```
app/Http/Requests/StorePostRequest.php
app/Http/Requests/UpdatePostRequest.php
```

**Ejemplo de código generado:**
```php
// StorePostRequest.php
class StorePostRequest extends FormRequest
{
    public function authorize(): bool
    {
        return true;
    }

    public function rules(): array
    {
        return [
            'title' => 'required|string|max:255',
            'content' => 'required',
        ];
    }
}
```

**El controlador usa estas clases:**
```php
public function store(StorePostRequest $request)
{
    // La validación ocurre automáticamente
    $validated = $request->validated();
    Post::create($validated);
}
```

**Comando equivalente:**
```bash
php artisan make:controller PostController --resource --requests
```

**Ventajas:**
- Código más limpio en el controlador
- Validación reutilizable
- Más fácil de testear

---

#### ☑️ **Force overwrite if exists**
Sobrescribe el controlador si ya existe un archivo con el mismo nombre.

**⚠️ ADVERTENCIA**: Esto eliminará el código existente sin confirmación.

**Cuándo usarlo:**
- Durante desarrollo cuando quieres regenerar un controlador
- Para reemplazar código de prueba
- **NO usar** en controladores con lógica importante

**Comando equivalente:**
```bash
php artisan make:controller PostController --force
```

---

#### ☑️ **Creatable singleton (add create/store)** 
Solo aparece cuando seleccionas tipo **Singleton**.

Agrega métodos `create()` y `store()` al controlador singleton.

**Cuándo usarlo:**
- Cuando el recurso único necesita ser creado por primera vez
- Ejemplo: Configuración inicial de cuenta, Perfil público

**Sin creatable:**
```php
// Solo tiene: show, edit, update, destroy
```

**Con creatable:**
```php
// Tiene: create, store, show, edit, update, destroy
```

**Comando equivalente:**
```bash
php artisan make:controller ProfileController --singleton --creatable
```

---

### Ejemplos Prácticos Completos

#### **Ejemplo 1: Blog Post Resource**
**Configuración:**
- Controller Name: `PostController`
- Type: `Resource`
- Model Name: `Post`
- ✅ Generate form request classes

**Comando equivalente:**
```bash
php artisan make:controller PostController --resource --model=Post --requests
```

**Archivos generados:**
```
app/Http/Controllers/PostController.php
app/Http/Requests/StorePostRequest.php
app/Http/Requests/UpdatePostRequest.php
```

---

#### **Ejemplo 2: API de Productos**
**Configuración:**
- Controller Name: `API/ProductController`
- Type: `API`
- Model Name: `Product`

**Comando equivalente:**
```bash
php artisan make:controller API/ProductController --api --model=Product
```

**Archivo generado:**
```
app/Http/Controllers/API/ProductController.php
```

---

#### **Ejemplo 3: Perfil de Usuario (Singleton)**
**Configuración:**
- Controller Name: `ProfileController`
- Type: `Singleton`
- Model Name: `User`
- ✅ Creatable singleton

**Comando equivalente:**
```bash
php artisan make:controller ProfileController --singleton --model=User --creatable
```

---

#### **Ejemplo 4: Comentarios de Posts (Parent Resource)**
**Configuración:**
- Controller Name: `CommentController`
- Type: `Resource`
- Model Name: `Comment`
- ✅ Parent resource controller

**Comando equivalente:**
```bash
php artisan make:controller CommentController --resource --model=Comment --parent=Post
```

**Uso en rutas:**
```php
// routes/web.php
Route::resource('posts.comments', CommentController::class);
```

---

#### **Ejemplo 5: Acción de Enviar Newsletter (Invokable)**
**Configuración:**
- Controller Name: `SendNewsletterController`
- Type: `Invokable`

**Comando equivalente:**
```bash
php artisan make:controller SendNewsletterController --invokable
```

**Uso en rutas:**
```php
Route::post('/newsletter/send', SendNewsletterController::class);
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa nombres descriptivos: `UserController`, no `UC`
- Agrupa controladores de API en carpeta `API/`
- Usa Resource para CRUD completos
- Usa Singleton para recursos únicos del usuario
- Genera Form Requests para validación compleja

❌ **DON'T (No hacer):**
- No uses `--force` sin verificar el archivo existente
- No crees Resource controllers para acciones únicas (usa Invokable)
- No mezcles lógica de negocio en controladores (usa Services)
- No olvides agregar las rutas después de crear el controlador

---

### Verificar el Controlador Creado

Después de generar el controlador, verifica en:

1. **Ubicación del archivo:**
   ```
   app/Http/Controllers/TuControlador.php
   ```

2. **Desde DevTools:**
   Ve a `View Controllers` en el Dashboard para ver el nuevo controlador listado.

3. **Desde terminal:**
   ```bash
   ls -la app/Http/Controllers/
   ```

---

## 2.2 🗄️ Model Generator

**Ruta**: `http://localhost:8000/devtools/generators/model`

### ¿Qué hace?

Crea modelos Eloquent con archivos relacionados (migraciones, factories, seeders, etc.). Es como ejecutar `php artisan make:model` con múltiples opciones en una sola interfaz.

---

### Campos del Formulario

#### 1. **Model Name*** (Requerido)

Nombre del modelo en **singular** y **PascalCase**.

**Reglas:**
- Singular (Laravel pluraliza automáticamente para la tabla)
- Primera letra en mayúscula
- Sin espacios ni guiones

**Ejemplos correctos:**
```
Post          → tabla: posts
User          → tabla: users
Category      → tabla: categories
BlogPost      → tabla: blog_posts
ProductImage  → tabla: product_images
```

**Ubicación del archivo:**
```
app/Models/TuModelo.php
```

**Comando equivalente básico:**
```bash
php artisan make:model Post
```

---

### 2. **Generate Additional Files** (Archivos Adicionales)

Checkboxes para generar archivos relacionados con el modelo:

#### ☑️ **Migration** (Migración)
Crea un archivo de migración para la tabla del modelo.

**Archivo generado:**
```
database/migrations/2024_01_15_120000_create_posts_table.php
```

**Contenido generado:**
```php
public function up(): void
{
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        $table->timestamps();
    });
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --migration
# o la forma corta:
php artisan make:model Post -m
```

**¿Por qué usarlo?**
- Siempre necesitas una tabla para el modelo
- Es la opción más común junto con Factory

---

#### ☑️ **Factory** (Fábrica de Datos)
Crea una clase Factory para generar datos falsos del modelo.

**Archivo generado:**
```
database/factories/PostFactory.php
```

**Contenido generado:**
```php
<?php

namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;

class PostFactory extends Factory
{
    public function definition(): array
    {
        return [
            'title' => fake()->sentence(),
            'content' => fake()->paragraph(),
            // Define más campos aquí
        ];
    }
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --factory
# o forma corta:
php artisan make:model Post -f
```

**Uso del Factory:**
```php
// Crear 1 post de prueba
Post::factory()->create();

// Crear 50 posts
Post::factory()->count(50)->create();

// En seeders
Post::factory()->count(100)->create();
```

**¿Cuándo usarlo?**
- Para testing (pruebas automatizadas)
- Para poblar BD de desarrollo
- Para demos y prototipos

---

#### ☑️ **Seeder** (Sembrador)
Crea una clase Seeder para poblar la base de datos con datos iniciales.

**Archivo generado:**
```
database/seeders/PostSeeder.php
```

**Contenido generado:**
```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;

class PostSeeder extends Seeder
{
    public function run(): void
    {
        // Lógica para crear registros
        Post::factory()->count(50)->create();
    }
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --seed
# o forma corta:
php artisan make:model Post -s
```

**Ejecutar el seeder:**
```bash
php artisan db:seed --class=PostSeeder
```

**Diferencia entre Factory y Seeder:**
| Factory | Seeder |
|---------|--------|
| Define CÓMO crear datos falsos | Define CUÁNDO y CUÁNTOS crear |
| Usado en tests y seeders | Usado para poblar BD inicial |
| Reutilizable | Específico para cada escenario |

---

#### ☑️ **Resource Controller** (Controlador)
Crea un controlador Resource vinculado al modelo.

**Archivo generado:**
```
app/Http/Controllers/PostController.php
```

**Contenido generado:**
```php
class PostController extends Controller
{
    public function index() { }
    public function create() { }
    public function store(Request $request) { }
    public function show(Post $post) { }  // Type-hinting automático
    public function edit(Post $post) { }
    public function update(Request $request, Post $post) { }
    public function destroy(Post $post) { }
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --controller --resource
# o forma corta:
php artisan make:model Post -cr
```

**Ventaja:**
El controlador ya tiene **Route Model Binding** configurado (recibe instancias del modelo directamente).

---

#### ☑️ **Policy** (Política de Autorización)
Crea una clase Policy para definir permisos sobre el modelo.

**Archivo generado:**
```
app/Policies/PostPolicy.php
```

**Contenido generado:**
```php
class PostPolicy
{
    public function viewAny(User $user): bool { }
    public function view(User $user, Post $post): bool { }
    public function create(User $user): bool { }
    public function update(User $user, Post $post): bool { }
    public function delete(User $user, Post $post): bool { }
    public function restore(User $user, Post $post): bool { }
    public function forceDelete(User $user, Post $post): bool { }
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --policy
```

**Uso en controladores:**
```php
public function update(Request $request, Post $post)
{
    $this->authorize('update', $post); // Verifica permiso
    
    $post->update($request->validated());
}
```

**¿Cuándo usarlo?**
- Cuando necesitas control de acceso (quién puede editar/eliminar)
- Para aplicaciones multiusuario
- Para roles y permisos

---

#### ☑️ **Form Requests** (Clases de Validación)
Crea clases Request para validar datos del modelo.

**Archivos generados:**
```
app/Http/Requests/StorePostRequest.php
app/Http/Requests/UpdatePostRequest.php
```

**Contenido generado:**
```php
// StorePostRequest.php
class StorePostRequest extends FormRequest
{
    public function authorize(): bool
    {
        return true;
    }

    public function rules(): array
    {
        return [
            'title' => 'required|string|max:255',
            'content' => 'required',
        ];
    }
}
```

**Comando equivalente:**
```bash
php artisan make:model Post --requests
# o forma corta:
php artisan make:model Post -R
```

**Uso en controladores:**
```php
public function store(StorePostRequest $request)
{
    // Validación automática antes de ejecutar
    Post::create($request->validated());
}
```

---

### 3. **Model Options** (Opciones del Modelo)

Configuraciones específicas del modelo:

#### ☑️ **Pivot Model** (Modelo Pivote)
Crea un modelo para tabla pivote en relaciones muchos-a-muchos.

**¿Qué es una tabla pivote?**
En relaciones many-to-many, necesitas una tabla intermedia:
```
posts (id, title)
tags (id, name)
post_tag (post_id, tag_id)  ← Tabla pivote
```

**Cuándo usar Pivot Model:**
- Cuando necesitas campos extra en la tabla pivote
- Ejemplo: `post_tag` con columna `order` o `created_by`

**Código generado:**
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Relations\Pivot;

class PostTag extends Pivot
{
    // Configuración especial para pivotes
    public $incrementing = true;
}
```

**Comando equivalente:**
```bash
php artisan make:model PostTag --pivot
# o forma corta:
php artisan make:model PostTag -p
```

**Diferencia con modelo normal:**
| Modelo Normal | Pivot Model |
|---------------|-------------|
| Extiende `Model` | Extiende `Pivot` |
| Tiene timestamps | No tiene timestamps (por defecto) |
| Tabla propia independiente | Tabla de relación |

**Ejemplo de uso:**
```php
// Post.php
public function tags()
{
    return $this->belongsToMany(Tag::class)
                ->using(PostTag::class)  // Usa el modelo pivote
                ->withPivot('order', 'created_by');
}
```

---

#### ☑️ **Soft Deletes** (Eliminación Suave)
Agrega la capacidad de "eliminar" registros sin borrarlos físicamente.

**Código agregado al modelo:**
```php
use Illuminate\Database\Eloquent\SoftDeletes;

class Post extends Model
{
    use SoftDeletes;
    
    // Laravel agregará automáticamente la columna deleted_at
}
```

**Migración modificada:**
```php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->text('content');
    $table->softDeletes();  // Agrega deleted_at
    $table->timestamps();
});
```

**Comando equivalente:**
```bash
php artisan make:model Post --migration --soft-deletes
```

**¿Cómo funciona?**
```php
// "Eliminar" un post
$post->delete();  // Solo pone fecha en deleted_at

// El post no aparece en consultas normales
Post::all();  // No incluye posts eliminados

// Ver posts eliminados
Post::withTrashed()->get();

// Restaurar post eliminado
$post->restore();

// Eliminar permanentemente
$post->forceDelete();
```

**¿Cuándo usarlo?**
- ✅ Datos importantes que no deben perderse (usuarios, pedidos)
- ✅ Cuando necesitas auditoría o historial
- ✅ Para funcionalidad de "papelera"
- ❌ NO usar en tablas con millones de registros (afecta rendimiento)

---

#### ☑️ **Timestamps** (Marcas de Tiempo)
Incluye las columnas `created_at` y `updated_at` en el modelo.

**⚠️ Nota**: Esta opción está **activada por defecto** en modelos normales.

**Código en migración:**
```php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->timestamps();  // Agrega created_at y updated_at
});
```

**Comportamiento:**
```php
// Al crear
$post = Post::create(['title' => 'Test']);
// created_at: 2024-01-15 10:30:00
// updated_at: 2024-01-15 10:30:00

// Al actualizar
$post->update(['title' => 'Updated']);
// created_at: 2024-01-15 10:30:00 (no cambia)
// updated_at: 2024-01-15 11:45:00 (actualizado)
```

**Desactivar timestamps:**
Si NO marcas esta opción, se agrega al modelo:
```php
class Post extends Model
{
    public $timestamps = false;  // Desactiva timestamps
}
```

**¿Cuándo desactivar?**
- Tablas pivote simples
- Tablas de solo lectura
- Migraciones de bases de datos existentes sin timestamps

---

#### 📝 **Fillable Fields** (Campos Asignables)
Lista de campos que pueden ser asignados masivamente (mass assignment).

**Formato:**
Campos separados por comas:
```
title, content, status, author_id
```

**Código generado:**
```php
class Post extends Model
{
    protected $fillable = [
        'title',
        'content',
        'status',
        'author_id',
    ];
}
```

**¿Por qué es importante?**
Laravel protege contra asignación masiva por seguridad:
```php
// Sin $fillable definido
Post::create($request->all());  // ❌ ERROR: Add [title] to fillable property

// Con $fillable
Post::create($request->all());  // ✅ Funciona
```

**Alternativa - $guarded:**
En lugar de listar campos permitidos, lista los NO permitidos:
```php
protected $guarded = ['id', 'created_at', 'updated_at'];
```

**Comando equivalente:**
No hay comando específico, pero puedes usar:
```bash
php artisan make:model Post --fillable=title,content,status
```

**Ejemplo práctico:**
Si creas un modelo `Post` con:
```
Fillable Fields: title, slug, content, excerpt, status, published_at, author_id
```

Se genera:
```php
protected $fillable = [
    'title',
    'slug',
    'content',
    'excerpt',
    'status',
    'published_at',
    'author_id',
];
```

---

### Ejemplos Prácticos Completos

#### **Ejemplo 1: Modelo de Blog Completo**

**Configuración:**
- Model Name: `Post`
- ✅ Migration
- ✅ Factory
- ✅ Seeder
- ✅ Resource Controller
- ❌ Policy
- ❌ Form Requests
- ❌ Pivot Model
- ✅ Soft Deletes
- ✅ Timestamps
- Fillable Fields: `title, slug, content, excerpt, status, published_at, author_id`

**Comando equivalente:**
```bash
php artisan make:model Post -mfsc --soft-deletes
```
*(-m=migration, -f=factory, -s=seeder, -c=controller)*

**Archivos generados:**
```
app/Models/Post.php
app/Http/Controllers/PostController.php
database/migrations/2024_01_15_create_posts_table.php
database/factories/PostFactory.php
database/seeders/PostSeeder.php
```

**Modelo generado:**
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;

class Post extends Model
{
    use HasFactory, SoftDeletes;

    protected $fillable = [
        'title',
        'slug',
        'content',
        'excerpt',
        'status',
        'published_at',
        'author_id',
    ];
}
```

---

#### **Ejemplo 2: Tabla Pivote con Campos Extra**

**Configuración:**
- Model Name: `PostTag`
- ✅ Migration
- ❌ Factory
- ❌ Seeder
- ❌ Resource Controller
- ❌ Policy
- ❌ Form Requests
- ✅ Pivot Model
- ❌ Soft Deletes
- ❌ Timestamps
- Fillable Fields: `order, created_by`

**Comando equivalente:**
```bash
php artisan make:model PostTag --pivot --migration
```

**Modelo generado:**
```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Relations\Pivot;

class PostTag extends Pivot
{
    public $incrementing = true;
    public $timestamps = false;
    
    protected $fillable = [
        'order',
        'created_by',
    ];
}
```

**Uso en relaciones:**
```php
// Post.php
public function tags()
{
    return $this->belongsToMany(Tag::class)
                ->using(PostTag::class)
                ->withPivot('order', 'created_by');
}

// Agregar tag con campos pivote
$post->tags()->attach($tagId, [
    'order' => 1,
    'created_by' => auth()->id(),
]);
```

---

#### **Ejemplo 3: Modelo para API con Testing**

**Configuración:**
- Model Name: `Product`
- ✅ Migration
- ✅ Factory
- ❌ Seeder
- ✅ Resource Controller
- ✅ Policy
- ✅ Form Requests
- ❌ Pivot Model
- ❌ Soft Deletes
- ✅ Timestamps
- Fillable Fields: `name, description, price, stock, category_id`

**Comando equivalente:**
```bash
php artisan make:model Product -mfcr --policy --requests
```

**Archivos generados:**
```
app/Models/Product.php
app/Http/Controllers/ProductController.php
app/Policies/ProductPolicy.php
app/Http/Requests/StoreProductRequest.php
app/Http/Requests/UpdateProductRequest.php
database/migrations/2024_01_15_create_products_table.php
database/factories/ProductFactory.php
```

---

#### **Ejemplo 4: Modelo Simple (Sin Archivos Extra)**

**Configuración:**
- Model Name: `Category`
- ❌ Migration (ya existe la tabla)
- ❌ Factory
- ❌ Seeder
- ❌ Resource Controller
- ❌ Policy
- ❌ Form Requests
- ❌ Pivot Model
- ❌ Soft Deletes
- ✅ Timestamps
- Fillable Fields: `name, slug, description`

**Comando equivalente:**
```bash
php artisan make:model Category
```

**Archivo generado:**
```
app/Models/Category.php
```

---

### Combinaciones Más Comunes

#### 🔥 **La Más Completa** (Para entidades principales)
```
✅ Migration
✅ Factory
✅ Seeder
✅ Resource Controller
✅ Policy
✅ Form Requests
✅ Soft Deletes
✅ Timestamps
```

**Comando:**
```bash
php artisan make:model Post -a --soft-deletes
```
*(-a = all, genera todo excepto pivot)*

---

#### 📦 **Para API** (Sin vistas)
```
✅ Migration
✅ Factory
❌ Seeder
✅ Resource Controller (tipo API)
✅ Policy
✅ Form Requests
```

**Comando:**
```bash
php artisan make:model Product -mfcr --api --policy --requests
```

---

#### 🔗 **Para Tabla Pivote**
```
✅ Migration
✅ Pivot Model
❌ Timestamps
❌ Todo lo demás
```

**Comando:**
```bash
php artisan make:model PostTag --pivot --migration
```

---

#### 🧪 **Para Testing**
```
✅ Migration
✅ Factory
✅ Seeder
❌ Controlador (se crea después)
```

**Comando:**
```bash
php artisan make:model Post -mfs
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa nombres en singular: `Post`, no `Posts`
- Siempre genera Migration con el modelo (casi obligatorio)
- Usa Factory para todos los modelos (útil para testing)
- Define Fillable Fields para evitar errores de asignación masiva
- Usa Soft Deletes en datos importantes (usuarios, pedidos)
- Genera Policy para modelos con control de acceso

❌ **DON'T (No hacer):**
- No uses nombres en plural en modelos
- No olvides agregar relaciones después de crear el modelo
- No dejes $fillable vacío (causa errores MassAssignmentException)
- No uses Soft Deletes en tablas con millones de registros
- No generes Controller si solo necesitas el modelo para relaciones

---

### Verificar Archivos Generados

**1. Modelo:**
```bash
cat app/Models/Post.php
```

**2. Migración:**
```bash
ls -la database/migrations/ | grep create_posts_table
```

**3. Factory:**
```bash
cat database/factories/PostFactory.php
```

**4. Ver desde DevTools:**
Ve a `View Controllers` o revisa la carpeta correspondiente en la UI.

---

### Siguientes Pasos Después de Crear el Modelo

1. **Modificar la migración:**
   ```php
   // database/migrations/xxxx_create_posts_table.php
   Schema::create('posts', function (Blueprint $table) {
       $table->id();
       $table->string('title');
       $table->string('slug')->unique();
       $table->text('content');
       $table->string('status')->default('draft');
       $table->foreignId('author_id')->constrained('users');
       $table->softDeletes();
       $table->timestamps();
   });
   ```

2. **Ejecutar la migración:**
   ```bash
   php artisan migrate
   ```

3. **Agregar relaciones al modelo:**
   ```php
   // app/Models/Post.php
   public function author()
   {
       return $this->belongsTo(User::class, 'author_id');
   }
   
   public function tags()
   {
       return $this->belongsToMany(Tag::class);
   }
   ```

4. **Configurar el Factory:**
   ```php
   // database/factories/PostFactory.php
   public function definition(): array
   {
       return [
           'title' => fake()->sentence(),
           'slug' => fake()->slug(),
           'content' => fake()->paragraphs(3, true),
           'status' => fake()->randomElement(['draft', 'published']),
           'author_id' => User::factory(),
       ];
   }
   ```

5. **Registrar rutas:**
   ```php
   // routes/web.php
   Route::resource('posts', PostController::class);
   ```

---

## 2.3 🗃️ Migration Generator

**Ruta**: `http://localhost:8000/devtools/generators/migration`

### ¿Qué hace?

Crea archivos de migración con un constructor visual de columnas. Permite crear tablas nuevas o modificar tablas existentes sin escribir código PHP manualmente.

---

### Campos del Formulario

#### 1. **Migration Name*** (Requerido)

Nombre descriptivo de la migración en formato **snake_case**.

**Reglas:**
- Usa snake_case (minúsculas con guiones bajos)
- Debe ser descriptivo de la acción
- Convención: `accion_nombre_tabla`

**Ejemplos correctos:**
```
create_posts_table           → Crear tabla posts
add_status_to_users_table    → Agregar columna status a users
create_categories_table      → Crear tabla categories
remove_email_from_profiles   → Eliminar columna email de profiles
add_indexes_to_posts_table   → Agregar índices a posts
```

**Archivo generado:**
```
database/migrations/2024_01_15_123456_create_posts_table.php
```

**Comando equivalente básico:**
```bash
php artisan make:migration create_posts_table
```

---

#### 2. **Migration Type** (Tipo de Migración)

Selecciona entre 2 tipos:

##### 🟢 **Create Table** (Crear Tabla)
- **Descripción**: Crea una nueva tabla en la base de datos
- **Color en UI**: Verde
- **Cuándo usarlo**: Para tablas que no existen
- **Campo adicional**: Aparece "Table Name"

**Código generado:**
```php
public function up(): void
{
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        // Tus columnas aquí
        $table->timestamps();
    });
}

public function down(): void
{
    Schema::dropIfExists('posts');
}
```

**Comando equivalente:**
```bash
php artisan make:migration create_posts_table --create=posts
```

---

##### 🟡 **Update Table** (Actualizar Tabla)
- **Descripción**: Modifica una tabla existente (agregar/eliminar columnas)
- **Color en UI**: Amarillo
- **Cuándo usarlo**: Para agregar o modificar columnas en tablas existentes
- **Campo adicional**: NO aparece "Table Name" (se infiere del nombre de migración)

**Código generado:**
```php
public function up(): void
{
    Schema::table('users', function (Blueprint $table) {
        // Tus columnas aquí
    });
}

public function down(): void
{
    Schema::table('users', function (Blueprint $table) {
        // Rollback de cambios
    });
}
```

**Comando equivalente:**
```bash
php artisan make:migration add_status_to_users_table --table=users
```

**⚠️ Importante:**
- **Create Table**: Usa `Schema::create()` y requiere nombre de tabla
- **Update Table**: Usa `Schema::table()` e infiere el nombre de la migración

---

#### 3. **Table Name*** (Requerido solo para "Create Table")

Nombre de la tabla en formato **plural** y **minúsculas**.

**Reglas:**
- Plural (Laravel sigue convención de nombres)
- Minúsculas
- Sin espacios, usa guiones bajos para separar palabras

**Ejemplos correctos:**
```
posts           → Tabla de posts
users           → Tabla de usuarios
categories      → Tabla de categorías
blog_posts      → Tabla de posts de blog
product_images  → Tabla de imágenes de productos
```

**⚠️ Nota:** Este campo solo aparece cuando seleccionas **"Create Table"**.

---

### 4. **Table Columns** (Constructor de Columnas)

Sección visual para agregar columnas personalizadas a la tabla.

#### Botón "Add Column"
Agrega una nueva fila para definir una columna con estos campos:

##### **Column Name** (Nombre de Columna)
- Nombre de la columna en snake_case
- Ejemplos: `title`, `user_id`, `published_at`, `is_active`

##### **Type** (Tipo de Dato)
Desplegable con 12 tipos de columna disponibles:

| Tipo | Laravel Method | Descripción | Base de Datos |
|------|----------------|-------------|---------------|
| **String** | `string()` | Texto corto | VARCHAR(255) |
| **Text** | `text()` | Texto largo | TEXT |
| **Integer** | `integer()` | Número entero | INT |
| **Big Integer** | `bigInteger()` | Entero grande | BIGINT |
| **Boolean** | `boolean()` | Verdadero/Falso | TINYINT(1) |
| **Date** | `date()` | Solo fecha | DATE |
| **DateTime** | `dateTime()` | Fecha y hora | DATETIME |
| **Timestamp** | `timestamp()` | Marca de tiempo | TIMESTAMP |
| **Decimal** | `decimal()` | Número con decimales | DECIMAL |
| **Float** | `float()` | Número flotante | FLOAT |
| **JSON** | `json()` | Datos JSON | JSON/TEXT |
| **Foreign Key** | `foreignId()` | Llave foránea | BIGINT UNSIGNED |

**Explicación de cada tipo:**

**🔤 String (VARCHAR)**
```php
$table->string('title'); // VARCHAR(255)
$table->string('slug', 100); // VARCHAR(100)
```
- Texto corto hasta 255 caracteres
- Usa para: nombres, emails, slugs, códigos

**📝 Text (TEXT)**
```php
$table->text('description');
$table->text('content');
```
- Texto largo sin límite definido
- Usa para: descripciones, contenido HTML, notas

**🔢 Integer (INT)**
```php
$table->integer('age');
$table->integer('stock');
```
- Números enteros de -2,147,483,648 a 2,147,483,647
- Usa para: cantidades, edades, contadores

**📊 Big Integer (BIGINT)**
```php
$table->bigInteger('views');
$table->bigInteger('population');
```
- Números enteros muy grandes
- Usa para: estadísticas grandes, IDs de API externas

**✅ Boolean (TINYINT)**
```php
$table->boolean('is_active');
$table->boolean('is_published');
```
- Valores true/false (1/0)
- Usa para: estados, banderas, permisos

**📅 Date (DATE)**
```php
$table->date('birth_date');
$table->date('published_date');
```
- Solo fecha (YYYY-MM-DD)
- Usa para: fechas de nacimiento, vencimientos

**🕐 DateTime (DATETIME)**
```php
$table->dateTime('published_at');
$table->dateTime('event_start');
```
- Fecha y hora completa
- Usa para: eventos, publicaciones programadas

**⏰ Timestamp (TIMESTAMP)**
```php
$table->timestamp('last_login');
$table->timestamps(); // created_at, updated_at
```
- Similar a DateTime pero con zona horaria
- Laravel usa esto para created_at/updated_at

**💰 Decimal (DECIMAL)**
```php
$table->decimal('price', 8, 2); // 999999.99
$table->decimal('tax_rate', 5, 2); // 100.00
```
- Números con decimales precisos
- Usa para: precios, porcentajes, dinero

**📈 Float (FLOAT)**
```php
$table->float('rating', 8, 2);
$table->float('latitude', 10, 6);
```
- Números con decimales (menos precisos que decimal)
- Usa para: coordenadas, calificaciones

**🗂️ JSON**
```php
$table->json('metadata');
$table->json('settings');
```
- Almacena objetos JSON
- Usa para: configuraciones, datos flexibles, metadatos

**🔗 Foreign Key (BIGINT UNSIGNED)**
```php
$table->foreignId('user_id');
$table->foreignId('category_id')->constrained();
```
- Llave foránea para relaciones
- Automáticamente BIGINT UNSIGNED
- Usa para: relaciones entre tablas

---

##### **Length** (Longitud - Opcional)
Define el tamaño de la columna (solo para algunos tipos).

**Cuándo usarlo:**
- **String**: Limitar caracteres (ej: `100` para slugs cortos)
- **Decimal**: Definir precisión (ej: `10,2` = 10 dígitos, 2 decimales)
- **Integer**: Raramente necesario

**Ejemplos:**
```
Type: String, Length: 100     → VARCHAR(100)
Type: String, Length: (vacío) → VARCHAR(255) por defecto
Type: Decimal, Length: 8,2    → DECIMAL(8,2)
```

---

##### **Modifiers** (Modificadores)
Checkboxes para opciones adicionales:

**☑️ Nullable**
Permite que la columna acepte valores `NULL`.

```php
// Sin Nullable
$table->string('title'); // Requerido

// Con Nullable
$table->string('title')->nullable(); // Opcional
```

**Cuándo usar:**
- ✅ Campos opcionales (teléfono, segundo apellido)
- ✅ Datos que pueden no existir al crear (published_at)
- ❌ NO usar en campos críticos (email, password)

---

**☑️ Unique**
Garantiza que no haya valores duplicados en la columna.

```php
$table->string('email')->unique();
$table->string('slug')->unique();
```

**Cuándo usar:**
- ✅ Emails (no puede haber 2 usuarios con el mismo email)
- ✅ Slugs (URLs únicas)
- ✅ Códigos de productos
- ✅ Usernames

**⚠️ Efecto en base de datos:**
Crea un índice único, rechaza inserciones duplicadas.

---

##### **Botón de Eliminar (Ícono de Basura)**
Elimina la fila de columna del constructor.

---

### Ejemplos Prácticos Completos

#### **Ejemplo 1: Tabla de Posts (Blog)**

**Configuración:**
- Migration Name: `create_posts_table`
- Type: **Create Table**
- Table Name: `posts`

**Columnas:**

| Column Name | Type | Length | Nullable | Unique |
|-------------|------|--------|----------|--------|
| `title` | String | 255 | ❌ | ❌ |
| `slug` | String | 255 | ❌ | ✅ |
| `excerpt` | Text | - | ✅ | ❌ |
| `content` | Text | - | ❌ | ❌ |
| `status` | String | 20 | ❌ | ❌ |
| `published_at` | DateTime | - | ✅ | ❌ |
| `user_id` | Foreign Key | - | ❌ | ❌ |

**Comando equivalente:**
```bash
php artisan make:migration create_posts_table --create=posts
```

**Código generado:**
```php
public function up(): void
{
    Schema::create('posts', function (Blueprint $table) {
        $table->id();
        $table->string('title');
        $table->string('slug')->unique();
        $table->text('excerpt')->nullable();
        $table->text('content');
        $table->string('status', 20);
        $table->dateTime('published_at')->nullable();
        $table->foreignId('user_id');
        $table->timestamps();
    });
}

public function down(): void
{
    Schema::dropIfExists('posts');
}
```

**Siguientes pasos:**
```bash
# Ejecutar migración
php artisan migrate

# Verificar tabla creada
php artisan db:show
```

---

#### **Ejemplo 2: Agregar Columnas a Tabla Existente**

**Configuración:**
- Migration Name: `add_social_fields_to_users_table`
- Type: **Update Table**

**Columnas:**

| Column Name | Type | Length | Nullable | Unique |
|-------------|------|--------|----------|--------|
| `bio` | Text | - | ✅ | ❌ |
| `twitter` | String | 255 | ✅ | ❌ |
| `github` | String | 255 | ✅ | ❌ |
| `website` | String | 255 | ✅ | ❌ |

**Comando equivalente:**
```bash
php artisan make:migration add_social_fields_to_users_table --table=users
```

**Código generado:**
```php
public function up(): void
{
    Schema::table('users', function (Blueprint $table) {
        $table->text('bio')->nullable();
        $table->string('twitter')->nullable();
        $table->string('github')->nullable();
        $table->string('website')->nullable();
    });
}

public function down(): void
{
    Schema::table('users', function (Blueprint $table) {
        $table->dropColumn(['bio', 'twitter', 'github', 'website']);
    });
}
```

---

#### **Ejemplo 3: Tabla de Productos (E-commerce)**

**Configuración:**
- Migration Name: `create_products_table`
- Type: **Create Table**
- Table Name: `products`

**Columnas:**

| Column Name | Type | Length | Nullable | Unique |
|-------------|------|--------|----------|--------|
| `name` | String | 255 | ❌ | ❌ |
| `slug` | String | 255 | ❌ | ✅ |
| `description` | Text | - | ✅ | ❌ |
| `price` | Decimal | 10,2 | ❌ | ❌ |
| `stock` | Integer | - | ❌ | ❌ |
| `sku` | String | 100 | ❌ | ✅ |
| `is_active` | Boolean | - | ❌ | ❌ |
| `category_id` | Foreign Key | - | ❌ | ❌ |

**Comando equivalente:**
```bash
php artisan make:migration create_products_table --create=products
```

**Código generado:**
```php
public function up(): void
{
    Schema::create('products', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->string('slug')->unique();
        $table->text('description')->nullable();
        $table->decimal('price', 10, 2);
        $table->integer('stock');
        $table->string('sku', 100)->unique();
        $table->boolean('is_active');
        $table->foreignId('category_id');
        $table->timestamps();
    });
}
```

---

#### **Ejemplo 4: Tabla Pivote (Relación Muchos a Muchos)**

**Configuración:**
- Migration Name: `create_post_tag_table`
- Type: **Create Table**
- Table Name: `post_tag`

**Columnas:**

| Column Name | Type | Length | Nullable | Unique |
|-------------|------|--------|----------|--------|
| `post_id` | Foreign Key | - | ❌ | ❌ |
| `tag_id` | Foreign Key | - | ❌ | ❌ |
| `order` | Integer | - | ✅ | ❌ |

**⚠️ Nota:** No agregar timestamps en tablas pivote simples.

**Comando equivalente:**
```bash
php artisan make:migration create_post_tag_table --create=post_tag
```

**Código generado:**
```php
public function up(): void
{
    Schema::create('post_tag', function (Blueprint $table) {
        $table->id();
        $table->foreignId('post_id')->constrained()->onDelete('cascade');
        $table->foreignId('tag_id')->constrained()->onDelete('cascade');
        $table->integer('order')->nullable();
        
        // Evitar duplicados
        $table->unique(['post_id', 'tag_id']);
    });
}
```

**Uso en modelos:**
```php
// Post.php
public function tags()
{
    return $this->belongsToMany(Tag::class)->withPivot('order');
}

// Tag.php
public function posts()
{
    return $this->belongsToMany(Post::class)->withPivot('order');
}
```

---

#### **Ejemplo 5: Agregar Índice y Soft Deletes**

**Configuración:**
- Migration Name: `add_soft_deletes_to_posts_table`
- Type: **Update Table**

**Columnas:**

| Column Name | Type | Length | Nullable | Unique |
|-------------|------|--------|----------|--------|
| `deleted_at` | Timestamp | - | ✅ | ❌ |

**Comando equivalente:**
```bash
php artisan make:migration add_soft_deletes_to_posts_table --table=posts
```

**Código generado:**
```php
public function up(): void
{
    Schema::table('posts', function (Blueprint $table) {
        $table->softDeletes(); // Agrega deleted_at
    });
}

public function down(): void
{
    Schema::table('posts', function (Blueprint $table) {
        $table->dropSoftDeletes();
    });
}
```

**Agregar trait al modelo:**
```php
use Illuminate\Database\Eloquent\SoftDeletes;

class Post extends Model
{
    use SoftDeletes;
}
```

---

### Patrones Comunes de Columnas

#### **Columnas Estándar (Casi Siempre)**
```
id              → Se agrega automáticamente
created_at      → Se agrega con timestamps
updated_at      → Se agrega con timestamps
```

#### **Para Auditoría**
```
created_by  → Foreign Key → Usuario que creó
updated_by  → Foreign Key → Usuario que actualizó
deleted_at  → Timestamp (Nullable) → Soft Deletes
```

#### **Para E-commerce**
```
name        → String
price       → Decimal(10,2)
stock       → Integer
sku         → String (Unique)
is_active   → Boolean
```

#### **Para Blog/CMS**
```
title       → String
slug        → String (Unique)
content     → Text
status      → String (draft/published)
published_at → DateTime (Nullable)
author_id   → Foreign Key
```

#### **Para Usuarios**
```
name        → String
email       → String (Unique)
password    → String
remember_token → String (Nullable)
email_verified_at → Timestamp (Nullable)
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa nombres de columna descriptivos en snake_case
- Marca como `nullable` solo lo realmente opcional
- Usa `unique` para emails, slugs, códigos
- Usa `foreignId()` para relaciones (no solo integer)
- Agrega índices en columnas que usarás en WHERE
- Usa Decimal para dinero (nunca Float)
- Crea migraciones separadas para cambios grandes

❌ **DON'T (No hacer):**
- No uses nombres ambiguos (`data`, `info`, `value`)
- No olvides agregar `constrained()` a foreign keys
- No uses Text para todo (afecta rendimiento)
- No crees tablas sin primary key (id)
- No uses Float para dinero (problemas de precisión)
- No modifiques migraciones ya ejecutadas (crea nuevas)
- No uses espacios en nombres de columnas

---

### Después de Generar la Migración

#### 1. **Verificar el archivo generado:**
```bash
cat database/migrations/2024_01_15_123456_create_posts_table.php
```

#### 2. **Editar manualmente (si es necesario):**
Agregar constraints, índices compuestos, valores por defecto:
```php
$table->string('status')->default('draft');
$table->foreignId('user_id')->constrained()->onDelete('cascade');
$table->index(['status', 'published_at']); // Índice compuesto
```

#### 3. **Ejecutar la migración:**
```bash
# Ejecutar todas las migraciones pendientes
php artisan migrate

# Ver estado
php artisan migrate:status

# Ejecutar en producción (con confirmación)
php artisan migrate --force
```

#### 4. **Rollback si hay errores:**
```bash
# Revertir última migración
php artisan migrate:rollback

# Revertir todo
php artisan migrate:reset

# Revertir y re-ejecutar todo
php artisan migrate:refresh
```

#### 5. **Verificar en base de datos:**
```bash
# Ver tabla creada
php artisan db:table posts

# Ver estructura
php artisan db:show
```

---

### Comandos Útiles Relacionados

```bash
# Crear migración básica
php artisan make:migration create_posts_table

# Crear con tabla
php artisan make:migration create_posts_table --create=posts

# Modificar tabla existente
php artisan make:migration add_status_to_posts --table=posts

# Ejecutar migraciones
php artisan migrate

# Ver estado de migraciones
php artisan migrate:status

# Rollback última migración
php artisan migrate:rollback

# Rollback últimas N migraciones
php artisan migrate:rollback --step=2

# Revertir todas las migraciones
php artisan migrate:reset

# Revertir y re-ejecutar todas
php artisan migrate:refresh

# Fresh: Eliminar todas las tablas y re-ejecutar
php artisan migrate:fresh

# Fresh con seeders
php artisan migrate:fresh --seed
```

---

### Errores Comunes y Soluciones

#### ❌ **Error: "SQLSTATE[42S01]: Base table or view already exists"**
**Causa:** La tabla ya existe en la base de datos.

**Solución:**
```bash
# Opción 1: Eliminar la tabla
DROP TABLE posts;

# Opción 2: Rollback
php artisan migrate:rollback

# Opción 3: Fresh start
php artisan migrate:fresh
```

---

#### ❌ **Error: "Syntax error or access violation: 1071 Specified key was too long"**
**Causa:** Índice de String demasiado largo (charset utf8mb4).

**Solución:**
```php
// En la migración, limita la longitud
$table->string('email', 191)->unique();
```

---

#### ❌ **Error: "SQLSTATE[23000]: Integrity constraint violation"**
**Causa:** Constraint de foreign key inválido (tabla referenciada no existe).

**Solución:**
```bash
# Ejecuta migraciones en orden correcto
# 1. Crea tabla users primero
php artisan migrate --path=/database/migrations/2024_01_01_create_users_table.php

# 2. Luego tabla posts (que referencia users)
php artisan migrate --path=/database/migrations/2024_01_02_create_posts_table.php
```

---

#### ❌ **Error: "Nothing to migrate"**
**Causa:** No hay migraciones pendientes o ya fueron ejecutadas.

**Solución:**
```bash
# Ver estado
php artisan migrate:status

# Si necesitas re-ejecutar
php artisan migrate:refresh
```

---

### Verificar Migración desde DevTools

Después de generar la migración, puedes:

1. **Ver el archivo en el sistema:**
   ```
   database/migrations/2024_01_15_123456_nombre_migracion.php
   ```

2. **Ejecutar desde Artisan Commands:**
   - Ve a `Artisan Commands` en el Dashboard
   - Busca `migrate`
   - Click en "Run"

3. **Ver tablas en Database Manager:**
   - Ve a `Database Manager`
   - Explora las tablas creadas
   - Ejecuta consultas SQL

---

## 3. 👁️ Visualizadores (Viewers)

Los visualizadores son herramientas de solo lectura que te permiten inspeccionar el estado actual de tu aplicación sin modificar nada. Son útiles para debugging, auditoría y documentación.

---

## 3.1 🎮 Controllers List (Explorador de Controladores)

**Ruta**: `http://localhost:8000/devtools/project/controllers`

### ¿Qué hace?

Muestra todos los controladores de tu aplicación con sus métodos y ubicación, sin necesidad de abrir archivos. Equivalente a explorar manualmente `app/Http/Controllers/`.

---

### Interfaz de Usuario

#### **Encabezado**
```
Controllers Explorer
View and analyze application controllers
```

#### **Contador Total**
```
Controllers (16)
```
Muestra el número total de controladores en tu proyecto.

---

### Estructura de la Lista

Cada controlador se muestra como una tarjeta con:

#### **1. Nombre del Controlador**
Ejemplo: `AuthenticatedSessionController`

#### **2. Namespace (Ubicación)**
Ejemplo: `App\Http\Controllers\Auth`

**Rutas comunes:**
```
App\Http\Controllers              → Controladores principales
App\Http\Controllers\Auth         → Autenticación
App\Http\Controllers\API          → API endpoints
App\Http\Controllers\Admin        → Panel de administración
```

#### **3. Contador de Métodos**
Ejemplo: `3 methods`

Indica cuántos métodos públicos tiene el controlador.

#### **4. Botón "Show methods"**
Expandible que muestra todos los métodos del controlador.

---

### Ejemplo de Controladores Listados

#### **Controlador de Autenticación**
```
┌─────────────────────────────────────────┐
│ AuthenticatedSessionController          │
│ 3 methods                               │
│ App\Http\Controllers\Auth               │
│                                         │
│ [Show methods ▼]                        │
│   ├─ create()                           │
│   ├─ store()                            │
│   └─ destroy()                          │
└─────────────────────────────────────────┘
```

#### **Controlador Resource**
```
┌─────────────────────────────────────────┐
│ VacanteController                       │
│ 7 methods                               │
│ App\Http\Controllers                    │
│                                         │
│ [Show methods ▼]                        │
│   ├─ index()                            │
│   ├─ create()                           │
│   ├─ store()                            │
│   ├─ show()                             │
│   ├─ edit()                             │
│   ├─ update()                           │
│   └─ destroy()                          │
└─────────────────────────────────────────┘
```

#### **Controlador Invokable**
```
┌─────────────────────────────────────────┐
│ InvokeController                        │
│ 0 methods                               │
│ App\Http\Controllers                    │
│                                         │
│ (No methods - Invokable controller)     │
└─────────────────────────────────────────┘
```

**⚠️ Nota:** Los controladores Invokable solo tienen el método mágico `__invoke()`, que no se muestra como método público normal.

---

### Tipos de Controladores Identificables

#### **🔐 Controladores de Autenticación**
Ubicados en `App\Http\Controllers\Auth`:
- `RegisteredUserController` (2 methods: create, store)
- `AuthenticatedSessionController` (3 methods: create, store, destroy)
- `PasswordResetLinkController` (2 methods: create, store)
- `NewPasswordController` (2 methods: create, store)
- `EmailVerificationNotificationController` (1 method: store)
- `PasswordController` (1 method: update)
- `ConfirmablePasswordController` (2 methods: show, store)
- `VerifyEmailController` (0 methods - Invokable)
- `EmailVerificationPromptController` (0 methods - Invokable)

**Generados por:** Laravel Breeze/Jetstream

---

#### **📦 Controladores Resource**
7 métodos CRUD completos:
```
index()     → Listar recursos
create()    → Formulario de creación
store()     → Guardar nuevo recurso
show()      → Mostrar un recurso
edit()      → Formulario de edición
update()    → Actualizar recurso
destroy()   → Eliminar recurso
```

**Ejemplos en tu proyecto:**
- `VacanteController` (7 methods)
- `ParentResourcesController` (7 methods)
- `ParentResoursesDosController` (7 methods)

---

#### **🔹 Controladores Singleton**
6 métodos (con creatable) o 3 métodos (sin creatable):
```
create()    → Formulario (solo con --creatable)
store()     → Guardar (solo con --creatable)
show()      → Mostrar recurso único
edit()      → Formulario de edición
update()    → Actualizar
destroy()   → Eliminar (marcado como never)
```

**Ejemplo en tu proyecto:**
- `SingletonController` (6 methods)

---

#### **👤 Controladores de Perfil**
Controladores personalizados para usuario autenticado:
```
edit()      → Ver/editar perfil
update()    → Actualizar perfil
destroy()   → Eliminar cuenta
```

**Ejemplo en tu proyecto:**
- `ProfileController` (3 methods)

---

#### **⚡ Controladores Invokable**
Solo tienen `__invoke()` (acción única):
```
0 methods (visible)
```

**Ejemplo en tu proyecto:**
- `InvokeController` (0 methods)
- `EmailVerificationPromptController` (0 methods)
- `VerifyEmailController` (0 methods)

**Nota:** Aunque aparecen como "0 methods", internamente tienen `__invoke()`.

---

### Uso Práctico

#### **1. Auditoría Rápida**
Verifica qué controladores existen sin abrir archivos:
```
✅ "¿Existe PostController?" → Busca en la lista
✅ "¿Cuántos métodos tiene?" → Lee el contador
✅ "¿Dónde está ubicado?" → Verifica el namespace
```

#### **2. Documentación Visual**
Para nuevos desarrolladores en el equipo:
```
"Los controladores de autenticación están en Auth/"
"VacanteController es un Resource completo"
"ProfileController tiene 3 métodos personalizados"
```

#### **3. Debugging**
Identificar controladores sin métodos (posibles errores):
```
❌ InvokeController: 0 methods → OK (es invokable)
❌ Controller: 0 methods → OK (es clase base)
⚠️  UserController: 0 methods → Problema (debería tener métodos)
```

#### **4. Comparación con Rutas**
Verificar que los métodos del controlador estén registrados en rutas:
```
VacanteController tiene 7 métodos
↓
Ve a Routes List
↓
Verifica que existan rutas para vacantes.index, vacantes.create, etc.
```

---

### Comandos Equivalentes

**Ver controladores manualmente:**
```bash
# Listar todos los controladores
ls -la app/Http/Controllers/

# Ver controladores de Auth
ls -la app/Http/Controllers/Auth/

# Contar controladores
find app/Http/Controllers -name "*Controller.php" | wc -l

# Ver métodos de un controlador específico
grep "public function" app/Http/Controllers/VacanteController.php
```

**Buscar controlador por nombre:**
```bash
find app/Http/Controllers -name "VacanteController.php"
```

**Ver namespace completo:**
```bash
head -n 3 app/Http/Controllers/VacanteController.php
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa esta vista para auditorías rápidas de código
- Verifica que controladores tengan los métodos esperados
- Documenta la arquitectura del proyecto con screenshots
- Compara con Routes List para encontrar rutas huérfanas
- Identifica controladores duplicados o sin uso

❌ **DON'T (No hacer):**
- No uses esto como reemplazo del IDE (no muestra código)
- No asumas que todos los métodos están en uso (verifica rutas)
- No confundas "0 methods" con error (puede ser invokable)

---

### Problemas Comunes

#### **❌ Controlador no aparece en la lista**
**Causas:**
- Archivo no tiene sufijo `Controller.php`
- Namespace incorrecto
- Archivo fuera de `app/Http/Controllers/`

**Solución:**
```bash
# Verificar ubicación
ls -la app/Http/Controllers/TuController.php

# Verificar namespace
head -n 3 app/Http/Controllers/TuController.php
# Debe ser: namespace App\Http\Controllers;
```

---

#### **⚠️ Controlador con 0 métodos (no es invokable)**
**Problema:** Controlador vacío sin métodos definidos.

**Ejemplo:**
```php
class EmptyController extends Controller
{
    // Sin métodos
}
```

**Solución:** Agrega métodos o elimina el controlador si no se usa.

---

#### **🔍 Métodos privados no aparecen**
**Comportamiento esperado:** Solo muestra métodos públicos.

```php
class UserController extends Controller
{
    public function index() { }      // ✅ Aparece
    protected function helper() { }  // ❌ No aparece
    private function internal() { }  // ❌ No aparece
}
```

---

## 3.2 🛣️ Routes List (Explorador de Rutas)

**Ruta**: `http://localhost:8000/devtools/project/routes`

### ¿Qué hace?

Muestra todas las rutas registradas en tu aplicación Laravel con detalles completos: método HTTP, URI, nombre, acción y middleware. Equivalente a ejecutar `php artisan route:list` pero con interfaz visual.

---

### Interfaz de Usuario

#### **Encabezado**
```
Routes Explorer
View and analyze application routes
```

#### **Selector de Archivo de Rutas**
Tabs para filtrar por archivo:
```
┌────────────────────────────────────────────┐
│ web.php | api.php | channels.php | auth.php │
│         | console.php                       │
└────────────────────────────────────────────┘
```

**Archivos de rutas:**
- `web.php` → Rutas web con sesiones (formularios, vistas)
- `api.php` → Rutas API sin estado (JSON, tokens)
- `auth.php` → Rutas de autenticación (Breeze)
- `channels.php` → Broadcasting (WebSockets)
- `console.php` → Comandos de consola

---

#### **Contador Total**
```
Routes (28)
```
Muestra el número de rutas en el archivo seleccionado.

---

### Estructura de la Tabla

Tabla con 5 columnas:

| Método HTTP | URI | Nombre | Acción | Middleware |
|-------------|-----|--------|--------|------------|
| GET | dashboard | vacantes.index | VacanteController@index | web, auth, verified |

---

### Columnas Explicadas

#### **1. Método HTTP**
Verbo HTTP de la petición:

| Método | Uso | Descripción |
|--------|-----|-------------|
| **GET** | Leer | Obtener datos (páginas, listados) |
| **POST** | Crear | Enviar datos (formularios, crear) |
| **PUT** | Actualizar | Actualizar recurso completo |
| **PATCH** | Modificar | Actualizar parcial |
| **DELETE** | Eliminar | Borrar recurso |

**Ejemplo visual:**
```
┌──────┐
│ GET  │ → Mostrar página/datos
└──────┘

┌──────┐
│ POST │ → Enviar formulario
└──────┘

┌────────┐
│ DELETE │ → Eliminar registro
└────────┘
```

---

#### **2. URI (Uniform Resource Identifier)**
Ruta URL de la aplicación.

**Patrones comunes:**

```
/                              → Página de inicio
/dashboard                     → Dashboard
/posts                         → Listar posts
/posts/create                  → Formulario crear post
/posts/{id}                    → Ver post específico
/posts/{id}/edit               → Editar post
/api/users                     → API de usuarios
/profile                       → Perfil del usuario
```

**Con parámetros:**
```
/posts/{post}                  → {post} = ID dinámico
/users/{user}/posts/{post}     → Rutas anidadas
/reset-password/{token}        → Token de recuperación
```

**Botón "Open in new tab":**
Click para abrir la ruta en el navegador.

---

#### **3. Nombre (Route Name)**
Nombre único asignado a la ruta para referencia.

**Formato común:** `recurso.accion`

```
posts.index      → GET /posts
posts.create     → GET /posts/create
posts.store      → POST /posts
posts.show       → GET /posts/{id}
posts.edit       → GET /posts/{id}/edit
posts.update     → PUT /posts/{id}
posts.destroy    → DELETE /posts/{id}
```

**Uso en Blade:**
```blade
<a href="{{ route('posts.index') }}">Ver Posts</a>
<form action="{{ route('posts.store') }}" method="POST">
```

**Uso en controladores:**
```php
return redirect()->route('posts.show', $post);
return redirect()->route('dashboard');
```

**Rutas sin nombre:**
Aparecen como `-` en la tabla. No son accesibles con `route()`.

---

#### **4. Acción (Action)**
Controlador y método que maneja la ruta.

**Formatos:**

**Controlador@Método:**
```
App\Http\Controllers\VacanteController@index
App\Http\Controllers\Auth\RegisteredUserController@create
```

**Clase Invokable:**
```
App\Http\Controllers\SendNewsletterController
(Solo el nombre, usa __invoke())
```

**Closure (Función anónima):**
```
Closure
```
Ruta definida directamente en `routes/web.php`:
```php
Route::get('/', function () {
    return view('welcome');
});
```

**Controladores de paquetes:**
```
Livewire\Mechanisms\HandleRequests\HandleRequests@handleUpdate
```

---

#### **5. Middleware**
Filtros que se ejecutan antes/después de la ruta.

**Middleware comunes:**

| Middleware | Descripción | Uso |
|------------|-------------|-----|
| **web** | Sesiones, CSRF, cookies | Rutas con formularios |
| **api** | Stateless, sin sesiones | APIs REST |
| **auth** | Usuario autenticado requerido | Áreas protegidas |
| **guest** | Solo usuarios NO autenticados | Login, registro |
| **verified** | Email verificado requerido | Contenido premium |
| **throttle:60,1** | Limita a 60 peticiones/minuto | Prevenir abuso |
| **signed** | URL firmada (segura) | Links de verificación |

**Ejemplo visual:**
```
┌────────────────────────────────────┐
│ GET /dashboard                     │
│ Middleware: web, auth, verified    │
└────────────────────────────────────┘
        ↓
    ┌──────┐    ┌──────┐    ┌──────────┐
    │ web  │ →  │ auth │ →  │ verified │ → Controlador
    └──────┘    └──────┘    └──────────┘
     sesión     logueado    email OK
```

**Middleware apilado:**
```
web, auth, verified
↓
1. web: Inicia sesión
2. auth: Verifica login (redirige a /login si no está autenticado)
3. verified: Verifica email (redirige a /verify-email si no está verificado)
```

---

### Ejemplos de Rutas por Tipo

#### **🏠 Rutas Públicas (Solo web)**
```
GET  /               Closure              web
GET  /about          PageController@about web
```
Accesibles sin login.

---

#### **🔐 Rutas Protegidas (web + auth)**
```
GET  /dashboard      DashboardController@index  web, auth
GET  /profile        ProfileController@edit     web, auth
```
Requieren autenticación.

---

#### **✅ Rutas con Verificación (web + auth + verified)**
```
GET  /vacantes/create    VacanteController@create    web, auth, verified
POST /vacantes           VacanteController@store     web, auth, verified
```
Requieren email verificado.

---

#### **🚪 Rutas de Invitados (web + guest)**
```
GET  /login          AuthController@create    web, guest
POST /register       AuthController@store     web, guest
```
Solo accesibles si NO estás logueado.

---

#### **🌐 Rutas de API (api + throttle)**
```
GET     /api/users          UserController@index    api, throttle:60,1
POST    /api/posts          PostController@store    api, auth:sanctum
DELETE  /api/posts/{id}     PostController@destroy  api, auth:sanctum
```
Sin sesiones, usan tokens.

---

#### **📧 Rutas Firmadas (signed)**
```
GET  /verify-email/{id}/{hash}    VerifyEmailController    web, auth, signed, throttle:6,1
```
URL con firma de seguridad, expira.

---

### Rutas Resource Completas

Cuando defines:
```php
Route::resource('posts', PostController::class);
```

Genera 7 rutas automáticamente:

| Método | URI | Nombre | Acción | Propósito |
|--------|-----|--------|--------|-----------|
| GET | /posts | posts.index | PostController@index | Listar |
| GET | /posts/create | posts.create | PostController@create | Formulario crear |
| POST | /posts | posts.store | PostController@store | Guardar |
| GET | /posts/{post} | posts.show | PostController@show | Ver |
| GET | /posts/{post}/edit | posts.edit | PostController@edit | Formulario editar |
| PUT/PATCH | /posts/{post} | posts.update | PostController@update | Actualizar |
| DELETE | /posts/{post} | posts.destroy | PostController@destroy | Eliminar |

---

### Rutas Singleton

Cuando defines:
```php
Route::singleton('profile', ProfileController::class);
```

Genera 3 rutas (sin ID en URL):

| Método | URI | Nombre | Acción |
|--------|-----|--------|--------|
| GET | /profile | profile.show | ProfileController@show |
| GET | /profile/edit | profile.edit | ProfileController@edit |
| PUT/PATCH | /profile | profile.update | ProfileController@update |

---

### Uso Práctico

#### **1. Debugging de Rutas**
```
❌ Error 404 en /posts/create
↓
Busca en Routes List: GET /posts/create
↓
✅ Ruta existe → Problema en el controlador
❌ Ruta NO existe → Falta registrar en routes/web.php
```

---

#### **2. Verificar Middleware**
```
❌ Usuario no autenticado puede acceder a /dashboard
↓
Busca: GET /dashboard
↓
Middleware: web, auth
↓
✅ Middleware correcto, verifica implementación
```

---

#### **3. Encontrar Nombre de Ruta**
```
Necesito redirigir a la edición de posts
↓
Busca: GET /posts/{post}/edit
↓
Nombre: posts.edit
↓
Usa: redirect()->route('posts.edit', $post)
```

---

#### **4. Auditoría de API**
```
Filtrar por: api.php
↓
Ver todas las rutas /api/*
↓
Verificar throttle para prevenir abuso
```

---

#### **5. Identificar Rutas Huérfanas**
```
Closure en Routes List
↓
No tiene nombre
↓
❌ Difícil de mantener
↓
Refactorizar a controlador
```

---

### Comandos Equivalentes

**Listar todas las rutas:**
```bash
php artisan route:list
```

**Filtrar por nombre:**
```bash
php artisan route:list --name=posts
```

**Filtrar por método:**
```bash
php artisan route:list --method=GET
```

**Filtrar por ruta:**
```bash
php artisan route:list --path=api
```

**Ordenar por URI:**
```bash
php artisan route:list --sort=uri
```

**Ver solo rutas de un archivo:**
```bash
php artisan route:list --path=api  # Para api.php
```

**Formato compacto:**
```bash
php artisan route:list --compact
```

**Buscar ruta específica:**
```bash
php artisan route:list | grep dashboard
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Revisa Routes List cuando tengas errores 404
- Verifica que middleware sean correctos para cada ruta
- Usa nombres de ruta consistentes (recurso.accion)
- Compara Routes List con Controllers List para encontrar métodos sin ruta
- Documenta tus APIs mostrando esta vista
- Usa throttle en rutas públicas (login, API)

❌ **DON'T (No hacer):**
- No definas Closures para lógica compleja (usa controladores)
- No olvides agregar middleware `auth` a rutas protegidas
- No uses rutas sin nombre si las vas a referenciar
- No expongas rutas sensibles sin throttle
- No dupliques nombres de ruta

---

### Problemas Comunes

#### **❌ Error: "Route [posts.index] not defined"**
**Causa:** Ruta no tiene nombre asignado.

**Solución:**
```php
// ❌ Mal - Sin nombre
Route::get('/posts', [PostController::class, 'index']);

// ✅ Bien - Con nombre
Route::get('/posts', [PostController::class, 'index'])->name('posts.index');
```

---

#### **❌ Error 404 en ruta que existe en Routes List**
**Causas posibles:**
1. **Método HTTP incorrecto:**
   ```html
   <!-- ❌ Mal -->
   <a href="/posts">Crear Post</a>
   
   <!-- ✅ Bien -->
   <form action="/posts" method="POST">
   ```

2. **Parámetros faltantes:**
   ```php
   // ❌ Mal
   route('posts.show') // Falta el ID
   
   // ✅ Bien
   route('posts.show', $post)
   ```

3. **Middleware bloqueando:**
   ```
   Ruta: /dashboard (middleware: auth)
   Usuario: No autenticado
   Resultado: Redirige a /login (no 404)
   ```

---

#### **⚠️ Ruta duplicada**
**Problema:** Dos rutas con el mismo método + URI.

```php
Route::get('/posts', [PostController::class, 'index']);
Route::get('/posts', [BlogController::class, 'list']); // ❌ Duplicado
```

**Detección en Routes List:**
La última definida sobrescribe la primera (sin advertencia).

**Solución:**
```bash
# Buscar duplicados
php artisan route:list | sort | uniq -d
```

---

#### **🔒 Ruta accesible sin autenticación**
**Problema:** Ruta protegida sin middleware `auth`.

**Detección:**
```
GET /admin/users    AdminController@index    web
                                             ↑ Falta 'auth'
```

**Solución:**
```php
Route::get('/admin/users', [AdminController::class, 'index'])
    ->middleware('auth'); // Agrega middleware
```

---

### Casos de Uso Avanzados

#### **1. API Versioning**
```
GET  /api/v1/users    UserV1Controller@index    api
GET  /api/v2/users    UserV2Controller@index    api
```

Identifica versiones de API en Routes List.

---

#### **2. Rutas Multilingües**
```
GET  /en/posts        PostController@index    web
GET  /es/posts        PostController@index    web
GET  /fr/posts        PostController@index    web
```

Detecta prefijos de idioma.

---

#### **3. Subdominios**
```
GET  admin.app.com/dashboard    AdminController    web, auth
GET  api.app.com/users          UserController     api
```

Rutas con subdominios específicos.

---

### Integración con Controllers List

**Flujo de trabajo:**

1. **Ve a Controllers List:**
   - Encuentra `PostController`
   - Ve que tiene 7 métodos (Resource)

2. **Ve a Routes List:**
   - Filtra por "posts"
   - Verifica que existan 7 rutas correspondientes

3. **Detecta problemas:**
   - ✅ 7 métodos en controlador = 7 rutas → OK
   - ⚠️ 7 métodos pero solo 5 rutas → Faltan 2 rutas
   - ❌ 5 métodos pero 7 rutas → 2 métodos no existen

---

### Verificación Completa

**Checklist de auditoría:**

```
✅ Todas las rutas tienen middleware apropiado
✅ Rutas protegidas tienen 'auth'
✅ Rutas de API tienen 'throttle'
✅ Rutas críticas usan 'signed'
✅ No hay Closures complejas
✅ Todos los nombres de ruta son únicos
✅ URLs RESTful correctas (/posts, no /listPosts)
✅ Métodos HTTP correctos (GET para ver, POST para crear)
✅ No hay rutas duplicadas
✅ Controladores existen en Controllers List
```

---

### Comandos Útiles Relacionados

```bash
# Limpiar caché de rutas
php artisan route:clear

# Cachear rutas (producción)
php artisan route:cache

# Ver ruta específica
php artisan route:list --name=posts.index

# Exportar rutas a archivo
php artisan route:list > routes.txt

# Ver rutas con middleware específico
php artisan route:list | grep "auth"

# Contar rutas totales
php artisan route:list --compact | wc -l

# Ver solo rutas API
php artisan route:list --path=api

# Ver rutas de un controlador
php artisan route:list | grep PostController
```

---

## 3.3 📊 Resumen de Visualizadores

### Comparación Rápida

| Característica | Controllers List | Routes List |
|----------------|------------------|-------------|
| **Muestra** | Controladores y métodos | Rutas registradas |
| **Filtros** | Por namespace | Por archivo (web/api) |
| **Interacción** | Ver métodos | Abrir en navegador |
| **Debugging** | Verificar métodos existen | Verificar ruta existe |
| **Equivalente CLI** | `ls app/Http/Controllers` | `php artisan route:list` |

---

### Workflow Completo de Debugging

```
1. Usuario reporta error 404 en /posts/create
   ↓
2. Ve a Routes List
   ↓
3. Busca: GET /posts/create
   ↓
4. Ruta existe → Verifica controlador
   ↓
5. Ve a Controllers List
   ↓
6. Busca: PostController
   ↓
7. Verifica que tenga método create()
   ↓
8. Si existe → Error en el método
9. Si no existe → Agrega el método
```

---

## 4. 🗄️ Database Manager (Administrador de Base de Datos)

**Ruta**: `http://localhost:8000/devtools/database`

### ¿Qué hace?

Herramienta visual para explorar tablas de la base de datos y ejecutar consultas SQL de solo lectura (SELECT). Es como tener phpMyAdmin o Adminer integrado en tu aplicación Laravel.

---

### Interfaz de Usuario

#### **Encabezado**
```
Database Manager
Explore database tables and execute queries
```

---

### Secciones Principales

#### **1. 📋 Tables (Explorador de Tablas)**

**Ubicación:** Panel lateral izquierdo

**Contador:**
```
Tables
11 tables
```

**Tabs disponibles:**
- **Tables** → Tablas normales de la aplicación
- **Views** → Vistas SQL (consultas guardadas)
- **Migrations** → Historial de migraciones ejecutadas

---

##### **Lista de Tablas**

Cada tabla se muestra como una tarjeta con:

**Nombre de la tabla:**
```
users
```

**Contador de registros:**
```
1 ← Número de filas en la tabla
```

**Ejemplo visual:**
```
┌─────────────────┐
│ 📊 users    (1) │
├─────────────────┤
│ 📊 vacantes (0) │
├─────────────────┤
│ 📊 sessions (8) │
├─────────────────┤
│ 📊 migrations(6)│
└─────────────────┘
```

---

##### **Tablas del Sistema Laravel**

**cache** (0 registros)
- Almacena caché de base de datos
- Generada por: `php artisan cache:table`
- Uso: `Cache::store('database')->put('key', 'value')`

**cache_locks** (0 registros)
- Control de bloqueos para caché
- Previene race conditions
- Usado internamente por Laravel

**failed_jobs** (0 registros)
- Trabajos en cola que fallaron
- Estructura: `id`, `uuid`, `connection`, `queue`, `payload`, `exception`, `failed_at`
- Ver con: `php artisan queue:failed`

**job_batches** (0 registros)
- Lotes de trabajos en cola
- Permite procesar múltiples jobs como grupo
- Usado con `Bus::batch()`

**jobs** (0 registros)
- Cola de trabajos pendientes
- Estructura: `id`, `queue`, `payload`, `attempts`, `reserved_at`, `available_at`, `created_at`
- Procesar con: `php artisan queue:work`

**migrations** (6 registros)
- Historial de migraciones ejecutadas
- Estructura: `id`, `migration`, `batch`
- NO eliminar manualmente (rompe `php artisan migrate:rollback`)

**password_reset_tokens** (0 registros)
- Tokens para recuperar contraseña
- Estructura: `email`, `token`, `created_at`
- Expiran automáticamente (ver `config/auth.php`)

**sessions** (8 registros)
- Sesiones de usuarios activos
- Estructura: `id`, `user_id`, `ip_address`, `user_agent`, `payload`, `last_activity`
- Solo si `SESSION_DRIVER=database` en `.env`

---

##### **Tablas de la Aplicación**

**users** (1 registro)
- Usuarios registrados
- Columnas típicas: `id`, `name`, `email`, `password`, `email_verified_at`, `created_at`, `updated_at`

**vacantes** (0 registros)
- Tabla personalizada de tu aplicación
- Depende de tu modelo `Vacante`

---

##### **Click en una Tabla**

Al hacer click en una tabla (ej: `users`), se muestra:

**Información de la tabla:**
```
Tabla: users
Registros: 1
Motor: InnoDB
Collation: utf8mb4_unicode_ci
```

**Estructura de columnas:**
| Columna | Tipo | Nulo | Default | Extra |
|---------|------|------|---------|-------|
| id | BIGINT UNSIGNED | NO | - | AUTO_INCREMENT |
| name | VARCHAR(255) | NO | - | - |
| email | VARCHAR(255) | NO | - | UNIQUE |
| email_verified_at | TIMESTAMP | YES | NULL | - |
| password | VARCHAR(255) | NO | - | - |
| remember_token | VARCHAR(100) | YES | NULL | - |
| created_at | TIMESTAMP | YES | NULL | - |
| updated_at | TIMESTAMP | YES | NULL | - |

**Datos de la tabla:**
Muestra los registros actuales (primeras 100 filas por defecto).

**Acciones:**
- **Export** → Descargar en CSV/JSON
- **Refresh** → Recargar datos
- **View SQL** → Ver CREATE TABLE statement

---

#### **2. ✍️ Query Editor (Editor de Consultas SQL)**

**Ubicación:** Panel central derecho

**Características:**

##### **Conexión Actual**
```
Connection: `mysql`
```
Muestra el driver de base de datos (mysql, pgsql, sqlite, sqlsrv).

##### **⚠️ Restricción de Seguridad**
```
Only SELECT queries are allowed for security
```

**Consultas permitidas:**
```sql
✅ SELECT * FROM users
✅ SELECT name, email FROM users WHERE id = 1
✅ SELECT COUNT(*) FROM vacantes
✅ SELECT * FROM users ORDER BY created_at DESC LIMIT 10
```

**Consultas bloqueadas:**
```sql
❌ INSERT INTO users ...
❌ UPDATE users SET ...
❌ DELETE FROM users ...
❌ DROP TABLE users
❌ TRUNCATE TABLE users
❌ ALTER TABLE users ...
```

**Razón:** Prevenir modificaciones accidentales en producción.

---

##### **Botones de Ayuda Rápida**

**SELECT**
Inserta plantilla:
```sql
SELECT * FROM tabla
```

**COUNT**
Inserta plantilla:
```sql
SELECT COUNT(*) FROM tabla
```

**WHERE**
Inserta plantilla:
```sql
WHERE columna = 'valor'
```

---

##### **Botones de Funcionalidad**

**🎨 Format**
Formatea automáticamente el SQL:
```sql
-- Antes
select*from users where id=1

-- Después (formatted)
SELECT *
FROM users
WHERE id = 1
```

---

**📜 History**
Muestra historial de consultas ejecutadas:
```
1. SELECT * FROM users
2. SELECT COUNT(*) FROM vacantes
3. SELECT * FROM sessions WHERE user_id IS NOT NULL
```

**Uso:**
- Click en consulta anterior para re-ejecutar
- Evita reescribir consultas complejas
- Útil para debugging

---

**⭐ Favorites**
Guarda consultas favoritas:
```sql
-- Consulta guardada: "Usuarios verificados"
SELECT * FROM users WHERE email_verified_at IS NOT NULL

-- Consulta guardada: "Sesiones activas"
SELECT * FROM sessions WHERE last_activity > UNIX_TIMESTAMP() - 3600
```

**Uso:**
- Click en "Add to Favorites" después de ejecutar
- Organiza consultas frecuentes
- Comparte con el equipo

---

**📊 EXPLAIN**
Analiza el plan de ejecución de la consulta:
```sql
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com'
```

**Resultado:**
```
id | select_type | table | type | possible_keys | key   | rows | Extra
1  | SIMPLE      | users | ref  | email_index   | email | 1    | Using where
```

**Interpretación:**
- `type: ref` → Usa índice (✅ Bueno)
- `type: ALL` → Full table scan (⚠️ Lento en tablas grandes)
- `rows: 1` → Lee solo 1 fila (✅ Eficiente)
- `rows: 10000` → Lee 10k filas (❌ Optimizar)

---

**🔧 Builder**
Constructor visual de consultas (sin escribir SQL):

**Interfaz:**
```
┌─────────────────────────────────────┐
│ Tabla:    [users ▼]                 │
│ Columnas: [☑ id ☑ name ☑ email]    │
│ WHERE:    [email] [=] [test@...]    │
│ ORDER BY: [created_at] [DESC ▼]    │
│ LIMIT:    [10]                      │
│                                     │
│ [Generate SQL]                      │
└─────────────────────────────────────┘
```

**SQL Generado:**
```sql
SELECT id, name, email
FROM users
WHERE email = 'test@example.com'
ORDER BY created_at DESC
LIMIT 10
```

---

##### **Ejecutar Consulta**

**Atajo de teclado:**
```
Ctrl + ↵ (Enter)
```

**Botón:**
```
[▶ Execute Query]
```

---

##### **Resultados de la Consulta**

Después de ejecutar, se muestra:

**Información:**
```
✅ Query executed successfully
Rows returned: 1
Execution time: 0.023s
```

**Tabla de resultados:**
| id | name | email | email_verified_at | created_at |
|----|------|-------|-------------------|------------|
| 1 | John Doe | john@example.com | 2024-01-15 10:30:00 | 2024-01-01 08:00:00 |

**Acciones sobre resultados:**
- **Copy** → Copiar al portapapeles
- **Export CSV** → Descargar como CSV
- **Export JSON** → Descargar como JSON
- **Copy as SQL** → Copiar como INSERT statements

---

### Ejemplos Prácticos de Consultas

#### **1. Ver todos los usuarios**
```sql
SELECT * FROM users;
```

---

#### **2. Contar registros totales**
```sql
SELECT COUNT(*) AS total FROM users;
```

**Resultado:**
```
total
-----
1
```

---

#### **3. Usuarios con email verificado**
```sql
SELECT id, name, email, email_verified_at
FROM users
WHERE email_verified_at IS NOT NULL;
```

---

#### **4. Últimos 10 registros**
```sql
SELECT *
FROM users
ORDER BY created_at DESC
LIMIT 10;
```

---

#### **5. Buscar por texto parcial**
```sql
SELECT *
FROM users
WHERE name LIKE '%John%';
```

---

#### **6. Registros de hoy**
```sql
SELECT *
FROM users
WHERE DATE(created_at) = CURDATE();
```

---

#### **7. Contar por agrupación**
```sql
SELECT DATE(created_at) AS fecha, COUNT(*) AS total
FROM users
GROUP BY DATE(created_at)
ORDER BY fecha DESC;
```

---

#### **8. Join entre tablas**
```sql
SELECT u.name, v.titulo
FROM users u
INNER JOIN vacantes v ON v.user_id = u.id;
```

---

#### **9. Sesiones activas**
```sql
SELECT *
FROM sessions
WHERE last_activity > UNIX_TIMESTAMP() - 3600
ORDER BY last_activity DESC;
```

---

#### **10. Usuarios sin verificar**
```sql
SELECT id, name, email, created_at
FROM users
WHERE email_verified_at IS NULL
ORDER BY created_at DESC;
```

---

### Casos de Uso

#### **🔍 Debugging**

**Problema:** Usuario reporta que no puede iniciar sesión.

**Consulta:**
```sql
SELECT id, email, email_verified_at, password
FROM users
WHERE email = 'user@example.com';
```

**Verificar:**
- ✅ Usuario existe
- ✅ Email está verificado
- ✅ Password no es NULL

---

#### **📊 Análisis de Datos**

**Pregunta:** ¿Cuántos usuarios registrados por mes?

**Consulta:**
```sql
SELECT 
    DATE_FORMAT(created_at, '%Y-%m') AS mes,
    COUNT(*) AS usuarios
FROM users
GROUP BY mes
ORDER BY mes DESC;
```

**Resultado:**
```
mes     | usuarios
--------|---------
2024-01 | 15
2023-12 | 8
2023-11 | 12
```

---

#### **🧹 Limpieza de Datos**

**Pregunta:** ¿Cuántas sesiones inactivas hay?

**Consulta:**
```sql
SELECT COUNT(*) AS sesiones_viejas
FROM sessions
WHERE last_activity < UNIX_TIMESTAMP() - 604800; -- 7 días
```

**Acción después:**
```bash
php artisan session:gc # Limpiar sesiones viejas
```

---

#### **✅ Validación de Migraciones**

**Pregunta:** ¿Se ejecutó la migración de `soft_deletes`?

**Consulta:**
```sql
SELECT * FROM migrations
WHERE migration LIKE '%soft_deletes%';
```

---

#### **🔐 Auditoría de Seguridad**

**Pregunta:** ¿Hay usuarios con contraseñas débiles (NULL o vacías)?

**Consulta:**
```sql
SELECT id, email
FROM users
WHERE password IS NULL OR password = '';
```

**⚠️ Resultado esperado:** 0 filas (ningún usuario sin contraseña).

---

### Comandos SQL Útiles

#### **Información de Tablas**

```sql
-- Ver todas las tablas
SHOW TABLES;

-- Estructura de tabla
DESCRIBE users;

-- CREATE statement completo
SHOW CREATE TABLE users;

-- Tamaño de tablas
SELECT 
    table_name AS tabla,
    ROUND(((data_length + index_length) / 1024 / 1024), 2) AS "Size (MB)"
FROM information_schema.TABLES
WHERE table_schema = DATABASE()
ORDER BY (data_length + index_length) DESC;
```

---

#### **Estadísticas**

```sql
-- Total de registros por tabla
SELECT 
    table_name AS tabla,
    table_rows AS registros
FROM information_schema.TABLES
WHERE table_schema = DATABASE()
ORDER BY table_rows DESC;

-- Índices de una tabla
SHOW INDEX FROM users;
```

---

#### **Datos del Sistema**

```sql
-- Versión de MySQL
SELECT VERSION();

-- Base de datos actual
SELECT DATABASE();

-- Charset y collation
SELECT @@character_set_database, @@collation_database;

-- Variables del sistema
SHOW VARIABLES LIKE 'max_connections';
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa `LIMIT` en consultas grandes para evitar timeouts
- Usa EXPLAIN para optimizar consultas lentas
- Guarda consultas frecuentes en Favorites
- Exporta resultados antes de hacer cambios manuales
- Verifica índices con `SHOW INDEX FROM tabla`
- Usa Query Builder para consultas complejas (evita errores de sintaxis)
- Formatea SQL con el botón Format (más legible)

❌ **DON'T (No hacer):**
- No ejecutes consultas sin `WHERE` en tablas grandes
- No copies contraseñas hasheadas (son inútiles sin salt)
- No compartas capturas con datos sensibles (emails, tokens)
- No intentes ejecutar INSERT/UPDATE (están bloqueados)
- No elimines registros de la tabla `migrations`
- No confíes en `SELECT *` en producción (especifica columnas)

---

### Errores Comunes

#### **❌ "Query execution time exceeded"**
**Causa:** Consulta muy pesada en tabla grande.

**Solución:**
```sql
-- ❌ Mal - Sin LIMIT
SELECT * FROM logs;

-- ✅ Bien - Con LIMIT
SELECT * FROM logs LIMIT 100;

-- ✅ Mejor - Con índice
SELECT * FROM logs
WHERE created_at > '2024-01-01'
ORDER BY created_at DESC
LIMIT 100;
```

---

#### **❌ "This query is not allowed (not a SELECT)"**
**Causa:** Intentaste ejecutar INSERT/UPDATE/DELETE.

**Mensaje:**
```
❌ Error: Only SELECT queries are allowed for security reasons
```

**Solución:**
Si necesitas modificar datos, usa:
```bash
php artisan tinker
>>> User::find(1)->update(['name' => 'New Name']);
```

O ejecuta desde terminal:
```bash
sail mysql
mysql> UPDATE users SET name = 'New Name' WHERE id = 1;
```

---

#### **❌ "Table 'database.tabla' doesn't exist"**
**Causa:** Tabla no existe o nombre incorrecto.

**Verificar:**
```sql
SHOW TABLES;
```

**Solución:**
```bash
# Ejecutar migraciones
php artisan migrate

# Ver estado
php artisan migrate:status
```

---

#### **⚠️ Consulta muy lenta**
**Síntomas:** Ejecutar consulta tarda más de 5 segundos.

**Diagnóstico:**
```sql
EXPLAIN SELECT * FROM users WHERE email = 'test@example.com';
```

**Si `type: ALL` (full table scan):**
```sql
-- Agregar índice
CREATE INDEX idx_email ON users(email);
```

**O en migración:**
```php
$table->string('email')->index();
```

---

### Integración con Otras Herramientas

#### **1. Con Artisan Commands**
```
Database Manager → Identificas sesiones viejas
      ↓
Artisan Commands → php artisan session:gc
      ↓
Database Manager → Verificas que se eliminaron
```

---

#### **2. Con Models**
```
Database Manager → SELECT * FROM users WHERE email_verified_at IS NULL
      ↓
Tinker → User::whereNull('email_verified_at')->count()
      ↓
Enviar emails de verificación masivos
```

---

#### **3. Con Migrations**
```
Database Manager → DESCRIBE users (falta columna 'bio')
      ↓
Migration Generator → Crear add_bio_to_users_table
      ↓
Artisan → php artisan migrate
      ↓
Database Manager → Verificar columna agregada
```

---

### Acceso desde Terminal

Si prefieres terminal en lugar de UI:

#### **MySQL/MariaDB:**
```bash
# Conectar con Sail
sail mysql

# O sin Sail
mysql -u usuario -p base_de_datos
```

#### **PostgreSQL:**
```bash
sail psql
```

#### **SQLite:**
```bash
sqlite3 database/database.sqlite
```

---

### Exportar Datos

#### **Desde Database Manager:**
1. Ejecuta consulta: `SELECT * FROM users`
2. Click en **Export CSV** o **Export JSON**
3. Archivo descargado: `users_2024-01-15.csv`

#### **Desde Terminal:**
```bash
# Exportar tabla a SQL
sail exec mysql mysqldump -u sail -p nombre_db users > users.sql

# Exportar a CSV
sail exec mysql mysql -u sail -p nombre_db -e "SELECT * FROM users" > users.csv

# Backup completo
php artisan backup:run
```

---

### Comandos Útiles Relacionados

```bash
# Ver tablas desde Artisan
php artisan db:table users

# Ver toda la base de datos
php artisan db:show

# Conectar a MySQL
sail mysql

# Ejecutar SQL desde archivo
sail mysql < query.sql

# Backup de base de datos
sail exec mysql mysqldump -u sail -p nombre_db > backup.sql

# Restaurar backup
sail mysql < backup.sql

# Ver configuración de BD
php artisan config:show database

# Limpiar tablas (fresh)
php artisan migrate:fresh

# Sembrar datos
php artisan db:seed
```

---

### Seguridad y Precauciones

#### **⚠️ IMPORTANTE en Producción**

**NO uses Database Manager en producción si:**
- Expone datos sensibles (contraseñas, tarjetas, etc.)
- No tiene autenticación adicional
- Está accesible públicamente

**Protección recomendada:**
```php
// En RouteServiceProvider o middleware
if (app()->environment('production')) {
    // Bloquear acceso en producción
    abort(403, 'Database Manager disabled in production');
}
```

**O limitar por IP:**
```php
Route::middleware(['auth', 'admin'])->group(function () {
    // Solo admins autenticados
});
```

---

#### **Datos Sensibles**

**Nunca consultes directamente:**
```sql
❌ SELECT password FROM users
❌ SELECT remember_token FROM users
❌ SELECT api_token FROM users
```

**Razón:** Las contraseñas hasheadas no deben ser visibles ni copiadas.

---

#### **Logs de Consultas**

Todas las consultas ejecutadas se registran en:
```
storage/logs/laravel.log
```

**Útil para:** Auditoría y debugging.

---

### Resumen de Funcionalidades

| Característica | Disponible | Notas |
|----------------|------------|-------|
| Ver tablas | ✅ | Con contador de registros |
| Estructura de columnas | ✅ | Tipos, índices, constraints |
| SELECT queries | ✅ | Solo lectura |
| INSERT/UPDATE/DELETE | ❌ | Bloqueado por seguridad |
| EXPLAIN queries | ✅ | Análisis de rendimiento |
| Query Builder visual | ✅ | Sin escribir SQL |
| Historial de consultas | ✅ | Últimas 50 consultas |
| Favoritos | ✅ | Guardar consultas frecuentes |
| Exportar CSV/JSON | ✅ | Resultados de consultas |
| Formato automático | ✅ | Embellece SQL |
| Múltiples conexiones | ✅ | Si tienes varias BD |

---

## 5. 🛠️ Herramientas (Tools)

Las herramientas son módulos avanzados para ejecutar comandos, gestionar dependencias y monitorear el estado de la aplicación en tiempo real.

---

## 5.1 ⚡ Artisan Commands (Comandos de Artisan)

**Ruta**: `http://localhost:8000/devtools/artisan`

### ¿Qué hace?

Interfaz visual para ejecutar todos los comandos de Artisan sin usar terminal. Equivalente a ejecutar `php artisan [comando]` pero con formularios interactivos.

---

### Interfaz de Usuario

#### **Encabezado**
```
Artisan Commands
Execute Laravel Artisan commands with visual interface
```

#### **Contador Total**
```
125 commands available
```

#### **Botón "History"**
Muestra historial de comandos ejecutados recientemente.

---

### Estructura de Comandos

Los comandos están agrupados por categoría:

| Categoría | Comandos | Uso Principal |
|-----------|----------|---------------|
| **_COMPLETE** | 1 | Autocompletado de shell |
| **ABOUT** | 1 | Información de la app |
| **AUTH** | 1 | Autenticación |
| **CACHE** | 4 | Gestión de caché |
| **CHANNEL** | 1 | Broadcasting |
| **CONFIG** | 5 | Configuración |
| **DB** | 6 | Base de datos |
| **DOCS** | 1 | Documentación |
| **DOWN/UP** | 2 | Modo mantenimiento |
| **ENV** | 3 | Variables de entorno |
| **EVENT** | 4 | Eventos y listeners |
| **HELP** | 1 | Ayuda de comandos |
| **INSPIRE** | 1 | Cita inspiradora |
| **INSTALL** | 2 | Instalar funcionalidades |
| **KEY** | 1 | Application key |
| **LANG** | 1 | Traducciones |
| **MAKE** | 37 | Generadores de archivos |
| **MIGRATE** | 7 | Migraciones |
| **MODEL** | 2 | Modelos Eloquent |
| **OPTIMIZE** | 2 | Optimización |
| **PACKAGE** | 1 | Paquetes |
| **QUEUE** | 15 | Colas de trabajo |
| **ROUTE** | 3 | Rutas |
| **SCHEDULE** | 7 | Tareas programadas |
| **SCHEMA** | 1 | Esquema de BD |
| **SERVE** | 1 | Servidor de desarrollo |
| **SESSION** | 1 | Sesiones |
| **STORAGE** | 2 | Enlaces simbólicos |
| **STUB** | 1 | Personalizar plantillas |
| **TEST** | 1 | Ejecutar tests |
| **TINKER** | 1 | REPL interactivo |
| **VENDOR** | 1 | Publicar assets |
| **VIEW** | 2 | Vistas Blade |

---

### Comandos Más Usados

#### **🗑️ CACHE (Caché)**

**`cache:clear`**
```
Descripción: Limpia toda la caché de la aplicación
Uso: Después de cambiar config, cuando hay datos en caché obsoletos
Equivalente: php artisan cache:clear
```

**`cache:forget`**
```
Descripción: Elimina un ítem específico del caché
Argumentos: key (nombre de la clave)
Ejemplo: key=user_123
Equivalente: php artisan cache:forget user_123
```

**`cache:table`**
```
Descripción: Crea migración para tabla de caché en BD
Uso: Si usas CACHE_DRIVER=database
Equivalente: php artisan cache:table
```

---

#### **⚙️ CONFIG (Configuración)**

**`config:cache`**
```
Descripción: Cachea archivos de configuración (acelera app)
Uso: En producción para mejor performance
⚠️ Advertencia: .env ya no se lee después de esto
Equivalente: php artisan config:cache
```

**`config:clear`**
```
Descripción: Elimina caché de configuración
Uso: Después de cambiar config/ o .env
Equivalente: php artisan config:clear
```

**`config:show`**
```
Descripción: Muestra valores de un archivo de configuración
Argumento: config (nombre del archivo)
Ejemplo: config=database
Equivalente: php artisan config:show database
```

---

#### **🗄️ DB (Base de Datos)**

**`db:seed`**
```
Descripción: Ejecuta seeders para poblar BD
Argumento opcional: class (nombre del seeder)
Ejemplo: class=UserSeeder
Equivalente: php artisan db:seed --class=UserSeeder
```

**`db:show`**
```
Descripción: Muestra información de la base de datos
Output: Tablas, tamaño, conexiones
Equivalente: php artisan db:show
```

**`db:table`**
```
Descripción: Muestra estructura de una tabla específica
Argumento: table (nombre de la tabla)
Ejemplo: table=users
Equivalente: php artisan db:table users
```

**`db:wipe`**
```
Descripción: Elimina TODAS las tablas de la BD
⚠️ PELIGRO: No se puede deshacer
Uso: Solo en desarrollo
Equivalente: php artisan db:wipe
```

---

#### **🏗️ MAKE (Generadores)**

**37 comandos para crear archivos:**

```
make:controller   → Crear controlador
make:model        → Crear modelo
make:migration    → Crear migración
make:seeder       → Crear seeder
make:factory      → Crear factory
make:request      → Crear form request
make:middleware   → Crear middleware
make:policy       → Crear policy
make:test         → Crear test
make:command      → Crear comando Artisan
make:job          → Crear job para cola
make:event        → Crear evento
make:listener     → Crear listener
make:mail         → Crear clase de email
make:notification → Crear notificación
make:resource     → Crear API resource
make:rule         → Crear regla de validación
... y 20 más
```

**Ejemplo de uso en UI:**
1. Busca `make:controller`
2. Click en el comando
3. Llena argumentos:
   - `name`: PostController
   - `--resource`: ✅
   - `--model`: Post
4. Click "Execute"

---

#### **🔄 MIGRATE (Migraciones)**

**`migrate`**
```
Descripción: Ejecuta migraciones pendientes
Equivalente: php artisan migrate
```

**`migrate:fresh`**
```
Descripción: Elimina todas las tablas y re-ejecuta migraciones
Opciones: --seed (ejecutar seeders después)
⚠️ PELIGRO: Borra todos los datos
Uso: Solo en desarrollo
Equivalente: php artisan migrate:fresh --seed
```

**`migrate:rollback`**
```
Descripción: Revierte la última migración
Opciones: --step=N (revertir N migraciones)
Equivalente: php artisan migrate:rollback --step=1
```

**`migrate:status`**
```
Descripción: Muestra estado de todas las migraciones
Output: ✅ Ran | ❌ Pending
Equivalente: php artisan migrate:status
```

---

#### **📦 QUEUE (Colas de Trabajo)**

**`queue:work`**
```
Descripción: Procesa trabajos en la cola (daemon)
Opciones:
  --queue=nombre    → Cola específica
  --tries=3         → Intentos antes de fallar
  --timeout=60      → Timeout en segundos
  --sleep=3         → Segundos entre ciclos
Equivalente: php artisan queue:work --tries=3 --timeout=60
```

**`queue:failed`**
```
Descripción: Lista todos los trabajos fallidos
Output: ID, Connection, Queue, Exception
Equivalente: php artisan queue:failed
```

**`queue:retry`**
```
Descripción: Reintentar un job fallido
Argumento: id (ID del job)
Ejemplo: id=12345
Equivalente: php artisan queue:retry 12345
```

**`queue:flush`**
```
Descripción: Elimina TODOS los jobs fallidos
⚠️ Cuidado: No se puede deshacer
Equivalente: php artisan queue:flush
```

---

#### **🛣️ ROUTE (Rutas)**

**`route:cache`**
```
Descripción: Cachea rutas para mejor performance
Uso: En producción
⚠️ Advertencia: No permite Closures en rutas
Equivalente: php artisan route:cache
```

**`route:clear`**
```
Descripción: Elimina caché de rutas
Uso: Después de agregar/modificar rutas
Equivalente: php artisan route:clear
```

**`route:list`**
```
Descripción: Lista todas las rutas registradas
Output: Método, URI, Nombre, Acción, Middleware
Equivalente: php artisan route:list
```

---

#### **🏃 SERVE (Servidor de Desarrollo)**

**`serve`**
```
Descripción: Inicia servidor PHP integrado
Opciones:
  --host=127.0.0.1   → Dirección IP
  --port=8000        → Puerto
Equivalente: php artisan serve --port=8000
Nota: Solo para desarrollo, NO usar en producción
```

---

#### **🧪 TEST (Pruebas)**

**`test`**
```
Descripción: Ejecuta suite de tests
Opciones:
  --filter=NombreTest  → Test específico
  --parallel           → Tests en paralelo
  --coverage           → Reporte de cobertura
Equivalente: php artisan test --parallel
```

---

#### **🔧 TINKER (REPL)**

**`tinker`**
```
Descripción: Abre consola interactiva de PHP/Laravel
Uso: Ejecutar código PHP en vivo
Ejemplo:
  >>> User::count()
  => 10
  >>> User::factory()->create()
Equivalente: php artisan tinker
Nota: No ejecutable desde UI (requiere terminal)
```

---

#### **👁️ VIEW (Vistas)**

**`view:cache`**
```
Descripción: Pre-compila todas las vistas Blade
Uso: En producción para acelerar renderizado
Equivalente: php artisan view:cache
```

**`view:clear`**
```
Descripción: Elimina vistas compiladas
Uso: Después de cambiar Blade templates
Equivalente: php artisan view:clear
```

---

### Ejecución de Comandos

#### **Paso a Paso:**

1. **Buscar comando:**
   - Scroll o busca en la lista
   - Click en el comando deseado

2. **Ver información:**
   ```
   make:controller
   Create a new controller class
   
   Argumentos:
   - name (requerido)
   
   Opciones:
   - --resource
   - --model
   - --api
   ```

3. **Llenar formulario:**
   ```
   name: PostController
   ☑ --resource
   model: Post
   ```

4. **Ejecutar:**
   - Click en botón "Run"
   - Espera resultado

5. **Ver output:**
   ```
   ✅ Success
   Controller created successfully.
   File: app/Http/Controllers/PostController.php
   ```

---

### Historial de Comandos

**Botón "History"** muestra últimos 10 comandos ejecutados:

```
┌──────────────────────────────────────────┐
│ History                                   │
├──────────────────────────────────────────┤
│ 1. migrate                                │
│ 2. db:seed --class=UserSeeder            │
│ 3. make:controller PostController        │
│ 4. cache:clear                            │
│ 5. route:list                             │
└──────────────────────────────────────────┘
```

**Uso:**
- Click en comando para re-ejecutar
- Útil para comandos repetitivos

---

### Comandos Equivalentes en Terminal

```bash
# Desde DevTools UI
Click en "cache:clear" → Run

# Desde Terminal
php artisan cache:clear

# Con Laravel Sail
sail artisan cache:clear
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa Artisan Commands para comandos esporádicos
- Verifica opciones antes de ejecutar comandos destructivos
- Usa History para repetir comandos frecuentes
- Lee la descripción antes de ejecutar comandos desconocidos
- Usa `--help` en terminal para ver todas las opciones

❌ **DON'T (No hacer):**
- No ejecutes `db:wipe` o `migrate:fresh` en producción
- No uses `serve` en producción (usa Nginx/Apache)
- No cachees config en desarrollo (no se reflejan cambios en .env)
- No ignores errores en el output (revísalos)
- No ejecutes comandos sin entender qué hacen

---

### Errores Comunes

#### **❌ "Command not found"**
**Causa:** Comando no existe o está mal escrito.

**Solución:** Verifica nombre exacto en la lista.

---

#### **❌ "The command requires the argument: name"**
**Causa:** Falta argumento requerido.

**Solución:** Llena todos los campos marcados como requeridos.

---

#### **⚠️ "Nothing to migrate"**
**Causa:** No hay migraciones pendientes.

**Solución:** Verifica con `migrate:status` si todas están ejecutadas.

---

## 5.2 📦 Composer Manager (Gestor de Dependencias)

**Ruta**: `http://localhost:8000/devtools/composer`

### ¿Qué hace?

Interfaz visual para gestionar paquetes de Composer (dependencias PHP). Muestra paquetes instalados y permite instalar/actualizar sin usar terminal.

---

### Interfaz de Usuario

#### **Encabezado**
```
Composer Manager
Manage PHP dependencies with Composer
```

#### **Botones Principales**

**🔍 Install Package**
Abre formulario para instalar nuevo paquete:
```
Package name: spatie/laravel-permission
Version: (optional, default: latest)
☐ Dev dependency (--dev)
```

**🔄 Update All**
Actualiza todos los paquetes a sus últimas versiones compatibles.
```
Equivalente: composer update
⚠️ Puede tardar varios minutos
```

---

### Lista de Paquetes Instalados

**Contador:**
```
Installed Packages (114)
```

**Tabs de filtro:**
- **All (114)** → Todos los paquetes
- **Dependencies (77)** → Dependencias de producción
- **Dev Dependencies (37)** → Dependencias de desarrollo

---

### Estructura de Cada Paquete

Cada paquete se muestra como una tarjeta:

```
┌─────────────────────────────────────────┐
│ laravel/framework                       │
│ v12.38.1                           prod │
│ The Laravel Framework.                  │
│                                         │
│ [View Details] [Remove]                 │
└─────────────────────────────────────────┘
```

**Información mostrada:**
- **Nombre:** `laravel/framework`
- **Versión:** `v12.38.1`
- **Tipo:** `prod` (producción) o `dev` (desarrollo)
- **Descripción:** Breve descripción del paquete

**Botones:**
- **View Details** → Ver en Packagist/GitHub
- **Remove** → Desinstalar paquete

---

### Paquetes Principales de Laravel

#### **Core de Laravel**

**laravel/framework** (v12.38.1) - prod
```
El framework completo de Laravel
```

**laravel/breeze** (v2.3.8) - dev
```
Scaffolding de autenticación minimalista
Genera: login, register, password reset, email verification
```

**laravel/sail** (v1.48.0) - dev
```
Entorno Docker para Laravel
Incluye: PHP, MySQL, Redis, Mailpit, Meilisearch
```

**laravel/tinker** (v2.10.1) - prod
```
REPL (consola interactiva) para Laravel
Uso: php artisan tinker
```

**laravel/pint** (v1.25.1) - dev
```
Formateador de código PHP opinionado
Basado en PHP-CS-Fixer
```

**laravel/pail** (v1.2.3) - dev
```
Visor de logs en tiempo real
Uso: php artisan pail
```

---

#### **Componentes de Symfony**

Laravel usa 20+ componentes de Symfony:

```
symfony/console         → CLI commands
symfony/http-foundation → Request/Response
symfony/http-kernel     → HTTP kernel
symfony/routing         → Enrutamiento
symfony/mailer          → Envío de emails
symfony/process         → Ejecutar procesos
symfony/var-dumper      → dd() y dump()
... y 13 más
```

---

#### **Utilidades**

**livewire/livewire** (v3.7.0) - prod
```
Framework frontend reactivo para Laravel
Componentes dinámicos sin escribir JavaScript
```

**guzzlehttp/guzzle** (v7.10.0) - prod
```
Cliente HTTP para PHP
Uso: Http::get(), APIs externas
```

**monolog/monolog** (v3.9.0) - prod
```
Sistema de logging
Usado internamente por Laravel
```

**nesbot/carbon** (v3.10.3) - prod
```
Librería de manejo de fechas
Extensión de DateTime
Uso: now(), today(), Carbon::parse()
```

**fakerphp/faker** (v1.24.1) - dev
```
Generador de datos falsos
Uso: en Factories y Seeders
```

---

#### **Testing**

**phpunit/phpunit** (v11.5.44) - dev
```
Framework de testing para PHP
Usado por: php artisan test
```

**mockery/mockery** (v1.6.12) - dev
```
Framework de mocking para tests
Crear objetos mock en tests
```

**nunomaduro/collision** (v8.8.2) - dev
```
Manejo de errores elegante en CLI
Mejora visualización de errores
```

---

### Instalar Nuevo Paquete

#### **Ejemplo: Instalar Spatie Permission**

1. **Click en "Install Package"**

2. **Llenar formulario:**
   ```
   Package name: spatie/laravel-permission
   Version: (dejar vacío para latest)
   ☐ Dev dependency
   ```

3. **Click "Install"**

4. **Esperar instalación** (puede tardar 30-60 segundos)

5. **Ver resultado:**
   ```
   ✅ Package installed successfully
   spatie/laravel-permission v6.9.0
   ```

6. **Siguiente paso:**
   ```bash
   # Publicar configuración
   php artisan vendor:publish --provider="Spatie\Permission\PermissionServiceProvider"
   
   # Ejecutar migraciones
   php artisan migrate
   ```

**Comando equivalente:**
```bash
composer require spatie/laravel-permission
```

---

### Actualizar Paquetes

#### **Actualizar Todo**
```
Click en "Update All"
↓
Equivalente: composer update
↓
Actualiza TODOS los paquetes a últimas versiones compatibles
```

#### **Actualizar Uno**
```
En la tarjeta del paquete:
Click en "Update"
↓
Equivalente: composer update vendor/package
```

---

### Eliminar Paquete

1. **Buscar paquete en la lista**
2. **Click en "Remove"**
3. **Confirmar eliminación**
4. **Esperar resultado:**
   ```
   ✅ Package removed successfully
   fakerphp/faker has been uninstalled
   ```

**Comando equivalente:**
```bash
composer remove fakerphp/faker
```

---

### Comandos Equivalentes

```bash
# Instalar paquete
composer require vendor/package

# Instalar dev dependency
composer require vendor/package --dev

# Actualizar todo
composer update

# Actualizar uno
composer update vendor/package

# Eliminar
composer remove vendor/package

# Ver paquetes instalados
composer show

# Ver solo prod
composer show --no-dev

# Ver info de uno
composer show vendor/package

# Buscar paquetes
composer search permissions
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Lee la documentación del paquete antes de instalar
- Verifica compatibilidad con tu versión de Laravel
- Usa versiones específicas en producción (no `*`)
- Actualiza paquetes regularmente (seguridad)
- Elimina paquetes no usados (reduce tamaño)

❌ **DON'T (No hacer):**
- No instales paquetes sin revisar su popularidad/mantenimiento
- No actualices en producción sin testear primero
- No ignores mensajes de deprecación
- No instales paquetes de fuentes no confiables
- No uses `composer update` en producción (usa `composer install`)

---

## 5.3 🐳 Sail Manager (Gestor de Docker)

**Ruta**: `http://localhost:8000/devtools/sail`

### ¿Qué hace?

Monitorea contenedores Docker de Laravel Sail. Muestra estado, puertos y permite operaciones básicas.

---

### Interfaz de Usuario

#### **Docker Status (Estado)**
```
┌────────────────┐
│ Docker Status  │
│ ✅ Running     │
└────────────────┘

[Refresh]
```

**Estados posibles:**
- **Running** → Docker activo
- **Stopped** → Docker detenido
- **Error** → Problema de conexión

---

### Containers (Contenedores)

**Contador:**
```
Containers
3 containers found
```

---

### Contenedores Típicos

#### **1. devjobs_laravel** (Aplicación)
```
┌──────────────────────────────────────────┐
│ devjobs_laravel                    running│
│ ID: cf61517ea854                         │
│ Image: sail-8.4/app                      │
│ Ports: 0.0.0.0:8000->80/tcp              │
│ Status: Up (current container)           │
│                                          │
│ [View Logs] [Restart]                    │
└──────────────────────────────────────────┘
```

**Información:**
- **ID:** Identificador único del contenedor
- **Image:** `sail-8.4/app` (PHP 8.4 + extensiones)
- **Ports:** Puerto 8000 (host) → 80 (contenedor)
- **Status:** Estado actual

**Contenido:**
- PHP 8.4
- Composer
- Node.js + NPM
- Supervisor (para queues)
- Código de la aplicación en `/var/www/html`

---

#### **2. devjobs_mysql** (Base de Datos)
```
┌──────────────────────────────────────────┐
│ devjobs_mysql                      running│
│ Image: mysql/mysql-server:8.0           │
│ Ports: 0.0.0.0:3306->3306/tcp            │
│ Status: Up (detected via network)        │
│                                          │
│ [View Logs] [Restart]                    │
└──────────────────────────────────────────┘
```

**Información:**
- **Image:** MySQL 8.0
- **Ports:** Puerto 3306 (ambos)
- **Datos:** Persistentes en volume `sail-mysql`

**Acceso:**
```bash
# Desde Sail
sail mysql

# Desde host
mysql -h 127.0.0.1 -P 3306 -u sail -p
Password: password
```

---

#### **3. devjobs_mailpit** (Mail Testing)
```
┌──────────────────────────────────────────┐
│ devjobs_mailpit                    running│
│ Image: axllent/mailpit:latest           │
│ Ports: 0.0.0.0:8025->8025/tcp            │
│ Status: Up (detected via network)        │
│                                          │
│ [Open Web UI] [View Logs]                │
└──────────────────────────────────────────┘
```

**Información:**
- **Image:** Mailpit (reemplazo de Mailhog)
- **Ports:** 
  - 8025 → Web UI
  - 1025 → SMTP (interno)

**Acceso:**
```
Web UI: http://localhost:8025
SMTP: localhost:1025 (sin autenticación)
```

**Uso:** Ver emails enviados por la aplicación en desarrollo.

---

### Otros Contenedores Opcionales

#### **Redis** (no presente en tu proyecto)
```
Uso: Cache, sessions, queues
Ports: 6379
```

#### **Meilisearch** (no presente)
```
Uso: Motor de búsqueda
Ports: 7700
Web UI: http://localhost:7700
```

#### **MinIO** (no presente)
```
Uso: Almacenamiento S3-compatible
Ports: 9000, 9001
```

---

### Comandos Disponibles

#### **View Logs**
Muestra logs del contenedor en tiempo real.

**Equivalente:**
```bash
sail logs laravel.test -f
```

---

#### **Restart**
Reinicia el contenedor específico.

**Equivalente:**
```bash
sail restart
```

---

#### **Refresh**
Recarga estado de contenedores.

---

### Comandos de Sail en Terminal

```bash
# Iniciar todos los contenedores
sail up
sail up -d  # En background

# Detener todos
sail down

# Reiniciar
sail restart

# Ver logs
sail logs
sail logs laravel.test -f  # Follow mode

# Ejecutar comandos
sail artisan migrate
sail composer install
sail npm run dev

# Acceder a shell
sail shell  # Contenedor de Laravel
sail mysql  # MySQL CLI
sail redis  # Redis CLI

# Ver contenedores activos
sail ps

# Reconstruir imágenes
sail build --no-cache
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa Sail Manager para verificar que servicios estén corriendo
- Revisa logs cuando hay errores
- Reinicia contenedores después de cambiar docker-compose.yml
- Usa Mailpit Web UI para testing de emails

❌ **DON'T (No hacer):**
- No detengas contenedores manualmente con `docker stop` (usa `sail down`)
- No elimines volumes sin backup (pierdes datos de BD)
- No expongas puertos sensibles en producción
- No modifiques `docker-compose.yml` sin entender las consecuencias

---

## 5.4 📜 Log Viewer (Visor de Logs)

**Ruta**: `http://localhost:8000/devtools/logs`

### ¿Qué hace?

Visualiza logs de Laravel en tiempo real con filtros y búsqueda. Reemplaza necesidad de abrir archivos en `storage/logs/`.

---

### Interfaz de Usuario

#### **Log Files (Archivos de Log)**

**Lista de archivos:**
```
┌────────────────────────────────────────┐
│ laravel.log                            │
│ 236.74 KB                              │
│ hace 1 hora                            │
│                                        │
│ [View] [Download] [Delete]             │
└────────────────────────────────────────┘
```

---

#### **Estadísticas**

```
┌──────────┬─────────┬────────────┬──────┐
│ Total: 21│ Errors:17│ Warnings: 0│ Info:4│
└──────────┴─────────┴────────────┴──────┘
```

**Filtros:**
- **Level:** ERROR, WARNING, INFO, DEBUG
- **Buscar:** Texto libre
- **Acciones:** Clear, Download, Delete

---

### Log Entries (Entradas de Log)

**Formato de cada entrada:**

```
┌─────────────────────────────────────────────────┐
│ ERROR  local  2025-11-26 06:17:51              │
│ Cannot use App\Models\ParentResoursesDos as    │
│ ParentResoursesDos because the name is already │
│ in use                                          │
│                                                 │
│ File: ParentResoursesDosController.php:6       │
│ User ID: 1                                      │
│                                                 │
│ [Show context]                                  │
└─────────────────────────────────────────────────┘
```

**Información:**
- **Nivel:** ERROR, WARNING, INFO, DEBUG
- **Entorno:** local, production, testing
- **Timestamp:** Fecha y hora exacta
- **Mensaje:** Descripción del error
- **Context:** Usuario, archivo, línea

---

### Niveles de Log

| Nivel | Descripción | Ejemplo |
|-------|-------------|---------|
| **ERROR** | Errores que impiden ejecución | Clase no encontrada, sintaxis inválida |
| **WARNING** | Advertencias no críticas | Deprecaciones, configuración subóptima |
| **INFO** | Información general | Comando ejecutado, acción completada |
| **DEBUG** | Debugging detallado | Valores de variables, flujo de ejecución |

---

### Ejemplos de Logs

#### **ERROR: Clase No Encontrada**
```
ERROR  local  2025-11-26 06:17:51
Cannot use App\Models\ParentResoursesDos as ParentResoursesDos
because the name is already in use

File: app/Http/Controllers/ParentResoursesDosController.php:6
User ID: 1

Context:
  - userId: 1
  - exception: Symfony\Component\ErrorHandler\Error\FatalError
```

**Causa:** Import duplicado en el controlador.

---

#### **ERROR: Tabla No Existe**
```
ERROR  local  2025-11-26 02:39:26
SQLSTATE[42S02]: Base table or view not found: 1146
Table 'devjobs.sessions' doesn't exist

SQL: select * from `sessions` where `id` = nlvuxNoifYmbEAkFT... limit 1

Context:
  - connection: mysql
  - bindings: []
```

**Causa:** Migración de sesiones no ejecutada.

**Solución:**
```bash
php artisan session:table
php artisan migrate
```

---

#### **INFO: Comando Ejecutado**
```
INFO  local  2025-11-26 02:12:20
Command selected

Context:
  - command: status
```

**Descripción:** Log informativo de acción en DevTools.

---

### Filtros y Búsqueda

#### **Filtrar por Nivel**
```
[All] [ERROR] [WARNING] [INFO] [DEBUG]
```

Click en nivel para mostrar solo ese tipo.

---

#### **Buscar Texto**
```
┌────────────────────────────────────┐
│ 🔍 Buscar                          │
└────────────────────────────────────┘
```

**Ejemplos:**
```
ParentResoursesDos    → Errores con ese modelo
sessions              → Errores de sesión
SQLSTATE              → Errores de base de datos
User ID: 1            → Errores del usuario 1
```

---

### Acciones

#### **Clear (Limpiar)**
```
Elimina todas las entradas del archivo de log actual
⚠️ No se puede deshacer
```

**Equivalente:**
```bash
# Vaciar log
echo "" > storage/logs/laravel.log

# O desde terminal
sail artisan log:clear  # Si existe el comando
```

---

#### **Download (Descargar)**
```
Descarga archivo de log completo
Formato: laravel-2025-11-26.log
Uso: Análisis offline, auditoría
```

---

#### **Delete (Eliminar)**
```
Elimina archivo de log completamente
⚠️ No se puede deshacer
```

---

### Comandos Equivalentes

```bash
# Ver últimas líneas del log
tail -f storage/logs/laravel.log

# Ver últimas 50 líneas
tail -n 50 storage/logs/laravel.log

# Buscar errores
grep "ERROR" storage/logs/laravel.log

# Contar errores
grep -c "ERROR" storage/logs/laravel.log

# Ver logs en tiempo real (paquete Pail)
sail artisan pail

# Vaciar log
echo "" > storage/logs/laravel.log

# Rotar logs manualmente
mv storage/logs/laravel.log storage/logs/laravel-$(date +%Y-%m-%d).log
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Revisa logs después de errores 500
- Filtra por ERROR para debugging
- Descarga logs antes de limpiar
- Usa `Log::info()` para debugging personalizado
- Configura rotación de logs en producción

❌ **DON'T (No hacer):**
- No ignores WARNINGs (pueden convertirse en errores)
- No logees información sensible (contraseñas, tokens)
- No dejes logs crecer indefinidamente (rotar)
- No uses `dd()` en producción (usa `Log::debug()`)

---

## 5.5 🧹 Cache Manager (Gestor de Caché)

**Ruta**: `http://localhost:8000/devtools/cache`

### ¿Qué hace?

Limpia y optimiza diferentes tipos de caché de Laravel con un solo click. Ahorra tiempo ejecutando múltiples comandos de caché.

---

### Información del Sistema

#### **Cache Driver**
```
database
```

**Drivers posibles:**
- `file` → Archivos en `storage/framework/cache/`
- `database` → Tabla `cache` en BD
- `redis` → Redis server
- `memcached` → Memcached server
- `array` → Solo en memoria (testing)

---

#### **Cache Size**
```
0 B
```

Tamaño actual del caché almacenado.

---

#### **Compiled Views**
```
57 views
1.08 MB
```

Plantillas Blade compiladas en `storage/framework/views/`.

---

#### **Cached Files**
```
Config: No
Routes: No
```

Indica si archivos de configuración y rutas están cacheados.

**✅ Yes** → Cacheado (producción)
**❌ No** → No cacheado (desarrollo)

---

### Quick Actions (Acciones Rápidas)

#### **🗑️ Clear All**
```
Limpia TODOS los cachés
Equivalente a ejecutar:
  - cache:clear
  - config:clear
  - route:clear
  - view:clear
  - event:clear
  - clear-compiled
```

**Uso:** Después de actualizar código, cuando algo "no funciona".

---

#### **🔥 Flush Store**
```
Elimina TODO del cache store actual (database, redis, etc.)
⚠️ Más agresivo que Clear All
Equivalente: cache:clear --store=database
```

---

#### **⚡ Optimize**
```
Cachea configuración y rutas para mejor performance
Equivalente: php artisan optimize
Ejecuta:
  - config:cache
  - route:cache
```

**Uso:** Antes de deploy a producción.

---

#### **🔄 Clear Optimization**
```
Elimina cachés de optimización
Equivalente: php artisan optimize:clear
```

**Uso:** En desarrollo después de cambiar config/ o routes/.

---

### Cache Types (Tipos de Caché)

#### **1. Application Cache**
```
Descripción: Cache facade (Cache::put(), Cache::get())
Comando: cache:clear
Ubicación: Según driver (file/database/redis)
```

**Ejemplo de uso:**
```php
// Guardar en caché
Cache::put('key', 'value', 3600); // 1 hora

// Leer
$value = Cache::get('key');

// Limpiar
// Click en "Clear" en DevTools o:
php artisan cache:clear
```

---

#### **2. Configuration Cache**
```
Descripción: Archivos config/* cacheados
Comando: config:clear
Ubicación: bootstrap/cache/config.php
```

**Cuándo limpiar:**
- Después de cambiar archivos en `config/`
- Después de modificar `.env`
- Si cambios en config no se reflejan

---

#### **3. Route Cache**
```
Descripción: Rutas cacheadas
Comando: route:clear
Ubicación: bootstrap/cache/routes-v7.php
```

**Cuándo limpiar:**
- Después de agregar/modificar rutas
- Si rutas nuevas no funcionan
- Error "Route not found" con ruta existente

---

#### **4. View Cache**
```
Descripción: Plantillas Blade compiladas
Comando: view:clear
Ubicación: storage/framework/views/*.php
```

**Cuándo limpiar:**
- Después de cambiar .blade.php
- Si cambios en vistas no se reflejan
- Errores "undefined variable" en Blade

---

#### **5. Event Cache**
```
Descripción: Eventos y listeners cacheados
Comando: event:clear
Ubicación: bootstrap/cache/events.php
```

**Cuándo limpiar:**
- Después de agregar eventos/listeners
- Si eventos no se disparan

---

#### **6. Compiled Services**
```
Descripción: Archivo de clases compiladas
Comando: clear-compiled
Ubicación: bootstrap/cache/services.php
```

**Cuándo limpiar:**
- Después de instalar paquetes
- Si cambios en providers no se reflejan

---

### Comandos Equivalentes

```bash
# Limpiar application cache
sail artisan cache:clear

# Limpiar config cache
sail artisan config:clear

# Limpiar route cache
sail artisan route:clear

# Limpiar view cache
sail artisan view:clear

# Limpiar event cache
sail artisan event:clear

# Limpiar compiled services
sail artisan clear-compiled

# Limpiar TODO (equivalente a Clear All)
sail artisan cache:clear && \
sail artisan config:clear && \
sail artisan route:clear && \
sail artisan view:clear && \
sail artisan event:clear && \
sail artisan clear-compiled

# Optimizar (cachear todo)
sail artisan optimize

# Revertir optimización
sail artisan optimize:clear
```

---

### Flujo de Trabajo Típico

#### **En Desarrollo**
```
1. Haces cambios en código
2. Click en "Clear All" en DevTools
3. Refrescar navegador
4. Verificar cambios
```

#### **Antes de Producción**
```
1. Click en "Optimize"
2. Verificar app funciona
3. Deploy a producción
4. App carga más rápido (config/routes cacheadas)
```

#### **Después de Deploy**
```
1. Si algo no funciona
2. SSH a servidor
3. Click en "Clear All" en DevTools
4. Click en "Optimize"
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Limpia caché cuando cambios no se reflejan
- Usa "Optimize" en producción
- Limpia view cache después de actualizar Blade
- Usa "Clear All" ante dudas

❌ **DON'T (No hacer):**
- No uses "Optimize" en desarrollo (complica debugging)
- No ignores caché al hacer troubleshooting
- No cachees rutas con Closures (causa error)
- No olvides limpiar caché después de `composer update`

---

## 5.6 📊 Queue Monitor (Monitor de Colas)

**Ruta**: `http://localhost:8000/devtools/queue`

### ¿Qué hace?

Monitorea trabajos en cola (jobs) y muestra estadísticas en tiempo real. Permite visualizar jobs pendientes y fallidos.

---

### Información del Sistema

#### **Queue Driver**
```
database
```

**Drivers posibles:**
- `sync` → Síncrono (sin cola, ejecuta inmediatamente)
- `database` → Tabla `jobs` en BD
- `redis` → Redis lists
- `sqs` → Amazon SQS
- `beanstalkd` → Beanstalk server

---

#### **Estadísticas**

```
┌──────────────┬──────────────┐
│ Pending Jobs │ Failed Jobs  │
│      0       │      0       │
└──────────────┴──────────────┘
```

---

### Tabs

#### **Pending (Pendientes)**
```
Jobs esperando ser procesados
Mostrados: ID, Queue, Clase, Payload, Attempts, Created
```

**Ejemplo:**
```
┌──────────────────────────────────────────────┐
│ ID: 12345                                    │
│ Queue: default                               │
│ Job: App\Jobs\SendWelcomeEmail               │
│ Payload: {"user_id": 123}                    │
│ Attempts: 0/3                                │
│ Created: 2 minutes ago                       │
│                                              │
│ [View Details] [Delete]                      │
└──────────────────────────────────────────────┘
```

---

#### **Failed (Fallidos)**
```
Jobs que fallaron después de max intentos
Mostrados: ID, Queue, Exception, Failed At
```

**Ejemplo:**
```
┌──────────────────────────────────────────────┐
│ ID: 67890                                    │
│ Queue: emails                                │
│ Job: App\Jobs\SendNewsletterEmail            │
│ Exception: SMTP connection failed            │
│ Failed At: 1 hour ago                        │
│                                              │
│ [Retry] [Delete] [View Stack Trace]          │
└──────────────────────────────────────────────┘
```

---

### Estado Actual (Tu Proyecto)

```
┌─────────────────────────────────────┐
│ Pending Jobs: 0                     │
│ Failed Jobs: 0                      │
│                                     │
│ No jobs found                       │
└─────────────────────────────────────┘
```

**Razón:** No hay jobs en cola actualmente.

---

### ¿Qué son los Jobs?

**Jobs** son tareas que se ejecutan en segundo plano (asíncrono) para no bloquear peticiones HTTP.

**Ejemplos de uso:**
- Enviar emails
- Procesar imágenes/videos
- Generar reportes PDF
- Llamar APIs externas lentas
- Limpiar datos antiguos

---

### Crear y Usar Jobs

#### **1. Crear Job**
```bash
php artisan make:job SendWelcomeEmail
```

**Archivo generado:** `app/Jobs/SendWelcomeEmail.php`

```php
<?php

namespace App\Jobs;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Foundation\Bus\Dispatchable;
use Illuminate\Queue\InteractsWithQueue;
use Illuminate\Queue\SerializesModels;

class SendWelcomeEmail implements ShouldQueue
{
    use Dispatchable, InteractsWithQueue, Queueable, SerializesModels;

    public function __construct(
        public User $user
    ) {}

    public function handle(): void
    {
        // Lógica para enviar email
        Mail::to($this->user->email)->send(new WelcomeMail($this->user));
    }
}
```

---

#### **2. Despachar Job**
```php
// En controlador o cualquier parte del código
SendWelcomeEmail::dispatch($user);
```

---

#### **3. Procesar Jobs**
```bash
# Iniciar worker (procesa jobs en loop)
sail artisan queue:work

# Con opciones
sail artisan queue:work --tries=3 --timeout=60

# Específica por queue
sail artisan queue:work --queue=emails,default
```

---

#### **4. Ver en Queue Monitor**
```
1. Despachar job: SendWelcomeEmail::dispatch($user)
2. Ir a Queue Monitor: http://localhost:8000/devtools/queue
3. Ver job en tab "Pending"
4. Si falla, aparece en tab "Failed"
```

---

### Acciones sobre Jobs

#### **Retry (Reintentar)**
```
Vuelve a ejecutar un job fallido
Mueve de "Failed" a "Pending"
```

**Equivalente:**
```bash
php artisan queue:retry 67890  # ID del job
php artisan queue:retry all    # Todos los fallidos
```

---

#### **Delete (Eliminar)**
```
Elimina job de la cola
No se ejecutará
```

**Equivalente:**
```bash
php artisan queue:forget 67890
```

---

#### **Flush Failed (Vaciar Fallidos)**
```
Elimina TODOS los jobs fallidos
```

**Equivalente:**
```bash
php artisan queue:flush
```

---

### Comandos Útiles

```bash
# Listar jobs fallidos
sail artisan queue:failed

# Reintentar todos los fallidos
sail artisan queue:retry all

# Eliminar job fallido
sail artisan queue:forget 12345

# Eliminar todos los fallidos
sail artisan queue:flush

# Limpiar queue específica
sail artisan queue:clear default

# Reiniciar workers (después de cambios en código)
sail artisan queue:restart

# Monitorear tamaño de colas
sail artisan queue:monitor default,emails --max=100
```

---

### Configuración de Colas

**En `.env`:**
```env
QUEUE_CONNECTION=database
```

**Opciones:**
- `sync` → Sin cola (desarrollo)
- `database` → BD (simple)
- `redis` → Redis (recomendado para producción)

**Si usas `database`, ejecutar:**
```bash
php artisan queue:table
php artisan migrate
```

---

### Consejos y Buenas Prácticas

✅ **DO (Hacer):**
- Usa colas para tareas lentas (emails, APIs, procesamiento)
- Configura `tries` y `timeout` apropiados
- Monitorea jobs fallidos regularmente
- Usa `queue:restart` después de deploy
- Separa jobs por queue (emails, images, default)

❌ **DON'T (No hacer):**
- No uses jobs para operaciones críticas sin retry logic
- No olvides ejecutar `queue:work` en producción
- No proceses jobs que modifican data sin validación
- No ignores jobs fallidos (investiga la causa)
- No uses `sync` en producción (bloquea peticiones)

---

### Integración con Supervisor (Producción)

**Para mantener workers corriendo 24/7:**

```ini
[program:laravel-worker]
process_name=%(program_name)s_%(process_num)02d
command=php /var/www/html/artisan queue:work --tries=3
autostart=true
autorestart=true
user=www-data
numprocs=4
redirect_stderr=true
stdout_logfile=/var/www/html/storage/logs/worker.log
```

---

## 📊 Resumen de Herramientas

| Herramienta | Uso Principal | Frecuencia |
|-------------|---------------|------------|
| **Artisan Commands** | Ejecutar comandos Laravel | Diaria |
| **Composer Manager** | Instalar/actualizar paquetes | Semanal |
| **Sail Manager** | Monitorear Docker | Diaria |
| **Log Viewer** | Debugging errores | Según necesidad |
| **Cache Manager** | Limpiar caché | Diaria (desarrollo) |
| **Queue Monitor** | Monitorear jobs | Diaria (si usas colas) |

---

## 6. 🎯 Flujos de Trabajo Completos

Esta sección muestra cómo usar DevTools en escenarios reales de desarrollo.

---

### 6.1 🚀 Crear un CRUD Completo

**Objetivo:** Sistema de gestión de posts con todas las funcionalidades.

#### **Paso 1: Crear el Modelo con Migración**

**Desde:** `http://localhost:8000/devtools/generators/model`

```
Nombre: Post
☑ Create Migration
☑ Create Factory
☑ Create Seeder
☑ Create Controller (resource)
☑ Create Form Requests
☐ Create Policy
☑ Add Soft Deletes
☑ Add Timestamps
☐ Make Pivot Model
☑ Set Fillable Fields
```

**Fillable Fields:**
```
title, content, status, published_at, user_id
```

**Resultado:**
- `app/Models/Post.php`
- `database/migrations/xxxx_create_posts_table.php`
- `database/factories/PostFactory.php`
- `database/seeders/PostSeeder.php`
- `app/Http/Controllers/PostController.php`
- `app/Http/Requests/StorePostRequest.php`
- `app/Http/Requests/UpdatePostRequest.php`

---

#### **Paso 2: Configurar la Migración**

**Desde:** `http://localhost:8000/devtools/generators/migration`

**Seleccionar:** La migración recién creada `xxxx_create_posts_table.php`

**Agregar columnas:**

| Campo | Tipo | Modificadores |
|-------|------|---------------|
| id | bigIncrements | - |
| title | string | - |
| slug | string | Unique |
| content | text | - |
| excerpt | text | Nullable |
| status | enum: draft,published | Default: draft |
| published_at | timestamp | Nullable |
| user_id | foreignId | constrained, cascadeOnDelete |
| created_at | timestamp | - |
| updated_at | timestamp | - |
| deleted_at | timestamp | Nullable |

**Código generado equivalente:**
```php
Schema::create('posts', function (Blueprint $table) {
    $table->id();
    $table->string('title');
    $table->string('slug')->unique();
    $table->text('content');
    $table->text('excerpt')->nullable();
    $table->enum('status', ['draft', 'published'])->default('draft');
    $table->timestamp('published_at')->nullable();
    $table->foreignId('user_id')->constrained()->cascadeOnDelete();
    $table->timestamps();
    $table->softDeletes();
});
```

---

#### **Paso 3: Ejecutar Migración**

**Desde:** `http://localhost:8000/devtools/artisan`

**Buscar:** `migrate`

**Ejecutar:** `migrate`

**Verificar en:** `http://localhost:8000/devtools/database`
- Tabla `posts` debe aparecer con 11 columnas

---

#### **Paso 4: Configurar Factory**

**Editar manualmente:** `database/factories/PostFactory.php`

```php
public function definition(): array
{
    return [
        'title' => fake()->sentence(),
        'slug' => fake()->unique()->slug(),
        'content' => fake()->paragraphs(5, true),
        'excerpt' => fake()->paragraph(),
        'status' => fake()->randomElement(['draft', 'published']),
        'published_at' => fake()->optional(0.7)->dateTimeBetween('-1 year', 'now'),
        'user_id' => User::factory(),
    ];
}
```

---

#### **Paso 5: Ejecutar Seeder**

**Desde:** `http://localhost:8000/devtools/artisan`

**Buscar:** `db:seed`

**Ejecutar con argumentos:**
```
--class=PostSeeder
```

**Verificar en:** `http://localhost:8000/devtools/database`
- Query: `SELECT * FROM posts LIMIT 10`
- Debe mostrar registros generados

---

#### **Paso 6: Registrar Rutas**

**Editar:** `routes/web.php`

```php
use App\Http\Controllers\PostController;

Route::middleware(['auth'])->group(function () {
    Route::resource('posts', PostController::class);
});
```

**Verificar en:** `http://localhost:8000/devtools/project/routes`
- Buscar: `posts.index`, `posts.create`, `posts.store`, etc.
- Deben aparecer 7 rutas resource

---

#### **Paso 7: Configurar Validación**

**Editar:** `app/Http/Requests/StorePostRequest.php`

```php
public function rules(): array
{
    return [
        'title' => ['required', 'string', 'max:255'],
        'slug' => ['required', 'string', 'max:255', 'unique:posts'],
        'content' => ['required', 'string'],
        'excerpt' => ['nullable', 'string', 'max:500'],
        'status' => ['required', 'in:draft,published'],
        'published_at' => ['nullable', 'date'],
    ];
}
```

---

#### **Paso 8: Implementar Controlador**

**Editar:** `app/Http/Controllers/PostController.php`

```php
public function index()
{
    $posts = Post::with('user')
        ->latest()
        ->paginate(15);
    
    return view('posts.index', compact('posts'));
}

public function store(StorePostRequest $request)
{
    $post = auth()->user()->posts()->create($request->validated());
    
    return redirect()
        ->route('posts.show', $post)
        ->with('success', 'Post creado exitosamente');
}
```

---

#### **Paso 9: Crear Vistas**

**Crear manualmente:**
- `resources/views/posts/index.blade.php`
- `resources/views/posts/create.blade.php`
- `resources/views/posts/edit.blade.php`
- `resources/views/posts/show.blade.php`

---

#### **Paso 10: Verificar Funcionamiento**

**Tests manuales:**
1. Visitar `http://localhost:8000/posts`
2. Crear nuevo post
3. Editar post
4. Eliminar post

**Desde DevTools:**
- **Database Manager:** Verificar registros en tabla `posts`
- **Routes List:** Confirmar rutas registradas
- **Controllers List:** Ver método `PostController`
- **Logs:** Revisar errores si algo falla

---

### 6.2 🔧 Debugging de Errores

**Escenario:** La aplicación muestra error 500.

#### **Paso 1: Verificar Logs**

**Desde:** `http://localhost:8000/devtools/logs`

**Buscar:** Últimos errores (nivel ERROR)

**Ejemplo de error encontrado:**
```
SQLSTATE[42S22]: Column not found: 1054 Unknown column 'slug' in 'field list'
```

**Diagnóstico:** Falta columna `slug` en tabla `posts`.

---

#### **Paso 2: Verificar Base de Datos**

**Desde:** `http://localhost:8000/devtools/database`

**Seleccionar tabla:** `posts`

**Verificar columnas:**
- Si falta `slug`, necesitas agregar columna

---

#### **Paso 3: Crear Migración de Actualización**

**Desde:** `http://localhost:8000/devtools/generators/migration`

```
Migration Type: Update Table
Table Name: posts
Migration Name: add_slug_to_posts_table
```

**Agregar columna:**
```
Column Name: slug
Type: string
Modifiers: 
  ☑ Unique
  ☑ After: title
```

---

#### **Paso 4: Ejecutar Migración**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `migrate`

---

#### **Paso 5: Limpiar Cachés**

**Desde:** `http://localhost:8000/devtools/cache`

**Click en:** "Clear All"

**Propósito:** Asegurar que cambios se reflejen.

---

#### **Paso 6: Verificar Solución**

1. Refrescar aplicación
2. Si persiste error, revisar logs nuevamente
3. Repetir proceso

---

### 6.3 📦 Instalar Nuevo Paquete

**Objetivo:** Agregar sistema de permisos con Spatie Permission.

#### **Paso 1: Instalar Paquete**

**Desde:** `http://localhost:8000/devtools/composer`

**Click en:** "Install Package"

```
Package name: spatie/laravel-permission
Version: (latest)
☐ Dev dependency
```

**Esperar:** Instalación completada.

---

#### **Paso 2: Publicar Configuración**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `vendor:publish`

**Provider:** `Spatie\Permission\PermissionServiceProvider`

---

#### **Paso 3: Ejecutar Migraciones**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `migrate`

**Resultado:** Tablas `roles`, `permissions`, `model_has_roles`, etc.

---

#### **Paso 4: Verificar Instalación**

**Desde:** `http://localhost:8000/devtools/database`

**Verificar tablas nuevas:**
- `roles`
- `permissions`
- `role_has_permissions`
- `model_has_roles`
- `model_has_permissions`

---

#### **Paso 5: Crear Seeders**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `make:seeder`

**Argumento:** `RoleSeeder`

**Editar manualmente:** `database/seeders/RoleSeeder.php`

```php
use Spatie\Permission\Models\Role;
use Spatie\Permission\Models\Permission;

public function run(): void
{
    $admin = Role::create(['name' => 'admin']);
    $editor = Role::create(['name' => 'editor']);
    $user = Role::create(['name' => 'user']);
    
    Permission::create(['name' => 'create posts']);
    Permission::create(['name' => 'edit posts']);
    Permission::create(['name' => 'delete posts']);
    
    $admin->givePermissionTo(Permission::all());
}
```

---

#### **Paso 6: Ejecutar Seeder**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `db:seed --class=RoleSeeder`

---

#### **Paso 7: Verificar Datos**

**Desde:** `http://localhost:8000/devtools/database`

**Query:**
```sql
SELECT * FROM roles;
SELECT * FROM permissions;
```

**Resultado:** Debe mostrar roles y permisos creados.

---

### 6.4 🚢 Preparar para Producción

#### **Paso 1: Ejecutar Tests**

**Desde:** `http://localhost:8000/devtools/artisan`

**Comando:** `test`

**Verificar:** Todos los tests pasan.

---

#### **Paso 2: Optimizar Aplicación**

**Desde:** `http://localhost:8000/devtools/cache`

**Click en:** "Optimize"

**Resultado:**
- Config cacheada
- Routes cacheadas
- Views pre-compiladas

---

#### **Paso 3: Verificar Logs**

**Desde:** `http://localhost:8000/devtools/logs`

**Filtrar:** Nivel ERROR

**Acción:** Resolver todos los errores antes de deploy.

---

#### **Paso 4: Revisar Dependencias**

**Desde:** `http://localhost:8000/devtools/composer`

**Verificar:**
- Todos los paquetes actualizados
- Sin vulnerabilidades conocidas

---

#### **Paso 5: Verificar Configuración Docker**

**Desde:** `http://localhost:8000/devtools/sail`

**Verificar:**
- Todos los contenedores corriendo
- Sin errores en logs

---

#### **Paso 6: Backup de Base de Datos**

**Desde:** `http://localhost:8000/devtools/database`

**Exportar:** Todas las tablas importantes.

---

## 7. 📚 Glosario de Términos

| Término | Definición |
|---------|------------|
| **Artisan** | CLI (Command Line Interface) de Laravel para tareas comunes |
| **Blade** | Motor de plantillas de Laravel para vistas |
| **Cache** | Almacenamiento temporal de datos para mejorar performance |
| **Controller** | Clase que maneja lógica de peticiones HTTP |
| **Closure** | Función anónima en PHP/Laravel |
| **Composer** | Gestor de dependencias para PHP |
| **DevTools** | Paquete de herramientas de desarrollo para Laravel |
| **Docker** | Plataforma de contenedores para aislar aplicaciones |
| **Eloquent** | ORM (Object-Relational Mapping) de Laravel |
| **Factory** | Clase para generar datos falsos en testing |
| **Fillable** | Propiedades de modelo que pueden asignarse masivamente |
| **Job** | Tarea que se ejecuta en segundo plano (asíncrono) |
| **Laravel Sail** | Entorno Docker preconfigurado para Laravel |
| **Livewire** | Framework full-stack para interfaces reactivas |
| **Mailpit** | Servidor SMTP de prueba para desarrollo |
| **Middleware** | Filtro que procesa peticiones HTTP |
| **Migration** | Script para modificar estructura de base de datos |
| **Model** | Clase que representa tabla de base de datos |
| **Namespace** | Organización jerárquica de clases PHP |
| **ORM** | Object-Relational Mapping (mapeo objeto-relacional) |
| **Policy** | Clase que define reglas de autorización |
| **Queue** | Sistema de colas para tareas asíncronas |
| **Request** | Clase que valida datos de peticiones HTTP |
| **Resource** | Transformador de datos para APIs |
| **Route** | Definición de URL y su handler |
| **Sail** | Alias para Laravel Sail (Docker) |
| **Seeder** | Clase para poblar base de datos con datos iniciales |
| **Singleton** | Ruta con solo create/store (sin index/show) |
| **Soft Delete** | Eliminación lógica (marca como eliminado sin borrar) |
| **Tinker** | REPL interactivo de Laravel |
| **Vendor** | Directorio con dependencias de Composer |
| **View** | Plantilla Blade para renderizar HTML |

---

## 8. ⚡ Atajos de Teclado y Tips

### Navegación Rápida

| Acción | Atajo |
|--------|-------|
| Ir al Dashboard | `http://localhost:8000/devtools` |
| Limpiar todos los cachés | Dashboard → Quick Action "Clear Caches" |
| Ver últimos logs | Dashboard → Quick Action "View Logs" |
| Ejecutar migraciones | Dashboard → Quick Action "Run Migrations" |

---

### Tips de Productividad

#### **1. Usa History en Artisan Commands**
```
En lugar de buscar el comando cada vez:
1. Ejecuta comando
2. Click en "History"
3. Selecciona comando de la lista
```

---

#### **2. Guarda Queries Favoritas**
```
Database Manager:
1. Escribe query útil
2. Click en "Save to Favorites"
3. Reutiliza en futuras sesiones
```

---

#### **3. Filtra Logs por Nivel**
```
En Logs Viewer:
- Click en "ERROR" para solo ver errores
- Usa búsqueda para términos específicos
```

---

#### **4. Crea Múltiples Archivos a la Vez**
```
En Model Generator:
☑ Marca todas las opciones necesarias
☑ Create Migration
☑ Create Factory
☑ Create Seeder
☑ Create Controller
☑ Create Form Requests
```

---

#### **5. Usa EXPLAIN para Optimizar Queries**
```
Database Manager:
1. Escribe query lenta
2. Click en "EXPLAIN"
3. Revisa índices sugeridos
```

---

## 9. 🔒 Seguridad y Mejores Prácticas

### ⚠️ IMPORTANTE: Seguridad en Producción

#### **1. Deshabilitar DevTools en Producción**

**En `.env` de producción:**
```env
APP_ENV=production
APP_DEBUG=false
```

**DevTools se deshabilitará automáticamente.**

---

#### **2. Proteger Rutas de DevTools**

**Si necesitas DevTools en staging:**

**Editar:** `config/devtools.php`

```php
'middleware' => ['web', 'auth', 'admin'],
```

**Crear middleware Admin:**
```bash
php artisan make:middleware EnsureUserIsAdmin
```

```php
public function handle($request, Closure $next)
{
    if (!auth()->user()?->isAdmin()) {
        abort(403);
    }
    
    return $next($request);
}
```

---

#### **3. No Exponer Información Sensible**

❌ **NO HAGAS:**
```php
// En logs
Log::info('User password: ' . $password); // ¡NUNCA!
```

✅ **HACER:**
```php
Log::info('User logged in', ['user_id' => $user->id]);
```

---

#### **4. Validar Queries en Database Manager**

DevTools solo permite `SELECT` queries por seguridad.

❌ **No permitido:**
```sql
DELETE FROM users;
UPDATE users SET role = 'admin';
DROP TABLE posts;
```

✅ **Permitido:**
```sql
SELECT * FROM users WHERE id = 1;
SELECT COUNT(*) FROM posts;
```

---

### 🛡️ Mejores Prácticas de Desarrollo

#### **1. Limpia Cachés Regularmente**
```
Después de:
- Cambiar archivos config/
- Modificar .env
- Actualizar rutas
- Cambiar vistas Blade
```

---

#### **2. Revisa Logs Diariamente**
```
- Filtra por ERROR
- Resuelve warnings antes que se conviertan en errores
- Usa context en logs para debugging
```

---

#### **3. Ejecuta Tests Antes de Commit**
```bash
sail artisan test
```

---

#### **4. Usa Migraciones para TODO Cambio de BD**
```
❌ No modifiques BD manualmente en phpMyAdmin
✅ Crea migration para cada cambio
```

---

#### **5. Documenta Comandos Complejos**
```php
// En seeders, agregar comentarios
// Crea usuario admin con permisos completos
$admin = User::factory()->create([...]);
```

---

## 10. 🆘 Solución de Problemas Comunes

### ❌ "DevTools no carga / Error 404"

**Causa:** Paquete no instalado o rutas no publicadas.

**Solución:**
```bash
# Verificar instalación
composer show zamyr/laravel-devtools

# Si no está instalado
composer require zamyr/laravel-devtools --dev

# Limpiar cachés
php artisan config:clear
php artisan route:clear
php artisan cache:clear
```

---

### ❌ "Access Denied" al acceder a DevTools

**Causa:** Middleware de autenticación o restricción de IP.

**Solución:**
```bash
# Verificar config
cat config/devtools.php

# Si requiere auth, iniciar sesión primero
# Si restricción IP, agregar tu IP en config
```

---

### ❌ "Database connection error" en Database Manager

**Causa:** Credenciales incorrectas en `.env`.

**Solución:**
```bash
# Verificar .env
DB_CONNECTION=mysql
DB_HOST=mysql  # o 127.0.0.1
DB_PORT=3306
DB_DATABASE=devjobs
DB_USERNAME=sail
DB_PASSWORD=password

# Limpiar config cache
sail artisan config:clear

# Verificar conexión
sail artisan db:show
```

---

### ❌ "No containers found" en Sail Manager

**Causa:** Docker no está corriendo.

**Solución:**
```bash
# Iniciar Docker Desktop
# Luego:
sail up -d

# Verificar
docker ps
```

---

### ❌ "Views not compiling" después de limpiar cache

**Causa:** Permisos de escritura en `storage/framework/views/`.

**Solución:**
```bash
# Dar permisos
chmod -R 775 storage
chmod -R 775 bootstrap/cache

# Limpiar y reconstruir
sail artisan view:clear
sail artisan view:cache
```

---

### ❌ "Queue jobs not processing"

**Causa:** Worker no está corriendo.

**Solución:**
```bash
# Iniciar worker
sail artisan queue:work

# Para que persista (usar Supervisor en producción)
```

---

### ❌ "Route not found" después de crear controlador

**Causa:** Rutas no registradas en `routes/web.php`.

**Solución:**
```php
// En routes/web.php
use App\Http\Controllers\PostController;

Route::resource('posts', PostController::class);
```

```bash
# Verificar rutas
sail artisan route:list
```

---

### ❌ "Class not found" después de crear archivo

**Causa:** Autoload de Composer desactualizado.

**Solución:**
```bash
composer dump-autoload
```

---

### ❌ Logs muestran "Maximum execution time exceeded"

**Causa:** Script PHP tarda demasiado.

**Solución:**
```php
// En archivo php.ini o .env
max_execution_time=300

// O en código específico
set_time_limit(300);
```

---

## 11. 📖 Recursos Adicionales

### Documentación Oficial

- **Laravel:** https://laravel.com/docs
- **Laravel Sail:** https://laravel.com/docs/sail
- **Eloquent ORM:** https://laravel.com/docs/eloquent
- **Artisan Console:** https://laravel.com/docs/artisan
- **Blade Templates:** https://laravel.com/docs/blade

---

### Paquetes Recomendados

| Paquete | Descripción | Instalación |
|---------|-------------|-------------|
| **spatie/laravel-permission** | Sistema de roles y permisos | `composer require spatie/laravel-permission` |
| **barryvdh/laravel-debugbar** | Debugbar para desarrollo | `composer require barryvdh/laravel-debugbar --dev` |
| **laravel/telescope** | Debugging avanzado | `composer require laravel/telescope --dev` |
| **spatie/laravel-backup** | Backups automáticos | `composer require spatie/laravel-backup` |
| **intervention/image** | Manipulación de imágenes | `composer require intervention/image` |

---

### Comunidad y Soporte

- **Laravel News:** https://laravel-news.com
- **Laracasts:** https://laracasts.com (tutoriales en video)
- **Laravel Daily:** https://laraveldaily.com
- **Stack Overflow:** https://stackoverflow.com/questions/tagged/laravel

---

### Herramientas Complementarias

| Herramienta | Propósito |
|-------------|-----------|
| **phpMyAdmin** | Administración de MySQL (alternativa a Database Manager) |
| **Redis Commander** | Visualización de datos Redis |
| **Mailpit Web UI** | Ver emails de desarrollo (incluido en Sail) |
| **VS Code Extensions** | Laravel Blade Snippets, PHP Intelephense |

---

## 12. 🎓 Conclusión

### ¿Qué Aprendiste?

En esta guía cubrimos:

✅ **Dashboard Principal** - Centro de control con Quick Actions  
✅ **Generadores** - Crear Controllers, Models, Migrations visualmente  
✅ **Visualizadores** - Explorar Controllers y Routes de la app  
✅ **Database Manager** - Consultar y explorar base de datos  
✅ **Herramientas** - Artisan, Composer, Sail, Logs, Cache, Queue  
✅ **Flujos Completos** - Crear CRUDs, debugging, instalar paquetes  
✅ **Mejores Prácticas** - Seguridad, optimización, troubleshooting  

---

### Próximos Pasos

1. **Practica cada módulo:**
   - Crea un CRUD de prueba
   - Experimenta con Query Builder
   - Ejecuta comandos Artisan

2. **Explora funcionalidades avanzadas:**
   - Políticas de autorización
   - Jobs y Queues
   - Testing automatizado

3. **Integra DevTools en tu workflow:**
   - Úsalo como primera herramienta al debuggear
   - Reemplaza terminal para comandos comunes
   - Monitorea logs regularmente

---

### Feedback y Contribuciones

Si encuentras errores en esta guía o tienes sugerencias:

1. Revisa la documentación oficial del paquete
2. Reporta issues en el repositorio del paquete
3. Comparte tips con la comunidad

---

### Licencia y Créditos

- **Laravel DevTools:** zamyr/laravel-devtools
- **Laravel Framework:** Taylor Otwell y contribuidores
- **Guía creada:** 26 de noviembre de 2025

---

## 📌 Apéndice A: Comandos de Referencia Rápida

### Sail (Docker)

```bash
sail up -d              # Iniciar contenedores
sail down               # Detener contenedores
sail artisan [cmd]      # Ejecutar Artisan
sail composer [cmd]     # Ejecutar Composer
sail npm [cmd]          # Ejecutar NPM
sail mysql              # Acceder a MySQL CLI
sail shell              # Acceder a shell del contenedor
sail logs -f            # Ver logs en tiempo real
sail restart            # Reiniciar contenedores
```

---

### Artisan Esenciales

```bash
# Generadores
php artisan make:controller PostController --resource
php artisan make:model Post -mfs
php artisan make:migration create_posts_table
php artisan make:seeder PostSeeder
php artisan make:factory PostFactory
php artisan make:request StorePostRequest

# Migraciones
php artisan migrate
php artisan migrate:fresh --seed
php artisan migrate:rollback
php artisan migrate:status

# Cache
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
php artisan optimize
php artisan optimize:clear

# Base de Datos
php artisan db:seed
php artisan db:show
php artisan db:table users

# Queue
php artisan queue:work
php artisan queue:failed
php artisan queue:retry all
php artisan queue:flush

# Otros
php artisan tinker
php artisan test
php artisan serve
php artisan route:list
```

---

### Composer

```bash
composer install           # Instalar dependencias
composer update            # Actualizar todo
composer require [pkg]     # Instalar paquete
composer require [pkg] --dev  # Dev dependency
composer remove [pkg]      # Eliminar paquete
composer dump-autoload     # Recargar autoload
composer show               # Listar paquetes
composer show [pkg]        # Info de paquete
```

---

## 📌 Apéndice B: Estructura de Archivos Laravel

```
devjobs/
├── app/
│   ├── Console/              # Comandos Artisan personalizados
│   ├── Exceptions/           # Handlers de excepciones
│   ├── Http/
│   │   ├── Controllers/      # Controladores
│   │   ├── Middleware/       # Middlewares
│   │   └── Requests/         # Form Requests
│   ├── Models/               # Modelos Eloquent
│   ├── Policies/             # Políticas de autorización
│   └── Providers/            # Service Providers
├── bootstrap/
│   ├── app.php               # Bootstrap de aplicación
│   └── cache/                # Archivos cacheados
├── config/                   # Archivos de configuración
│   ├── app.php
│   ├── database.php
│   ├── cache.php
│   └── ...
├── database/
│   ├── factories/            # Factories para testing
│   ├── migrations/           # Migraciones
│   └── seeders/              # Seeders
├── public/                   # Punto de entrada público
│   ├── index.php
│   └── assets/
├── resources/
│   ├── css/                  # Estilos
│   ├── js/                   # JavaScript
│   ├── views/                # Vistas Blade
│   └── lang/                 # Traducciones
├── routes/
│   ├── web.php               # Rutas web
│   ├── api.php               # Rutas API
│   └── console.php           # Comandos Artisan
├── storage/
│   ├── app/                  # Archivos de aplicación
│   ├── framework/            # Framework cache/sessions
│   └── logs/                 # Logs
├── tests/                    # Tests automatizados
│   ├── Feature/
│   └── Unit/
├── vendor/                   # Dependencias Composer
├── .env                      # Variables de entorno
├── artisan                   # CLI Artisan
├── composer.json             # Dependencias PHP
├── package.json              # Dependencias NPM
└── docker-compose.yml        # Configuración Sail
```

---

## 📌 Apéndice C: Variables de Entorno (.env)

### Configuración Esencial

```env
# Aplicación
APP_NAME=DevJobs
APP_ENV=local                # local | staging | production
APP_KEY=base64:...           # Generada con: php artisan key:generate
APP_DEBUG=true               # false en producción
APP_URL=http://localhost

# Base de Datos
DB_CONNECTION=mysql
DB_HOST=mysql                # o 127.0.0.1
DB_PORT=3306
DB_DATABASE=devjobs
DB_USERNAME=sail
DB_PASSWORD=password

# Cache
CACHE_DRIVER=database        # file | database | redis | memcached
CACHE_PREFIX=devjobs_cache

# Sessions
SESSION_DRIVER=database      # file | database | redis
SESSION_LIFETIME=120

# Queue
QUEUE_CONNECTION=database    # sync | database | redis | sqs

# Mail (Mailpit en Sail)
MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="noreply@devjobs.com"
MAIL_FROM_NAME="${APP_NAME}"

# Redis (opcional)
REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379

# Sail
SAIL_XDEBUG_MODE=develop,debug
SAIL_SKIP_CHECKS=true
```

---

## 🎉 ¡Felicitaciones!

Has completado la guía completa de **Laravel DevTools**.

Ahora tienes todas las herramientas para:
- Desarrollar más rápido con generadores visuales
- Debuggear eficientemente con logs y database manager
- Gestionar tu aplicación con interfaces intuitivas
- Optimizar tu workflow de desarrollo

**¡Empieza a construir algo increíble con Laravel!** 🚀

---

**Última actualización:** 26 de noviembre de 2025  
**Versión de la guía:** 1.0.0  
**Compatible con:** Laravel 11+, DevTools dev-main

---

*Esta guía fue creada con fines educativos. Para documentación oficial y actualizada, consulta la documentación de Laravel y del paquete DevTools.*
