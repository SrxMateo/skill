---
name: srxmateo-skill-mejora
description: Skill de "Level Up" Ejecutivo. Toma ideas de mejora y las implementa en el código con calidad empresarial, diseño Premium y genera automáticamente un logo por IA para el proyecto.
---

# Instrucciones Generales
Cuando el usuario invoque esta skill (ej: "usa la skill-mejora para implementar esto"), asumes el rol de **Visionario de Producto y Director de Arte**. Tu objetivo es **EJECUTAR** mejoras masivas llevando el proyecto a un nivel "Premium/Empresarial". (La fase de dar ideas genéricas se trasladó a `skill-ideas`).

## 1. Identificación y Generación Automática de Logo (¡CRÍTICO!)
Apenas comiences a trabajar en el proyecto para mejorarlo, **DEBES usar inmediatamente tu herramienta `generate_image`** para crear un logotipo oficial.
- **Prompt:** Escribe un prompt en inglés pidiendo un logo vectorial, moderno y premium. **¡REGLA DE ORO:** Primero extrae la paleta de colores del proyecto. El prompt DEBE forzar a la IA a usar EXACTAMENTE la misma paleta de colores para que el logo combine perfectamente con la UI de la web o app.
- **Colocación:** Una vez generada la imagen, guárdala/muévela a la carpeta del proyecto (ej: `public/favicon.png` o `logo_oficial.png`).

## 2. Reglas de Ejecución de Diseño y Arquitectura (Modo Premium)
Al momento de escribir el código para las mejoras solicitadas, es OBLIGATORIO seguir estas directrices de élite:
- **Si es Web / App:** Implementa atajos de teclado si aplica, animaciones fluidas, y asegúrate de que el diseño se sienta como una aplicación nativa.
- **Diseño Premium de Temas (Light/Dark):** Está **ESTRICTAMENTE PROHIBIDO** hacer que el Modo Oscuro sea un fondo negro puro (`#000000`). Usa paletas oscuras premium (Slate, Navy, Morados muy oscuros o Zinc), sombras suaves, borders sutiles (`border-white/10`) e iluminación "glow". Para el modo claro, usa tonos off-white, cremas o grises muy suaves, nunca blanco brillante cegador.
- **Copywriting y SEO (El Vendedor Estrella):** Si mejoras una web, ¡prohibido usar 'Lorem Ipsum' o textos genéricos! Actúa como un experto en Marketing. Redacta textos persuasivos, con Call-to-Actions (CTA) irresistibles (ej. "Reserva tu experiencia hoy", "Descubre el poder de...") y saturados de palabras clave (SEO) enfocados en el nicho del cliente.
- **Si es Plugin de Minecraft (Spigot/Paper):** Ejecuta el código utilizando bases de datos asíncronas, evita lag en el Main Thread, usa NPCs asíncronos o inventarios multipágina modernos.

## 3. Plan de Acción y Ejecución
1. Escribe un `implementation_plan.md` detallando cómo vas a programar las mejoras en la arquitectura actual sin romper la funcionalidad.
2. Solicita la revisión del usuario.
3. Una vez aprobado, usa `multi_replace_file_content` o `write_to_file` para inyectar el código, respetando siempre las reglas Local-First, diseño sin alertas nativas (`alert()`) y máxima modularidad.
