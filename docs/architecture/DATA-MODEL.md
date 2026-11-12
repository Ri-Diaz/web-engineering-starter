# **`07 — DATA MODEL`**

**`Proyecto:`** `[Nombre del proyecto]`  
**`Versión:`** `1.0`  
**`Aplicable:`** `WEBAPP / SENSITIVE / STATIC con persistencia`

---

## **`1. Propósito`**

`Este documento describe la estructura principal de los datos del sistema, sus relaciones y las reglas necesarias para mantener su integridad.`

`No es necesario completarlo si el proyecto no posee persistencia relevante.`

---

## **`2. Tecnología`**

**`Base de datos:`** `[PostgreSQL / SQLite / MySQL / otra]`

**`Acceso:`**

* `ORM`  
* `SQL`  
* `Query Builder`  
* `Otro`

**`Herramienta:`** `[Django ORM / Prisma / etc.]`

---

## **`3. Entidades principales`**

| `Entidad` | `Responsabilidad` | `Módulo propietario` |
| ----- | ----- | ----- |
| `[Usuario]` | `[Descripción]` | `[users]` |
| `[Pedido]` | `[Descripción]` | `[orders]` |
| `[Producto]` | `[Descripción]` | `[catalog]` |

`Cada entidad debe tener una responsabilidad clara.`

---

## **`4. Relaciones`**

`Ejemplo:`

`USER`

 `│`

 `│ 1`

 `│`

 `│ N`

 `▼`

`ORDER`

 `│`

 `│ 1`

 `│`

 `│ N`

 `▼`

`ORDER_ITEM`

 `│`

 `│ N`

 `│`

 `│ 1`

 `▼`

`PRODUCT`

### **`Relaciones relevantes`**

| `Entidad A` | `Relación` | `Entidad B` | `Eliminación` |
| ----- | ----- | ----- | ----- |
| `[User]` | `1:N` | `[Order]` | `[RESTRICT/CASCADE/etc.]` |

`Las cascadas deben justificarse cuando puedan producir pérdida de información.`

---

## **`5. Modelo por entidad`**

### **`[Entidad]`**

**`Propósito:`** `[ ]`

| `Campo` | `Tipo` | `Obligatorio` | `Regla` |
| ----- | ----- | ----- | ----- |
| `id` | `[UUID/int]` | `Sí` | `PK` |
| `[campo]` | `[tipo]` | `Sí/No` | `[constraint]` |
| `created_at` | `datetime` | `Sí` | `automático` |
| `updated_at` | `datetime` | `Sí` | `automático` |

---

## **`6. Invariantes`**

`Registrar reglas que siempre deben cumplirse.`

`Ejemplo:`

`email debe ser único`

`fecha_fin >= fecha_inicio`

`total >= 0`

| `ID` | `Regla` | `Enforcement` |
| ----- | ----- | ----- |
| `INV-001` | `[Regla]` | `[DB / App / Ambos]` |

`Cuando sea razonable, las reglas críticas deberían protegerse también en la base de datos.`

---

## **`7. Estados`**

`Cuando una entidad tenga un ciclo de vida, definir estados explícitos.`

`Ejemplo:`

`DRAFT`

  `↓`

`PENDING`

  `↓`

`APPROVED`

  `↓`

`COMPLETED`

`Evitar múltiples booleanos si un único estado representa mejor el dominio.`

---

## **`8. NULL y valores desconocidos`**

`NULL debe tener un significado conocido.`

`Distinguir cuando sea necesario:`

`TRUE`

`FALSE`

`UNKNOWN`

`No convertir automáticamente UNKNOWN en FALSE.`

---

## **`9. Identificadores y formato canónico`**

`Definir identificadores importantes:`

| `Dato` | `Formato` | `Único` |
| ----- | ----- | ----- |
| `[email]` | `lowercase normalizado` | `Sí` |
| `[identificador]` | `[formato]` | `[ ]` |

`Datos como email, teléfono, RUT, SKU o identificadores externos deberían normalizarse cuando corresponda.`

---

## **`10. Eliminación`**

