# Web Engineering Starter — Engineering Constitution

**Versión:** 1.0.0  
**Estado:** Ratificada  
**Aplicación:** Todos los proyectos derivados de Web Engineering Starter

---

## 1. Propósito

Esta constitución establece los principios técnicos y de ingeniería que deben guiar el diseño, desarrollo, revisión, despliegue y mantenimiento de los proyectos creados a partir de Web Engineering Starter.

Su objetivo no es eliminar completamente la deuda técnica, sino prevenir deuda accidental, hacer visibles las decisiones técnicas y mantener una base de software comprensible, segura, mantenible y preparada para evolucionar.

---

# 2. Principios fundamentales

## I. Simplicidad antes que complejidad

La solución técnicamente más sencilla que satisfaga los requisitos actuales debe ser preferida frente a alternativas más complejas.

No se incorporarán arquitecturas, patrones, frameworks, servicios o dependencias únicamente por tendencias o por una eventual necesidad futura.

La complejidad debe estar justificada por un problema concreto.

---

## II. Arquitectura proporcional al problema

Todo proyecto debe clasificarse antes de seleccionar su arquitectura.

### Perfil Static

Adecuado para:

* sitios corporativos;  
* portfolios;  
* landing pages;  
* sitios informativos;  
* sitios de artistas;  
* documentación.

Preferencias:

* generación estática;  
* mínimo JavaScript;  
* despliegue simple;  
* alta performance;  
* SEO.

### Perfil Web Application

Adecuado para:

* autenticación;  
* paneles administrativos;  
* persistencia;  
* lógica de negocio;  
* múltiples roles;  
* integraciones.

Debe incorporar separación explícita entre responsabilidades y módulos.

### Perfil Sensitive

Adecuado para sistemas que procesen:

* datos personales;  
* información clínica;  
* información financiera;  
* información confidencial;  
* información regulada.

Además de las reglas anteriores debe implementar controles reforzados de seguridad, auditoría, respaldo, recuperación, privacidad y trazabilidad.

---

## III. Monolito modular como arquitectura inicial

Las aplicaciones comenzarán preferentemente como monolitos modulares.

Los límites entre dominios deben ser claros y explícitos.

La extracción de microservicios solamente se justificará cuando existan razones técnicas u operacionales demostrables.

No se adoptará arquitectura distribuida anticipadamente.

---

## IV. Specification before implementation

Una funcionalidad relevante debe describirse antes de implementarse.

La especificación debe indicar al menos:

* problema;  
* objetivo;  
* usuario;  
* comportamiento esperado;  
* criterios de aceptación;  
* restricciones relevantes.

El código constituye la implementación de una decisión previamente descrita.

---

## V. Separación de responsabilidades

Cada módulo debe tener una responsabilidad claramente identificable.

Se debe minimizar:

* acoplamiento;  
* duplicación;  
* dependencias circulares;  
* conocimiento innecesario entre módulos.

Las abstracciones deben aparecer cuando exista una necesidad real y no anticipadamente.

---

## VI. Uso justificado de patrones

Los patrones de diseño son herramientas y no requisitos arquitectónicos.

Un patrón solamente debe introducirse cuando:

1. resuelva un problema identificable;  
2. reduzca complejidad o acoplamiento;  
3. facilite pruebas o evolución;  
4. su coste sea inferior al problema que resuelve.

No se deben introducir patrones únicamente para aumentar artificialmente la estructura del proyecto.

---

## VII. Seguridad por defecto

La seguridad debe considerarse durante el diseño y no después de la implementación.

Todo proyecto debe considerar cuando corresponda:

* autenticación;  
* autorización;  
* validación de entrada;  
* codificación de salida;  
* gestión de secretos;  
* HTTPS;  
* dependencias vulnerables;  
* protección contra abuso;  
* carga de archivos;  
* logging seguro;  
* privacidad.

Las credenciales nunca deben almacenarse dentro del repositorio.

---

## VIII. Privacidad y minimización de datos

Los proyectos que procesen datos personales deben:

* recopilar únicamente información necesaria;  
* definir para qué se utiliza;  
* limitar quién puede acceder;  
* evitar exposición innecesaria;  
* definir políticas de retención;  
* proteger respaldos;  
* mantener trazabilidad cuando corresponda.

La privacidad debe incorporarse desde el diseño.

---

## IX. Calidad verificable

La calidad del software no debe depender únicamente de revisión manual.

Siempre que la tecnología lo permita deben automatizarse:

* build;  
* lint;  
* type checking;  
* tests;  
* dependency audit;  
* secret scanning;  
* security checks.

Una modificación que rompa estos controles no debe integrarse a la rama principal.

---

## X. Testing basado en riesgo

El objetivo de las pruebas no será alcanzar arbitrariamente un porcentaje específico de cobertura.

Las pruebas deben concentrarse principalmente en:

* reglas de negocio;  
* validaciones;  
* autorización;  
* persistencia;  
* transformaciones de datos;  
* flujos críticos;  
* regresiones conocidas.

Se utilizarán diferentes niveles cuando correspondan:

* unitarios;  
* integración;  
* componentes;  
* end-to-end.

---

## XI. Accesibilidad desde el diseño

La accesibilidad no debe ser una corrección posterior.

Las interfaces deben considerar desde su diseño:

* navegación mediante teclado;  
* estructura semántica;  
* etiquetas;  
* contraste;  
* estados de foco;  
* mensajes de error;  
* tecnologías asistivas.

