---
name: srxmateo-skill-sello
description: Skill de despliegue absoluto. Genera README.md, sube a GitHub (SSH), y despliega en producción mediante PM2, Nginx (auto-puerto) y SSL (Certbot) en el VPS (Sin Docker). Actualiza automáticamente si ya fue desplegado.
---

# Instrucciones Generales
Cuando el usuario invoque esta skill (ej: "usa la skill-sello" o "ponle el sello"), asumes el rol de **Ingeniero DevOps y Release Manager Senior**. Tu misión es dar el "sello final" al proyecto: documentarlo, subirlo a su repositorio y publicarlo en producción de forma robusta.

**¡ESTRICTAMENTE PROHIBIDO USAR DOCKER!** Todo se gestiona nativamente con PM2 (Node/Ecosistemas), y Nginx.

## 1. Fase de Preparación, Inteligencia y Datos
1. **Detección Automática:** Analiza el código para saber qué tipo de proyecto es (Web, Plugin de Minecraft, Script CLI).
2. **Decisión de Destino:**
   - Si es una **Web (SaaS/App)**, asume que va al VPS. Pídele el **enlace de GitHub SSH**, el **Dominio** para Nginx/Certbot, y pregúntale si es la primera vez que se publica o una actualización.
   - Si es un **Script, Herramienta CLI, Plugin o proyecto entregable para cliente**, el flujo por defecto es **SOLO GITHUB**. Pregúntale al usuario: *"Veo que es un [Tipo], ¿solo generamos el README y lo subimos a GitHub, o también lo desplegamos en tu VPS?"*. Si el usuario elige "Solo GitHub", **OMITE COMPLETAMENTE LA FASE 3**.

## 2. Optimización SEO y Semántica (Para que Google te entienda)
**¡OBLIGATORIO CADA VEZ QUE USES LA SKILL!** Ya sea la primera vez que despliegas o solo una actualización, debes volver a escanear los archivos. Si hay código nuevo, páginas añadidas o mejoras, re-adapta el SEO antes de hacer commit:

1. **Meta Etiquetas (Detalladas):** Inyecta `<title>`, `<meta name="description">` y Open Graph (`og:`) en el `<head>` de **CADA PÁGINA**. Redacta textos ricos que le expliquen a Google *exactamente* para qué sirve esa página específica y qué problema resuelve.
2. **Semántica HTML:** Asegúrate de que el contenido usa etiquetas correctas (`<main>`, `<section>`, un solo `<h1>` por página).
3. **Archivos Clave:** Genera automáticamente un `robots.txt` permitiendo el rastreo y, si es posible, un `sitemap.xml` básico en la carpeta pública.

## 3. Documentación y Control de Versiones (GitHub)
Antes de subir nada al servidor remoto:
1. **Generar README.md:** Escanea todo el código actual y genera un archivo `README.md` espectacular y profesional. Incluye: insignias (badges) premium, descripción técnica del stack, instrucciones de uso y paleta de colores del proyecto.
2. **Commit y Push:** Usa la herramienta `run_command` para inicializar git (si no está), añadir todo, hacer commit (ej. "Deploy Sello Final") y forzar el push a la rama `main` usando el link SSH proporcionado por el usuario.

## 4. Despliegue en Producción (VPS) - *Solo si aplica*
Utilizarás las siguientes credenciales para acceder al servidor del usuario:
- **IP:** [YOUR_SERVER_IP]
- **Usuario:** [YOUR_SSH_USER]
- **Contraseña:** [YOUR_SSH_PASSWORD]
*(NOTA TÉCNICA PARA LA IA: Para automatizar comandos sin interacción en la terminal local, deberás usar la herramienta `sshpass`. Ej: `sshpass -p '[YOUR_SSH_PASSWORD]' ssh [YOUR_SSH_USER]@[YOUR_SERVER_IP] "comando"` o `sshpass -p '[YOUR_SSH_PASSWORD]' rsync -avz ...`).*

> [!CAUTION]
> **¡ADVERTENCIA DE SEGURIDAD PARA LA IA!**
> Estas credenciales están hardcodeadas aquí por comodidad del usuario. **NUNCA, BAJO NINGÚN CONCEPTO**, debes hacer push de este archivo exacto a GitHub mientras contenga estas claves. Si el usuario te pide subir o actualizar la carpeta de skills en GitHub en el futuro, **DEBES recordar borrar temporalmente estas credenciales** antes de hacer el commit y el push, y luego volver a ponerlas.

### Fase 4A: Primer Despliegue (Instalación Nueva)
1. **Transferencia:** Compila el proyecto localmente (si aplica, ej: `npm run build`). Sube la carpeta del proyecto a `/var/www/[nombre_proyecto]` en el VPS usando `rsync` (excluyendo `node_modules` y `.git`).
2. **Dependencias Remotas:** Conéctate por SSH e instala las dependencias (ej. `npm install`).
3. **Asignación de Puertos Anti-Bugs (¡CRÍTICO!):** Para evitar conflictos, inspecciona el servidor mediante SSH. Revisa los procesos activos de PM2 (`pm2 list`) y los puertos usados (`netstat -tuln` o revisando las configuraciones en `/etc/nginx/sites-enabled/`). Asigna **el siguiente puerto libre** de forma ascendente (ej. si el 3000 y 3001 están ocupados, usa el 3002).
4. **Lanzamiento con PM2:** Inicia el proyecto usando PM2 pasándole el puerto elegido. (ej: `pm2 start build/index.js --name "[proyecto]" --port [puerto_elegido]`). Guarda el estado con `pm2 save`.
5. **Configuración Nginx & Certbot:** Crea el archivo de configuración en `/etc/nginx/sites-available/[proyecto]`. Configúralo como *Reverse Proxy* (`proxy_pass`) apuntando al puerto elegido localmente en el VPS (`http://127.0.0.1:[puerto_elegido]`). Crea el symlink hacia `sites-enabled`, reinicia Nginx (`systemctl reload nginx`), y ejecuta Certbot para instalar el SSL (`certbot --nginx -d [dominio] --non-interactive --agree-tos -m mateodomina@gmail.com`).

### Fase 4B: Actualización (Despliegue Recurrente)
Si el usuario indica que es solo una actualización de un proyecto ya desplegado:
1. **Re-Auditoría SEO:** Asegúrate de haber cumplido la Fase 2 (readaptar meta-etiquetas y sitemap de cualquier página nueva o modificada).
2. Haz el Commit y Push a GitHub (Paso 3).
3. Sincroniza los archivos nuevos al VPS con `rsync` excluyendo `node_modules`.
3. Entra por SSH, reconstruye el proyecto si es necesario (`npm run build`) y ejecuta `pm2 restart [nombre_proyecto]`. **NO toques Nginx ni Certbot**, asume que el puerto y el proxy ya están configurados correctamente del despliegue original.

## 5. Reporte de Finalización
Entrega un mensaje de celebración indicando que el "Sello" ha sido aplicado. Muestra la URL oficial en vivo, el puerto interno asignado en el VPS, y confirma que el código está respaldado en GitHub.
