# **PROJECT CLASSIFICATION**

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `0.1`  
**Fecha:** `[YYYY-MM-DD]`  
**Responsable:** `[Nombre / Equipo]`

---

# **1\. Objetivo**

Este documento clasifica el proyecto según su complejidad funcional, sensibilidad de datos, criticidad operativa y necesidades arquitectónicas.

La clasificación determina qué controles, documentos y prácticas son obligatorios.

Los perfiles disponibles son:

* `STATIC`  
* `WEBAPP`  
* `SENSITIVE`

La clasificación debe basarse en necesidades reales y no en preferencias tecnológicas.

---

# **2\. Regla general**

Debe seleccionarse el nivel más bajo que permita satisfacer correctamente los requisitos del proyecto.

No se debe escoger una arquitectura más compleja únicamente por escalabilidad futura hipotética.

La clasificación puede cambiar si aparecen nuevos requisitos.

---

# **3\. Perfil STATIC**

Adecuado para proyectos principalmente informativos o de contenido.

## **Características típicas**

* contenido público;  
* pocas interacciones;  
* sin autenticación;  
* sin base de datos propia o con uso mínimo;  
* sin información sensible;  
* lógica de negocio mínima;  
* generación estática o server-side simple;  
* bajo riesgo operacional.

  ## **Ejemplos**

* sitio corporativo;  
* landing page;  
* portafolio;  
* sitio de banda;  
* blog;  
* sitio de restaurante;  
* documentación;  
* catálogo sin compra.

  ## **Arquitectura habitual**

* Browser  
*    │  
*    ▼  
* Static / SSR Website  
*    │  
*    ├── CDN  
*    ├── CMS opcional  
     └── servicios externos opcionales

  ## **Requisitos mínimos**

* responsive design;  
* accesibilidad;  
* SEO;  
* optimización de imágenes;  
* performance budget;  
* HTTPS;  
* gestión de secretos si existen integraciones;  
* build reproducible;  
* lint;  
* control de dependencias.  
  ---

  # **4\. Perfil WEBAPP**

Adecuado para aplicaciones con estado, usuarios o lógica de negocio relevante.

## **Características típicas**

* autenticación;  
* persistencia;  
* formularios complejos;  
* panel administrativo;  
* múltiples flujos;  
* usuarios registrados;  
* lógica de negocio;  
* integraciones;  
* API;  
* base de datos.

  ## **Ejemplos**

* sistema de reservas;  
* CRM;  
* e-commerce;  
* gestor de clientes;  
* plataforma educativa;  
* sistema de inventario;  
* panel administrativo.

  ## **Arquitectura habitual**

* Frontend  
*    │  
*    ▼  
* Application  
*    │  
*    ├── Domain / Business Logic  
*    │  
*    ├── Services  
*    │  
*    └── Persistence  
*            │  
*            ▼  
          Database

Se prefiere inicialmente una arquitectura de **monolito modular** salvo necesidad demostrable de separación adicional.

## **Requisitos mínimos adicionales**

* autenticación segura;  
* autorización;  
* validación de entrada;  
* manejo de errores;  
* migraciones de base de datos;  
* pruebas unitarias;  
* pruebas de integración;  
* logging;  
* backups;  
* CI;  
* política de despliegue;  
* documentación de arquitectura.  
  ---

  # **5\. Perfil SENSITIVE**

Adecuado para aplicaciones que procesan información sensible, regulada o cuya operación tiene consecuencias relevantes.

## **Características típicas**

* datos personales sensibles;  
* datos clínicos;  
* información financiera;  
* información privada crítica;  
* decisiones con impacto operacional;  
* múltiples niveles de acceso;  
* requisitos legales;  
* necesidad de auditoría;  
* elevada criticidad.

  ## **Ejemplos**

* sistemas de salud;  
* plataformas financieras;  
* sistemas de recursos humanos;  
* gestión de información confidencial;  
* sistemas gubernamentales;  
* aplicaciones con trazabilidad obligatoria.

  ## **Arquitectura habitual**

Puede utilizar monolito modular o arquitectura distribuida según necesidades reales.

La clasificación `SENSITIVE` no implica automáticamente microservicios.

## **Requisitos adicionales**

* RBAC o ABAC según necesidad;  
* mínimo privilegio;  
* auditoría;  
* trazabilidad;  
* políticas de retención;  
* clasificación de información;  
* cifrado en tránsito;  
* cifrado en reposo cuando corresponda;  
* backups verificados;  
* recuperación documentada;  
* threat modeling;  
* logging seguro;  
* monitoreo;  
* control de acceso administrativo;  
* segregación de ambientes;  
* gestión de incidentes;  
* revisión reforzada de dependencias;  
* privacidad por diseño.  
  ---

  # **6\. Cuestionario de clasificación**

Responder cada pregunta con:

