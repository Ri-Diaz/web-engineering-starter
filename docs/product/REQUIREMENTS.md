# **REQUIREMENTS**

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `0.1`  
**Estado:** `[Draft | Review | Approved | Superseded]`  
**Última actualización:** `[YYYY-MM-DD]`  
**Responsable:** `[Nombre / Equipo]`

---

# **1\. Propósito**

Este documento define los requisitos funcionales, no funcionales y reglas de negocio del proyecto.

Su objetivo es establecer qué debe hacer el sistema y bajo qué condiciones debe operar antes de definir detalles de implementación.

Los requisitos deben ser:

* claros;  
* verificables;  
* trazables;  
* consistentes;  
* necesarios;  
* comprensibles;  
* independientes de tecnologías específicas cuando sea posible.

---

# **2\. Alcance**

Este documento cubre:

* requisitos funcionales;  
* requisitos no funcionales;  
* reglas de negocio;  
* restricciones;  
* criterios de aceptación generales;  
* prioridades;  
* dependencias;  
* trazabilidad.

No sustituye:

* `PROJECT-BRIEF.md`;  
* especificaciones detalladas de funcionalidades;  
* `ARCHITECTURE.md`;  
* ADR;  
* planes de prueba.

---

# **3\. Convención de identificadores**

Utilizar identificadores estables.

## **Requisitos funcionales**

RF-001  
RF-002  
RF-003

## **Requisitos no funcionales**

RNF-001  
RNF-002  
RNF-003

## **Reglas de negocio**

BR-001  
BR-002  
BR-003

## **Restricciones**

CON-001  
CON-002

## **Requisitos de datos**

DATA-001  
DATA-002

Los identificadores no deben reutilizarse aunque un requisito sea eliminado.

---

# **4\. Estado de los requisitos**

Cada requisito puede encontrarse en uno de estos estados:

* `PROPOSED`  
* `APPROVED`  
* `IMPLEMENTED`  
* `VERIFIED`  
* `DEFERRED`  
* `REJECTED`  
* `SUPERSEDED`

---

# **5\. Prioridad**

Se utilizará inicialmente el modelo MoSCoW.

## **MUST**

Necesario para que el producto cumpla su propósito principal.

## **SHOULD**

Importante, pero el sistema puede operar temporalmente sin él.

## **COULD**

Aporta valor, pero no es necesario para la versión actual.

## **WON'T**

Se decide explícitamente no implementarlo dentro del alcance actual.

La categoría `MUST` debe utilizarse con moderación.

Si prácticamente todos los requisitos son `MUST`, la priorización pierde utilidad.

---

# **6\. Requisitos funcionales**

Los requisitos funcionales describen comportamientos observables del sistema.

No deben especificar tecnología salvo que esta constituya una restricción explícita.

---

## **RF-001 — `[Nombre del requisito]`**

**Estado:** `PROPOSED`  
**Prioridad:** `MUST`  
**Fuente:** `[Usuario / negocio / regulación / stakeholder]`

### **Descripción**

El sistema debe `[comportamiento esperado]`.

### **Justificación**

`[Por qué este requisito es necesario]`

### **Actor**

`[Usuario o sistema que inicia la acción]`

### **Precondiciones**

* `[Condición]`

### **Flujo esperado**

1. `[Acción]`  
2. `[Respuesta]`  
3. `[Resultado]`

### **Resultado esperado**

`[Estado final observable]`

### **Criterios de aceptación**

Given \[contexto\]  
When \[acción\]  
Then \[resultado esperado\]

### **Dependencias**

* `[RF / servicio / regla de negocio]`

### **Riesgo**

`[Bajo / Medio / Alto]`

---

## **RF-002 — `[Nombre]`**

**Estado:** `PROPOSED`  
**Prioridad:** `SHOULD`

### **Descripción**

`[ ]`

### **Criterios de aceptación**

Given ...  
When ...  
Then ...  
---

# **7\. Catálogo resumido de requisitos funcionales**

| ID | Requisito | Prioridad | Estado | Spec |
| ----- | ----- | ----- | ----- | ----- |
| `RF-001` | `[Descripción breve]` | `MUST` | `PROPOSED` | `[SPEC-001]` |
| `RF-002` | `[Descripción breve]` | `SHOULD` | `PROPOSED` | `[SPEC-002]` |

---

# **8\. Requisitos no funcionales**

Los requisitos no funcionales deben expresarse de forma medible siempre que sea razonable.

Evitar:

> El sistema debe ser rápido.

Preferir:

> Las páginas públicas críticas deberían alcanzar un LCP ≤ 2.5 s en condiciones de red definidas.

---

# **9\. Performance**

## **RNF-PERF-001**

**Prioridad:** `[MUST / SHOULD]`

El sistema debe `[objetivo medible]`.

### **Métrica**

`[LCP / INP / TTFB / API response / otra]`

### **Objetivo**

`[Valor]`

### **Condiciones de medición**

`[Ambiente / dispositivo / red / carga]`

---

## **RNF-PERF-002**

Los recursos visuales deberán utilizar formatos y estrategias de carga apropiadas cuando generen una mejora medible.

---

# **10\. Seguridad**

## **RNF-SEC-001**

Las funcionalidades protegidas deben requerir autenticación cuando corresponda.

## **RNF-SEC-002**

El sistema debe aplicar autorización en el servidor y no depender exclusivamente de controles de interfaz.

## **RNF-SEC-003**

Los secretos no deben almacenarse dentro del repositorio.

## **RNF-SEC-004**

La entrada proporcionada por usuarios debe validarse antes de ser procesada.

## **RNF-SEC-005**

Las dependencias deberán revisarse periódicamente para detectar vulnerabilidades conocidas.

---

# **11\. Privacidad**

## **RNF-PRIV-001**

El sistema deberá recopilar únicamente datos necesarios para sus funciones declaradas.

## **RNF-PRIV-002**

Los datos personales no deberán registrarse en logs salvo necesidad documentada.

## **RNF-PRIV-003**

Debe existir una finalidad identificable para cada categoría relevante de datos almacenados.

---

# **12\. Accesibilidad**

## **RNF-A11Y-001**

Las funciones principales deberán poder utilizarse mediante teclado cuando corresponda.

## **RNF-A11Y-002**

Los controles interactivos deberán contar con nombres accesibles.

## **RNF-A11Y-003**

Los errores de formularios deberán comunicarse de forma perceptible y comprensible.

## **RNF-A11Y-004**

El proyecto utilizará como referencia:

`[WCAG 2.x / nivel objetivo / criterio definido]`

---

# **13\. Compatibilidad**

## **RNF-COMP-001**

La aplicación deberá funcionar correctamente en los navegadores definidos por el proyecto.

### **Matriz objetivo**

| Plataforma | Soporte |
| ----- | ----- |
| Chrome | `[ ]` |
| Firefox | `[ ]` |
| Safari | `[ ]` |
| Edge | `[ ]` |
| Mobile Safari | `[ ]` |
| Chrome Android | `[ ]` |

---

# **14\. Responsive Design**

## **RNF-RESP-001**

Las funcionalidades esenciales deben estar disponibles en los tamaños de pantalla definidos.

### **Dispositivos objetivo**

* Mobile  
* Tablet  
* Desktop

No deben definirse breakpoints únicamente según dispositivos comerciales específicos.

---

# **15\. Disponibilidad**

## **RNF-AVAIL-001**

**Aplicable:** `[Sí / No]`

### **Objetivo**

`[Ej.: 99.9 % mensual]`

### **Exclusiones**

`[Mantenimiento planificado / terceros / otros]`

No establecer objetivos de disponibilidad que la infraestructura y el presupuesto no puedan sostener.

---

# **16\. Escalabilidad**

## **RNF-SCALE-001**

El sistema debe poder soportar inicialmente:

* `[X] usuarios concurrentes`;  
* `[X] solicitudes por minuto`;  
* `[X] registros`;  
* `[X GB] de información`.

Las estimaciones deben corresponder a necesidades plausibles.

No debe diseñarse arquitectura distribuida exclusivamente por crecimiento hipotético.

---

# **17\. Mantenibilidad**

## **RNF-MAINT-001**

Los módulos deberán mantener responsabilidades claramente delimitadas.

## **RNF-MAINT-002**

Las decisiones arquitectónicas relevantes deberán documentarse mediante ADR.

## **RNF-MAINT-003**

Las modificaciones de comportamiento deberán actualizar las pruebas correspondientes.

## **RNF-MAINT-004**

La duplicación significativa de lógica de negocio debe evitarse.

---

# **18\. Observabilidad**

## **RNF-OBS-001**

Los errores relevantes deberán poder diagnosticarse mediante mecanismos adecuados al perfil del proyecto.

Estos pueden incluir:

* logs;  
* error tracking;  
* métricas;  
* audit trail;  
* health checks.

## **RNF-OBS-002**

Los logs no deberán contener secretos.

---

# **19\. Respaldo y recuperación**

**Aplicable:** `[Sí / No]`

