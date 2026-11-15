# **00 — WEB ENGINEERING STARTER — INDEX**

**Versión:** 1.0  
**Estado:** Active  
**Última revisión:** `[YYYY-MM-DD]`

---

## **1\. Propósito**

**Web Engineering Starter** es una base reutilizable para iniciar proyectos web con criterios consistentes de ingeniería de software.

Su objetivo es ayudar a definir correctamente un proyecto antes de comenzar a programar y mantener durante su desarrollo una estructura clara respecto de:

* producto;  
* requisitos;  
* arquitectura;  
* datos;  
* seguridad;  
* testing;  
* decisiones técnicas;  
* mantenibilidad.

La plantilla busca reducir improvisación, deuda técnica accidental y decisiones arquitectónicas innecesarias.

No todos los documentos deben completarse con el mismo nivel de profundidad.

> **La documentación debe ser proporcional a la complejidad y riesgo del proyecto.**

---

## **2\. Principios**

Los proyectos derivados de esta plantilla deben priorizar:

1. simplicidad antes que complejidad;  
2. requisitos antes que implementación;  
3. arquitectura proporcional al problema;  
4. seguridad por diseño;  
5. separación de responsabilidades;  
6. decisiones técnicas explícitas;  
7. testing basado en riesgo;  
8. automatización de controles repetibles;  
9. documentación útil y mantenible;  
10. evolución incremental.

La plantilla no busca producir la arquitectura más sofisticada.

Busca producir la **arquitectura más sencilla que resuelva correctamente el problema y permita evolucionar el sistema**.

---

## **3\. Flujo general**

IDEA  
 │  
 ▼  
PROJECT BRIEF  
 │  
 ▼  
PROJECT CLASSIFICATION  
 │  
 ▼  
PROJECT CONTEXT  
 │  
 ▼  
REQUIREMENTS  
 │  
 ▼  
ARCHITECTURE  
 │  
 ├── DATA MODEL  
 │  
 └── ADR cuando sea necesario  
 │  
 ▼  
IMPLEMENTATION  
 │  
 ▼  
TESTING  
 │  
 ▼  
DEPLOYMENT  
 │  
 ▼  
MAINTENANCE

El proceso puede iterar.

No es obligatorio completar todos los documentos antes de escribir una sola línea de código, pero las decisiones importantes deben estar suficientemente definidas antes de implementarse.

---

# **4\. Clasificación de proyectos**

Todo proyecto debe clasificarse inicialmente como uno de los siguientes perfiles.

## **STATIC**

Sitios principalmente públicos o informativos.

Ejemplos:

* landing pages;  
* portfolios;  
* sitios corporativos;  
* bandas;  
* restaurantes;  
* documentación.

Características habituales:

* poca lógica de negocio;  
* sin autenticación;  
* sin persistencia relevante;  
* bajo riesgo operacional.

---

## **WEBAPP**

Aplicaciones con comportamiento dinámico y persistencia.

Ejemplos:

* reservas;  
* inventarios;  
* e-commerce;  
* paneles administrativos;  
* plataformas con usuarios.

Características habituales:

* autenticación;  
* base de datos;  
* lógica de negocio;  
* roles;  
* APIs;  
* integraciones.

---

## **SENSITIVE**

Aplicaciones que procesan información sensible o poseen mayor criticidad.

Ejemplos:

* salud;  
* información financiera;  
* recursos humanos;  
* sistemas institucionales;  
* información regulada.

Características habituales:

* datos sensibles;  
* múltiples permisos;  
* auditoría;  
* requisitos legales;  
* mayor necesidad de trazabilidad y seguridad.

---

# **5\. Documentos del Starter**

## **01 — Engineering Constitution**

Define los principios generales de ingeniería.

Documento activo: `.specify/memory/constitution.md`.

Contiene reglas relacionadas con:

* simplicidad;  
* arquitectura;  
* seguridad;  
* testing;  
* dependencias;  
* deuda técnica;  
* mantenibilidad.

### **Uso**

**Obligatorio para todos los proyectos.**

Normalmente no se modifica entre proyectos salvo evolución del propio Starter.

---

## **02 — Project Brief**

Define el proyecto desde la perspectiva de producto.

Incluye:

* problema;  
* usuarios;  
* objetivos;  
* alcance;  
* MVP;  
* restricciones;  
* riesgos iniciales;  
* métricas de éxito.

### **Uso**

**Obligatorio.**