* `0` \= No  
* `1` \= Parcial / Bajo  
* `2` \= Sí / Relevante  
* `3` \= Crítico  
  ---

  ## **6.1 Usuarios y autenticación**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿Existen usuarios autenticados? | `[0-3]` |
| ¿Existen diferentes roles? | `[0-3]` |
| ¿Los permisos afectan funcionalidades relevantes? | `[0-3]` |
| ¿Existen administradores con privilegios elevados? | `[0-3]` |

**Subtotal:** `[ ]`

---

## **6.2 Persistencia y datos**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿Existe base de datos propia? | `[0-3]` |
| ¿Los usuarios crean o modifican información? | `[0-3]` |
| ¿La pérdida de datos tendría impacto relevante? | `[0-3]` |
| ¿Existe historial que debe conservarse? | `[0-3]` |

**Subtotal:** `[ ]`

---

## **6.3 Sensibilidad de información**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿Se procesan datos personales? | `[0-3]` |
| ¿Se procesan datos sensibles o regulados? | `[0-3]` |
| ¿La exposición de datos podría causar perjuicio? | `[0-3]` |
| ¿Existen obligaciones legales específicas? | `[0-3]` |

**Subtotal:** `[ ]`

---

## **6.4 Lógica de negocio**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿Existen reglas de negocio relevantes? | `[0-3]` |
| ¿Las reglas pueden cambiar frecuentemente? | `[0-3]` |
| ¿Una regla incorrecta podría causar daños o pérdidas? | `[0-3]` |
| ¿Existen múltiples flujos dependientes entre sí? | `[0-3]` |

**Subtotal:** `[ ]`

---

## **6.5 Integraciones externas**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿Existen APIs externas? | `[0-3]` |
| ¿El sistema depende de terceros críticos? | `[0-3]` |
| ¿Existen pagos u operaciones financieras? | `[0-3]` |
| ¿La indisponibilidad de terceros puede afectar el sistema? | `[0-3]` |

**Subtotal:** `[ ]`

---

## **6.6 Criticidad operacional**

| Pregunta | Puntaje |
| ----- | ----- |
| ¿La indisponibilidad tendría impacto importante? | `[0-3]` |
| ¿Existen usuarios que dependen del sistema para trabajar? | `[0-3]` |
| ¿La pérdida de datos sería difícil de recuperar? | `[0-3]` |
| ¿Se requiere continuidad operacional? | `[0-3]` |

**Subtotal:** `[ ]`

---

# **7\. Puntaje orientativo**

### **0–10 puntos**

Probablemente:

**STATIC**

Características esperadas:

* sitio público;  
* poca lógica;  
* baja criticidad;  
* sin datos sensibles.  
  ---

  ### **11–30 puntos**

Probablemente:

**WEBAPP**

Características esperadas:

* usuarios;  
* persistencia;  
* lógica;  
* integraciones;  
* administración.  
  ---

  ### **31 puntos o más**

Evaluar:

**SENSITIVE**

Especialmente si existen:

* datos regulados;  
* auditoría;  
* autorización compleja;  
* consecuencias relevantes ante errores.  
  ---

  # **8\. Reglas de sobrescritura**

El puntaje es solamente orientativo.

Un proyecto debe clasificarse automáticamente como `SENSITIVE` si presenta cualquiera de las siguientes condiciones críticas.

## **Datos altamente sensibles**

* información clínica;  
* información financiera privada;  
* antecedentes personales altamente confidenciales;  
* credenciales críticas;  
* información protegida por regulación específica.

  ## **Operaciones críticas**

* decisiones médicas;  
* transferencias financieras;  
* autorizaciones sensibles;  
* procesos con consecuencias legales relevantes.

  ## **Requisitos de trazabilidad**

* auditoría obligatoria;  
* no repudio;  
* historial legalmente exigido;  
* trazabilidad de acciones administrativas.  
  ---

  # **9\. Factores que NO justifican mayor complejidad**

Los siguientes argumentos no son suficientes por sí solos para aumentar la clasificación:

* "podría crecer mucho";  
* "quizás tengamos millones de usuarios";  
* "microservicios son más escalables";  
* "queremos usar Kubernetes";  
* "es una buena práctica";  
* "las grandes empresas lo hacen";  
* "quizás necesitemos una API en el futuro".

Las decisiones deben basarse en requisitos presentes o previsibles con evidencia.

---

# **10\. Evaluación arquitectónica**

Completar después del cuestionario.

## **Clasificación propuesta**

* `STATIC`  
* `WEBAPP`  
* `SENSITIVE`

  ## **Justificación**

`[Explicar por qué se selecciona este nivel]`

---

# **11\. Arquitectura inicial recomendada**

### **Estilo arquitectónico**

`[Static / SSR / Monolito modular / Otro]`

### **Frontend**

