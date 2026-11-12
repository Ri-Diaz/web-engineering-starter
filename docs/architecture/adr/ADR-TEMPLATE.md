# **ADR-XXXX — \[Título de la decisión\]**

**Estado:** `[Proposed | Accepted | Rejected | Deprecated | Superseded]`  
**Fecha:** `[YYYY-MM-DD]`  
**Responsable:** `[Nombre / Equipo]`  
**Decisores:** `[Personas / roles]`  
**Relacionado con:** `[Requirement / Issue / Spec / ADR]`

---

# **1\. Contexto**

Describir el problema o situación que obliga a tomar una decisión.

Responder, cuando corresponda:

* ¿qué problema existe?  
* ¿por qué debe decidirse ahora?  
* ¿qué restricciones afectan la decisión?  
* ¿qué riesgos existen?  
* ¿qué requisitos dependen de esta decisión?

### **Contexto**

`[Escribir aquí]`

---

# **2\. Decisión**

Describir claramente qué se decidió.

La decisión debe poder resumirse en una frase.

### **Decisión**

> `[Adoptaremos / utilizaremos / evitaremos ...]`

---

# **3\. Drivers de decisión**

Registrar los factores que influyeron principalmente.

* `[Simplicidad]`  
* `[Seguridad]`  
* `[Performance]`  
* `[Mantenibilidad]`  
* `[Costo]`  
* `[Experiencia del equipo]`  
* `[Compatibilidad]`  
* `[Escalabilidad]`  
* `[Restricción regulatoria]`

No todos los factores tienen la misma importancia.

---

# **4\. Criterios de evaluación**

| Criterio | Peso |
| ----- | ----- |
| `[Mantenibilidad]` | `[Alta / Media / Baja]` |
| `[Costo]` | `[ ]` |
| `[Complejidad]` | `[ ]` |
| `[Seguridad]` | `[ ]` |
| `[Performance]` | `[ ]` |

Utilizar únicamente cuando ayude a comparar alternativas.

---

# **5\. Alternativas consideradas**

## **Opción A — `[Nombre]`**

### **Descripción**

`[ ]`

### **Ventajas**

* `[ ]`  
* `[ ]`

### **Desventajas**

* `[ ]`  
* `[ ]`

### **Riesgos**

* `[ ]`

---

## **Opción B — `[Nombre]`**

### **Descripción**

`[ ]`

### **Ventajas**

* `[ ]`

### **Desventajas**

* `[ ]`

### **Riesgos**

* `[ ]`

---

## **Opción C — `[Nombre]`**

**Opcional**

`[ ]`

---

# **6\. Comparación**

Cuando sea útil:

| Criterio | Opción A | Opción B | Opción C |
| ----- | ----- | ----- | ----- |
| Simplicidad | `[ ]` | `[ ]` | `[ ]` |
| Mantenibilidad | `[ ]` | `[ ]` | `[ ]` |
| Seguridad | `[ ]` | `[ ]` | `[ ]` |
| Costo | `[ ]` | `[ ]` | `[ ]` |
| Performance | `[ ]` | `[ ]` | `[ ]` |
| Riesgo | `[ ]` | `[ ]` | `[ ]` |

No es necesario cuantificar artificialmente una decisión si la comparación cualitativa es suficiente.

---

# **7\. Justificación**

Explicar por qué la alternativa seleccionada representa el mejor equilibrio para el contexto actual.

### **Razones principales**

1. `[ ]`  
2. `[ ]`  
3. `[ ]`

---

# **8\. Consecuencias positivas**

La decisión permitirá:

* `[ ]`  
* `[ ]`  
* `[ ]`

---

# **9\. Consecuencias negativas**

La decisión implica aceptar:

* `[ ]`  
* `[ ]`  
* `[ ]`

Las consecuencias negativas no deben ocultarse.

Una decisión arquitectónica normalmente representa un trade-off.

---

# **10\. Riesgos residuales**

| Riesgo | Probabilidad | Impacto | Mitigación |
| ----- | ----- | ----- | ----- |
| `[Riesgo]` | `[B/M/A]` | `[B/M/A]` | `[ ]` |

---

# **11\. Impacto arquitectónico**

La decisión afecta:

* frontend;  
* backend;  
* base de datos;  
* infraestructura;  
* seguridad;  
* testing;  
* deployment;  
* observabilidad;  
* documentación;  
* integraciones.

### **Detalle**

`[ ]`

---

# **12\. Impacto en datos**

**Aplicable:** `[Sí / No]`

Si aplica:

* migraciones necesarias: `[ ]`;  
* compatibilidad: `[ ]`;  
* riesgo de pérdida: `[ ]`;  
* rollback: `[ ]`.

---

# **13\. Impacto en seguridad**

**Aplicable:** `[Sí / No]`

### **Consideraciones**

`[ ]`

---

# **14\. Impacto operacional**

Considerar:

* complejidad de despliegue;  
* monitoreo;  
* backups;  
* recuperación;  
* soporte;  
* mantenimiento.

### **Impacto**

`[ ]`

---

# **15\. Dependencias introducidas**

| Dependencia | Tipo | Justificación |
| ----- | ----- | ----- |
| `[ ]` | `[Framework / servicio / librería]` | `[ ]` |

Si no se agregan dependencias:

`No aplica.`

---

# **16\. Vendor lock-in**

**Nivel:** `[Nulo / Bajo / Medio / Alto]`

### **Justificación**

`[ ]`

### **Estrategia de salida**

`[No requerida / Descripción]`

---

# **17\. Compatibilidad**

¿La decisión rompe comportamiento existente?

* No  
* Sí

Si sí:

### **Impacto**

`[ ]`

### **Estrategia de migración**

`[ ]`

---

# **18\. Rollback**

¿Puede revertirse la decisión?

* Fácilmente  
* Con esfuerzo moderado  
* Difícilmente  
* Prácticamente irreversible

### **Procedimiento**

`[ ]`

---

# **19\. Validación**

¿Cómo comprobaremos que la decisión funciona?

* `[Test]`  
* `[Métrica]`  
* `[Prueba de concepto]`  
* `[Monitoreo]`

### **Criterio de éxito**

`[ ]`

---

# **20\. Evidencia**

Registrar evidencia relevante.

Puede incluir:

* benchmarks;  
* documentación;  
* pruebas internas;  
* métricas;  
* incidentes;  
* experimentos;  
* requisitos.

### **Evidencia**

`[ ]`

---

# **21\. Fecha de revisión**

**Revisión necesaria:** `[Sí / No]`

**Fecha sugerida:** `[YYYY-MM-DD / evento]`



