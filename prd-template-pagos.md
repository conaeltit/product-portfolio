# PRD Template — Producto de Medios de Pago

> Template listo para usar al especificar un nuevo producto o feature en una PSP / pasarela de pagos.

---

## 📋 Metadatos

| Campo | Valor |
|---|---|
| **Nombre del producto / feature** | |
| **PM responsable** | |
| **Fecha de creación** | |
| **Última actualización** | |
| **Estado** | `Draft` / `In Review` / `Approved` / `In Development` / `Soft-Launched` / `Launched` |
| **Stakeholders** | |
| **Squad / equipo** | |

---

## 1. Contexto y problema

### 1.1 ¿Qué problema estamos resolviendo?

> Describe el problema desde la perspectiva del usuario / comercio. Siempre se debe ser lo más objetivo posible y evita hablar de la solución aquí.

**Problema:** [...]

**¿Para quién?** [Segmento: ecommerce, aseguradoras, clubes, etc.]

**¿Qué tan frecuente y grave es?** [...]

### 1.2 Evidencia del problema

> Datos cuantitativos y cualitativos que validan que vale la pena resolver esto.

- Dato 1: [e.g. "X% de los comercios abandonan el onboarding en el paso de integración"]
- Dato 2: [e.g. "Y tickets de soporte/mes relacionados a este tema"]
- Dato 3: [Research / entrevistas: quote representativo]

### 1.3 Contexto de negocio

¿Por qué ahora? ¿Qué oportunidad de mercado o presión competitiva lo hace urgente?

---

## 2. Objetivo

### 2.1 Goal principal

> Una sola oración. ¿Qué queremos lograr?

**Goal:** [...]

### 2.2 Métricas de éxito

| Métrica | Baseline actual | Target | Plazo |
|---|---|---|---|
| Tasa de conversión | | | |
| Time to integrate | | | |
| Tasa de abandono | | | |
| Churn de suscripciones | | | |
| Cantidad de problemas en integración | | | |
| [Otra métrica relevante] | | | |

### 2.3 Métricas de observación constante (no empeorar)

- [ ] Tasa de transacciones rechazadas
- [ ] Tasa de transacciones en proceso de reintento (estado intermedio)
- [ ] Tiempo de respuesta del checkout (p95)
- [ ] Tasa de chargebacks
- [ ] [Otra]

---

## 3. Usuarios y casos de uso

### 3.1 Usuarios primarios

| Usuario | Contexto | Job-to-be-done |
|---|---|---|
| Comercio (admin) | | |
| Comprador final | | |
| Integrador / dev | | |
| Equipo de soporte interno | | |

### 3.2 User stories principales

```
Como [tipo de usuario],
quiero [acción / capacidad],
para [beneficio / resultado esperado].

Criterios de aceptación:
- DADO [contexto] CUANDO [acción] ENTONCES [resultado esperado]
- DADO [contexto] CUANDO [acción] ENTONCES [resultado esperado]
```

**Historia 1:**
```
Como...
Quiero...
Para...

AC:
- DADO... CUANDO... ENTONCES...
```

**Historia 2:**
```
Como...
Quiero...
Para...

AC:
- DADO... CUANDO... ENTONCES...
```

---

## 4. Solución propuesta

### 4.1 Descripción de alto nivel

> Qué vamos a construir. Sin entrar en detalles de implementación aún.

### 4.2 Flujo principal (happy path)

```
[Paso 1] → [Paso 2] → [Paso 3] → [Resultado exitoso]
```

### 4.3 Flujos alternativos y de error

| Escenario | Comportamiento esperado |
|---|---|
| Pago rechazado por fondos insuficientes | |
| Timeout de red durante el proceso | |
| 3DS challenge requerido | |
| Usuario cancela a mitad del flujo | |
| [Otro escenario de error relevante] | |

### 4.4 Estados del sistema

> Para features de pagos, siempre mapear los estados posibles.

```
Estados posibles:
PENDING → PROCESSING → AUTHORIZED → CAPTURED → SETTLED
                    ↘ REJECTED
                    ↘ CANCELLED
                    ↘ REFUNDED
```

### 4.5 Wireframes / prototipos

> Links a Figma o imágenes embebidas.

---

## 5. Especificación técnica (para engineers)

### 5.1 Endpoints afectados o nuevos

```
POST /api/v1/[recurso]
GET  /api/v1/[recurso]/{id}
```

### 5.2 Payload de ejemplo

```json
{
  "field": "value"
}
```

### 5.3 Webhooks

| Evento | Descripción | Cuándo se dispara |
|---|---|---|
| `payment.authorized` | | |
| `payment.rejected` | | |
| `subscription.created` | | |

### 5.4 Consideraciones de seguridad

- [ ] ¿Maneja datos de tarjeta? → Scope PCI definido
- [ ] ¿Requiere autenticación 3DS 2.x?
- [ ] ¿Hay tokenización involucrada?
- [ ] ¿Qué datos se loggean y qué no?

### 5.5 Dependencias externas

| Dependencia | Tipo | Notas |
|---|---|---|
| Transbank | Adquirente | |
| Khipu | Transferencias | |
| [Otra] | | |

---

## 6. Scope

### 6.1 In scope (MVP)

- [ ] Feature A
- [ ] Feature B

### 6.2 Out of scope (explícitamente)

- Feature X (fase 2)
- Feature Y (decisión de no hacer)

### 6.3 Supuestos

1. [Supuesto 1]
2. [Supuesto 2]

---

## 7. Riesgos y mitigaciones

| Riesgo | Probabilidad | Impacto | Mitigación |
|---|---|---|---|
| Rechazo por parte del adquirente | Media | Alto | |
| Baja adopción por complejidad de integración | Alta | Alto | |
| Fallo en horario peak (Navidad, CyberDay) | Baja | Crítico | |

---

## 8. Plan de lanzamiento

### 8.1 Fases

| Fase | Descripción | Criterio de salida |
|---|---|---|
| Alpha | Prueba interna | 0 errores críticos |
| Beta cerrada | Piloto con N comercios | Conversión ≥ X% |
| GA | Disponible para todos | Métricas de guardia OK |

### 8.2 Rollback plan

> ¿Cómo revertimos si algo sale mal en producción?

---

## 9. Apéndice

### Glosario

| Término | Definición |
|---|---|
| PAT | Pago Automático con Tarjeta — débito automático en Chile |
| 3DS | 3-D Secure — protocolo de autenticación del pagador |
| Token de red | Token emitido por la red (Visa/MC) vinculado a un dispositivo |
| D+1 | Abono al comercio al día siguiente del pago |
| Chargeback | Disputa iniciada por el tarjetahabiente ante el emisor |
| Dunning | Proceso de reintento y comunicación en pagos recurrentes fallidos |

### Links de referencia

- [Documentación API VirtualPOS](https://virtualpos.readme.io/reference/getting-started-with-your-api)
- [Estándar EMV 3DS](https://www.emvco.com/emv-technologies/3d-secure/)
- [Normativa CMF medios de pago](https://www.cmfchile.cl/)