`[Pendiente de definir / Tecnología]`

### **Backend**

`[No requerido / Pendiente / Tecnología]`

### **Persistencia**

`[No requerida / Pendiente / Tecnología]`

### **Hosting**

`[Pendiente]`

### **Servicios externos**

`[Pendiente]`

---

# **12\. Escalabilidad esperada**

Registrar expectativas realistas.

## **Usuarios estimados**

* lanzamiento: `[ ]`  
* 12 meses: `[ ]`  
* 36 meses: `[ ]`

  ## **Volumen de datos**

`[Estimación]`

## **Patrón de uso**

* estable;  
* estacional;  
* eventos con picos;  
* desconocido.  
  ---

  # **13\. Estrategia de crecimiento**

La arquitectura debe permitir crecer de forma incremental.

Orden recomendado:

* Aplicación simple  
*       ↓  
* Monolito organizado  
*       ↓  
* Monolito modular  
*       ↓  
* Optimización de infraestructura  
*       ↓  
* Caching / colas cuando sea necesario  
*       ↓  
* Separación de componentes críticos  
*       ↓  
  Servicios independientes solo si existe necesidad

No debe comenzarse por el último nivel.

---

# **14\. Requisitos por perfil**

| Control | STATIC | WEBAPP | SENSITIVE |
| ----- | ----- | ----- | ----- |
| Project Brief | ✓ | ✓ | ✓ |
| Project Context | ✓ | ✓ | ✓ |
| Requirements | básico | ✓ | ✓ |
| Architecture Document | básico | ✓ | ✓ |
| ADR | opcional | ✓ | ✓ |
| Design System | ✓ | ✓ | ✓ |
| Accessibility | ✓ | ✓ | ✓ |
| SEO | ✓ | según caso | según caso |
| Unit Testing | opcional | ✓ | ✓ |
| Integration Testing | opcional | ✓ | ✓ |
| E2E | según riesgo | ✓ | ✓ |
| Authentication | — | según caso | ✓ |
| Authorization | — | según caso | ✓ |
| Audit Trail | — | según caso | ✓ |
| Threat Model | básico | recomendado | ✓ |
| Backup Plan | — | ✓ | ✓ |
| Recovery Plan | — | recomendado | ✓ |
| Observability | básico | ✓ | ✓ |
| Incident Response | — | recomendado | ✓ |
| Privacy Assessment | según datos | según datos | ✓ |

---

# **15\. Documentación obligatoria**

Según la clasificación seleccionada deberán habilitarse los documentos correspondientes.

## **STATIC**

* PROJECT-BRIEF.md  
* PROJECT-CONTEXT.md  
* DESIGN-SYSTEM.md  
* ACCESSIBILITY.md  
* SEO.md  
  PERFORMANCE.md

  ## **WEBAPP**

Además:

* REQUIREMENTS.md  
* ARCHITECTURE.md  
* DATA-MODEL.md  
* TEST-STRATEGY.md  
* SECURITY.md  
  DEPLOYMENT.md

  ## **SENSITIVE**

Además:

* THREAT-MODEL.md  
* PRIVACY.md  
* AUDIT.md  
* BACKUP-RESTORE.md  
* INCIDENT-RESPONSE.md  
  RUNBOOK.md  
  ---

  # **16\. Revisión de clasificación**

La clasificación debe revisarse cuando ocurra alguno de estos cambios:

* incorporación de autenticación;  
* incorporación de nuevos roles;  
* almacenamiento de nuevos tipos de datos;  
* incorporación de información sensible;  
* pagos;  
* APIs externas críticas;  
* crecimiento operacional significativo;  
* nuevas obligaciones legales;  
* cambios relevantes en criticidad.  
  ---

  # **17\. Decisión final**

**Clasificación:** `[STATIC / WEBAPP / SENSITIVE]`

**Fecha de decisión:** `[YYYY-MM-DD]`

**Responsable:** `[Nombre]`

**Justificación resumida:**

`[Escribir aquí]`

---

# **18\. Checklist de cierre**

* El cuestionario fue completado.  
* La sensibilidad de datos fue revisada.  
* La criticidad operacional fue evaluada.  
* Se aplicaron las reglas de sobrescritura.  
* La arquitectura propuesta es proporcional al problema.  
* No existen componentes incorporados únicamente por anticipación.  
* La clasificación está justificada.  
* Los documentos obligatorios fueron identificados.  
  ---

  # **19\. Principio de decisión**

La clasificación no mide cuán importante es un proyecto.

Mide cuánta disciplina técnica necesita para operar correctamente.

Un sitio `STATIC` puede ser comercialmente crítico.

Un sistema `SENSITIVE` puede tener pocos usuarios.

La arquitectura debe responder al riesgo y a los requisitos, no al prestigio técnico de las herramientas utilizadas.

* 

