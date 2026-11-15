# **ARCHITECTURE**

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `0.1`  
**Estado:** `[Draft | Review | Approved | Superseded]`  
**Última actualización:** `[YYYY-MM-DD]`  
**Responsable:** `[Nombre / Equipo]`

---

# **1\. Propósito**

Este documento describe la arquitectura actual del sistema y las reglas estructurales que deben respetarse durante su evolución.

Debe permitir responder:

* qué componentes existen;  
* qué responsabilidad tiene cada componente;  
* cómo se comunican;  
* dónde viven las reglas de negocio;  
* dónde se almacena la información;  
* qué dependencias están permitidas;  
* cómo se despliega;  
* cómo escala;  
* cómo falla;  
* cómo se recupera.

No debe convertirse en documentación teórica desconectada de la implementación.

---

# **2\. Principios arquitectónicos**

La arquitectura debe respetar los principios definidos en `.specify/memory/constitution.md`.

Principios aplicables:

1. simplicidad antes que complejidad;  
2. arquitectura proporcional al problema;  
3. monolito modular por defecto;  
4. separación clara de responsabilidades;  
5. dependencias explícitas;  
6. seguridad por diseño;  
7. observabilidad proporcional;  
8. escalabilidad basada en necesidades reales;  
9. decisiones relevantes documentadas mediante ADR;  
10. evitar abstracciones sin necesidad.

---

# **3\. Clasificación del proyecto**

**Perfil:** `[STATIC | WEBAPP | SENSITIVE]`

**Referencia:** `docs/product/PROJECT-CLASSIFICATION.md`

### **Implicaciones arquitectónicas**

`[Describir qué exige esta clasificación]`

---

# **4\. Contexto del sistema**

## **4.1 Objetivo técnico**

`[Explicar qué debe permitir la arquitectura]`

---

## **4.2 Actores principales**

| Actor | Interacción |
| ----- | ----- |
| `[Usuario]` | `[Qué hace]` |
| `[Administrador]` | `[Qué hace]` |
| `[Sistema externo]` | `[Interacción]` |

---

# **5\. Diagrama de contexto**

Representación de alto nivel.

\[Usuario\]  
    │  
    ▼  
\[Aplicación\]  
    │  
    ├──────────────► \[Servicio externo A\]  
    │  
    ├──────────────► \[Servicio externo B\]  
    │  
    ▼  
\[Base de datos\]

Adaptar según corresponda.

---

# **6\. Arquitectura de alto nivel**

## **Estilo arquitectónico**

`[Static / SSR / Monolito / Monolito modular / Otro]`

## **Justificación**

`[Por qué esta arquitectura es adecuada]`

---

# **7\. Componentes principales**

| Componente | Responsabilidad |
| ----- | ----- |
| `[Frontend]` | `[Presentación / interacción]` |
| `[Application]` | `[Casos de uso]` |
| `[Domain]` | `[Reglas de negocio]` |
| `[Infrastructure]` | `[Persistencia / servicios externos]` |
| `[Database]` | `[Persistencia]` |

---

# **8\. Límites arquitectónicos**

Cada capa o módulo debe conocer únicamente lo necesario.

Ejemplo recomendado:

Presentation  
    ↓  
Application  
    ↓  
Domain  
    ↓  
Infrastructure

Las dependencias deben avanzar en una dirección definida.

Evitar:

Domain ─────────► Presentation  
Database ───────► UI  
Infrastructure ─► componentes visuales

salvo justificación explícita.

---

# **9\. Monolito modular**

Cuando el proyecto utilice monolito modular, la estructura debe organizarse alrededor de capacidades del dominio.

Ejemplo:

src/  
├── modules/  
│   ├── users/  
│   ├── auth/  
│   ├── orders/  
│   ├── products/  
│   └── notifications/  
│  
├── shared/  
│   ├── config/  
│   ├── logging/  
│   ├── errors/  
│   └── utilities/

Cada módulo debería poder explicar claramente:

* qué responsabilidad tiene;  
* qué expone;  
* qué consume;  
* qué datos controla.

---

# **10\. Catálogo de módulos**

## **Módulo `[Nombre]`**

### **Responsabilidad**

`[ ]`

### **Expone**

* `[API / servicio / función]`

### **Consume**

* `[Otro módulo / dependencia]`

### **Datos propios**

* `[Entidad]`

### **Dependencias permitidas**

* `[ ]`

### **Dependencias prohibidas**

