# abrirUsuarios() > Análisis


## Información del artefacto

- **Proyecto**: Centro de Gestión Universitaria (CGU)
- **Caso de uso**: abrirUsuarios()
- **Fase RUP**: Elaboración
- **Disciplina**: Análisis y Diseño
- **Versión**: 1.0
- **Fecha**: 2026-05-26
- **Autor**: Gemini CLI

## Propósito

Análisis de colaboración del caso de uso `abrirUsuarios()` mediante el patrón MVC (BCE), identificando las clases de análisis y sus interacciones para el listado y búsqueda de usuarios en el sistema.

## Diagramas de Análisis

### Colaboración (BCE)

<div align=center>

|![Análisis: abrirUsuarios()](/images/01-analisis/casos-uso/abrirUsuarios/abrirUsuarios-analisis.svg)|
|-|
|Código fuente: [colaboracion.puml](/modelosUML/01-analisis/casos-uso/abrirUsuarios/colaboracion.puml)|

</div>

## Clases de análisis identificadas

### Clases de vista (Boundary)

#### ListarUsuariosView
**Estereotipo**: Vista (Boundary)  
**Responsabilidades**:
- Presentar la interfaz de listado de usuarios.
- Capturar criterios de búsqueda/filtrado.
- Mostrar la lista de usuarios obtenida del controlador.
- Facilitar la navegación hacia la creación o consulta de un usuario.

### Clases de control

#### UsuarioController
**Estereotipo**: Control  
**Responsabilidades**:
- Coordinar la obtención de la lista de usuarios.
- Manejar la lógica de filtrado por criterios.
- Servir como intermediario con el repositorio.

### Clases de entidad (Entity)

#### UsuarioRepository
**Estereotipo**: Entidad  
**Responsabilidades**:
- Proveer acceso a la colección persistente de usuarios.
- Implementar métodos de búsqueda y recuperación masiva.

#### Usuario
**Estereotipo**: Entidad  
**Responsabilidades**:
- Representar los datos básicos del usuario para su visualización en el listado.

## Flujo de colaboración

1.  **El Administrador** solicita "Abrir Usuarios" desde el menú principal (`SISTEMA_DISPONIBLE`).
2.  `ListarUsuariosView` solicita al `UsuarioController` la lista completa de usuarios.
3.  `UsuarioController` delega la obtención a `UsuarioRepository`.
4.  Si el Administrador ingresa un criterio, `ListarUsuariosView` solicita filtrar al `UsuarioController`, quien a su vez consulta al repositorio.
5.  **Navegación**: La vista permite invocar las colaboraciones `crearUsuario()` o `consultarUsuario(id)` según la acción del usuario.

## Conexión con disciplina de requisitos

- **Caso de uso**: [Detallado Administrador](/RUP/00-requisitos/01-casos-de-uso/DetalladoCasosDeUso/Administrador/README.md).
- **Contexto**: Transición `SISTEMA_DISPONIBLE` → `USUARIOS_ABIERTO`.

---