## **RNF-BACKUP-001**

Los datos críticos deberán respaldarse según:

**Frecuencia:** `[ ]`

**Retención:** `[ ]`

**Ubicación:** `[ ]`

## **RNF-REC-001**

El procedimiento de recuperación deberá verificarse periódicamente.

### **Objetivos**

**RPO:** `[ ]`

**RTO:** `[ ]`

No definir RPO o RTO arbitrarios sin relación con las necesidades reales del proyecto.

---

# **20\. SEO**

**Aplicable:** `[Sí / No]`

## **RNF-SEO-001**

Las páginas públicas relevantes deberán disponer de:

* títulos apropiados;  
* metadatos;  
* URLs comprensibles;  
* semántica HTML adecuada;  
* indexabilidad controlada.

## **RNF-SEO-002**

El contenido que no deba indexarse deberá configurarse explícitamente.

---

# **21\. Localización e internacionalización**

**Aplicable:** `[Sí / No]`

## **RNF-I18N-001**

Los textos visibles no deberán quedar acoplados innecesariamente al código si el proyecto requiere múltiples idiomas.

## **RNF-I18N-002**

Fechas, números y monedas deberán utilizar formatos apropiados al locale definido.

---

# **22\. Reglas de negocio**

Las reglas de negocio representan restricciones del dominio y no detalles de interfaz.

---

## **BR-001 — `[Nombre]`**

### **Regla**

`[Descripción precisa]`

### **Justificación**

`[Motivo funcional / legal / comercial]`

### **Ejemplo válido**

`[ ]`

### **Ejemplo inválido**

`[ ]`

### **Requisitos afectados**

* `RF-001`  
* `RF-004`

---

## **BR-002 — `[Nombre]`**

### **Regla**

`[ ]`

---

# **23\. Requisitos de datos**

## **DATA-001 — `[Entidad / dato]`**

### **Descripción**

`[Qué información debe almacenarse]`

### **Fuente**

`[Usuario / sistema externo / cálculo]`

### **Obligatorio**

`[Sí / No]`

### **Sensibilidad**

* Pública  
* Interna  
* Personal  
* Sensible  
* Confidencial

### **Retención**

`[Periodo / indefinido / pendiente]`

---

# **24\. Integridad de datos**

## **DATA-INT-001**

`[Regla de unicidad / consistencia / relación]`

## **DATA-INT-002**

`[Restricción]`

Las reglas críticas de integridad deberían implementarse lo más cerca posible de la fuente de verdad, no solamente en la interfaz.

---

# **25\. Integraciones**

## **INT-001 — `[Servicio externo]`**

**Propósito:** `[ ]`

**Criticidad:** `[Alta / Media / Baja]`

### **Requisitos**

* `[ ]`  
* `[ ]`

### **Fallo esperado**

Si el servicio no está disponible:

`[Comportamiento del sistema]`

### **Timeout**

`[ ]`

### **Retry**

`[Sí / No / estrategia]`

### **Fallback**

`[ ]`

---

# **26\. Restricciones**

## **CON-001 — `[Nombre]`**

### **Restricción**

`[Descripción]`

### **Motivo**

`[ ]`

### **Impacto**

`[ ]`

---

# **27\. Casos límite**

Registrar casos relevantes que probablemente generen comportamientos ambiguos.

| ID | Situación | Comportamiento esperado |
| ----- | ----- | ----- |
| `EDGE-001` | `[Situación]` | `[Resultado]` |
| `EDGE-002` | `[Situación]` | `[Resultado]` |

Ejemplos:

* campos vacíos;  
* información duplicada;  
* sesión expirada;  
* servicio externo caído;  
* envío repetido;  
* navegación atrás;  
* solicitudes concurrentes.

---

# **28\. Manejo de errores**

Los errores deben categorizarse cuando corresponda.

### **Errores de usuario**

Ejemplo:

* campos inválidos;  
* permisos insuficientes.

### **Errores del sistema**

Ejemplo:

* base de datos no disponible;  
* dependencia externa caída.

### **Comportamiento esperado**

El sistema debe:

1. evitar pérdida de datos cuando sea posible;  
2. entregar mensajes comprensibles;  
3. evitar exposición de detalles internos;  
4. registrar información suficiente para diagnóstico.

---

# **29\. Requisitos legales y regulatorios**

**Aplicable:** `[Sí / No]`

| ID | Norma | Requisito afectado | Implicación |
| ----- | ----- | ----- | ----- |
| `LEG-001` | `[Norma]` | `[RF/RNF]` | `[Impacto]` |

