# 🛠️ Laravel DevTools - Plan de Desarrollo

## 📋 Descripción del Proyecto
Paquete de Composer (require-dev) que proporciona una interfaz visual para ejecutar comandos Artisan, Composer, Sail y gestionar el proyecto Laravel sin necesidad de usar la terminal.

---

## 🎯 Objetivos Principales

1. **Interfaz Visual Completa**: Panel web para ejecutar todos los comandos comunes
2. **Solo Desarrollo**: Funciona únicamente en entorno local (APP_ENV=local)
3. **Reutilizable**: Se puede instalar en cualquier proyecto Laravel
4. **No Invasivo**: No afecta al código del proyecto principal
5. **Fácil Instalación**: `composer require --dev zamyr/laravel-devtools`

---

## 🏗️ Estructura del Paquete

```
packages/laravel-devtools/
├── src/
│   ├── DevToolsServiceProvider.php          # Service Provider principal
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── ArtisanController.php        # Manejo de comandos Artisan
│   │   │   ├── ComposerController.php       # Manejo de Composer
│   │   │   ├── SailController.php           # Manejo de Docker/Sail
│   │   │   └── GeneratorController.php      # Generadores visuales
│   │   └── Middleware/
│   │       └── DevToolsEnabled.php          # Verifica entorno local
│   ├── Commands/
│   │   └── InstallDevTools.php              # Comando de instalación
│   └── Services/
│       ├── ArtisanService.php               # Lógica de Artisan
│       ├── ComposerService.php              # Lógica de Composer
│       └── SailService.php                  # Lógica de Sail/Docker
├── resources/
│   └── views/
│       ├── layouts/
│       │   └── app.blade.php                # Layout principal
│       ├── dashboard.blade.php              # Panel principal
│       ├── artisan/
│       │   ├── index.blade.php              # Lista de comandos Artisan
│       │   └── run.blade.php                # Ejecutar comando
│       ├── generators/
│       │   ├── controller.blade.php         # Generar Controller
│       │   ├── model.blade.php              # Generar Model
│       │   ├── migration.blade.php          # Generar Migration
│       │   ├── seeder.blade.php             # Generar Seeder
│       │   ├── middleware.blade.php         # Generar Middleware
│       │   ├── request.blade.php            # Generar Request
│       │   ├── livewire.blade.php           # Generar Livewire
│       │   └── command.blade.php            # Generar Command
│       ├── composer/
│       │   ├── index.blade.php              # Gestión de paquetes
│       │   └── install.blade.php            # Instalar paquete
│       └── sail/
│           ├── index.blade.php              # Estado de contenedores
│           └── manage.blade.php             # Gestionar Sail
├── routes/
│   └── web.php                              # Rutas del paquete
├── public/
│   └── css/
│       └── devtools.css                     # Estilos personalizados
├── config/
│   └── devtools.php                         # Configuración del paquete
├── composer.json
├── README.md
└── LICENSE
```

---

## 🚀 Funcionalidades por Módulo

### 1. **Dashboard Principal** (`/devtools`)
- Resumen del estado del proyecto
- Accesos rápidos a generadores
- Últimos comandos ejecutados
- Estado de Sail/Docker
- Información del entorno

### 2. **Generadores Visuales** (`/devtools/generators`)

#### 2.1 Controller Generator
- Nombre del controller
- Tipo: Resource, API, Invokable, Plain
- Opción: Con model binding
- Opción: Con middleware
- Preview del código generado

#### 2.2 Model Generator
- Nombre del modelo
- Opciones:
  - Con migration
  - Con seeder
  - Con factory
  - Con resource controller
  - Soft deletes
  - Timestamps
- Definir fillable/guarded
- Definir relaciones básicas

#### 2.3 Migration Generator
- Nombre de la migración
- Tipo: Create, Modify, Drop
- Constructor visual de columnas:
  - Tipo de dato
  - Nullable
  - Default
  - Index
  - Unique
  - Foreign keys
- Preview del código

#### 2.4 Seeder Generator
- Nombre del seeder
- Seleccionar modelo
- Cantidad de registros

#### 2.5 Middleware Generator
- Nombre del middleware
- Tipo: Global, Route, Group

#### 2.6 Request Generator
- Nombre del request
- Definir reglas de validación visuales

#### 2.7 Livewire Component Generator
- Nombre del componente
- Con/sin view inline

#### 2.8 Command Generator
- Nombre del comando
- Signature
- Description

### 3. **Comandos Artisan** (`/devtools/artisan`)
- Lista categorizada de todos los comandos Artisan
- Buscador de comandos
- Formularios dinámicos para argumentos/opciones
- Ejecución en tiempo real
- Historial de comandos ejecutados
- Output en tiempo real

**Comandos más usados (acceso rápido):**
- `migrate` / `migrate:fresh` / `migrate:rollback`
- `db:seed`
- `cache:clear` / `config:clear` / `route:clear`
- `queue:work` / `queue:restart`
- `storage:link`
- `optimize` / `optimize:clear`

### 4. **Composer Manager** (`/devtools/composer`)
- Instalar paquete (require/require-dev)
- Actualizar paquetes
- Remover paquetes
- Listar paquetes instalados
- Ver información de paquetes
- Ejecutar scripts de composer.json
- Output en tiempo real

