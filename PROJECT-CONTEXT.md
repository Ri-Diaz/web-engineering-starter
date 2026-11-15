# **PROJECT CONTEXT**

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `0.1`  
**Estado:** `[Draft | Active | Maintenance | Archived]`  
**Última actualización:** `[YYYY-MM-DD]`  
**Responsable:** `[Nombre / Equipo]`

---

# **1\. Propósito**

Este documento contiene el contexto técnico y funcional necesario para comprender el proyecto sin depender de conversaciones previas, conocimiento informal o interpretación del código.

Debe mantenerse actualizado durante el ciclo de vida del sistema.

Su contenido está orientado a:

* desarrolladores;  
* revisores;  
* mantenedores;  
* colaboradores;  
* herramientas de IA;  
* nuevos integrantes del proyecto.

---

# **2\. Resumen del proyecto**

## **Qué es**

`[Describir en 2–5 párrafos qué producto se está construyendo]`

---

## **Qué problema resuelve**

`[Descripción resumida del problema]`

---

## **Para quién está construido**

**Usuario principal:** `[Tipo de usuario]`

**Usuarios secundarios:**

* `[Usuario]`  
* `[Usuario]`  
* `[Usuario]`

---

# **3\. Qué NO es el proyecto**

Registrar explícitamente interpretaciones incorrectas o funcionalidades que no forman parte del objetivo actual.

El proyecto:

* NO es `[ ]`;  
* NO intenta `[ ]`;  
* NO reemplaza `[ ]`;  
* NO contempla actualmente `[ ]`;  
* NO debe utilizarse para `[ ]`.

Esta sección debe evitar expansiones de alcance accidentales.

---

# **4\. Objetivos actuales**

## **Objetivo principal**

`[Objetivo]`

## **Objetivos secundarios**

1. `[Objetivo]`  
2. `[Objetivo]`  
3. `[Objetivo]`

---

# **5\. Alcance actual**

## **Incluido**

* `[Funcionalidad]`  
* `[Funcionalidad]`  
* `[Funcionalidad]`

## **Fuera de alcance**

* `[Funcionalidad]`  
* `[Integración]`  
* `[Plataforma]`

---

# **6\. Clasificación del proyecto**

**Perfil:** `[STATIC | WEBAPP | SENSITIVE]`

**Documento asociado:** `docs/product/PROJECT-CLASSIFICATION.md`

### **Justificación resumida**

`[Explicar brevemente la clasificación]`

---

# **7\. Estado actual**

Seleccionar la etapa principal.

* Discovery  
* Specification  
* UX/UI  
* Architecture  
* Development  
* Testing  
* Pre-production  
* Production  
* Maintenance

### **Estado resumido**

`[Describir qué está terminado y qué está en curso]`

---

# **8\. Arquitectura actual**

## **Estilo arquitectónico**

`[Static / SSR / Monolito / Monolito modular / Otro]`

## **Diagrama conceptual**

\[Cliente\]  
    │  
    ▼  
\[Aplicación\]  
    │  
    ├── \[Módulo\]  
    ├── \[Módulo\]  
    └── \[Módulo\]  
            │  
            ▼  
       \[Persistencia\]

Modificar según corresponda.

---

# **9\. Stack tecnológico**

Registrar solamente tecnologías efectivamente adoptadas.

## **Frontend**

* Framework: `[ ]`  
* Lenguaje: `[ ]`  
* Estilos: `[ ]`  
* Componentes/UI: `[ ]`

## **Backend**

* Framework: `[ ]`  
* Lenguaje: `[ ]`  
* Runtime: `[ ]`

## **Persistencia**

* Base de datos: `[ ]`  
* ORM / acceso a datos: `[ ]`

## **Infraestructura**

* Hosting: `[ ]`  
* CDN: `[ ]`  
* Storage: `[ ]`  
* DNS: `[ ]`

## **Desarrollo**

* Package manager: `[ ]`  
* Testing: `[ ]`  
* Lint: `[ ]`  
* Formatter: `[ ]`  
* CI/CD: `[ ]`

---

# **10\. Versiones relevantes**

| Tecnología | Versión |
| ----- | ----- |
| `[Tecnología]` | `[Versión]` |
| `[Tecnología]` | `[Versión]` |
| `[Tecnología]` | `[Versión]` |

No registrar versiones si el proyecto no depende realmente de ellas.

---

# **11\. Estructura principal**

project/  
├── src/  
│   ├── ...  
│   └── ...  
├── tests/  
├── docs/  
├── public/  
└── ...

### **Descripción**

* `src/`: `[ ]`  
* `tests/`: `[ ]`  
* `docs/`: `[ ]`  
* `public/`: `[ ]`

---

# **12\. Dominios o módulos**

Registrar las áreas funcionales principales.

| Módulo | Responsabilidad |
| ----- | ----- |
| `[Módulo]` | `[Responsabilidad]` |
| `[Módulo]` | `[Responsabilidad]` |
| `[Módulo]` | `[Responsabilidad]` |

