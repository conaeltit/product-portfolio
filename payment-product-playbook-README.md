# 🗂 Payment Product Playbook

> Frameworks y learnings de construir una pasarela de pagos desde cero en Chile.

Este repositorio documenta mi forma de pensar producto en el contexto de medios de pago: decisiones de arquitectura, tradeoffs, anti-patrones y lo que aprendí construyendo los productos de [VirtualPOS](https://www.virtualpos.cl/).

No es un manual genérico. Es el destilado de construir desde cero Web Checkout, SmartPOS, Suscripciones, Portal de Pagos, Link de Pago, Quick Checkout y PIX.

---

## 📂 Contenido

```
payment-product-playbook/
├── 01-fundamentos/
│   ├── ecosistema-pagos-chile.md
│   ├── actores-y-roles.md          # adquirentes, emisores, redes, PSPs
│   └── regulacion-cmf.md
├── 02-producto/
│   ├── checkout-design-principles.md
│   ├── flujos-de-pago-estados.md
│   ├── tokenizacion-y-3ds.md
│   └── metricas-clave.md
├── 03-suscripciones/
│   ├── arquitectura-estados-suscripcion.md
│   ├── dunning-logic.md
│   └── pat-vs-token.md
├── 04-presencial/
│   ├── smartpos-producto.md
│   └── integracion-sii-boleta.md
├── 05-go-to-market/
│   ├── segmentacion-industrias.md
│   └── modelo-tarifas.md
└── 06-learnings/
    ├── anti-patrones-checkout.md
    └── decisiones-que-tomaria-diferente.md
```

---

## 🧭 Conceptos clave que cubro

### Ecosistema de pagos en Chile
- Rol de Transbank como adquirente dominante
- Nuevos actores en el ecosistema de Chile y LatAm
- Klap y la transferencia bancaria como diferenciador local
- PIX como oportunidad cross-border con Brasil
- Regulación CMF y PCI-DSS en la práctica

### Arquitectura de un checkout de alta conversión
- Por qué el 3DS bien implementado sube conversión (no la baja)
- Tokenización de red vs tokenización de gateway
- Quick Checkout: la diferencia entre frictionless y fast
- Multiadquirencia como palanca de resiliencia y smart-routing

### Suscripciones y pagos recurrentes
- Débito automático PAT: cómo funciona en Chile y cómo optimizar la seguridad y conversión
- Diseño del ciclo de vida de una suscripción y adaptación a distintos clientes y usuarios
- Dunning logic: cuándo reintentar y cómo comunicarlo
- 97% de conversión no es magia, es diseño de estados
 
### POS presencial como producto
- SmartPOS: por qué el hardware importa menos que el software
- Integración con el SII: boleta electrónica como diferenciador
- Abono D+1: promesa de producto vs promesa operacional

---

## 💡 Principios que guían mi trabajo

1. **La conversión es la métrica madre del checkout** — todo lo demás es ruido si el pago no se completa.
2. **El error handling es UX** — cómo manejas el rechazo define la experiencia más que el flujo feliz.
3. **El PM de pagos debe leer los logs** — no para hacer debugging, sino para entender el comportamiento real.
4. **La integración es un producto** — el tiempo que le toma a un developer integrarse es una métrica de producto.
5. **Confía en los datos, desconfía de los self-reports** — los usuarios no saben por qué abandonan un checkout.

---

## 📬 Contexto

Construido mientras trabajaba en [VirtualPOS](https://www.virtualpos.cl/), pasarela de pagos con 5.000+ clientes en Chile.
