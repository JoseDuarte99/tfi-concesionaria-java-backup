---
description: Audita el proyecto contra los 14 ejes técnicos y la rúbrica oficial del TFI
---

# Auditar el TFI contra los 14 ejes y la rúbrica

Auditá el proyecto completo de Concesionaria Multimarcas: código bajo `src/`, persistencia, documentación y diagrama UML disponible. Usá como fuente los 14 ejes técnicos del enunciado y la rúbrica oficial. **No atribuyas funcionalidades que no puedas verificar**: respaldá cada hallazgo con archivo/clase/método y, cuando sea posible, línea. Si falta `src/`, UML u otro artefacto, declaralo como **No verificable**.

No modifiques archivos ni generes clases completas durante la auditoría. No presentes estimaciones como nota oficial; son una guía de estudio para preparar la defensa.

## A. Los 14 ejes técnicos obligatorios

Revisá y asigná estado **Cumple / Parcial / Falta / No verificable** con evidencia y acción recomendada:

1. Dominio y abstracción del escenario de concesionaria.
2. Arquitectura en capas: separación Diseño vs. Negocio.
3. Modelado POJO/JavaBean: estado privado, accesores y encapsulamiento.
4. Herencia y polimorfismo: `Vehiculo` abstracta; `Auto`, `Camioneta` y `Motocicleta`.
5. Interfaces de comportamiento realmente implementadas.
6. Excepciones estándar y excepciones propias del dominio.
7. Enums para tipos/estados de dominio, incluida la distinción nuevo 0 km / usado con kilometraje.
8. Interfaz de consola interactiva, controles de ingreso, validaciones y mensajes.
9. Wrappers y conversiones/parseo de entradas.
10. Colecciones `List`/`Map` y sobrescritura coherente de `equals()`, `hashCode()` y `toString()`.
11. Persistencia duradera del stock mediante archivos o BD SQL.
12. Clases, métodos o repositorios genéricos parametrizados.
13. Diagrama UML coherente con las clases, herencia e interfaces existentes.
14. JavaDoc y documentación técnica estructurada.

Señalá expresamente acoplamientos indebidos:

- `Scanner`, `System.out` o `System.err` en `negocio.modelo`, `negocio.servicio` o `negocio.persistencia`.
- SQL, rutas de archivo o formato de persistencia dentro de `diseno`.
- Reglas de negocio en la vista o en el repositorio.
- Vista ligada a una implementación concreta de almacenamiento.
- Dependencias cíclicas entre capas o clases de Dios.

## B. Ponderaciones oficiales (100%)

Calculá una estimación ponderada basada **solo en evidencia**:

| Criterio de rúbrica | Peso |
|---|---:|
| Persistencia de datos (archivos / BD SQL) | 15% |
| Arquitectura “Diseño vs. Negocio” | 10% |
| Herencia, clases abstractas y polimorfismo | 10% |
| Interfaces y tipos enumerativos (Enums) | 10% |
| Tratamiento de excepciones propias | 10% |
| Colecciones y sobrescritura de métodos | 10% |
| Uso de genéricos | 10% |
| Interfaz de consola y data-entry | 10% |
| Diagrama de clases UML (arquitectura) | 5% |
| Modelado POJO/JavaBean y Wrappers | 5% |
| Documentación y calidad de código (incluye JavaDoc) | 5% |

Estos 11 criterios ponderados suman 100%; no inventes pesos para subdivisiones de los 14 ejes. Evaluá JavaDoc dentro de documentación y señalá por separado el eje 14 para que no se pierda de vista.

## C. Formato del informe

1. **Resumen ejecutivo** con estimación ponderada y principales riesgos.
2. **Tabla de los 14 ejes**: estado, evidencia concreta (archivo/clase/método) y faltante.
3. **Tabla de los 11 criterios ponderados**: logro estimado, aporte al total y justificación. Marcá como no verificable lo que no puedas inspeccionar.
4. **Lista priorizada** de errores de arquitectura, riesgos de persistencia/validación y próximos pasos incrementales.
5. **Preguntas de defensa** sugeridas para los tres hallazgos más débiles.

```
## Resumen ejecutivo
- Estimación: <x>/100 (guía de estudio, no nota oficial)
- Riesgos principales: ...

## Ejes técnicos
| # | Eje | Estado | Evidencia | Acción |
|---|---|---|---|---|

## Rúbrica ponderada
| Criterio | Peso | Logro | Aporte | Justificación |
|---|---:|---:|---:|---|

## Acoplamientos y riesgos
...

## Próximos pasos
1. ...
```
