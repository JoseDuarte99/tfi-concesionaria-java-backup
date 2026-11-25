Creá (o sobrescribí por completo si ya existe) el archivo `bitacora_de_uso_de_iag_tfi.md` en la raíz del proyecto, redactado en español formal académico y cumpliendo con todos los apartados exigidos en `material_catedra/consignas_tfi/Guia_Uso_IAG_y_Defensa_Coloquio_TFI.pdf`.

El documento debe reflejar fielmente que el proyecto se desarrolla con **OpenCode Desktop** conectado al modelo gratuito **DeepSeek V4.1 Flash**, bajo una metodología incremental de 6 fases («Plan TFI») y trabajo colaborativo en GitHub.

Estructurá el archivo exactamente con las siguientes secciones:

### Encabezado / Carátula
Incluí una ficha con los siguientes campos:
- **Institución:** Universidad Tecnológica Nacional – Facultad Regional Resistencia (UTN FRRe)
- **Carrera y Cátedra:** Tecnicatura Universitaria en Programación – Programación II (Año 2026)
- **Comisión:** [ ] Comisión 2 / [ ] Comisión 3 *(dejar marcado o listo para completar)*
- **Integrantes y Legajos:** *(Tabla o lista con 3 filas para completar Nombre, Apellido y Legajo N° de cada integrante del grupo)*
- **Proyecto:** Trabajo Final Integrador – Sistema de Gestión de Concesionaria Multimarcas en Java
- **IAG Seleccionada:** OpenCode Desktop (conectado al LLM gratuito: DeepSeek V4.1 Flash)

### 1. Introducción y Metodología de Trabajo
Redactá dos párrafos claros explicando:
- Que la bitácora documenta el uso crítico, ético y planificado de Inteligencia Artificial Generativa (IAG) durante el desarrollo del TFI, incorporando **OpenCode Desktop** —un entorno de agente multiplataforma con gestión de sesiones, pestañas y visualización de cambios (*diffs*)— bajo el rol de «copiloto socrático» y auditor de código, sin sustituir el criterio de diseño ni el dominio técnico exigido en el coloquio individual.
- Que el desarrollo se organizó en etapas incrementales («Plan TFI» de 6 fases) sobre un repositorio compartido en GitHub, utilizando archivos de gobernanza de contexto (`AGENTS.md`, `opencode.json` y `.opencode/`) para que el asistente respete estrictamente los contenidos enseñados en la cátedra y la separación entre capas de Diseño y Negocio.

### 2. Justificación Técnica de la Elección
Desarrollá una fundamentación técnica estructurada en cuatro puntos detallados sobre por qué se eligió **OpenCode Desktop + DeepSeek V4.1 Flash**:
- **Entorno de escritorio orientado a la auditoría de código (OpenCode Desktop):** Permite aislar el desarrollo en sesiones y pestañas independientes por fase, inspeccionar cada modificación mediante vistas de *diffs* línea por línea antes de aceptarla y monitorear el consumo de contexto en tiempo real.
- **Gobernanza estricta del contexto y alineación con el temario:** Mediante `AGENTS.md`, `.opencode/instructions/reglas-java.md` y comandos personalizados (`/simular-coloquio`, `/auditar-rubrica`), se restringe al modelo a la sintaxis de Java 21 y a los conceptos vistos en clase, evitando librerías externas o acoplamientos indebidos entre vista y lógica de negocio.
- **Control explícito entre planificación y ejecución (`plan` vs. `build`):** Sus modos de trabajo permiten validar primero el diseño de clases y las decisiones arquitectónicas antes de autorizar la escritura de archivos fuente, asegurando la comprensión previa de cada bloque.
- **Uso de LLM gratuito avalado por la cátedra (`DeepSeek V4.1 Flash`):** Cumple con el requisito obligatorio de utilizar un modelo de acceso gratuito, destacando por su precisión en el seguimiento de instrucciones estructuradas, lectura de documentación técnica y generación de código Java limpio.

### 3. Documentación de Errores u Inexactitudes (Casos Reales)
Incluí una breve nota introductoria indicando que cada integrante debe registrar al menos un fallo o inconsistencia real detectada durante el desarrollo, seguida de **3 plantillas numeradas (Caso 1, Caso 2 y Caso 3)** con los siguientes campos listos para completar:
- **Integrante que detectó el fallo:** *(Completar)*
- **Fecha y Fase del Plan TFI:** *(Completar)*
- **Categoría del error:** *(Seleccionar: Alucinación de código / Incompatibilidad arquitectónica Diseño vs. Negocio / Error sintáctico o lógico en `equals()`, `hashCode()` o conversiones / Sesgo conceptual en POO o Genéricos)*
- **Prompt utilizado:** *(Pegar instrucción enviada a OpenCode)*
- **Salida errónea o comportamiento detectado:** *(Describir o pegar el fragmento generado por la IAG)*
- **Auditoría y solución aplicada:** *(Explicar cómo se identificó el error y cómo se corrigió)*

### 4. Valoración Crítica de la Experiencia de Codificación Asistida
Creá una plantilla estructurada para completar al finalizar el proyecto, dividida en tres subapartados con preguntas guía breves:
- **Impacto en el proceso de aprendizaje y preparación para el coloquio:** *(Reflexión sobre cómo el enfoque socrático y la revisión mediante diffs contribuyeron a comprender todo el código fuente).*
- **Ventajas identificadas (Pros):** *(Completar con puntos concretos de productividad, detección de errores y orden arquitectónico).*
- **Limitaciones y riesgos detectados (Contras):** *(Completar con dificultades de contexto, tendencia a sobre-ingeniería o errores que requirieron intervención manual).*