Debe completarse al iniciar un proyecto.

---

## **03 — Project Classification**

Determina si el proyecto corresponde a:

STATIC  
WEBAPP  
SENSITIVE

La clasificación permite decidir cuánto rigor técnico y documental requiere.

### **Uso**

**Obligatorio.**

Debe realizarse después del Project Brief.

---

## **04 — Project Context**

Actúa como memoria técnica del proyecto.

Resume:

* estado actual;  
* stack;  
* arquitectura;  
* módulos;  
* decisiones;  
* reglas importantes;  
* trabajo realizado;  
* trabajo pendiente.

### **Uso**

**Obligatorio y vivo.**

Debe actualizarse cuando existan cambios relevantes.

---

## **05 — Requirements**

Define qué debe hacer el sistema.

Incluye:

* requisitos funcionales;  
* requisitos no funcionales;  
* reglas de negocio;  
* restricciones;  
* criterios de aceptación;  
* trazabilidad.

### **Uso**

**Obligatorio**, pero su profundidad depende del proyecto.

---

## **06 — Architecture**

Describe cómo se organiza técnicamente el sistema.

Incluye:

* arquitectura general;  
* módulos;  
* responsabilidades;  
* dependencias;  
* flujo de información;  
* persistencia;  
* integraciones;  
* infraestructura.

### **Uso**

**Obligatorio.**

En proyectos `STATIC` puede ser muy breve.

---

## **07 — Data Model**

Describe:

* entidades;  
* relaciones;  
* restricciones;  
* integridad;  
* ownership;  
* migraciones;  
* clasificación de datos.

### **Uso**

Condicional.

STATIC       → normalmente no necesario  
WEBAPP       → normalmente necesario  
SENSITIVE    → normalmente obligatorio  
---

## **08 — ADR Template**

Plantilla para crear **Architecture Decision Records**.

Se utiliza para documentar decisiones técnicas importantes.

Ejemplos:

ADR-0001 — Uso de Astro  
ADR-0002 — PostgreSQL como base de datos  
ADR-0003 — Estrategia de autenticación  
ADR-0004 — Plataforma de despliegue

### **Uso**

Solo cuando exista una decisión arquitectónica suficientemente importante.

No crear ADR para decisiones triviales.

---

## **09 — Security**

Define el modelo y los controles principales de seguridad.

Puede incluir:

* autenticación;  
* autorización;  
* sesiones;  
* secretos;  
* validación;  
* protección de datos;  
* dependencias;  
* logging;  
* controles de infraestructura.

### **Uso**

La profundidad depende del perfil.

STATIC  
→ baseline

WEBAPP  
→ seguridad de aplicación

SENSITIVE  
→ controles reforzados  
---

## **10 — Test Strategy**

Define cómo se validará el sistema.

Puede incluir:

* unit tests;  
* integration tests;  
* E2E;  
* seguridad;  
* accesibilidad;  
* performance;  
* regresiones;  
* CI.

### **Uso**

Proporcional al riesgo.

STATIC  
→ testing ligero

WEBAPP  
→ estrategia completa

SENSITIVE  
→ testing reforzado basado en riesgo  
---

# **6\. Matriz de uso**

| Documento | STATIC | WEBAPP | SENSITIVE |
| ----- | ----- | ----- | ----- |
| 01 Constitution | ✅ | ✅ | ✅ |
| 02 Project Brief | ✅ | ✅ | ✅ |
| 03 Classification | ✅ | ✅ | ✅ |
| 04 Project Context | ✅ | ✅ | ✅ |
| 05 Requirements | ✅ Ligero | ✅ | ✅ |
| 06 Architecture | ✅ Ligero | ✅ | ✅ |
| 07 Data Model | Opcional | ✅ | ✅ |
| 08 ADR | Según necesidad | Según necesidad | Según necesidad |
| 09 Security | Baseline | ✅ | ✅ Reforzado |
| 10 Test Strategy | Ligero | ✅ | ✅ Reforzado |

---

# **7\. Orden recomendado para iniciar un proyecto**

## **Paso 1 — Idea**

Describir brevemente qué se quiere construir.

No seleccionar todavía tecnologías salvo que exista una restricción previa.

---

## **Paso 2 — Project Brief**

Definir:

Problema  
Usuario  
Objetivo  
Alcance  
MVP  
---

## **Paso 3 — Classification**

Determinar:

STATIC  
WEBAPP  
SENSITIVE  
---

