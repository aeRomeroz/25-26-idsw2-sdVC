# iniciarSesion() > Análisis


## Información del artefacto

- **Proyecto**: Centro de Gestión Universitaria (CGU)
- **Caso de uso**: iniciarSesion()
- **Fase RUP**: Elaboración
- **Disciplina**: Análisis y Diseño
- **Versión**: 1.0
- **Fecha**: 2026-05-26
- **Autor**: Gemini CLI

## Propósito

Análisis del caso de uso `iniciarSesion()` mediante el patrón MVC (BCE), identificando las clases de análisis y sus interacciones para el proceso de autenticación de usuarios.

## Diagramas de Análisis

### Colaboración (BCE)

<div align=center>

|![Análisis: iniciarSesion()](/images/01-analisis/casos-uso/iniciarSesion/iniciarSesion-analisis.svg)|
|-|
|Código fuente: [colaboracion.puml](/modelosUML/01-analisis/casos-uso/iniciarSesion/colaboracion.puml)|

</div>

### Secuencia de Análisis

<div align=center>

|![Secuencia: iniciarSesion()](/images/01-analisis/casos-uso/iniciarSesion/iniciarSesion-analisis-secuencia.svg)|
|-|
|Código fuente: [secuencia.puml](/modelosUML/01-analisis/casos-uso/iniciarSesion/secuencia.puml)|

</div>

## Clases de análisis identificadas

### Clases de vista (Boundary)

#### LoginView
**Estereotipo**: Vista (Boundary)  
**Responsabilidades**:
- Presentar la interfaz de inicio de sesión.
- Capturar las credenciales (username, password).
- Mostrar mensajes de error en caso de autenticación fallida.
- Coordinar la transición al menú principal tras el éxito.

### Clases de control

#### IniciarSesionController
**Estereotipo**: Control  
**Responsabilidades**:
- Coordinar el proceso de autenticación.
- Solicitar la validación de credenciales al repositorio.
- Gestionar la creación de la sesión activa.

### Clases de entidad (Entity)

#### UsuarioRepository
**Estereotipo**: Entidad  
**Responsabilidades**:
- Abstraer el acceso a los datos de seguridad de los usuarios.
- Validar credenciales contra la persistencia.

#### Usuario
**Estereotipo**: Entidad  
**Responsabilidades**:
- Representar al usuario autenticado y su rol.

#### Sesion
**Estereotipo**: Entidad  
**Responsabilidades**:
- Representar el estado de autenticación activa en el sistema.

## Flujo de colaboración

1.  **El Usuario No Registrado** solicita acceder al sistema a través de `LoginView`.
2.  `LoginView` delega la autenticación a `IniciarSesionController`.
3.  `IniciarSesionController` solicita a `UsuarioRepository` validar las credenciales.
4.  Si son válidas, `IniciarSesionController` instancia un objeto `Sesion` vinculado al `Usuario`.
5.  Finalmente, `LoginView` redirige al Administrador al estado `SISTEMA_DISPONIBLE`.

---