Cada módulo debe tener una responsabilidad principal claramente identificable.

---

# **13\. Modelo de datos resumido**

Registrar únicamente entidades relevantes.

| Entidad | Propósito |
| ----- | ----- |
| `[Entidad]` | `[Descripción]` |
| `[Entidad]` | `[Descripción]` |

El diseño completo debe mantenerse en `docs/architecture/DATA-MODEL.md` cuando corresponda.

---

# **14\. Flujos principales**

## **Flujo 1 — `[Nombre]`**

Usuario  
  ↓  
\[Acción\]  
  ↓  
\[Validación\]  
  ↓  
\[Proceso\]  
  ↓  
\[Resultado\]

## **Flujo 2 — `[Nombre]`**

\[Flujo\]  
---

# **15\. Reglas de negocio relevantes**

Registrar únicamente reglas que condicionen significativamente el comportamiento del sistema.

### **BR-001**

**Regla:** `[Descripción]`

**Razón:** `[Motivo]`

---

### **BR-002**

**Regla:** `[Descripción]`

**Razón:** `[Motivo]`

---

# **16\. Restricciones técnicas**

El proyecto debe respetar las siguientes restricciones.

* `[Restricción]`  
* `[Restricción]`  
* `[Restricción]`

Ejemplos:

* no introducir una SPA completa sin necesidad;  
* mantener compatibilidad con determinado navegador;  
* evitar dependencias propietarias;  
* utilizar base de datos existente;  
* desplegar únicamente en infraestructura aprobada.

---

# **17\. Restricciones funcionales**

* `[Restricción]`  
* `[Restricción]`

---

# **18\. Restricciones legales o regulatorias**

Cuando corresponda:

* `[Norma / regulación]`  
* `[Norma / regulación]`

### **Impacto**

`[Explicar cómo afecta al diseño o implementación]`

---

# **19\. Decisiones técnicas activas**

Registrar decisiones importantes sin sustituir los ADR.

| ID | Decisión | ADR |
| ----- | ----- | ----- |
| `D-001` | `[Decisión]` | `ADR-0001` |
| `D-002` | `[Decisión]` | `ADR-0002` |

---

# **20\. ADR relevantes**

* `ADR-0001` — `[Título]`  
* `ADR-0002` — `[Título]`  
* `ADR-0003` — `[Título]`

Los ADR constituyen la fuente de verdad sobre decisiones arquitectónicas.

---

# **21\. Convenciones importantes**

## **Naming**

* componentes: `[convención]`  
* variables: `[convención]`  
* archivos: `[convención]`  
* rutas: `[convención]`  
* tablas: `[convención]`

## **Código**

* `[Regla]`  
* `[Regla]`

## **Git**

* ramas: `[convención]`  
* commits: `[convención]`  
* pull requests: `[convención]`

---

# **22\. Reglas que no deben romperse**

Esta sección es especialmente importante para mantenimiento y desarrollo asistido por IA.

1. No modificar arquitectura sin revisar los ADR.  
2. No añadir dependencias sin justificación.  
3. No duplicar funcionalidades existentes.  
4. No modificar código ajeno al alcance de la tarea sin razón.  
5. No introducir secretos en el repositorio.  
6. No desactivar validaciones para resolver errores.  
7. No eliminar pruebas para conseguir un build exitoso.  
8. No cambiar contratos públicos sin analizar compatibilidad.  
9. No mezclar lógica de negocio con presentación cuando exista separación definida.  
10. No introducir patrones nuevos sin necesidad verificable.

Agregar reglas específicas del proyecto cuando corresponda.

---

# **23\. Dependencias externas**

| Servicio | Propósito | Criticidad |
| ----- | ----- | ----- |
| `[Servicio]` | `[Uso]` | `[Alta / Media / Baja]` |

---

# **24\. Variables de entorno**

No incluir valores reales.

| Variable | Propósito | Obligatoria |
| ----- | ----- | ----- |
| `DATABASE_URL` | Conexión a base de datos | Sí |
| `[VARIABLE]` | `[Uso]` | `[Sí/No]` |

Los valores deben mantenerse fuera del repositorio.

---

# **25\. Seguridad**

## **Autenticación**

`[No aplica / descripción]`

## **Autorización**

`[No aplica / descripción]`

## **Roles**

| Rol | Acceso principal |
| ----- | ----- |
| `[Rol]` | `[Permisos]` |

## **Datos sensibles**

`[Descripción / No aplica]`

## **Controles relevantes**

* `[Control]`  
* `[Control]`

El detalle debe mantenerse en `docs/security/SECURITY.md`.

---

# **26\. Estrategia de testing**

### **Unit**

`[Qué se prueba]`

### **Integration**

`[Qué se prueba]`

### **E2E**

`[Qué se prueba]`

### **Manual**

`[Qué requiere validación manual]`

Documento detallado:

`docs/engineering/TEST-STRATEGY.md`

---

# **27\. Quality gates**

Antes de merge deben cumplirse, según corresponda:

* build;  
* lint;  
* formatting;  
* type checking;  
* unit tests;  
* integration tests;  
* security checks;  
* dependency audit;  
* secret scanning.

---

# **28\. Performance**

### **Objetivos actuales**

* `[Métrica / objetivo]`  
* `[Métrica / objetivo]`

### **Riesgos conocidos**

* `[Riesgo]`

Documento asociado opcional (crear solo si aplica):

`PERFORMANCE.md`

---

# **29\. Accesibilidad**

### **Estándar objetivo**

`[WCAG / nivel / otro]`

### **Consideraciones relevantes**

* navegación mediante teclado;  
* estructura semántica;  
* foco visible;  
* contraste;  
* formularios accesibles;  
* mensajes de error comprensibles.

Documento asociado opcional (crear solo si aplica):

`ACCESSIBILITY.md`

---

# **30\. SEO**

**Aplicable:** `[Sí / No]`

### **Requisitos**

* `[Requisito]`  
* `[Requisito]`

Documento asociado opcional (crear solo si aplica):

`SEO.md`

---

# **31\. Despliegue**

## **Ambientes**

* Local  
* Development  
* Staging  
* Production

## **Producción**

**Proveedor:** `[ ]`

**Dominio:** `[ ]`

**Método de despliegue:** `[ ]`

Documento asociado opcional (crear solo si aplica):

`DEPLOYMENT.md`

---

# **32\. Observabilidad**

Actualmente se utiliza:

* logs;  
* error tracking;  
* analytics;  
* uptime monitoring;  
* métricas;  
* audit trail.

### **Herramientas**

`[ ]`

---

# **33\. Backups y recuperación**

**Aplicable:** `[Sí / No]`

### **Backup**

`[Descripción]`

### **Recuperación**

`[Descripción]`

Documento asociado opcional (crear solo si aplica):

`BACKUP-RESTORE.md`

---

# **34\. Riesgos técnicos conocidos**

| ID | Riesgo | Impacto | Estado |
| ----- | ----- | ----- | ----- |
| `TR-001` | `[Riesgo]` | `[Bajo / Medio / Alto]` | `[Abierto / Mitigado]` |

---

# **35\. Deuda técnica conocida**

| ID | Descripción | Prioridad | Issue |
| ----- | ----- | ----- | ----- |
| `TD-001` | `[Descripción]` | `[Baja / Media / Alta]` | `#XX` |

No ocultar deuda técnica relevante dentro de comentarios del código.

---

# **36\. Funcionalidades implementadas**

* `[Funcionalidad]`  
* `[Funcionalidad]`  
* `[Funcionalidad pendiente]`

---

# **37\. Trabajo actual**

### **En desarrollo**

* `[Tarea]`  
* `[Tarea]`

### **Próximamente**

* `[Tarea]`  
* `[Tarea]`

---

# **38\. Funcionalidades futuras**

Ideas aceptadas pero no incluidas en el alcance actual:

* `[Funcionalidad]`  
* `[Funcionalidad]`

Estas funcionalidades no deben implementarse anticipadamente.

---

# **39\. Problemas conocidos**

### **ISSUE-001**

**Problema:** `[Descripción]`

**Impacto:** `[ ]`

**Solución temporal:** `[ ]`

---

# **40\. Preguntas abiertas**

* `[Pregunta]`  
* `[Pregunta]`

---

# **41\. Instrucciones para asistentes de IA**

Las instrucciones operativas para agentes de IA están en `AGENTS.md`. Este documento mantiene la memoria técnica del proyecto y sus decisiones.


---

# **42\. Fuentes de verdad**

La autoridad sobre principios de ingeniería es `.specify/memory/constitution.md`. Para requisitos y decisiones específicas del proyecto, en caso de conflicto utilizar el siguiente orden:

1. requisitos aprobados;  
2. ADR vigentes;  
3. arquitectura documentada;  
4. especificación de la funcionalidad;  
5. este documento;  
6. código actual.

Si el código contradice una decisión aprobada, no asumir automáticamente que el código representa el comportamiento correcto.

---

# **43\. Actualización de este documento**

Actualizar `PROJECT-CONTEXT.md` cuando ocurra:

* cambio importante de arquitectura;  
* incorporación de un módulo;  
* modificación relevante del stack;  
* nuevo proveedor crítico;  
* cambio en seguridad;  
* nueva restricción;  
* cambio de alcance;  
* modificación de reglas de negocio importantes;  
* incorporación de deuda técnica relevante.

No es necesario actualizarlo por cada cambio menor de implementación.

---

# **44\. Resumen rápido**

## **Proyecto**

`[Nombre]`

## **Perfil**

`[STATIC / WEBAPP / SENSITIVE]`

## **Objetivo**

`[Una frase]`

## **Stack**

`[Resumen]`

## **Arquitectura**

`[Resumen]`

## **Estado**

`[Estado actual]`

## **Principal tarea actual**

`[Tarea]`

## **Principal riesgo actual**

`[Riesgo]`

## **Próximo hito**

`[Hito]`


