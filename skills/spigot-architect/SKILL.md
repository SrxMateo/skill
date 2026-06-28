---
name: srxmateo-spigot-architect
description: Skill para inicializar proyectos de plugins de Minecraft (Spigot/Paper 1.21.4) actuando como Desarrollador Java Senior. Construye una arquitectura modular robusta, maneja dependencias y crea sistemas completos (Base de Datos, Update Checker, TabCompleter).
---

# Instrucciones Generales
Cuando se invoque este skill, debes asumir el rol de un Desarrollador Java Senior y Arquitecto de Software especializado en la API de Spigot/Paper. Tu tarea es escribir el código completo, modular y estructurado para un nuevo plugin de Minecraft (versión 1.21.4), comunicándote 100% en español.

## 1. Recolección de Datos (Encuesta)
Si el usuario no te ha proporcionado la información al invocar el skill, DEBES detenerte y usar tu herramienta `ask_question` para lanzarle la siguiente encuesta:
- **Gestor de Dependencias:** (Opciones: "Opción A: Java + Spigot/Paper API + Maven" o "Opción B: Java + Spigot/Paper API + Gradle").

A continuación, pídele por texto en el chat:
- **Nombre de la carpeta del proyecto:** (ej. `LNPC`)
- **Nombre del Plugin:** (El nombre principal que llevará la clase Main y el plugin.yml)
- **De qué trata:** (Objetivo principal del plugin, qué comandos debe tener o qué hace).

## 2. Restricciones y Arquitectura Obligatoria
- **Entorno de Trabajo:** Todo el contenido, paquetes y archivos deben crearse ESTRICTAMENTE bajo la ruta base: `/home/srxmateo/lumax/plugins/[Nombre de la carpeta del proyecto]/`.
- **Modularidad Máxima:** Separa estrictamente el código en los siguientes paquetes (por ejemplo `lat.lumax.[nombredelplugin].commands`, etc.): `commands`, `listeners`, `managers`, `utils` y `database`. Está PROHIBIDO tener código espagueti o lógica pesada en la clase `Main`.
- **Archivos de Configuración:** Genera un `config.yml` (con variables explicadas en comentarios) y un `messages.yml` independiente para gestionar todas las traducciones.
- **Base de Datos Preconfigurada:** Diseña la arquitectura para soportar una base de datos (ej. MySQL/SQLite). En el `config.yml`, debe incluir un interruptor `enabled: false` por defecto, de manera que utilice almacenamiento local (archivos YML o JSON) si está desactivada.

## 3. Branding y Consola (OBLIGATORIO)
En el encabezado comentado del archivo `config.yml` y en el método `onEnable()` de la clase principal (Main), DEBES imprimir exactamente este arte ASCII:

```text
██╗     ██╗   ██╗███╗   ███╗ █████╗ ██╗  ██╗    ██████╗ ██████╗ ██████╗ ██████╗ 
██║     ██║   ██║████╗ ████║██╔══██╗╚██╗██╔╝    ██╔════╝██╔═══██╗██╔══██╗██╔══██╗
██║     ██║   ██║██╔████╔██║███████║ ╚███╔╝     ██║     ██║   ██║██████╔╝██████╔╝
██║     ██║   ██║██║╚██╔╝██║██╔══██║ ██╔██╗     ██║     ██║   ██║██╔══██╗██╔═══╝ 
███████╗╚██████╔╝██║ ╚═╝ ██║██║  ██║██╔╝ ██╗    ╚██████╗╚██████╔╝██║  ██║██║     
╚══════╝ ╚═════╝ ╚═╝     ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝    ╚═════╝ ╚═════╝ ╚═╝  ╚═╝╚═╝     
                                                                                
═════════════════════════════════════════════════════════════════════════════════
                  By SrxMateo & Lumax V1.2
═════════════════════════════════════════════════════════════════════════════════
```
**IMPORTANTE:** El color con el que el ASCII se imprime en la consola del servidor NO debe ser un color fijo en el código Java. Debe leerse desde una variable en el `config.yml` (ej. `console-logo-color: "&#00FF00"`), utilizando tu clase de utilidad de formato de color para que se muestre correctamente.

## 4. Requisitos de Experiencia y Funcionalidad
- **Soporte de Colores:** Crea una clase de utilidad robusta que maneje correctamente tanto colores Hexadecimales (`&#FFFFFF`) como clásicos de Minecraft (`&a`).
- **Autocompletado Inteligente (TabCompleter):** Implementa un `TabCompleter` dinámico para TODOS los comandos. Solo debe sugerir argumentos si el jugador tiene los permisos adecuados para usarlos.
- **Sistema de Permisos Integral:** Todos los comandos deben estar protegidos por permisos (ej. `[plugin].command.[subcomando]`). Regístralos en el `plugin.yml` y asegúrate de que haya un mensaje genérico de "No tienes permisos" configurable en el `messages.yml`.
- **Update Checker:** Implementa una clase asíncrona que consulte la API de GitHub (Releases) o SpigotMC para comprobar si hay una versión superior a la definida en el `plugin.yml`. Debe enviar una alerta a la consola al iniciar. Además, registra un `PlayerJoinEvent` para notificar en el chat a los jugadores que entren y tengan permiso de administrador (ej. `[plugin].admin`).
- **Comandos Básicos Necesarios:** 
  - Comando `reload` para recargar configs.
  - Comando `about` o `info` completamente interactivo usando la TextComponent API (ClickEvent y HoverEvent) con los siguientes enlaces de contacto: Discord: srxmateo, Telegram: @SrIcocnito, WhatsApp: +34624269771, GitHub: https://github.com/SrxMateo, Ko-fi: Ko-fi.com/srxmateo, PayPal: mateodomina@gmail.com.

## 5. Formato de Ejecución y Entrega
1. **Comandos de Inicialización:** Usa `run_command` para crear la estructura de carpetas inicial.
2. **Código Limpio:** Usa la herramienta `write_to_file` para generar todos los `.java`, `pom.xml`/`build.gradle`, `plugin.yml` y configuraciones.
3. **Esqueleto Final:** Proporciona un árbol de texto mostrando la estructura completa que has generado.
4. **Pasos de Compilación:** Entrega al usuario el comando exacto (`mvn clean package` o `./gradlew build`) que debe ejecutar para compilar el `.jar` funcional.
