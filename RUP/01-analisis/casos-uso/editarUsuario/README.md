# editarUsuario() > Análisis


## Información del artefacto

- **Proyecto**: Centro de Gestión Universitaria (CGU)
- **Caso de uso**: editarUsuario()
- **Fase RUP**: Elaboración
- **Disciplina**: Análisis y Diseño
- **Versión**: 1.0
- **Fecha**: 2026-05-26
- **Autor**: Gemini CLI

## Propósito

Análisis del caso de uso `editarUsuario()` mediante el patrón MVC (BCE), identificando las clases de análisis y sus interacciones para la modificación de datos de un usuario existente.

## Diagramas de Análisis

### Colaboración (BCE)

<div align=center>

|![Análisis: editarUsuario()](/images/01-analisis/casos-uso/editarUsuario/editarUsuario-analisis.svg)|
|-|
|Código fuente: [colaboracion.puml](/modelosUML/01-analisis/casos-uso/editarUsuario/colaboracion.puml)|

</div>

## Clases de análisis identificadas

### Clases de vista (Boundary)

#### EditarUsuarioView
**Estereotipo**: Vista (Boundary)  
**Responsabilidades**:
- Presentar el formulario de edición con los datos actuales del usuario.
- Capturar las modificaciones ingresadas por el administrador.
- Validar formalmente los cambios.
- Delegar la actualización al controlador.

### Clases de control

#### UsuarioController
**Estereotipo**: Control  
**Responsabilidades**:
- Coordinar el flujo de actualización de datos.
- Validar reglas de negocio (ej. asegurar que el nuevo username no colisione con otros).
- Orquestar la persistencia de los cambios.

### Clases de entidad (Entity)

#### UsuarioRepository
**Estereotipo**: Entidad  
**Responsabilidades**:
- Implementar la lógica de actualización (update) en el almacenamiento.
- Proveer métodos de verificación de integridad.

#### Usuario
**Estereotipo**: Entidad  
**Responsabilidades**:
- Mantener su propio estado y permitir la actualización de sus atributos internos.
- Validar la consistencia de los nuevos datos asignados.

## Flujo de colaboración

1.  **El Administrador** inicia la edición desde la ficha del usuario (`USUARIO_ABIERTO`).
2.  `EditarUsuarioView` carga los datos actuales y solicita a `UsuarioController` validar los cambios propuestos (específicamente si el username cambia).
3.  `UsuarioController` verifica la disponibilidad del username en `UsuarioRepository`.
4.  Tras la confirmación del administrador, `UsuarioController` solicita a la entidad `Usuario` actualizar sus datos y ordena a `UsuarioRepository` persistir el objeto modificado.
5.  **Retorno (C→U)**: Una vez guardados los cambios, el sistema redirige automáticamente a `consultarUsuario()` para visualizar la ficha actualizada.

## Conexión con disciplina de requisitos

- **Requisito funcional**: RF-ADM-03 (Editar Usuario).
- **Caso de uso**: [Detallado Administrador](/RUP/00-requisitos/01-casos-de-uso/DetalladoCasosDeUso/Administrador/README.md#DetalladoEditarUsuario).

---
