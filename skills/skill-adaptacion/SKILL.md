---
name: srxmateo-skill-adaptacion
description: Skill súper robusta para adaptar cualquier proyecto web existente a un diseño Mobile-First nativo. Reestructura el Tailwind CSS, inyecta botones de descarga de APK y crea guías interactivas para instalación en iOS (PWA).
---

# Instrucciones Generales
Cuando el usuario invoque esta skill (ej: "usa la skill de adaptación en esta página"), asumes el rol de **Especialista en UI/UX Móvil y Desarrollador Frontend Elite**. Tu objetivo principal es transformar una web que se ve mal (o normal) en celulares, en una experiencia que parezca y se sienta como una **Aplicación Móvil Nativa de Alta Gama**.

## 1. Auditoría de Código y Tailwind
Antes de tocar nada, DEBES leer a fondo el código fuente (`view_file` en las rutas principales, layouts y componentes).
- **Entiende el Tailwind:** Busca y marca mentalmente clases rígidas (`w-[800px]`, `h-screen`, `flex-row` forzados) o paddings/márgenes excesivos que hacen que la web tenga un scroll horizontal molesto en móviles.
- **Entiende la Funcionalidad:** Estudia qué hace el proyecto para decidir la mejor navegación móvil (¿necesita un menú hamburguesa o una barra de navegación inferior tipo Instagram/TikTok?).

## 2. Rediseño Móvil Estricto (Mobile-First)
Refactoriza el código usando Tailwind CSS bajo la filosofía Mobile-First pura:
- **Estructura Base:** El diseño base en las clases de Tailwind (sin prefijos) DEBE ser para celulares. Usa `w-full`, `flex-col`, `px-4` o `px-6`. Usa los prefijos `md:` y `lg:` ÚNICAMENTE para adaptar el contenido si alguien lo abre en PC.
- **Navegación App-Like:** Elimina los "Headers" gigantes clásicos de PC. Implementa en su lugar una **Bottom Navigation Bar** (barra inferior) pegada a la pantalla (`fixed bottom-0 w-full`) o un menú lateral (Drawer) elegante.
- **Accesibilidad Táctil:** Modifica absolutamente todos los botones e inputs interactivos para que tengan un tamaño mínimo de `min-h-[48px]` o `min-h-[3rem]`. Los botones pequeños son un error grave en móviles.
- **Colocación Inteligente de Herramientas:** Todas las opciones, filtros, menús o paneles de control DEBEN rediseñarse de forma inteligente para el alcance del pulgar. Usa "Bottom Sheets" (paneles deslizantes desde abajo), botones flotantes (FAB) o carruseles horizontales ocultos. Está prohibido dejar controles críticos fuera del alcance natural de una mano.

## 3. Elementos Obligatorios: Descarga APK & Guía iOS (¡CRÍTICO!)
Sin importar de qué trate la web, DEBES diseñar e inyectar en la interfaz dos secciones nuevas y súper Premium:

1. **Botón de Descarga APK (Android):** 
   Crea un botón o sección "Call to Action" masivo y visualmente espectacular. Debe tener el icono de Android, un texto claro (ej: "Descargar APK Nativa") y usar colores que destaquen. Puede ser un componente pegajoso (Sticky) o un gran banner en el Hero de la versión móvil.
   
2. **Guía de Instalación para iOS (Añadir a Inicio):** 
   Dado que iOS no usa APKs, crea un componente visual hermoso (un Modal de ayuda, una Card, o un Banner) que le explique a los usuarios de iPhone cómo instalar la app.
   *Debe contener instrucciones claras y gráficas:* "1. Toca el icono de Compartir (icono cuadrado con flecha) en Safari. 2. Desliza hacia abajo y selecciona 'Añadir a la pantalla de inicio'. 3. ¡Disfruta la app a pantalla completa!". Utiliza iconos que simulen la UI de Apple para mayor realismo.

## 4. Ejecución Robusta
- Modifica el código utilizando `multi_replace_file_content` o `write_to_file`.
- Modularidad: Si estás en SvelteKit o Astro, extrae el "Botón APK" y el "Modal de iOS" en sus propios componentes (`ApkDownloadButton.svelte`, `IosInstallGuide.svelte`) para mantener el código limpio.
- **Valida:** Asegúrate de que las animaciones (transiciones) se vean fluidas a 60fps en pantallas móviles (usa `transform`, `opacity` y `transition-all`).
