# P1-Tarea4-Java

Sistema de Gestión de Usuarios desarrollado en Java con interfaz gráfica Swing y base de datos MySQL.

## 📋 Descripción

Este proyecto es una aplicación de escritorio para la gestión de usuarios que permite realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar) con una interfaz gráfica intuitiva y moderna. La aplicación incluye un sistema de autenticación con login y registro de usuarios.

## ✨ Características Principales

- 🔐 **Sistema de Autenticación**: Login seguro con validación de credenciales
- 📝 **Registro de Usuarios**: Formulario completo para crear nuevas cuentas
- 👥 **Gestión de Usuarios**: Panel administrativo con tabla interactiva
- ✏️ **Operaciones CRUD**: 
  - Crear nuevos usuarios
  - Visualizar lista completa de usuarios
  - Actualizar información de usuarios existentes
  - Eliminar usuarios con confirmación
- 🎨 **Interfaz Moderna**: Diseño limpio con paleta de colores personalizada
- 💾 **Persistencia de Datos**: Conexión a base de datos MySQL
- 🏗️ **Arquitectura Limpia**: Separación de capas (UI, Modelo, Repositorio, Factory)

## 🛠️ Tecnologías Utilizadas

- **Java**: Lenguaje de programación principal
- **Swing**: Framework para la interfaz gráfica de usuario
- **MySQL**: Sistema de gestión de base de datos
- **JDBC**: Conectividad con base de datos
- **MySQL Connector/J 9.5.0**: Driver JDBC para MySQL
- **IntelliJ IDEA**: IDE de desarrollo

## 📁 Estructura del Proyecto

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

## 📋 Requisitos Previos

- **JDK 8 o superior** instalado
- **MySQL Server** instalado y ejecutándose
- **IDE Java** (IntelliJ IDEA recomendado) o compilador Java
- **MySQL Connector/J** (incluido en el proyecto)

## 🚀 Instalación

### 1. Clonar el Repositorio

```bash
git clone https://github.com/Patsydev/P1-Tarea4-Java.git
cd P1-Tarea4-Java
```

### 2. Configurar la Base de Datos

Crear la base de datos y la tabla necesaria:

```sql
CREATE DATABASE IF NOT EXISTS almacenitlafinal;

USE almacenitlafinal;

CREATE TABLE IF NOT EXISTS usuarios (
    idUser INT AUTO_INCREMENT PRIMARY KEY,
    UserName VARCHAR(50) NOT NULL UNIQUE,
    Nombre VARCHAR(100) NOT NULL,
    Apellido VARCHAR(100) NOT NULL,
    Telefono VARCHAR(20),
    Email VARCHAR(100) NOT NULL,
    Password VARCHAR(255) NOT NULL
);
```

### 3. Configurar Credenciales de Base de Datos

Editar el archivo `src/db/DatabaseConnection.java` con tus credenciales:

```java
private static final String JDBC_URL = "jdbc:mysql://localhost:3306/almacenitlafinal";
private static final String USERNAME = "tu_usuario";
private static final String PASSWORD = "tu_contraseña";
```

**Nota**: Si tu MySQL está en otro servidor o puerto, ajusta `localhost:3306` según corresponda.

**⚠️ Nota de Seguridad**: En producción, las credenciales deben almacenarse en variables de entorno o archivos de configuración externos, no en el código fuente.

### 4. Configurar el Proyecto en IntelliJ IDEA

1. Abrir IntelliJ IDEA
2. Seleccionar `File > Open` y elegir la carpeta del proyecto
3. Ir a `File > Project Structure > Libraries`
4. Asegurarse de que `mysql-connector-j-9.5.0.jar` esté añadido como biblioteca
5. Configurar el SDK del proyecto (JDK 8 o superior)

### 5. Compilar y Ejecutar

Desde IntelliJ:
- Navegar a `src/ui/Main.java`
- Click derecho > `Run 'Main.main()'`

Desde terminal:
```bash
# Compilar (crear directorio bin primero)
mkdir -p bin
javac -cp "src/lib/*" -d bin src/db/*.java src/model/*.java src/factory/*.java src/repository/*.java src/ui/*.java

# Ejecutar (en Windows usar ; en lugar de : para el classpath)
java -cp "bin:src/lib/*" ui.Main
```

## 💻 Uso de la Aplicación

### Pantalla de Login

1. Ingresar nombre de usuario y contraseña
2. Hacer clic en **"INICIAR SESIÓN"**
3. Si no tienes cuenta, hacer clic en **"CREAR CUENTA"**

### Registro de Usuario

1. Completar todos los campos del formulario:
   - Nombre
   - Apellido
   - Teléfono
   - Correo electrónico
   - Nombre de usuario
   - Contraseña (confirmar)
2. Hacer clic en **"CREAR CUENTA"**
3. Serás redirigido al login automáticamente

### Panel de Administración

Una vez autenticado:

- **Ver usuarios**: La tabla muestra todos los usuarios registrados
- **Crear usuario**: Click en "Nuevo Usuario" y completar los campos en la tabla
- **Editar usuario**: Click en una celda (excepto ID) para editar directamente
- **Guardar cambios**: Click en "Guardar/Actualizar" después de editar
- **Eliminar usuario**: Seleccionar fila y hacer click en "Eliminar Usuario"
- **Cerrar sesión**: Click en "Cerrar Sesión" para volver al login

## 🏗️ Arquitectura del Proyecto

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

## 🎨 Diseño de la Interfaz

La aplicación utiliza una paleta de colores personalizada:
- **Color Principal**: #7E1B27 (Borgoña)
- **Fondo**: #FFFDEE (Crema)
- **Color Secundario**: #F0E4D6 (Beige)
- **Fuentes**: Segoe UI con soporte para emojis

Características visuales:
- Esquinas redondeadas en campos de texto
- Efectos hover en botones
- Tabla con filas alternas en colores
- Iconos emoji para mejor UX

## ⚠️ Consideraciones de Seguridad

**Nota Importante**: Este es un proyecto educativo. Para producción considerar:

1. **Contraseñas**: Implementar hashing (BCrypt, Argon2)
2. **SQL Injection**: Ya se usan PreparedStatements (✅)
3. **Validación**: Añadir validación más robusta de inputs
4. **Conexión BD**: Usar pool de conexiones
5. **Credenciales**: Mover a variables de entorno
6. **HTTPS**: Para conexiones remotas a la BD

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crear una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir un Pull Request

## 📝 Licencia

Este proyecto es de código abierto y está disponible para fines educativos.

## 👤 Autor

**Patsydev**
- GitHub: [@Patsydev](https://github.com/Patsydev)

## 🙏 Agradecimientos

- Instituto Tecnológico de Las Américas (ITLA)
- Comunidad Java y Swing
- MySQL y Oracle

---

⭐ Si este proyecto te resultó útil, considera darle una estrella en GitHub
