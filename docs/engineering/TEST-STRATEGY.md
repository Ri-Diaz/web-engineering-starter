# 10 — TEST STRATEGY

**Proyecto:** `[Nombre del proyecto]`  
**Versión:** `1.0`  
**Perfil:** `[STATIC | WEBAPP | SENSITIVE]`  
**Última actualización:** `[YYYY-MM-DD]`

---

## 1. Propósito

Este documento define qué debe probarse, con qué profundidad y en qué nivel.

La estrategia debe ser proporcional al riesgo del proyecto.

El objetivo no es maximizar la cantidad de tests ni perseguir un porcentaje de cobertura arbitrario, sino reducir el riesgo de:

* regresiones;  
* errores de negocio;  
* fallos de integración;  
* accesos incorrectos;  
* pérdida o corrupción de datos;  
* errores en flujos críticos.

---

## 2. Principios

1. `Probar comportamiento, no implementación interna.`  
2. `Priorizar funcionalidades críticas.`  
3. `Automatizar lo repetible.`  
4. `Utilizar el nivel de prueba más bajo que entregue confianza suficiente.`  
5. `Evitar E2E innecesarios.`  
6. `Incluir casos negativos y límites.`  
7. `Toda regresión importante debería generar una prueba.`  
8. `Los tests deben ser reproducibles y deterministas.`  
9. `Una prueba frágil o incomprensible tiene poco valor.`  
10. `Coverage es una señal, no una garantía de calidad.`

---

## 3. Perfil de testing

**Clasificación:** `[STATIC / WEBAPP / SENSITIVE]`

**Riesgo general:** `[Bajo / Medio / Alto / Crítico]`

### Principal riesgo

[ ]

---

## 4. Estrategia por riesgo

### Riesgo alto

Ejemplos:

* autenticación;  
* autorización;  
* pagos;  
* información sensible;  
* reglas críticas;  
* migraciones;  
* concurrencia;  
* auditoría.

Requieren mayor profundidad y normalmente más de un nivel de prueba.

### Riesgo medio

Ejemplos:

* formularios;  
* búsquedas;  
* filtros;  
* exportaciones;  
* integraciones secundarias.

### Riesgo bajo

Ejemplos:

* textos;  
* estilos;  
* contenido estático;  
* cambios visuales menores.

---

## 5. Matriz de riesgo

| `Funcionalidad` | `Impacto` | `Probabilidad` | `Riesgo` | `Pruebas` |
| ----- | ----- | ----- | ----- | ----- |
| `[Login]` | `Alto` | `Medio` | `Alto` | `Integration + E2E + Security` |
| `[Regla de negocio]` | `Alto` | `Medio` | `Alto` | `Unit + Integration` |
| `[Filtro]` | `Medio` | `Medio` | `Medio` | `Unit / Integration` |
| `[Contenido]` | `Bajo` | `Bajo` | `Bajo` | `Manual / Smoke` |

---

## 6. Niveles de prueba

### Unit

Para:

* reglas de negocio;  
* cálculos;  
* validadores;  
* transformaciones;  
* estados;  
* funciones con lógica.

Ejemplo:

entrada

  `↓`

regla

  `↓`

resultado esperado

---

### Integration

Para verificar colaboración entre componentes.

Ejemplos:

Application + Database

Controller + Service + Persistence

API + Authentication

Especialmente importante para:

* persistencia;  
* constraints;  
* transacciones;  
* autorización;  
* migraciones;  
* integraciones.

---

### End-to-End

Para flujos críticos desde la perspectiva del usuario.

Ejemplo:

Login

  `↓`

Crear reserva

  `↓`

Confirmar

  `↓`

Visualizar resultado

No convertir cada requisito en un E2E.

---

## 7. Qué probar por funcionalidad

Toda feature relevante debería considerar:

Happy path

Negative cases

Boundary cases

Permissions

Failure scenarios

Regression cases

No todos aplican siempre.

---

## 8. Reglas de negocio

Las reglas importantes deben tener pruebas directas.

Ejemplo:

BR-003

"Una reserva no puede finalizar antes de comenzar"

          `↓`

Unit test

Priorizar aquí lógica determinista y crítica.

---

## 9. Datos e integridad

