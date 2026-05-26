# crearUsuario() > Análisis


## Información del artefacto

- **Proyecto**: Centro de Gestión Universitaria (CGU)
- **Caso de uso**: crearUsuario()
- **Fase RUP**: Elaboración
- **Disciplina**: Análisis y Diseño
- **Versión**: 1.2
- **Fecha**: 2026-05-26
- **Autor**: Gemini CLI

## Propósito

Análisis del caso de uso `crearUsuario()` mediante el patrón MVC (BCE), identificando las clases de análisis y sus interacciones para la creación de nuevos usuarios en el sistema siguiendo la filosofía C→U.

## Diagramas de Análisis

### Colaboración (BCE)

<div align=center>

|![Análisis: crearUsuario()](/images/01-analisis/casos-uso/crearUsuario/crearUsuario-analisis.svg)|
|-|
|Código fuente: [colaboracion.puml](/modelosUML/01-analisis/casos-uso/crearUsuario/colaboracion.puml)|

</div>

## Clases de análisis identificadas

### Clases de vista (Boundary)

#### CrearUsuarioView
**Estereotipo**: Vista (Boundary)  
**Responsabilidades**:
- Presentar el formulario de creación de usuario.
- Capturar los datos ingresados por el administrador (username, password, rol).
- Validar formalmente los campos (no vacíos, formato de contraseña).
- Delegar la lógica de creación al controlador.
- Gestionar la transferencia automática al caso de uso `consultarUsuario()` tras el éxito.

### Clases de control

#### UsuarioController
**Estereotipo**: Control  
**Responsabilidades**:
- Coordinar el flujo de creación del usuario.
- Validar reglas de negocio (ej. unicidad de nombre de usuario en el repositorio).
- Orquestar la persistencia de la nueva entidad.
- Manejar la lógica de encriptación inicial (si aplica en esta fase).

### Clases de entidad (Entity)

#### UsuarioRepository
**Estereotipo**: Entidad  
**Responsabilidades**:
- Abstraer el acceso a la persistencia de los objetos `Usuario`.
- Implementar la verificación de unicidad del `username`.
- Ejecutar la operación de creación y retorno de la entidad persistida.

#### Usuario
**Estereotipo**: Entidad  
**Responsabilidades**:
- Representar los datos del usuario en el sistema.
- Encapsular atributos: `id`, `username`, `password`, `rol`.
- Validar la integridad de su propio estado interno.

## Flujo de colaboración exhaustivo

1.  **El Administrador** solicita la creación de un usuario a través de `CrearUsuarioView`.
2.  `CrearUsuarioView` invoca a `UsuarioController.validarDatosMínimos(username, password, rol)`:
    *   `UsuarioController` solicita a `UsuarioRepository.verificarUnicidad(username)` para garantizar que el nombre de usuario sea único.
    *   `UsuarioRepository` confirma la validez.
3.  Tras validación formal y de negocio exitosa, el Administrador confirma la creación.
4.  `CrearUsuarioView` invoca a `UsuarioController.crearUsuario(username, password, rol)`:
    *   `UsuarioController` instancia un nuevo objeto `Usuario(username, password, rol)`.
    *   `UsuarioController` solicita a `UsuarioRepository.crear(usuarioNuevo)` la persistencia del objeto.
5.  **Transferencia (C→U)**: Una vez creado el usuario, `CrearUsuarioView` incluye la colaboración `consultarUsuario(usuarioNuevo)` para mostrar automáticamente la ficha del usuario recién creado al Administrador.

## Conexión con disciplina de requisitos

- **Requisito funcional**: RF-ADM-01 (Crear Usuario).
- **Prototipo relacionado**: [Prototipo Administrador](/images/00-requisitos/01-casos-de-uso/Prototipos/Administrador/crearUsuario.png).
- **Caso de uso**: [Detallado Administrador](/RUP/00-requisitos/01-casos-de-uso/DetalladoCasosDeUso/Administrador/README.md#DetalladoCrearUsuario).

---