WCAG debe utilizarse como referencia cuando corresponda.

---

## XII. Performance con presupuesto

Todo proyecto web debe definir objetivos de rendimiento proporcionales a su uso.

Debe evitarse especialmente:

* JavaScript innecesario;  
* imágenes sin optimización;  
* fuentes excesivas;  
* scripts externos injustificados;  
* solicitudes bloqueantes;  
* carga anticipada innecesaria.

Las optimizaciones complejas deben basarse en mediciones.

---

## XIII. Dependencias mínimas

Antes de instalar una nueva dependencia debe evaluarse:

1. qué problema resuelve;  
2. si el proyecto ya posee una solución;  
3. mantenimiento del paquete;  
4. seguridad;  
5. tamaño e impacto;  
6. posibilidad razonable de implementarlo internamente.

Una dependencia no debe instalarse por conveniencia si introduce más coste que valor.

---

## XIV. Decisiones arquitectónicas documentadas

Toda decisión que afecte significativamente la arquitectura debe registrarse mediante un Architecture Decision Record (ADR).

Los ADR deben registrar:

* contexto;  
* alternativas consideradas;  
* decisión;  
* razones;  
* consecuencias.

Los ADR aceptados no deben modificarse retroactivamente.

Una nueva decisión debe generar un nuevo ADR que reemplace al anterior.

---

## XV. Observabilidad proporcional

Las aplicaciones deben proporcionar suficiente información para poder diagnosticar fallos.

Dependiendo de su perfil podrán utilizar:

* logs;  
* errores estructurados;  
* métricas;  
* health checks;  
* performance monitoring;  
* analytics;  
* audit trails.

Los logs nunca deben exponer secretos o datos personales innecesarios.

---

# 3. Gestión de deuda técnica

La existencia de deuda técnica debe hacerse explícita.

Cuando una solución temporal sea adoptada debe documentarse indicando:

* problema;  
* causa;  
* riesgo;  
* impacto;  
* solución recomendada;  
* prioridad.

No deben utilizarse comentarios `TODO` permanentes como sustituto de una gestión explícita.

La deuda técnica relevante deberá registrarse como issue.

---

# 4. Definition of Done

Una funcionalidad solamente podrá considerarse terminada cuando corresponda:

* cumple los criterios de aceptación;  
* el proyecto compila correctamente;  
* lint y type checking pasan;  
* las pruebas requeridas pasan;  
* no introduce vulnerabilidades conocidas relevantes;  
* no expone secretos;  
* maneja adecuadamente errores previsibles;  
* mantiene accesibilidad;  
* mantiene comportamiento responsive;  
* actualiza documentación cuando corresponde;  
* no contiene código temporal;  
* respeta la arquitectura existente;  
* no introduce deuda técnica no documentada.

---

# 5. Regla para desviaciones

Las reglas de esta constitución pueden ser excepcionalmente omitidas cuando exista una razón técnica válida.

La desviación debe documentarse indicando:

* regla afectada;  
* contexto;  
* razón;  
* consecuencias;  
* eventual plan de corrección.

La urgencia por sí sola no elimina la obligación de documentar la decisión.

---

# 6. Prioridad de decisiones

Cuando exista conflicto entre alternativas técnicas se utilizará, en este orden general:

1. seguridad;  
2. corrección;  
3. mantenibilidad;  
4. simplicidad;  
5. experiencia de usuario;  
6. performance;  
7. escalabilidad futura.

El orden puede variar según los requisitos del proyecto, pero cualquier cambio significativo deberá poder justificarse.

---

# 7. Principio final

El objetivo del proyecto no es construir la arquitectura más sofisticada.

El objetivo es construir la arquitectura más sencilla que permita mantener correctamente el sistema actual y evolucionarlo de forma controlada.

**Build for today's requirements while preserving reasonable paths for tomorrow's changes.**


---

## Governance

Esta constitución es la fuente de autoridad para los principios de ingeniería de los proyectos derivados de Web Engineering Starter.

### Cumplimiento

Las especificaciones, planes de implementación, tareas, revisiones y Pull Requests deben respetar estos principios de forma proporcional al perfil y riesgo del proyecto.

Las reglas específicas de un proyecto pueden ser más estrictas, pero no deben contradecir esta constitución sin una desviación documentada.

### Modificaciones

Toda modificación significativa de esta constitución debe:

1. indicar el motivo del cambio;
2. identificar principios afectados;
3. evaluar impacto sobre documentación, arquitectura y procesos existentes;
4. actualizar los documentos relacionados cuando corresponda;
5. quedar registrada mediante control de versiones.

### Versionado

La constitución utiliza Semantic Versioning:

- **MAJOR:** eliminación o redefinición incompatible de principios fundamentales;
- **MINOR:** incorporación de nuevos principios o ampliaciones materiales;
- **PATCH:** aclaraciones, correcciones editoriales o mejoras que no cambian el significado de las reglas.

### Desviaciones

Cuando una feature o proyecto necesite apartarse de un principio, la desviación debe quedar explícitamente justificada y documentada.

El nivel de formalidad requerido debe ser proporcional al riesgo del proyecto.

### Revisión

El cumplimiento de la constitución debe comprobarse especialmente durante planificación, decisiones arquitectónicas y revisión previa a integración.

**Version**: 1.0.0 | **Ratified**: 2026-11-15 | **Last Amended**: 2026-11-15