## **Paso 4 — Project Context**

Crear la memoria inicial del proyecto.

---

## **Paso 5 — Requirements**

Transformar necesidades en requisitos verificables.

---

## **Paso 6 — Architecture**

Diseñar la solución técnica más sencilla que satisfaga los requisitos.

---

## **Paso 7 — Data Model**

Solo cuando exista persistencia relevante.

---

## **Paso 8 — ADR**

Crear ADR únicamente para decisiones técnicas importantes.

---

## **Paso 9 — Development**

Desarrollar mediante funcionalidades pequeñas y verificables.

---

## **Paso 10 — Testing**

Aplicar la estrategia correspondiente al nivel de riesgo.

---

# **8\. Reglas para evitar burocracia**

No completar una sección únicamente porque exista.

Antes de documentar algo preguntar:

> ¿Esta información ayudará a diseñar, implementar, comprobar o mantener el proyecto?

Si la respuesta es no, probablemente no sea necesaria.

---

## **No duplicar información**

Cada concepto debe tener una fuente principal.

Ejemplo:

PROJECT CONTEXT  
      │  
      │ referencia  
      ▼  
ARCHITECTURE  
      │  
      │ detalle específico  
      ▼  
ADR

No repetir la misma explicación completa en varios documentos.

---

## **Utilizar referencias**

Preferir:

> La estrategia de seguridad se encuentra definida en `docs/security/SECURITY.md`.

en lugar de copiar nuevamente toda la estrategia.

---

# **9\. Escalabilidad documental**

La documentación debe crecer junto al proyecto.

Proyecto simple  
      │  
      ▼  
Documentación mínima  
      │  
      ▼  
Mayor complejidad  
      │  
      ▼  
Mayor documentación

No:

Proyecto simple  
      │  
      ▼  
Documentación empresarial completa  
---

# **10\. Documentos adicionales**

Los siguientes documentos **no forman parte obligatoria del Starter v1.0.0**.

Pueden agregarse cuando exista necesidad:

PERFORMANCE.md  
ACCESSIBILITY.md  
SEO.md  
PRIVACY.md  
THREAT-MODEL.md  
BACKUP-RESTORE.md  
INCIDENT-RESPONSE.md  
DEPLOYMENT.md  
RUNBOOK.md  
DESIGN-SYSTEM.md  
API.md

También puede incorporarse `AUDIT.md` si el proyecto lo requiere. La incorporación de estos documentos debe justificarse por características reales del proyecto.

---

# **11\. Uso con Spec-Driven Development**

Las especificaciones de funcionalidades deben complementar esta documentación.

Flujo conceptual:

REQUIREMENTS  
      │  
      ▼  
FEATURE SPEC  
      │  
      ▼  
PLAN  
      │  
      ▼  
TASKS  
      │  
      ▼  
IMPLEMENTATION  
      │  
      ▼  
TEST

Los documentos globales definen el sistema.

Las specs definen funcionalidades concretas.

---

# **12\. Uso de IA**

Las instrucciones operativas para agentes de IA están en `AGENTS.md`. Allí se indican las fuentes que deben consultarse antes de cambios significativos; la constitución de ingeniería activa es `.specify/memory/constitution.md`.

---

# **13\. Evolución**

Cuando cambien significativamente:

* objetivo;  
* alcance;  
* arquitectura;  
* datos;  
* seguridad;  
* integraciones;

deben actualizarse los documentos correspondientes.

No modificar documentación por cambios triviales.

---

# **14\. Versionado del Starter**

Utilizar Semantic Versioning con el formato `MAJOR.MINOR.PATCH`:

* `v1.0.0`: primer release;
* `v1.0.1`: correcciones compatibles;
* `v1.1.0`: mejoras compatibles;
* `v2.0.0`: cambios incompatibles.

---

# **15\. Estado de la plantilla**

**Versión actual:** `v1.0.0`

Incluye:

00 Web Engineering Starter — Index  
01 Engineering Constitution  
02 Project Brief  
03 Project Classification  
04 Project Context  
05 Requirements  
06 Architecture  
07 Data Model  
08 ADR Template  
09 Security  
10 Test Strategy  
---

# **16\. Regla final**

> La plantilla debe ayudar a construir software, no convertirse en trabajo administrativo adicional.

Cuando una práctica o documento deja de aportar claridad, control de riesgo o mantenibilidad, debe simplificarse.