* `[ ]`

---

# **11\. Reglas de dependencia**

Ejemplo:

users  
   ↓  
shared

orders  
   ↓  
users  
   ↓  
shared

No permitir:

users ↔ orders

si genera dependencia circular.

Las dependencias circulares deben considerarse señal de límites incorrectos.

---

# **12\. Presentación**

## **Responsabilidades**

La capa de presentación puede:

* mostrar información;  
* recibir entrada;  
* realizar validaciones de formato;  
* gestionar interacción;  
* traducir acciones del usuario.

No debe contener:

* reglas de negocio críticas;  
* acceso directo no controlado a datos;  
* secretos;  
* lógica duplicada del backend.

---

# **13\. Application Layer**

La capa de aplicación coordina casos de uso.

Puede:

* ejecutar flujos;  
* coordinar módulos;  
* invocar reglas de dominio;  
* manejar transacciones;  
* invocar servicios externos mediante interfaces.

No debería contener lógica de presentación.

---

# **14\. Domain Layer**

El dominio contiene las reglas fundamentales del negocio.

Debe minimizar dependencias de:

* frameworks;  
* interfaces gráficas;  
* HTTP;  
* proveedores externos;  
* infraestructura.

Ejemplos:

* cálculos;  
* validaciones de dominio;  
* políticas;  
* estados;  
* transiciones;  
* invariantes.

---

# **15\. Infrastructure Layer**

Incluye mecanismos concretos como:

* base de datos;  
* correo;  
* almacenamiento;  
* APIs;  
* logging;  
* cache;  
* colas;  
* proveedores externos.

La infraestructura implementa necesidades del sistema.

El dominio no debe adaptarse artificialmente al proveedor.

---

# **16\. Flujo de una solicitud**

Ejemplo:

HTTP Request  
     ↓  
Controller / Route  
     ↓  
Validation  
     ↓  
Use Case  
     ↓  
Domain Rule  
     ↓  
Repository / Gateway  
     ↓  
Database / External Service  
     ↓  
Response  
---

# **17\. Arquitectura del frontend**

**Aplicable:** `[Sí / No]`

## **Tipo**

* Static  
* SSR  
* SPA  
* Islands  
* Hybrid

## **Estructura**

frontend/  
├── pages/  
├── components/  
├── layouts/  
├── features/  
├── services/  
└── styles/  
---

# **18\. Componentes visuales**

Los componentes deben clasificarse cuando sea útil:

UI primitives  
    ↓  
Reusable components  
    ↓  
Feature components  
    ↓  
Pages

Evitar que componentes de bajo nivel dependan de lógica específica de negocio.

---

# **19\. Estado del frontend**

Definir estrategia:

`[Local state / Server state / Global state / URL state]`

Antes de introducir una librería global de estado debe justificarse por complejidad real.

---

# **20\. Comunicación frontend-backend**

## **Mecanismo**

`[HTTP / REST / RPC / Server Actions / GraphQL / Otro]`

## **Contrato**

`[Descripción]`

## **Serialización**

`[JSON / otro]`

## **Versionado**

`[Si aplica]`

---

# **21\. Backend**

## **Framework**

`[ ]`

## **Estilo**

`[MVC / Service layer / Modular / Otro]`

## **Responsabilidades**

* autorización;  
* reglas de negocio;  
* validaciones;  
* persistencia;  
* integración;  
* auditoría;  
* seguridad.

---

# **22\. API**

**Aplicable:** `[Sí / No]`

## **Tipo**

* REST  
* GraphQL  
* RPC  
* Internal only  
* Public

## **Reglas**

* contratos explícitos;  
* validación de entrada;  
* códigos de estado coherentes;  
* respuestas estructuradas;  
* errores no deben exponer detalles internos;  
* cambios incompatibles requieren evaluación.

---

# **23\. Contratos**

Ejemplo:

{  
  "id": "123",  
  "status": "active"  
}

Los contratos públicos deben considerarse interfaces estables.

Cambiar estructura, semántica o tipos puede requerir versionado o ADR.

---

# **24\. Persistencia**

## **Motor**

`[PostgreSQL / SQLite / MySQL / Otro]`

## **Estrategia**

`[ORM / SQL directo / Query builder]`

## **Responsabilidad**

La base de datos debe proteger, cuando corresponda:

* unicidad;  
* integridad referencial;  
* restricciones críticas;  
* transacciones;  
* consistencia.

