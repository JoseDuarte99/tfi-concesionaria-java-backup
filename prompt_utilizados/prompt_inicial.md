Relevá de forma exhaustiva todo el contenido local de la carpeta `material_catedra/` (apuntes de clase y ejemplos de código), la subcarpeta `material_catedra/consignas_tfi/` (la guía obligatoria de uso de IAG y el enunciado del Trabajo Final Integrador) y el curso completo publicado en `https://facundouferer.ar/cursos/java/`.

Para el sitio web, utilizá tu herramienta `webfetch` primero sobre `https://facundouferer.ar/cursos/java/` para extraer el índice completo de unidades/lecciones y luego ingresá a cada enlace del temario de Java para relevar su contenido.

A partir de ese análisis, identificá con precisión:
- La versión de Java/JDK utilizada en la cátedra, tomando **Java / JDK 21** como entorno objetivo de compilación, pero restringiendo la sintaxis y APIs estrictamente a los temas enseñados en clase.
- Las estructuras de datos, colecciones, manejo de excepciones y conceptos de POO vistos en el curso.
- El mecanismo de persistencia enseñado (Archivos I/O binarios/texto o JDBC con SQL) y las librerías permitidas, prohibiendo explícitamente librerías externas (como Lombok, Jackson o Gson) que no formen parte del material de la cátedra.

Con base en ese relevamiento, los 14 ejes técnicos y la rúbrica oficial del TFI, creá los siguientes archivos en el proyecto:

1. `AGENTS.md` (en la raíz del proyecto):
   - **Rol pedagógico:** Actuá como un «copiloto socrático» de estudio. Nunca generes clases completas de una sola vez sin explicar primero el diseño y qué concepto de la cátedra se aplica en cada bloque.
   - **Desarrollo incremental:** Respetá el avance por etapas (1. Modelo de dominio y excepciones; 2. Genéricos, persistencia y capa de servicio; 3. Interfaz de consola). No generes código de capas posteriores si no fueron solicitadas.
   - **Inventario técnico permitido vs. prohibido:** Listá las herramientas, clases de Java 21 y patrones habilitados según el material relevado, prohibiendo recursos fuera de programa.
   - **Arquitectura en capas obligatoria:** Separación estricta entre `Diseño` (paquete de vista/consola) y `Negocio` (paquetes de modelo, servicio y persistencia). Prohibición absoluta de usar `Scanner` o `System.out` fuera de la capa de vista/consola.
   - **Reglas del dominio (Concesionaria Multimarcas):** Clase abstracta `Vehiculo` con subclases `Auto`, `Camioneta` y `Motocicleta`; atributos obligatorios (Marca, Modelo, Año, Color, Tipo de Carrocería / Estilo de Motocicleta y valores comerciales); distinción entre unidades Nuevas (0 Km) y Usadas (con kilometraje recorrido); uso obligatorio de `Enums`, `Interfaces`, `Excepciones Propias`, `Generics`, `Wrappers`, `Colecciones` (`List`/`Map`), persistencia y `JavaDoc`.

2. `opencode.json` (en la raíz del proyecto):
   - Configurá el esquema `"$schema": "https://opencode.ai/config.json"` y registrá `"instructions": [".opencode/instructions/reglas-java.md"]` para que OpenCode cargue las reglas técnicas automáticamente. (Si el archivo ya existe, agregá la clave `instructions` sin sobrescribir la configuración existente).

3. `.opencode/instructions/reglas-java.md`:
   - Convenciones de nombrado en español (clases en PascalCase, métodos/variables en camelCase, constantes y Enums en UPPER_SNAKE_CASE).
   - Encapsulamiento POJO / JavaBean (atributos privados, constructores, getters/setters).
   - Sobrescritura obligatoria y coherente de `equals()`, `hashCode()` y `toString()` en las entidades del dominio.
   - Uso de clases Wrapper (`Integer`, `Double`, etc.) para conversiones/parseo y validación de reglas de negocio lanzando excepciones personalizadas.
   - Documentación interna mediante comentarios `JavaDoc` (`@param`, `@return`, `@throws`) en clases, interfaces y métodos clave.

4. `.opencode/commands/simular-coloquio.md`:
   - Incluí cabecera YAML válida con `description: Simula preguntas de defensa oral y un ejercicio de live coding sobre el código del TFI`.
   - Instrucción: Analizá las clases actuales dentro de `src/` y formulame 3 preguntas técnicas de defensa oral sobre decisiones de diseño, POO y arquitectura en capas, seguidas de 1 consigna práctica de modificación en vivo (*live coding*) resoluble en menos de 5 minutos, sin darme la solución hasta que yo responda.

5. `.opencode/commands/auditar-rubrica.md`:
   - Incluí cabecera YAML válida con `description: Audita el proyecto contra los 14 ejes técnicos y la rúbrica oficial del TFI`.
   - Instrucción: Revisá todo el código fuente en `src/` y evaluá el cumplimiento contra los 14 ejes técnicos y las ponderaciones oficiales (Persistencia 15%, Arquitectura Diseño vs. Negocio 10%, Herencia/Abstractas/Polimorfismo 10%, Interfaces/Enums 10%, Excepciones Propias 10%, Colecciones/Object 10%, Genéricos 10%, Consola/Data-Entry 10%, Diagrama UML 5%, POJO/Wrappers 5%, Documentación/JavaDoc 5%), listando qué está completo, qué falta y si existe algún acoplamiento indebido entre capas.