Cuando exista persistencia, probar cuando corresponda:

* unicidad;  
* relaciones;  
* constraints;  
* NULL;  
* transacciones;  
* estados;  
* eliminación;  
* migraciones;  
* concurrencia.

Ejemplo:

email duplicado

      `↓`

operación rechazada

Las invariantes de DATA-MODEL.md deberían poder verificarse.

---

## 10. Autenticación y autorización

**Aplicable:** `[Sí / No]`

Probar tanto accesos permitidos como rechazados.

No basta con:

Admin puede editar

También debe verificarse:

Usuario normal NO puede editar

Cuando corresponda probar:

* login;  
* logout;  
* sesión expirada;  
* recuperación;  
* permisos;  
* ownership;  
* roles;  
* operaciones administrativas.

---

## 11. Integraciones externas

**Aplicable:** `[Sí / No]`

Para servicios externos definir:

| `Integración` | `Estrategia` |
| ----- | ----- |
| `[Email]` | `Fake / Mock` |
| `[Pago]` | `Sandbox` |
| `[API]` | `Contract + Integration` |

Probar al menos:

* respuesta exitosa;  
* error;  
* timeout;  
* respuesta inválida.

No hacer que la suite dependa innecesariamente de Internet real.

---

## 12. Casos negativos

Incluir cuando sean relevantes:

* datos inválidos;  
* recurso inexistente;  
* permiso insuficiente;  
* estado incompatible;  
* sesión expirada;  
* envío duplicado;  
* dependencia externa caída.

El sistema debe fallar de manera controlada.

---

## 13. Casos límite

Probar valores cercanos a los límites.

Ejemplos:

mínimo

mínimo - 1

máximo

máximo + 1

También:

* fechas;  
* tamaño de archivos;  
* longitud de campos;  
* cantidad máxima de elementos.

---

## 14. Regresiones

Cuando se corrija un defecto relevante:

Bug

 `↓`

Test que reproduce el bug

 `↓`

Fix

 `↓`

Test queda permanente

Esto evita que el mismo problema reaparezca silenciosamente.

---

## 15. Frontend

Cuando exista interfaz interactiva, revisar:

* comportamiento;  
* validación;  
* estados de carga;  
* errores;  
* navegación;  
* responsive;  
* interacción mediante teclado.

No testear detalles internos irrelevantes de componentes.

---

## 16. Accesibilidad

**Aplicable:** `[Sí / No]`

Puede combinar:

### Automatizado

* labels;  
* roles;  
* errores básicos;  
* estructura;  
* contraste detectable.

### Manual

* teclado;  
* foco;  
* orden de navegación;  
* interacción;  
* zoom;  
* lector de pantalla cuando el riesgo lo justifique.

---

## 17. Performance

**Aplicable:** `[Sí / No]`

Validar únicamente métricas que tengan objetivos definidos.

Puede incluir:

* Core Web Vitals;  
* tamaño de bundle;  
* tiempos de respuesta;  
* consultas críticas;  
* carga.

No realizar pruebas de carga sin una capacidad esperada definida.

---

## 18. Seguridad

Las pruebas de seguridad deben alinearse con SECURITY.md.

Según el proyecto pueden incluir:

* autorización;  
* autenticación;  
* sesiones;  
* validación;  
* CSRF;  
* headers;  
* rate limiting;  
* uploads;  
* dependencia vulnerable;  
* secret scanning.

---

## 19. Smoke tests

Después de un despliegue comprobar rápidamente que las capacidades esenciales funcionan.

Ejemplos:

* sitio carga;  
* aplicación inicia;  
* login responde;  
* endpoint principal funciona;  
* conexión a base de datos está disponible.

Los smoke tests no sustituyen la suite completa.

---

## 20. Datos de prueba

Preferir:

* factories;  
* fixtures sintéticos;  
* datos anonimizados.

Evitar datos personales reales.

Los tests deben preparar y limpiar su propio estado cuando corresponda.

---

## 21. Mocks y fakes

Usar principalmente en límites externos.

Preferencia general:

Domain            → real

Application       → real

Database          → real en integration

External service  → fake/mock cuando corresponda

Evitar mockear toda la aplicación porque puede producir pruebas que no representan el comportamiento real.

