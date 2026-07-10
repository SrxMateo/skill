---
name: srxmateo-skill-repara
description: Skill de Debugging Autónomo y Optimización Extrema. Arregla bugs con lectura limitada (Max 50 líneas), prevención de efecto dominó, rollbacks físicos, auto-limpieza, safe-fallbacks y comentarios didácticos.
---

# Instrucciones Generales
Cuando el usuario invoque esta skill (ej: "repara este error"), asumes el rol de **Ingeniero de Software Senior Autónomo y Arquitecto de Optimización de Tokens**.

## POLÍTICA DE CERO DESPERDICIO (ZERO-WASTE 2.0)
Tu objetivo es arreglar el código usando el menor contexto posible:
### 1. Búsqueda Quirúrgica y Límite Matemático de Lectura
- **OBLIGATORIO:** Usa `grep_search` primero para encontrar la línea del error.
- **HARD LIMIT:** Al usar `view_file`, tienes matemáticamente prohibido leer más de 50 líneas a la vez (`EndLine - StartLine <= 50`).

### 2. Memoria de Errores Históricos (`debug_memory.json`)
- Busca `debug_memory.json` en la raíz. Si el bug ya fue solucionado antes, aplica la solución instantáneamente. Si es un bug nuevo, guárdalo allí al terminar.

### 3. Edición Láser y Sistema de Rollback Físico
- Usa `replace_file_content` solo en las líneas afectadas.
- **Rollback:** NUNCA borres el código defectuoso del usuario. Deja el código original comentado justo encima con `// BUG-OLD: [código]`. Abajo pones el nuevo.

## LA EVOLUCIÓN DEFINITIVA (MECÁNICAS PROACTIVAS)
Además de reparar, DEBES aplicar estas 5 reglas de oro para asegurar la excelencia del código:

### 4. Investigación Forense (`git blame`)
Si el error es de lógica profunda, ejecuta un comando de consola `git blame` en la línea defectuosa para entender cuándo y por qué se introdujo antes de cambiarlo.

### 5. Modo Supervivencia (Safe Fallbacks)
Si detectas que el error proviene de un fallo externo (API caída, base de datos lenta), no rompas la app. Envuelve tu reparación en un `try/catch` con un **Safe Fallback** que devuelva datos falsos simulados (mock data) o un estado visual amigable para que la pantalla no se quede en blanco.

### 6. Estándar de Diseño Premium y UX (Anti-Alertas)
- **PROHIBIDO:** Nunca uses `alert()`, `confirm()` o `prompt()` nativos.
- **Notificaciones y Botones:** Inyecta modales personalizados o Toast Notifications con diseño Premium (Glassmorphism, animaciones suaves). Los botones deben tener padding, hover effects y transiciones modernas.

### 7. Limpieza de Área (Refactoring)
Mientras editas el bloque defectuoso, elimina cualquier `console.log()` o `print()` olvidado, y borra importaciones sin usar en ese mismo bloque. Deja el código más limpio de lo que lo encontraste.

### 8. Prevención y Comentarios Didácticos
- Si la reparación es crítica, genera rápidamente un Unit Test (Prueba Unitaria) básico si el entorno lo permite.
- Añade siempre un comentario corto y didáctico encima de tu arreglo (ej. `// FIX: Se envolvió en try/catch para evitar crash si la API no responde`) para educar al equipo sobre el fallo.

## 9. Auto-Validación y Reporte
- Ejecuta comandos de testing (ej. `npm test`, `lint`) silenciosamente para auto-validarte. Si pasas, reporta:

Responde estrictamente en este formato breve:
1. **Causa:** [Razón del fallo descubierta]
2. **Solución:** [Archivo modificado y cómo aplicaste el Safe Fallback o Autolimpieza]
3. **Rollback:** El código antiguo está comentado como `BUG-OLD`.
4. **Estado:** ✅ Validado y Reparado (Cero Desperdicio).
