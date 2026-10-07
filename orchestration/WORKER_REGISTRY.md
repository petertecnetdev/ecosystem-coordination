# Cutinapp Auxiliary Worker Registry

## Orchestrator
- W00 — Global Cutinapp Orchestrator — conta principal — cadence: hourly :54

## AUX-01
capacity: 3 daily workers
- W1 — Cutinapp Code Scout — automation `6ac63ead13d08191a4d6c01e2e0d9181` — strengths: code, product, general development
- W2 — Cutinapp UX QA Revenue — automation `6ac63eaefff081919c27b012e699c255` — strengths: UX, QA, funnel, revenue
- W3 — Cutinapp Growth Content — automation `6ac63eb0df0c819196cb464e9dd2e673` — strengths: growth, content, market

## AUX-02
capacity: 3 daily workers
- W1 — Backend, Data & Security — automation `6ac63f1438508191b3d3fe9d7524bdf8` — strengths: API, database, auth, security
- W2 — Frontend, PWA & SEO — automation `6ac63f15e9e881918a81cb1057741ef8` — strengths: React, performance, PWA, technical SEO
- W3 — Integrations & Reliability — automation `6ac63f18a35c8191b3daa673dc59ee0b` — strengths: email, queues, webhooks, automation, observability

## AUX-03
capacity: 3 daily workers
- W1 — Instagram & Social Growth — automation `6ac63f8109f88191857bd8a425e242d1` — strengths: Instagram, social distribution
- W2 — SEO, Blog & Public Discovery — automation `6ac63f82b67c8191bfa83f7bf632c88c` — strengths: SEO editorial, blog, public discovery
- W3 — Producer Acquisition & Conversion — automation `6ac63f84bf9c81919067f463be9ecef9` — strengths: acquisition, landing, onboarding, conversion

## AUX-04 .. AUX-11
status: NOT_CONFIGURED
capacity_when_configured: 3 daily workers each

## Allocation policy
- Prefer matching worker strengths.
- W00 may override specialization for P0/P1 or when idle capacity is more valuable elsewhere.
- Target model: roughly 70% specialization / 30% dynamic allocation.
- Never assign duplicate implementation scope while an active claim exists.