No depender solamente de validaciones de interfaz.

---

# **25\. Propiedad de datos**

Cada entidad debe tener un dueño arquitectónico.

| Entidad | Módulo propietario |
| ----- | ----- |
| `[User]` | `[users]` |
| `[Order]` | `[orders]` |

Los módulos no deberían modificar directamente datos ajenos sin una interfaz definida.

---

# **26\. Transacciones**

Identificar operaciones que deben ser atómicas.

Ejemplo:

crear pedido  
   \+  
reservar stock  
   \+  
registrar pago

Si una parte falla, definir claramente qué debe ocurrir.

---

# **27\. Consistencia**

Seleccionar según caso:

* fuerte;  
* eventual;  
* mixta.

No adoptar consistencia eventual si no existe necesidad real.

---

# **28\. Integraciones externas**

| Servicio | Uso | Criticidad |
| ----- | ----- | ----- |
| `[Servicio]` | `[Propósito]` | `[Alta / Media / Baja]` |

Cada integración debe definir:

* timeout;  
* error handling;  
* retry;  
* fallback;  
* observabilidad.

---

# **29\. Adaptadores**

Cuando un proveedor externo sea relevante, se recomienda aislarlo mediante una interfaz.

Ejemplo:

Application  
    ↓  
EmailService  
    ↓  
Provider Adapter  
    ↓  
External Email API

Esto evita acoplamiento innecesario al proveedor.

---

# **30\. Estrategia de errores**

Clasificar errores.

## **Domain Errors**

Ejemplo:

InsufficientStock  
InvalidStateTransition

## **Validation Errors**

Ejemplo:

InvalidEmail  
MissingField

## **Infrastructure Errors**

Ejemplo:

DatabaseUnavailable  
ExternalServiceTimeout

## **Unexpected Errors**

Errores no previstos.

---

# **31\. Propagación de errores**

La capa externa debe traducir errores internos a respuestas apropiadas.

Ejemplo:

Domain Error  
      ↓  
Application Error  
      ↓  
HTTP 409

No exponer:

* stack traces;  
* SQL;  
* rutas internas;  
* secretos;  
* datos privados.

---

# **32\. Logging**

El logging debe ser:

* estructurado cuando corresponda;  
* útil;  
* proporcional;  
* seguro.

## **Niveles**

* DEBUG  
* INFO  
* WARNING  
* ERROR  
* CRITICAL

No utilizar logs como sustituto de auditoría.

---

# **33\. Auditoría**

**Aplicable:** `[Sí / No]`

Registrar cuando corresponda:

* quién;  
* qué acción;  
* sobre qué recurso;  
* cuándo;  
* resultado;  
* contexto relevante.

Auditoría y logging operacional cumplen funciones distintas.

---

# **34\. Seguridad arquitectónica**

## **Trust boundaries**

Identificar límites relevantes.

Internet  
   │  
   ▼  
Application Boundary  
   │  
   ▼  
Database Boundary  
---

# **35\. Autenticación**

`[Descripción]`

Ejemplos:

* sesión;  
* OAuth;  
* OIDC;  
* token.

---

# **36\. Autorización**

`[RBAC / ABAC / simple roles / no aplica]`

Las decisiones de autorización deben ejecutarse del lado del servidor.

---

# **37\. Gestión de secretos**

Los secretos deben almacenarse en:

* variables de entorno;  
* secret managers;  
* infraestructura segura.

Nunca en:

* código;  
* README;  
* fixtures reales;  
* commits;  
* logs.

---

# **38\. Threat boundaries**

Registrar superficies relevantes:

* formularios;  
* login;  
* APIs;  
* uploads;  
* panel administrador;  
* integraciones;  
* webhooks.

El análisis completo debe mantenerse en `THREAT-MODEL.md` para proyectos que lo requieran.

---

# **39\. Performance**

Las decisiones arquitectónicas deben considerar:

* tamaño de bundle;  
* consultas;  
* caché;  
* imágenes;  
* I/O;  
* latencia;  
* servicios externos.

No introducir caché sin identificar primero el cuello de botella.

---

# **40\. Cache**

**Aplicable:** `[Sí / No]`

## **Tipo**

* browser;  
* CDN;  
* application;  
* database;  
* distributed cache.

## **Invalidation**

`[Estrategia]`

Si la estrategia de invalidación no puede explicarse claramente, probablemente la caché sea prematura.

---

# **41\. Escalabilidad**

