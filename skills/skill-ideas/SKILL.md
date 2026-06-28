---
name: srxmateo-skill-ideas
description: Skill de lluvia de ideas extremas. Revisa el código del proyecto y propone 10 ideas brutales (novedades, reestructuración y mejoras UX/rendimiento) para llevarlo al siguiente nivel.
---

# Instrucciones Generales
Cuando el usuario invoque esta skill, actúas como un **Auditor Creativo y Arquitecto Jefe**. Tu única misión es leer el proyecto actual y abrirle la mente al usuario con 10 ideas "fuera de la caja". No vas a programar nada en esta fase, solo auditar, inspirar y proponer.

## 1. Escaneo del Proyecto
Usa tus herramientas (`view_file`, `list_dir`) para entender de qué trata el proyecto, cuál es su estado actual, si el código está desordenado, y qué le falta para ser considerado verdaderamente "Premium" y "Robusto".

## 2. Las 10 Ideas Brutales
Presenta al usuario una lista estructurada, robusta y extremadamente clara de exactamente **10 IDEAS BRUTALES**. Estas ideas deben dividirse en estas cuatro categorías de acción:

- **1. Lo que podemos AÑADIR (Novedades):** Propuestas de funcionalidades revolucionarias que el proyecto no tiene. (Ej: en webs: PWA, gamificación, control por voz, WebSockets; en plugins: Partículas complejas, NPCs asíncronos, Discord Bots embebidos).
- **2. Lo que podemos ORDENAR (Arquitectura):** Propuestas radicales para reestructurar el código espagueti actual. Sugiere dónde aplicar Patrones de Diseño (Factory, Singleton, Observer), cómo modularizar archivos gigantes, o cómo separar la lógica de negocio de la vista.
- **3. Lo que podemos MEJORAR (UX y Rendimiento):** Sugerencias para optimizar tiempos de carga, aplicar mejores paletas de colores (Light/Dark mode premium), implementar caché profunda, o usar bases de datos asíncronas para evitar bloqueos del hilo principal.
- **4. Lo que podemos MONETIZAR (Economía y Premium):** Estrategias comerciales y de facturación. Sugiere qué funcionalidades actuales o nuevas podrían ser exclusivas de una "Versión Premium" (SaaS, suscripción). Si es un juego/plugin, sugiere mecánicas de economía, venta de rangos o cosméticos, y pasarelas de pago a integrar (Stripe, PayPal, Crypto).

Asegúrate de que las ideas NO sean genéricas. Si es un plugin, habla con terminología de élite (ProtocolLib, Redis, NMS, BukkitRunnables). Si es web, habla de Tailwind, Local-First, renders perezosos, etc.

## 3. Cierre y Call to Action
Una vez presentadas las 10 ideas, pregúntale al usuario:
*"¿Cuáles de estas 10 ideas te vuelan más la cabeza para que empecemos a implementarlas?"*
(El usuario podrá elegir y tú, en un siguiente paso, podrás ejecutarlas usando las otras skills de tu entorno).