`Definir estrategia por entidad cuando sea relevante:`

* `borrado físico;`  
* `soft delete;`  
* `inactivación;`  
* `anulación;`  
* `archivado.`

`No tratar estos conceptos como equivalentes.`

`Por ejemplo:`

`ANULAR OPERACIÓN`

`≠`

`ELIMINAR REGISTRO`

---

## **`11. Datos derivados`**

`Evitar almacenar información que pueda calcularse fácilmente salvo que exista una razón concreta.`

| `Dato` | `Fuente` | `Persistido` |
| ----- | ----- | ----- |
| `[edad]` | `fecha nacimiento` | `No` |
| `[total]` | `líneas pedido` | `[Sí/No]` |

`Si se persiste un dato derivado, debe existir una fuente de verdad claramente definida.`

---

## **`12. Clasificación de datos`**

`Utilizar cuando corresponda:`

`PUBLIC`

`INTERNAL`

`PERSONAL`

`SENSITIVE`

`SECRET`

| `Dato` | `Clasificación` |
| ----- | ----- |
| `[nombre]` | `PERSONAL` |
| `[token]` | `SECRET` |

---

## **`13. Retención`**

`Para información personal o relevante:`

| `Dato` | `Retención` | `Motivo` |
| ----- | ----- | ----- |
| `[ ]` | `[ ]` | `[ ]` |

`No conservar información indefinidamente sin una razón.`

---

## **`14. Integridad y concurrencia`**

`Identificar operaciones susceptibles a conflictos.`

`Ejemplos:`

* `reservas;`  
* `stock;`  
* `cupos;`  
* `estados;`  
* `edición simultánea.`

**`Estrategia:`** `[transaction / constraint / locking / versioning / no aplica]`

---

## **`15. Índices`**

`Crear índices según consultas reales.`

| `Campo(s)` | `Motivo` |
| ----- | ----- |
| `[email]` | `búsqueda frecuente` |
| `[status, created_at]` | `listado filtrado` |

`No indexar automáticamente todas las columnas.`

---

## **`16. Migraciones`**

`Todos los cambios de esquema deben realizarse mediante migraciones versionadas.`

`Flujo:`

`Schema actual`

     `↓`

`Migration`

     `↓`

`Testing`

     `↓`

`Deployment`

     `↓`

`Verification`

`Los cambios destructivos requieren revisión especial.`

---

## **`17. Migración de datos`**

`Cuando sea necesario importar información:`

`Fuente`

  `↓`

`Validación`

  `↓`

`Normalización`

  `↓`

`Detección de conflictos`

  `↓`

`Importación`

  `↓`

`Verificación`

`Los importadores no deberían sobrescribir información silenciosamente.`

---

## **`18. Datos de prueba`**

`Preferir:`

* `factories;`  
* `fixtures sintéticos;`  
* `datos anonimizados.`

`Evitar utilizar información personal real en ambientes de desarrollo.`

---

## **`19. Backup`**

**`Aplicable:`** `[Sí / No]`

**`Frecuencia:`** `[ ]`

**`Retención:`** `[ ]`

**`Restore probado:`** `[Sí / No]`

`Un backup no se considera confiable si nunca se ha comprobado que puede restaurarse.`

---

## **`20. Diagrama definitivo`**

`Insertar aquí ERD o enlace al modelo actualizado.`

`[Diagrama / referencia]`

---

## **`21. Riesgos`**

| `Riesgo` | `Impacto` | `Mitigación` |
| ----- | ----- | ----- |
| `[ ]` | `[ ]` | `[ ]` |

---

## **`22. Checklist`**

* `Entidades principales definidas.`  
* `Relaciones documentadas.`  
* `Invariantes identificadas.`  
* `Unicidad definida.`  
* `NULL tiene semántica clara.`  
* `Estados correctamente modelados.`  
* `Estrategia de eliminación definida.`  
* `Datos sensibles identificados.`  
* `Migraciones controladas.`  
* `Concurrencia considerada cuando aplica.`  
* `Índices responden a consultas reales.`  
* `Backup considerado cuando aplica.`