## **Capacidad inicial**

`[ ]`

## **Principal dimensión de crecimiento**

* usuarios;  
* tráfico;  
* datos;  
* archivos;  
* procesamiento.

---

# **42\. Estrategia de escalamiento**

Orden preferido:

1\. optimizar aplicación  
2\. optimizar consultas  
3\. mejorar infraestructura  
4\. escalar verticalmente  
5\. escalar horizontalmente  
6\. cache  
7\. procesamiento asíncrono  
8\. extraer servicios si existe necesidad

No saltar automáticamente al último nivel.

---

# **43\. Procesamiento asíncrono**

**Aplicable:** `[Sí / No]`

Utilizar para operaciones como:

* envío de correos;  
* generación pesada;  
* procesamiento diferido;  
* integraciones lentas.

No utilizar colas si una operación síncrona simple es suficiente.

---

# **44\. Resiliencia**

Considerar:

* timeouts;  
* retries;  
* circuit breaking;  
* degradación controlada;  
* idempotencia.

Solo implementar mecanismos proporcionales al riesgo.

---

# **45\. Idempotencia**

Identificar operaciones sensibles a repetición.

Ejemplo:

POST /payment  
POST /order  
webhook

Definir estrategia:

`[ ]`

---

# **46\. Concurrencia**

**Aplicable:** `[Sí / No]`

Riesgos:

* doble envío;  
* actualización simultánea;  
* reservas;  
* stock;  
* estados incompatibles.

Estrategia:

`[Optimistic locking / transactions / constraints / otro]`

---

# **47\. Disponibilidad**

## **Objetivo**

`[ ]`

## **Dependencias críticas**

* `[ ]`

## **Single Points of Failure**

* `[ ]`

---

# **48\. Backup y recuperación**

**Aplicable:** `[Sí / No]`

## **Backup**

`[ ]`

## **Restauración**

`[ ]`

## **RPO**

`[ ]`

## **RTO**

`[ ]`

---

# **49\. Ambientes**

| Ambiente | Propósito |
| ----- | ----- |
| Local | Desarrollo |
| Development | Integración |
| Staging | Validación |
| Production | Operación |

No todos los proyectos requieren todos los ambientes.

---

# **50\. Configuración**

Separar configuración de código.

Ejemplo:

config/  
├── base  
├── development  
├── test  
└── production

Los valores sensibles deben gestionarse externamente.

---

# **51\. CI/CD**

Si el proyecto utiliza CI/CD, definir un pipeline proporcional a su perfil, stack, riesgo y necesidades. No todos los proyectos requieren un pipeline automatizado.

Las etapas posibles incluyen lint, type checking, tests, security checks, build y deploy. No todas son necesarias en cada proyecto: un proyecto simple puede utilizar solo algunas, mientras que `WEBAPP` y `SENSITIVE` pueden requerir controles adicionales.

Documentar los detalles de deployment o workflows cuando dichos artefactos existan o sean necesarios para el proyecto.

---

# **52\. Observabilidad**

El sistema puede utilizar:

* logs;  
* tracing;  
* metrics;  
* error tracking;  
* uptime monitoring;  
* analytics.

## **Señales principales**

`[ ]`

---

# **53\. Health checks**

**Aplicable:** `[Sí / No]`

Ejemplos:

/health  
/ready  
/live

Evitar health checks costosos o que expongan detalles internos.

---

# **54\. Arquitectura de despliegue**

Internet  
    │  
    ▼  
DNS / CDN  
    │  
    ▼  
Application  
    │  
    ├── Database  
    ├── Storage  
    └── External Services

Modificar según implementación.

---

# **55\. Dependencias críticas**

| Dependencia | Tipo | Riesgo |
| ----- | ----- | ----- |
| `[PostgreSQL]` | Infraestructura | `[ ]` |
| `[API]` | Externa | `[ ]` |

---

# **56\. Portabilidad**

Registrar dependencias específicas de proveedor.

| Componente | Vendor lock-in |
| ----- | ----- |
| `[Servicio]` | `[Bajo / Medio / Alto]` |

Vendor lock-in no es automáticamente negativo.

Debe evaluarse frente al valor aportado.

---

# **57\. ADR asociados**

| ADR | Decisión |
| ----- | ----- |
| `ADR-0001` | `[Stack]` |
| `ADR-0002` | `[Arquitectura]` |
| `ADR-0003` | `[Persistencia]` |

---

