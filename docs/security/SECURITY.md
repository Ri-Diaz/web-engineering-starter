# **09 — SECURITY**

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `1.0`  
**Perfil:** `[STATIC | WEBAPP | SENSITIVE]`  
**Última actualización:** `[YYYY-MM-DD]`

---

## **1\. Propósito**

Este documento define los controles principales de seguridad del proyecto.

La profundidad requerida depende de su clasificación:

STATIC  
→ baseline de seguridad web

WEBAPP  
→ seguridad de aplicación

SENSITIVE  
→ controles reforzados

La seguridad debe formar parte del diseño y no agregarse solamente antes del despliegue.

---

## **2\. Perfil de seguridad**

**Clasificación del proyecto:** `[STATIC / WEBAPP / SENSITIVE]`

**Nivel de riesgo:** `[Bajo / Medio / Alto / Crítico]`

### **Justificación**

`[Explicar brevemente]`

---

## **3\. Activos principales**

Identificar qué necesita protección.

| Activo | Sensibilidad | Criticidad |
| ----- | ----- | ----- |
| `[Datos usuarios]` | `[Personal]` | `[Alta]` |
| `[Base de datos]` | `[Interna]` | `[Alta]` |
| `[Credenciales]` | `Secret` | `Crítica` |
| `[Código fuente]` | `Internal` | `[Media]` |

---

## **4\. Superficie de ataque**

Identificar las entradas principales al sistema.

* sitio público;  
* autenticación;  
* formularios;  
* API;  
* panel administrativo;  
* uploads;  
* webhooks;  
* integraciones externas;  
* servicios de terceros.

### **Principal superficie de riesgo**

`[ ]`

---

## **5\. Autenticación**

**Aplicable:** `[Sí / No]`

**Método:** `[Sesiones / OAuth / OIDC / Otro]`

### **Reglas**

* utilizar mecanismos mantenidos por el framework o proveedor;  
* no implementar criptografía o autenticación propia sin necesidad;  
* proteger recuperación de cuentas;  
* utilizar MFA cuando el riesgo lo justifique.

### **MFA**

* No requerido  
* Administradores  
* Usuarios privilegiados  
* Todos

---

## **6\. Autorización**

**Modelo:** `[RBAC / ABAC / Ownership / Otro / No aplica]`

La autorización debe verificarse en el servidor o componente confiable.

Ocultar botón en frontend  
≠  
control de autorización

### **Principio**

**Deny by default.**

Solo deben concederse permisos explícitamente autorizados.

---

## **7\. Roles y permisos**

| Acción | Guest | User | Admin |
| ----- | ----- | ----- | ----- |
| `[Ver]` | ✓ | ✓ | ✓ |
| `[Editar]` | — | ✓ | ✓ |
| `[Administrar]` | — | — | ✓ |

Adaptar según proyecto.

Para operaciones relevantes también debe verificarse acceso al **recurso concreto**, no únicamente el rol global.

---

## **8\. Sesiones**

**Aplicable:** `[Sí / No]`

Cuando se utilicen cookies de sesión, evaluar:

Secure  
HttpOnly  
SameSite

Además:

* expiración apropiada;  
* invalidación al cerrar sesión;  
* regeneración después de cambios relevantes de privilegio;  
* reautenticación para operaciones críticas cuando corresponda.

---

## **9\. Validación de entradas**

Toda información externa debe considerarse no confiable.

Incluye:

* formularios;  
* query parameters;  
* URLs;  
* cookies;  
* headers;  
* APIs;  
* archivos;  
* webhooks;  
* servicios externos.

Validar:

tipo  
formato  
longitud  
rango  
valores permitidos  
reglas de negocio

La validación del frontend mejora UX, pero no sustituye la validación del servidor.

---

## **10\. Protección de aplicación**

Evaluar según corresponda:

### **SQL Injection**

Utilizar ORM correctamente o consultas parametrizadas.

### **XSS**

Mantener escaping del framework y evitar HTML no confiable.

### **CSRF**

Aplicar protección cuando la autenticación utilice cookies.

### **CORS**

Permitir solamente los orígenes necesarios.

### **Redirects**

Evitar redirecciones abiertas.

### **Mass assignment**

Permitir explícitamente los campos modificables.

---

## **11\. Headers y navegador**

Evaluar:

Content-Security-Policy  
Strict-Transport-Security  
X-Content-Type-Options  
Referrer-Policy  
Permissions-Policy

No aplicar configuraciones copiadas sin comprobar compatibilidad con el proyecto.

### **HTTPS**

Producción debe utilizar HTTPS.

---

## **12\. Rate limiting y abuso**

Aplicar cuando corresponda especialmente a:

* login;  
* recuperación de contraseña;  
* APIs públicas;  
* búsquedas costosas;  
* formularios;  
* envío de correo;  
* operaciones repetibles.

### **Estrategia**

`[No aplica / Proveedor / Aplicación / Otra]`

---

## **13\. Uploads**

**Aplicable:** `[Sí / No]`

Si existen archivos:

**Tamaño máximo:** `[ ]`

**Tipos permitidos:** `[ ]`

**Storage:** `[ ]`

**Acceso:** `[Público / Privado]`

Validar al menos:

* tamaño;  
* extensión;  
* MIME;  
* nombres seguros;  
* permisos.

No confiar únicamente en la extensión proporcionada por el usuario.

---

## **14\. Gestión de secretos**

Considerar secretos:

passwords  
API keys  
tokens  
private keys  
database credentials  
signing secrets

Nunca deben almacenarse en:

código  
Git  
README  
logs  
fixtures

Se recomienda:

.env.example        ✓