---

## 22. Determinismo

Los tests no deberían depender innecesariamente de:

* hora real;  
* Internet;  
* orden de ejecución;  
* datos compartidos;  
* aleatoriedad sin control.

Una prueba debe poder reproducirse.

---

## 23. Flaky tests

Los tests intermitentes son defectos.

No utilizar retries permanentes simplemente para obtener CI verde.

Si uno no puede corregirse inmediatamente:

* registrar el problema;  
* aislarlo temporalmente;  
* definir una acción de corrección.

---

## 24. Coverage

No utilizar cobertura como principal indicador de calidad.

Un proyecto puede tener:

95 % coverage

y seguir sin probar los comportamientos importantes.

Si se establece un threshold, debe utilizarse principalmente para detectar retrocesos evidentes.

La prioridad son los módulos de mayor riesgo.

---

## 25. CI

Pipeline recomendado:

Lint

 `↓`

Type check

 `↓`

Unit tests

 `↓`

Integration tests

 `↓`

Security checks

 `↓`

Build

 `↓`

E2E críticos

No todos los proyectos requieren todas las etapas.

---

## 26. Quality gates

Antes de merge, según corresponda:

* build exitoso;  
* lint exitoso;  
* type checking exitoso;  
* unit tests exitosos;  
* integration tests exitosos;  
* E2E críticos exitosos;  
* controles de seguridad exitosos;  
* no existen regresiones conocidas no documentadas.

Una prueba no debe eliminarse únicamente para permitir un merge.

---

## 27. Estrategia por perfil

### STATIC

Mínimo recomendado:

Build

Smoke

Responsive

Accessibility

Links

Performance básica

---

### WEBAPP

Además:

Unit

Integration

E2E críticos

Database

Authentication

Authorization

API

Security

---

### SENSITIVE

Además:

Permisos reforzados

Integridad

Concurrencia

Migraciones

Auditoría

Regresiones críticas

Security testing

Restore cuando corresponda

---

## 28. Trazabilidad

Cuando exista riesgo suficiente, relacionar:

Requirement

    `↓`

Spec

    `↓`

Test

Ejemplo:

| `Requisito` | `Prueba` |
| ----- | ----- |
| `RF-004` | `test_create_order` |
| `BR-002` | `test_invalid_transition` |
| `RNF-SEC-003` | `test_unauthorized_access` |

No es necesario mantener trazabilidad formal para pruebas triviales.

---

## 29. Definition of Tested

Una funcionalidad se considera suficientemente probada cuando:

* cumple criterios de aceptación;  
* reglas críticas están cubiertas;  
* casos negativos relevantes están considerados;  
* permisos están verificados;  
* errores esperables están manejados;  
* regresiones relevantes están cubiertas;  
* CI pasa.

La profundidad dependerá del riesgo.

---

## 30. Checklist preproducción

* Suite crítica pasa.  
* Flujos principales fueron verificados.  
* Autorización revisada.  
* Migraciones probadas cuando aplica.  
* Datos de prueba no contienen información real sensible.  
* Seguridad crítica validada.  
* Smoke test definido.  
* Errores críticos resueltos.  
* Problemas conocidos aceptados.  
* Rollback considerado cuando corresponde.

---

## 31. Herramientas

Definir después de seleccionar stack.

**Unit:** `[ ]`  
**Integration:** `[ ]`  
**E2E:** `[ ]`  
**Accessibility:** `[ ]`  
**Performance:** `[ ]`  
**Security:** `[ ]`

No incorporar herramientas únicamente para llenar esta sección.

---

## 32. Riesgos y deuda

### Riesgo principal de testing

[ ]

### Deuda conocida

| `ID` | `Problema` | `Riesgo` | `Acción` |
| ----- | ----- | ----- | ----- |
| `TEST-TD01` | `[ ]` | `[ ]` | `[ ]` |

---

## 33. Resumen

**Perfil:** `[ ]`

**Riesgo:** `[ ]`

**Unit:** `[Sí / No]`

**Integration:** `[Sí / No]`

**E2E:** `[Sí / No]`

**Security testing:** `[ ]`

**Flujo más crítico:** `[ ]`

**Principal riesgo de regresión:** `[ ]`


