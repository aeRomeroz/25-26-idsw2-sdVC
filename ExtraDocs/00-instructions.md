# Estándares de Modelado UML-RUP (BCE)

Este artefacto define las restricciones sintácticas, semánticas y estéticas obligatorias para la generación de diagramas de análisis bajo el patrón **Boundary-Control-Entity (BCE / MVC)**.

---

## 🛑 Reglas de Diseño Obligatorias

### 1. Prohibición de Términos Genéricos
Queda estrictamente **PROHIBIDO** el uso de palabras abstractas como `datos`, `info` o `información` en las firmas de los métodos y mensajes de las flechas. 
* Se deben explicitar siempre los atributos reales extraídos del Modelo de Dominio.
* *Ejemplo correcto (Usuarios):* `validarDatosMínimos(username, password, rol)`
* *Ejemplo correcto (Profesores):* `crearProfesor(codigo, nombres, apellidos)`

### 2. Estereotipos de Inclusión Obligatorios
Toda relación de dependencia o flujo de navegación representado mediante líneas punteadas (`..>`) dirigida hacia otra colaboración externa debe incluir de forma explícita el estereotipo `<<include>>`.
* *Sintaxis en PlantUML:* `Vista ..> Colaboracion : <<include>> metodo()`

### 3. Consistencia en el Paso de Parámetros (Capas BCE)
Se debe respetar el desacoplamiento estricto de los flujos de datos según el nivel de abstracción:
* **De Vista a Controlador:** Se envían los campos primitivos sueltos capturados por la interfaz (ej. `guardarCambios(username, password, rol)`).
* **De Controlador a Repositorio (Persistencia):** Se debe enviar el objeto de la entidad completamente instanciado y empaquetado (ej. `crear(usuario)` o `actualizar(usuario)`).

### 4. Estándar Estético y Paleta de Colores
Para mantener la homogeneidad visual en el repositorio, todos los diagramas de análisis deben utilizar elementos tipificados como `rectangle` respetando los siguientes códigos hexadecimales:

| Componente | Rol Arquitectónico | Color Hex | Visualización |
| :--- | :--- | :--- | :--- |
| **Boundary** | Clase de Vista / Interfaz | `#629EF9` | ![#629EF9](https://via.placeholder.com/15/629EF9/000000?text=+) Azul |
| **Control** | Clase de Control / Lógica | `#b5bd68` | ![#b5bd68](https://via.placeholder.com/15/b5bd68/000000?text=+) Verde oliva |
| **Entity** | Clase de Entidad / Persistencia | `#F2AC4E` | ![#F2AC4E](https://via.placeholder.com/15/F2AC4E/000000?text=+) Naranja |

> 💡 **Nota de Configuración:** Es mandatorio incluir la directiva `skinparam linetype polyline` al inicio de cada archivo fuente `.puml` para asegurar el correcto ruteo de las líneas de comunicación.