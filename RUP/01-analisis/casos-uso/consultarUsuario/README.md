# consultarUsuario() > Análisis


## Información del artefacto

- **Proyecto**: Centro de Gestión Universitaria (CGU)
- **Caso de uso**: consultarUsuario()
- **Fase RUP**: Elaboración
- **Disciplina**: Análisis y Diseño
- **Versión**: 1.0
- **Fecha**: 2026-05-26
- **Autor**: Gemini CLI

## Propósito

Análisis del caso de uso `consultarUsuario()` mediante el patrón MVC (BCE), identificando las clases de análisis y sus interacciones para la visualización detallada de un usuario en el sistema.

## Diagramas de Análisis

### Colaboración (BCE)

<div align=center>

|![Análisis: consultarUsuario()](/images/01-analisis/casos-uso/consultarUsuario/consultarUsuario-analisis.svg)|
|-|
|Código fuente: [colaboracion.puml](/modelosUML/01-analisis/casos-uso/consultarUsuario/colaboracion.puml)|

</div>

### Secuencia de Análisis

<div align=center>

|![Secuencia: consultarUsuario()](/images/01-analisis/casos-uso/consultarUsuario/consultarUsuario-analisis-secuencia.svg)|
|-|
|Código fuente: [secuencia.puml](/modelosUML/01-analisis/casos-uso/consultarUsuario/secuencia.puml)|

</div>

## Clases de análisis identificadas

### Clases de vista (Boundary)

#### ConsultarUsuarioView
**Estereotipo**: Vista (Boundary)  
**Responsabilidades**:
- Recibir la solicitud de consulta de un usuario específico.
- Presentar la ficha completa del usuario (Datos, Roles y Permisos).
- Permitir la navegación hacia la edición del usuario.
- Gestionar el retorno al listado general.

### Clases de control

#### UsuarioController
**Estereotipo**: Control  
**Responsabilidades**:
- Coordinar la obtención de datos detallados del usuario.
- Servir como intermediario entre la vista y el repositorio.

### Clases de entidad (Entity)

#### UsuarioRepository
**Estereotipo**: Entidad  
**Responsabilidades**:
- Proveer métodos de búsqueda de usuarios por identificador.
- Abstraer la lógica de acceso a datos.

#### Usuario
**Estereotipo**: Entidad  
**Responsabilidades**:
- Representar los datos persistentes del usuario.
- Encapsular la información de identidad y perfiles asociados.

## Flujo de colaboración

1.  **El Administrador** solicita consultar el detalle de un usuario desde el listado general (`USUARIOS_ABIERTO`).
2.  `ConsultarUsuarioView` solicita al `UsuarioController` la información detallada del usuario mediante su ID.
3.  `UsuarioController` delega la búsqueda a `UsuarioRepository`, que retorna una instancia de `Usuario`.
4.  `ConsultarUsuarioView` presenta la ficha completa al Administrador.
5.  **Navegación**: Desde esta vista, el sistema permite invocar la colaboración `editarUsuario()` para gestionar cambios.

## Conexión con disciplina de requisitos

- **Requisito funcional**: RF-ADM-02 (Consultar Usuario).
- **Caso de uso**: [Detallado Administrador](/RUP/00-requisitos/01-casos-de-uso/DetalladoCasosDeUso/Administrador/README.md#DetalladoConsultarUsuario).

---
