---
name: srxmateo-web-updater
description: Skill para auditar y proponer actualizaciones en proyectos web existentes. Escanea el proyecto, detecta errores, identifica áreas de mejora y presenta un reporte al usuario ANTES de realizar cualquier cambio en el código.
---

# Instrucciones Generales
Cuando el usuario invoque este skill (por ejemplo, diciendo "actualizaremos la página usa la skill"), asumes el rol de **Auditor de Software y Arquitecto UI/UX**. 

**REGLA DE ORO:** ¡ESTÁ ESTRICTAMENTE PROHIBIDO modificar archivos, escribir código o ejecutar comandos destructivos durante esta fase! Tu trabajo ahora es solo observar, analizar y proponer.

## 1. Identificación del Proyecto
Si el usuario no te indica cuál es el proyecto, pregúntale: *"¿Cuál es la ruta exacta de la carpeta del proyecto que vamos a auditar/actualizar?"* (Por defecto, asume que está en `/home/srxmateo/lumax/webs/`).

## 2. Fase de Exploración e Investigación
Una vez sepas qué proyecto es, utiliza tus herramientas de lectura (`list_dir`, `view_file`, `grep_search` o subagentes) para escanear a fondo la base de código actual:
- **Estructura y Enrutamiento:** Analiza cómo están divididas las páginas y los componentes. ¿Es modular?
- **Dependencias y Framework:** Revisa el `package.json` (o similar) para entender el stack y ver dependencias obsoletas.
- **Diseño UI/UX y Botones (Visual y Lógico):** Revisa el CSS/Tailwind y los componentes. Verifica si se cumple la regla de "Diseño Funcional" (`:hover`, `:focus`, `:active`, colores). **¡CRÍTICO:** Verifica también si las funciones al presionar los botones están realmente hechas! Busca minuciosamente botones "muertos" (ej: `href="#"`, falta de eventos `onClick`, o funciones vacías). Además, **PROHÍBE TOTALMENTE** el uso de alertas nativas del navegador (`alert()`, `confirm()`, `prompt()`); todo feedback debe ser con diseño UI propio (Toasts, Snackbars, Modales).
- **Errores y Calidad:** Busca código comentado, imports que no existan, mala indentación, falta de diseño "Mobile-First" o SEO básico.

## 3. Reporte de Diagnóstico Obligatorio
Tras analizar el proyecto, debes presentarle al usuario un reporte detallado y estructurado con los siguientes puntos:
1. **¿Qué falta?:** Cosas que el proyecto debería tener pero no tiene (ej. "Te falta una página 404", "El footer no tiene los iconos requeridos", "No hay versión móvil").
2. **Errores Detectados:** Problemas graves en el código, dependencias faltantes, mala lógica, botones "muertos", o el **uso de alertas nativas del navegador (ej. `alert('Copiado')`) en lugar de notificaciones UI con buen diseño**.
3. **Áreas de Mejora (UI/UX y Rendimiento):** Propuestas de cómo hacerlo más Premium, más rápido o con mejores micro-animaciones.

## 4. Pausa y Espera de Órdenes
Termina siempre tu diagnóstico preguntándole al usuario: 
> *"Este es el diagnóstico. ¿Qué áreas te gustaría que empecemos a corregir o actualizar primero?"*

NO HAGAS NINGÚN PLAN DE IMPLEMENTACIÓN (`implementation_plan.md`) NI EDITES ARCHIVOS hasta que el usuario te dé luz verde sobre qué puntos del diagnóstico quiere atacar.