### 5. **Sail/Docker Manager** (`/devtools/sail`)
- Estado de contenedores
- Iniciar/Detener contenedores
- Ver logs de contenedores
- Ejecutar comandos en contenedores
- Ver uso de recursos
- Accesos rápidos:
  - `sail up -d`
  - `sail down`
  - `sail artisan`
  - `sail composer`
  - `sail npm`

### 6. **File Explorer** (Opcional - Fase 2)
- Navegador de archivos del proyecto
- Editor de código básico
- Crear/Editar/Eliminar archivos

---

## 🔒 Seguridad

1. **Middleware de Protección**:
   - Solo funciona si `APP_ENV=local`
   - Solo accesible desde `localhost`
   - Token CSRF en todos los formularios

2. **Validación de Comandos**:
   - Lista blanca de comandos permitidos
   - Sanitización de inputs
   - No permitir comandos destructivos sin confirmación

3. **Confirmaciones**:
   - Confirmación para:
     - `migrate:fresh`
     - `db:wipe`
     - `cache:clear`
     - Eliminar archivos

---

## 📦 Instalación y Configuración

### Paso 1: Crear estructura del paquete
```bash
mkdir -p packages/laravel-devtools
cd packages/laravel-devtools
```

### Paso 2: Composer.json del paquete
```json
{
  "name": "zamyr/laravel-devtools",
  "description": "Visual interface for Laravel development tools",
  "type": "library",
  "require": {
    "php": "^8.2",
    "illuminate/support": "^11.0"
  },
  "autoload": {
    "psr-4": {
      "Zamyr\\LaravelDevTools\\": "src/"
    }
  },
  "extra": {
    "laravel": {
      "providers": [
        "Zamyr\\LaravelDevTools\\DevToolsServiceProvider"
      ]
    }
  }
}
```

### Paso 3: Configurar en el proyecto principal
```json
// composer.json del proyecto
{
  "repositories": [
    {
      "type": "path",
      "url": "./packages/laravel-devtools"
    }
  ],
  "require-dev": {
    "zamyr/laravel-devtools": "@dev"
  }
}
```

### Paso 4: Instalar
```bash
composer require --dev zamyr/laravel-devtools
php artisan devtools:install
```

---

## 🎨 Stack Tecnológico

- **Backend**: Laravel 11+
- **Frontend**: 
  - Blade Templates
  - Tailwind CSS (usa el del proyecto)
  - Alpine.js (para interactividad)
  - Livewire (opcional, para updates en tiempo real)
- **Ejecución de Comandos**: 
  - `Artisan::call()`
  - `Process` facade de Laravel
  - Symfony Process component

---

## 📝 Plan de Implementación (Fases)

### **Fase 1: Setup Inicial** ⭐ (Empezamos aquí)
1. Crear estructura del paquete
2. Service Provider básico
3. Configuración de rutas
4. Layout base con Tailwind
5. Dashboard simple

### **Fase 2: Generadores Básicos**
1. Controller Generator
2. Model Generator
3. Migration Generator

### **Fase 3: Comandos Artisan**
1. Lista de comandos
2. Ejecución de comandos
3. Output en tiempo real

### **Fase 4: Composer Manager**
1. Instalar paquetes
2. Listar paquetes
3. Remover paquetes

### **Fase 5: Sail Manager**
1. Estado de contenedores
2. Iniciar/Detener
3. Ver logs

### **Fase 6: Mejoras y Pulido**
1. Historial de comandos
2. Favoritos
3. Shortcuts de teclado
4. Temas (dark/light)

---

## 🔄 Flujo de Trabajo

```
Usuario accede a /devtools
    ↓
Middleware verifica APP_ENV=local
    ↓
Dashboard muestra opciones
    ↓
Usuario selecciona "Crear Controller"
    ↓
Formulario visual con opciones
    ↓
Usuario completa formulario
    ↓
Controller ejecuta Artisan::call('make:controller', [...])
    ↓
Muestra resultado y archivo generado
    ↓
Usuario puede editar o crear otro
```

---

## 📊 Métricas de Éxito

- ✅ Reducir tiempo de desarrollo en comandos repetitivos
- ✅ No necesitar abrir terminal para tareas comunes
- ✅ Interfaz intuitiva y rápida
- ✅ 0 errores de sintaxis en comandos
- ✅ Reutilizable en múltiples proyectos

---

## 🚧 Limitaciones Conocidas

1. Solo funciona en entorno local
2. Requiere permisos de escritura en directorios
3. Comandos de larga duración pueden tener timeout
4. No reemplaza completamente la terminal (casos avanzados)

---

## 📚 Documentación Adicional

- **README.md**: Guía de instalación y uso
- **CONTRIBUTING.md**: Guía para contribuir
- **CHANGELOG.md**: Registro de cambios
- **LICENSE**: MIT License

---

## 🎯 Siguiente Paso

**Ahora vamos a crear la Fase 1: Setup Inicial**

1. Crear la estructura de carpetas del paquete
2. Crear `composer.json`
3. Crear `DevToolsServiceProvider`
4. Crear rutas básicas
5. Crear layout y dashboard inicial
6. Configurar en el proyecto DevJobs para testing

¿Listo para empezar con el Paso 1?
