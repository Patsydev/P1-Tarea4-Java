# Proyecto de Programación 1 - Tarea 4
Proyecto de la Tarea 4: Formulario y Gestión de Usuarios en Java (Swing + MySQL).

Sistema de Gestión de Usuarios desarrollado en Java con interfaz gráfica Swing y base de datos MySQL.

## Descripción

Este proyecto es una aplicación de escritorio para la gestión de usuarios que permite realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) con una interfaz gráfica intuitiva y moderna. La aplicación incluye un sistema de autenticación con login y registro de usuarios.

## Características Principales

- **Sistema de Autenticación**: Login seguro con validación de credenciales
- **Registro de Usuarios**: Formulario completo para crear nuevas cuentas
- **Gestión de Usuarios**: Panel administrativo con tabla interactiva
- **Operaciones CRUD**: 
  - Crear nuevos usuarios
  - Visualizar lista completa de usuarios
  - Actualizar información de usuarios existentes
  - Eliminar usuarios con confirmación

## Tecnologías Utilizadas

- **Java**: Lenguaje de programación principal
- **Swing**: Framework para la interfaz gráfica de usuario
- **MySQL**: Sistema de gestión de base de datos
- **JDBC**: Conectividad con base de datos
- **MySQL Connector/J 9.5.0**: Driver JDBC para MySQL
- **IntelliJ IDEA**: IDE de desarrollo

## Estructura del Proyecto

```
P1-Tarea4-Java/
│
├── src/
│   ├── db/
│   │   └── DatabaseConnection.java    # Singleton para conexión BD
│   │
│   ├── model/
│   │   └── Usuario.java               # Modelo de datos Usuario
│   │
│   ├── repository/
│   │   └── UsuarioRepository.java     # Operaciones CRUD en BD
│   │
│   ├── factory/
│   │   └── UsuarioFactory.java        # Factory para crear usuarios
│   │
│   ├── ui/
│   │   ├── Main.java                  # Punto de entrada
│   │   ├── LoginForm.java             # Pantalla de login
│   │   ├── RegisterForm.java          # Formulario de registro
│   │   └── UserManagement.java        # Panel de administración
│   │
│   └── lib/
│       └── mysql-connector-j-9.5.0.jar # Driver MySQL
│
├── .gitignore
├── Tarea4.iml                         # Configuración IntelliJ
└── README.md
```

## Requisitos Previos

- **JDK 7 o superior** instalado
- **MySQL Server** instalado y con la base de datos
- **IDE Java** (IntelliJ IDE recomendado) 
- **MySQL Connector/J** (incluido en el proyecto, hay que aplicarlo como plugin)

### 4. Configurar el Proyecto en IntelliJ IDEA

1. Abrir IntelliJ IDEA
2. Seleccionar `File > Open` y elegir la carpeta del proyecto
3. Ir a `File > Project Structure > Libraries`
4. Asegurarse de que `mysql-connector-j-9.5.0.jar` esté añadido como biblioteca
5. Configurar el SDK del proyecto (JDK 7)

### 5. Compilar y Ejecutar

Desde IntelliJ:
- Navegar a `src/ui/Main.java`
- Click derecho > `Run 'Main.main()'`

## Arquitectura del Proyecto

El proyecto sigue una arquitectura en capas:

### Capa de Presentación (UI)
- **LoginForm**: Interfaz de autenticación
- **RegisterForm**: Formulario de registro completo
- **UserManagement**: Panel CRUD con tabla interactiva
- **Main**: Punto de entrada de la aplicación

### Capa de Negocio
- **UsuarioFactory**: Patrón Factory para crear instancias de Usuario

### Capa de Datos
- **Usuario**: Modelo de datos (POJO)
- **UsuarioRepository**: Patrón Repository para operaciones CRUD
- **DatabaseConnection**: Patrón Singleton para gestión de conexión

### Patrones de Diseño Utilizados

- **Singleton**: Para la conexión a base de datos y repositorio
- **Factory**: Para la creación de objetos Usuario
- **Repository**: Para abstraer el acceso a datos
- **MVC**: Separación entre modelo, vista y lógica

## Licencia

Este proyecto es de código abierto y está disponible para fines educativos.

## Autor

**⭐ Patsydev**
- GitHub: [@Patsydev](https://github.com/Patsydev)

