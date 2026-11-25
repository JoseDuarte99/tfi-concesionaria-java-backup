# Reglas de Java para el TFI Concesionaria Multimarcas

Estas reglas se aplican a todo archivo `.java` del proyecto. Complementan `AGENTS.md` y no las reemplazan.

## 1. Versión y dependencias

- Versión objetivo: **JDK 21**. No uses features posteriores ni preview.
- Solo APIs del JDK: `java.lang`, `java.util`, `java.io`, `java.nio.file` y, si se elige JDBC, `java.sql`.
- **Prohibido** agregar Lombok, Jackson, Gson, Spring, Hibernate, HikariCP, Maven/Gradle u otra dependencia de terceros sin autorización expresa.
- No uses `record` para sustituir el POJO/JavaBean exigido, ni streams funcionales como estilo dominante.

## 2. Nombres y convenciones

- Identificadores en **español**, descriptivos y consistentes con el dominio.
- `PascalCase` para clases, interfaces y enums.
- `camelCase` para métodos, variables y parámetros.
- Paquetes en minúsculas: `diseno`, `negocio.modelo`, `negocio.servicio`, `negocio.persistencia`.
- Constantes y valores de `enum` en `UPPER_SNAKE_CASE`.
- Nombres de la API de Java y del enunciado se conservan tal cual (`equals`, `hashCode`, `Vehiculo`, `Auto`, etc.).

## 3. POJO / JavaBean y encapsulamiento

- Atributos `private`; nada de estado mutable público.
- Constructores coherentes que validen invariantes desde el inicio.
- Getters y setters solo cuando aportan; los setters validan y preservan el estado válido.
- No agregues setters a valores inmutables por automatismo.
- No expongas colecciones mutables internas sin protección: devolvé copia, vista no modificable o métodos acotados.
- La identidad y las reglas del dominio viven en el modelo o servicio, no en la vista.

## 4. `equals()`, `hashCode()` y `toString()`

- Sobrescribí `equals` con la firma `public boolean equals(Object obj)` y `@Override`.
- Respetá el contrato: reflexividad, simetría, transitividad, consistencia y comparación con `null`.
- `hashCode()` debe usar **los mismos campos de igualdad** que `equals()`.
- Evitá campos mutables en igualdad si el objeto se usa como clave de `Map` o miembro de `Set`.
- `toString()` debe ser legible para diagnóstico; no lo uses como formato de persistencia ni incluyas datos sensibles.

## 5. Wrappers, parseo y validación

- Convertí entradas con clases Wrapper: `Integer.parseInt`, `Double.parseDouble`, `Boolean.parseBoolean`, `valueOf`, etc.
- Validá formato y rango; no uses valores por defecto silenciosos ante entradas inválidas.
- Traducí fallos de parseo (`NumberFormatException`) a mensajes de Diseño o a excepciones de dominio, según la capa.
- Los campos del dominio conservan su tipo natural; no envuelvas todos los primitivos artificialmente.

## 6. Excepciones

- Usá excepciones estándar cuando correspondan y **excepciones propias** para errores de dominio recuperables.
- Las excepciones propias heredan de `Exception` (checked) salvo justificación; documentá constructores y mensajes.
- Validá en modelo/servicio y propagá hasta Diseño, que decide cómo informar.
- Cerrá recursos con try-with-resources o `finally`.
- **Prohibido** `catch` vacío, `catch (Exception e)` genérico sin tratamiento, o mensajes de éxito falsos.

## 7. Colecciones y genéricos

- Declará variables mediante interfaces: `List<Vehiculo>`, `Map<String, Vehiculo>`.
- Tipá explícitamente; **sin raw types** ni casts no comprobados.
- Usá `List`/`ArrayList` y `Map`/`HashMap` como mínimo. `Set`, `Queue`, `Iterator`, `Comparable`/`Comparator` solo si aportan al requisito.
- Implementá contratos o métodos genéricos propios cuando el diseño lo justifique (por ejemplo un repositorio parametrizado).
- Documentá la clave de identidad usada en `Map`.

## 8. Arquitectura y capas

- `diseno`: menú, captura, parseo inicial, mensajes. **Único lugar** con `Scanner`, `System.out` y `System.err`.
- `negocio.modelo`: entidades, enums, interfaces y excepciones de dominio. Sin consola ni persistencia.
- `negocio.servicio`: casos de uso, reglas, coordinación y colecciones. Sin consola ni detalles de archivo/SQL.
- `negocio.persistencia`: lectura/escritura de archivos o JDBC. Sin consola ni reglas de negocio.
- Dependencias: `diseno → negocio.servicio → negocio.persistencia`; el modelo no depende de las otras capas.
- **Prohibido** `Scanner`, `System.out` o `System.err` en `negocio.*`, y SQL o rutas de archivo en `diseno`.

## 9. Persistencia

- Preferida: archivos con `java.io` (texto con buffer, binario o serialización).
- Admitida: NIO.2 (`Files`, `Path`).
- Alternativa: JDBC/DAO con `PreparedStatement`, cierre de recursos y transacciones; requiere autorización para el driver.
- Rutas relativas al proyecto o configurables; nunca rutas absolutas personales ni credenciales en el repositorio.
- Informá errores de E/S con excepción y probá guardar → cerrar → reabrir → cargar.

## 10. JavaDoc y documentación

- Documentá clases, interfaces, enums, excepciones y métodos públicos.
- Usá `@param`, `@return` y `@throws` cuando corresponda.
- Explicá propósito, invariantes y decisiones no obvias; no repitas literalmente el código.
- Mantené el UML y la documentación alineados con las clases, herencia, interfaces y relaciones reales.

## 11. Calidad

- Un método, una responsabilidad; evitá clases de Dios y duplicación innecesaria.
- Preferí composición sobre herencia cuando la relación no sea “es un”.
- No dejes código comentado, `TODO` sin dueño ni imports sin usar.
- Todo cambio debe compilar con JDK 21 y poder explicarse en la defensa.
