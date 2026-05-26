<div align=right>
 
|[![](https://img.shields.io/badge/-Inicio-FFF?style=flat&logo=Emlakjet&logoColor=black)](../../../README.md) [![](https://img.shields.io/badge/-RUP-FFF?style=flat&logo=Elsevier&logoColor=black)](../../README.md) [![](https://img.shields.io/badge/-Modelo_del_dominio-FFF?style=flat&logo=freedesktop.org&logoColor=black)](../../00-requisitos/00-modelo-de-dominio/README.MD) [![](https://img.shields.io/badge/-Actores_&_Casos_de_Uso-FFF?style=flat&logo=crewunited&logoColor=black)](../../00-requisitos/01-casos-de-uso/README.md) [![](https://img.shields.io/badge/-Análisis-FFF?style=flat&logo=multisim&logoColor=black)](README.md)
|-:
|[![](https://img.shields.io/badge/-Log_de_conversación-FFF?style=flat&logo=gnometerminal&logoColor=black)](../../../conversation-log.md)

</div>

# Análisis de Casos de Uso

Esta carpeta contiene el análisis MVC (Model-View-Controller) de cada caso de uso especificado para el Centro de Gestión Universitaria (CGU), siguiendo la disciplina de Análisis y Diseño de RUP.

## Casos de uso analizados

### Gestión de Usuarios (Seguridad)
- **crearUsuario()**: Análisis de creación de nuevos usuarios en el sistema.
- **consultarUsuario()**: Análisis de visualización de perfiles de usuario.
- **editarUsuario()**: Análisis de modificación de datos de usuario.

### Gestión Académica
- **consultarListaAlumnos()**: Análisis de visualización de listados por curso.
- **importarMatricula()**: Análisis del proceso de carga masiva.

### Gestión de Dispensas
- **crearSolicitudDispensa()**: Análisis del flujo de solicitud por parte del alumno.
- **editarSolicitudDispensa()**: Análisis de la gestión de solicitudes.

## Metodología de análisis

- **Patrón MVC**: Aplicación sistemática de clases Boundary, Control y Entity.
- **Estereotipos BCE**:
    - **Boundary (Vista)**: `#629EF9` - Interfaz con el actor.
    - **Control (Controlador)**: `#b5bd68` - Lógica de coordinación.
    - **Entity (Entidad)**: `#F2AC4E` - Datos y persistencia.
- **Trazabilidad**: Mapeo directo desde los requisitos de la fase 00.

---
[![](https://img.shields.io/badge/-Regresar_a_Requisitos-0D47A1?style=flat&logo=arrow-left&logoColor=white)](/RUP/00-requisitos/)