No convertir interpretaciones legales inciertas en requisitos definitivos sin validación cuando el riesgo sea relevante.

---

# **30\. Dependencias entre requisitos**

Ejemplo:

RF-004  
   ↓  
depende de  
   ↓  
RF-001  
RF-002  
BR-003

Registrar únicamente dependencias relevantes.

---

# **31\. Conflictos conocidos**

| ID | Requisitos en conflicto | Resolución |
| ----- | ----- | ----- |
| `CONF-001` | `[RF/RNF]` | `[Decisión]` |

Cuando el conflicto sea arquitectónico, puede requerir un ADR.

---

# **32\. Matriz de trazabilidad**

Cada requisito importante debería poder seguirse desde el origen hasta su validación.

| Requisito | Fuente | Spec | Implementación | Test | Estado |
| ----- | ----- | ----- | ----- | ----- | ----- |
| `RF-001` | Brief | `SPEC-001` | `[módulo]` | `T-001` | `[ ]` |
| `RNF-SEC-001` | Security | `[ ]` | `[ ]` | `T-SEC-001` | `[ ]` |
| `BR-001` | Negocio | `SPEC-002` | `[ ]` | `T-002` | `[ ]` |

---

# **33\. Relación con Spec Kit**

Los requisitos de alto nivel definidos en este documento deben transformarse en especificaciones detalladas cuando requieran implementación.

Ejemplo:

RF-007  
"El usuario puede recuperar su contraseña"  
             ↓  
SPEC-004  
Password Recovery  
             ↓  
plan.md  
             ↓  
tasks.md  
             ↓  
implementation  
             ↓  
tests

`REQUIREMENTS.md` mantiene la visión global.

Las specs mantienen el detalle de cada funcionalidad.

---

# **34\. Criterios de calidad de un requisito**

Antes de aprobar un requisito verificar:

* ¿Es necesario?  
* ¿Es comprensible?  
* ¿Es verificable?  
* ¿Evita ambigüedad?  
* ¿Tiene prioridad?  
* ¿Tiene una fuente?  
* ¿Evita imponer una solución técnica innecesaria?  
* ¿Puede relacionarse con una prueba?  
* ¿No duplica otro requisito?  
* ¿No contradice una decisión vigente?

---

# **35\. Señales de requisitos deficientes**

Revisar requisitos que utilicen expresiones como:

* rápido;  
* moderno;  
* intuitivo;  
* seguro;  
* escalable;  
* amigable;  
* robusto;  
* eficiente;  
* fácil de usar.

Estas expresiones pueden mantenerse solamente si existe posteriormente una forma verificable de determinar su cumplimiento.

---

# **36\. Gestión de cambios**

Un requisito aprobado no debería modificarse silenciosamente.

Los cambios relevantes deben registrar:

**Requisito:** `[ID]`

**Cambio:** `[Descripción]`

**Motivo:** `[ ]`

**Impacto:** `[ ]`

**Fecha:** `[ ]`

**Responsable:** `[ ]`

Si el cambio modifica significativamente el producto, debe revisarse también:

* alcance;  
* arquitectura;  
* estimaciones;  
* pruebas;  
* documentación.

---

# **37\. Requisitos diferidos**

| ID | Requisito | Motivo | Revisión futura |
| ----- | ----- | ----- | ----- |
| `[ID]` | `[ ]` | `[ ]` | `[ ]` |

Un requisito diferido no debe permanecer implícitamente dentro del alcance.

---

# **38\. Requisitos rechazados**

| ID | Requisito | Motivo |
| ----- | ----- | ----- |
| `[ID]` | `[ ]` | `[ ]` |

Registrar decisiones relevantes evita volver a discutir repetidamente la misma funcionalidad.

---

# **39\. Revisión final**

Antes de aprobar este documento:

* El alcance coincide con `PROJECT-BRIEF.md`.  
* Los requisitos están identificados.  
* Los `MUST` son realmente imprescindibles.  
* Los requisitos críticos tienen criterios verificables.  
* Las reglas de negocio están separadas de la interfaz.  
* Las necesidades de seguridad están identificadas.  
* Las necesidades de privacidad están identificadas.  
* Las dependencias críticas están identificadas.  
* Los casos límite importantes están considerados.  
* No existen contradicciones conocidas sin resolver.  
* Existe trazabilidad suficiente para comenzar las specs.

---

# **40\. Aprobación**

**Estado:** `[Draft / Approved]`

**Fecha:** `[YYYY-MM-DD]`

**Responsable:** `[ ]`

### **Comentarios**

`[ ]`

