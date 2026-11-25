# Bitácora de Uso de Inteligencia Artificial Generativa (IAG)

* **Institución:** Universidad Tecnológica Nacional – Facultad Regional Resistencia (UTN FRRe)
* **Carrera y Cátedra:** Tecnicatura Universitaria en Programación – Programación II (Año 2026)
* **Comisión:** [ ] Comisión 3

### Integrantes:
* **Alumno/a:** *Luque Antonella Desiree *
* **Legajo N°:** * --- *
* **Alumno/a:** *Duarte Jose Esteban*
* **Legajo N°:** *26216*

* **Proyecto:** Trabajo Final Integrador – Sistema de Gestión de Concesionaria Multimarcas en Java
* **IAG Seleccionada:** OpenCode Desktop (conectado al LLM gratuito: DeepSeek V4.1 Flash)
* **Alternativas gratuitas contempladas:** otros modelos de acceso gratuito disponibles a través de OpenCode y Google Gemini mediante una API key gratuita de Google AI Studio (acceso estudiante).

---

## 1. Introducción y Metodología de Trabajo

La presente bitácora documenta el uso crítico, ético y planificado de herramientas de Inteligencia Artificial Generativa (IAG) durante el desarrollo del Trabajo Final Integrador (TFI). Siguiendo los lineamientos establecidos por la cátedra, se incorpora **OpenCode Desktop** —un entorno de agente de IAG multiplataforma con gestión de sesiones, pestañas y visualización de cambios (*diffs*)— bajo el rol de «copiloto socrático» y auditor de código, funcionando como un apoyo a la productividad y al estudio sin sustituir el criterio de diseño ni el dominio técnico del código fuente exigido para la defensa en el coloquio individual.

Para garantizar un aprendizaje progresivo y evitar la generación automática de código que exceda los contenidos de la asignatura, el flujo de trabajo se estructuró en las etapas incrementales del **Plan TFI** (modelo de dominio y excepciones; genéricos, persistencia y servicios; interfaz de consola). Cada sugerencia de OpenCode se audita contra las reglas de arquitectura en capas (`Diseño` vs. `Negocio`), los principios de Programación Orientada a Objetos y el temario de Programación II antes de incorporarla al repositorio.

---

## 2. Justificación Técnica de la Elección (OpenCode)

Para la resolución del proyecto se seleccionó **OpenCode** en su modalidad de acceso gratuito, contemplada por la guía de la cátedra, por sobre otras alternativas centradas exclusivamente en interfaces web o en extensiones propietarias de un IDE. La decisión se fundamenta en los siguientes criterios técnicos:

* **Entorno de escritorio orientado a la auditoría de código (OpenCode Desktop):** Permite aislar el desarrollo en sesiones y pestañas independientes por fase, inspeccionar cada modificación mediante vistas de *diffs* antes de aceptarla y monitorear el consumo de contexto en tiempo real, facilitando la revisión línea por línea del código generado.
* **Arquitectura open-source y flexibilidad de modelos LLM gratuitos:** Al ser un agente independiente del proveedor, permite conectar modelos de lenguaje de acceso gratuito admitidos por la cátedra (como Google Gemini o DeepSeek) manteniendo una interfaz uniforme y auditable. Para este proyecto se utiliza DeepSeek V4.1 Flash, y queda abierta la posibilidad de conectar una API key gratuita de Google AI Studio o de recurrir a otros modelos gratuitos habilitados por OpenCode según disponibilidad y necesidad.
* **Gobernanza estricta del contexto mediante `AGENTS.md` y `.opencode/`:** OpenCode facilita configurar instrucciones permanentes (`AGENTS.md`, `opencode.json`, `.opencode/instructions/`) y comandos propios (`/simular-coloquio`, `/auditar-rubrica`) para restringir al asistente exclusivamente al temario visto en Programación II (Java 21, POO y separación Diseño vs. Negocio). Así se evita que el modelo proponga dependencias externas, estructuras ajenas a la cursada o soluciones que rompan las capas.
* **Control explícito entre planificación y escritura (`plan` vs. `build`):** Sus modos de trabajo permiten validar primero el diseño de clases y las decisiones arquitectónicas antes de modificar archivos fuente, evitando la generación automática de código sin comprensión previa. El estudiante revisa y aprueba el plan, y recién después el agente escribe cambios acotados y verificables.

---

## 3. Documentación de Errores u Inexactitudes (Casos Reales)

*(Completar durante las Fases 1 a 5 con al menos un fallo real detectado en las respuestas de OpenCode: alucinaciones de código, violación de la separación Diseño vs. Negocio, errores en `equals()`/`hashCode()` o sesgos conceptuales).*

### Caso 1: *(Título breve del fallo detectado)*
* **Fase del Plan TFI:** *(Ej. Fase 1 - Configuración de contexto / Fase 2 - Dominio)*
* **Prompt / Contexto utilizado:** *(Transcribir brevemente qué se le pidió a OpenCode)*
* **Inexactitud o error propuesto por la IAG:** *(Describir o pegar el fragmento erróneo)*
* **Auditoría y resolución aplicada:** *(Explicar cómo lo detectaste y cómo lo corregiste según lo visto en clase)*


### Caso 2: *(Título breve del fallo detectado)*
* **Fase del Plan TFI:** *(Ej. Fase 1 - Configuración de contexto / Fase 2 - Dominio)*
* **Prompt / Contexto utilizado:** *(Transcribir brevemente qué se le pidió a OpenCode)*
* **Inexactitud o error propuesto por la IAG:** *(Describir o pegar el fragmento erróneo)*
* **Auditoría y resolución aplicada:** *(Explicar cómo lo detectaste y cómo lo corregiste según lo visto en clase)*

---

## 4. Valoración Crítica de la Experiencia de Codificación Asistida

*(Completar al finalizar la Fase 5 evaluando el impacto real de OpenCode en tu proceso de aprendizaje y desarrollo: ventajas, limitaciones encontradas y recomendaciones de uso).*