# **58\. Decisiones explícitamente descartadas**

Registrar alternativas importantes rechazadas.

## **Microservicios**

**Estado:** `[No adoptado]`

**Motivo:** `[ ]`

## **SPA**

**Estado:** `[ ]`

**Motivo:** `[ ]`

## **Otro**

`[ ]`

Esto evita reabrir decisiones sin nueva evidencia.

---

# **59\. Restricciones arquitectónicas**

* `[ ]`  
* `[ ]`  
* `[ ]`

Ejemplo:

* no acceso directo a DB desde presentación;  
* no dependencias circulares;  
* no lógica crítica en frontend;  
* no acceso cross-module sin contrato;  
* no proveedor externo acoplado directamente al dominio.

---

# **60\. Reglas para nuevas dependencias**

Antes de incorporar una dependencia debe evaluarse:

* necesidad;  
* alternativas;  
* mantenimiento;  
* seguridad;  
* tamaño;  
* impacto arquitectónico;  
* licencia;  
* riesgo de abandono.

---

# **61\. Reglas para nuevos módulos**

Crear un módulo nuevo únicamente cuando exista:

* responsabilidad diferenciable;  
* conjunto coherente de reglas;  
* frontera clara;  
* motivo real de separación.

No crear módulos únicamente para reducir tamaño de archivos.

---

# **62\. Reglas para nuevos servicios**

Un servicio independiente debe justificarse por factores como:

* necesidad de despliegue independiente;  
* carga muy distinta;  
* aislamiento operacional;  
* seguridad;  
* ownership separado;  
* tecnología especializada.

No por moda arquitectónica.

---

# **63\. Evolución arquitectónica**

La arquitectura debe cambiar cuando cambie el problema.

Proceso:

Problema identificado  
        ↓  
Evidencia  
        ↓  
Alternativas  
        ↓  
ADR  
        ↓  
Cambio arquitectónico  
        ↓  
Validación  
---

# **64\. Anti-patterns a evitar**

* God objects;  
* módulos genéricos sin responsabilidad;  
* carpetas `utils` ilimitadas;  
* lógica de negocio en controllers;  
* consultas desde UI;  
* duplicación;  
* dependencias circulares;  
* abstracciones innecesarias;  
* premature optimization;  
* premature distribution;  
* secretos en repositorio;  
* manejo silencioso de errores.

---

# **65\. Architecture fitness checks**

Cuando sea posible, automatizar reglas arquitectónicas.

Ejemplos:

* dependencias prohibidas;  
* ciclos;  
* cobertura de módulos críticos;  
* imports incorrectos;  
* límites de capas.

---

# **66\. Estado de la arquitectura**

## **Estable**

* `[Componente]`

## **En evolución**

* `[Componente]`

## **Pendiente de decisión**

* `[Componente]`

---

# **67\. Riesgos arquitectónicos**

| ID | Riesgo | Impacto | Mitigación |
| ----- | ----- | ----- | ----- |
| `AR-001` | `[ ]` | `[ ]` | `[ ]` |

---

# **68\. Deuda arquitectónica**

| ID | Deuda | Riesgo | Acción |
| ----- | ----- | ----- | ----- |
| `AD-001` | `[ ]` | `[ ]` | `[ ]` |

---

# **69\. Checklist de revisión**

Antes de aprobar la arquitectura:

* La solución es proporcional al problema.  
* Los módulos tienen responsabilidades claras.  
* No existen dependencias circulares conocidas.  
* Las reglas de negocio tienen ubicación definida.  
* La persistencia tiene límites claros.  
* Las integraciones están identificadas.  
* Los errores tienen estrategia.  
* Seguridad fue considerada.  
* Concurrencia fue considerada cuando aplica.  
* Backup fue considerado cuando aplica.  
* Observabilidad fue considerada.  
* Escalabilidad responde a necesidades plausibles.  
* Las decisiones importantes tienen ADR.  
* No se introdujo complejidad sin justificación.

---

# **70\. Resumen ejecutivo de arquitectura**

## **Perfil**

`[STATIC / WEBAPP / SENSITIVE]`

## **Arquitectura**

`[ ]`

## **Frontend**

`[ ]`

## **Backend**

`[ ]`

## **Persistencia**

`[ ]`

## **Infraestructura**

`[ ]`

## **Principal decisión**

`[ ]`

## **Principal riesgo**

`[ ]`

## **Próxima decisión arquitectónica**

`[ ]`