.env con secretos   ✗

Producción debe utilizar mecanismos seguros del proveedor o secret manager cuando corresponda.

---

## **15\. Dependencias y supply chain**

Antes de agregar una dependencia evaluar:

* necesidad;  
* mantenimiento;  
* vulnerabilidades conocidas;  
* licencia;  
* procedencia.

Cuando sea posible automatizar:

dependency audit  
dependency updates  
secret scanning

Los lockfiles deben versionarse cuando el ecosistema los utilice.

---

## **16\. Datos sensibles y logs**

Clasificar los datos mediante `docs/architecture/DATA-MODEL.md`.

No registrar innecesariamente:

* contraseñas;  
* tokens;  
* claves;  
* Authorization headers;  
* datos personales sensibles.

Los logs deben contener suficiente información para diagnóstico sin convertirse en una copia de los datos del sistema.

---

## **17\. Auditoría**

**Aplicable:** `[Sí / No]`

Especialmente relevante para `SENSITIVE`.

Registrar cuando corresponda:

QUIÉN  
QUÉ  
CUÁNDO  
SOBRE QUÉ  
RESULTADO

Auditoría y logging operacional no son equivalentes.

---

## **18\. Base de datos**

Cuando exista persistencia:

* utilizar mínimo privilegio;  
* evitar exposición pública innecesaria;  
* utilizar conexiones cifradas cuando corresponda;  
* proteger backups;  
* mantener integridad mediante constraints.

La aplicación de producción no debería utilizar permisos administrativos de DB sin necesidad.

---

## **19\. Ambientes**

Cuando corresponda separar:

Development  
Staging  
Production

Cada ambiente debe tener sus propias:

* credenciales;  
* configuraciones;  
* servicios;  
* datos.

Evitar utilizar datos reales de producción en desarrollo.

---

## **20\. Configuración de producción**

Antes de desplegar verificar:

DEBUG \= false  
HTTPS activo  
secrets configurados  
hosts/origins restringidos  
DB protegida  
errores internos ocultos

Eliminar además:

* endpoints de prueba;  
* configuraciones temporales;  
* credenciales por defecto;  
* servicios innecesarios.

---

## **21\. CI/CD**

Los workflows deben tener mínimo privilegio.

Evitar proporcionar secrets de producción a jobs que no los necesiten.

Checks recomendados:

lint  
tests  
dependency audit  
secret scan  
build

Para proyectos sensibles pueden agregarse controles adicionales.

---

## **22\. Backups**

**Aplicable:** `[Sí / No]`

Cuando existan datos importantes:

**Frecuencia:** `[ ]`

**Retención:** `[ ]`

**Cifrado:** `[ ]`

**Última restauración probada:** `[ ]`

Un backup no debe considerarse suficiente si no existe una forma conocida de restaurarlo.

---

## **23\. Controles por perfil**

### **STATIC**

Baseline:

* HTTPS;  
* headers;  
* secretos fuera de Git;  
* dependencias revisadas;  
* formularios seguros;  
* scripts externos revisados;  
* CI básico.

### **WEBAPP**

Además:

* autenticación;  
* autorización;  
* sesiones;  
* validación server-side;  
* rate limiting;  
* DB protegida;  
* logging;  
* backups;  
* security tests.

### **SENSITIVE**

Además:

* MFA para accesos privilegiados;  
* auditoría;  
* threat modeling;  
* privacidad;  
* controles reforzados de acceso;  
* restore testing;  
* monitoreo;  
* respuesta ante incidentes.

---

## **24\. Excepciones**

Si un control necesario no puede implementarse:

**Control:** `[ ]`

**Motivo:** `[ ]`

**Riesgo:** `[ ]`

**Mitigación temporal:** `[ ]`

**Fecha de revisión:** `[ ]`

No aceptar excepciones permanentes sin revisión.

---

## **25\. Riesgos conocidos**

| ID | Riesgo | Impacto | Mitigación |
| ----- | ----- | ----- | ----- |
| `SEC-R01` | `[ ]` | `[ ]` | `[ ]` |

---

## **26\. Deuda de seguridad**

| ID | Deuda | Prioridad | Acción |
| ----- | ----- | ----- | ----- |
| `SEC-TD01` | `[ ]` | `[ ]` | `[ ]` |

No ocultar deuda relevante en comentarios `TODO`.

---

## **27\. Checklist preproducción**

* HTTPS funciona.  
* DEBUG deshabilitado.  
* Secretos fuera del repositorio.  
* Autenticación revisada.  
* Autorización revisada.  
* Entradas validadas en servidor.  
* Permisos administrativos revisados.  
* CORS revisado.  
* Headers revisados.  
* Rate limiting aplicado donde corresponde.  
* Uploads revisados.  
* Dependencias sin vulnerabilidades críticas conocidas.  
* Logs no exponen secretos.  
* DB no está expuesta innecesariamente.  
* Backups configurados cuando aplica.  
* Tests críticos pasan.  
* Excepciones están documentadas.

---

## **28\. Referencias**

Referencias recomendadas:

* OWASP ASVS;  
* OWASP Cheat Sheet Series;  
* documentación de seguridad del framework;  
* documentación del proveedor de infraestructura.

No es necesario copiar estos estándares completos dentro del proyecto.

---

## **29\. Resumen**

**Perfil:** `[ ]`

**Riesgo:** `[ ]`

**Autenticación:** `[ ]`

**Autorización:** `[ ]`

**Datos sensibles:** `[Sí / No]`

**MFA:** `[ ]`

**Auditoría:** `[ ]`

**Principal riesgo:** `[ ]`

**Principal mitigación:** `[ ]`

