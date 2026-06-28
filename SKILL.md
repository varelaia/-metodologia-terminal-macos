---
name: metodologia-terminal-macos
description: "Instrucciones metodológicas y scripts interactivos para configurar, optimizar y asegurar la terminal en macOS (CPMAI + Premortem Gates)."
---

# Metodología de Terminal macOS (CPMAI + Premortem)

Esta skill contiene las directrices metodológicas de Varela y los scripts de automatización para estructurar y mantener un entorno de desarrollo eficiente, seguro y optimizado en macOS.

---

## 1. Estructura de la Skill

La skill está distribuida de la siguiente manera en este repositorio:
*   `SKILL.md` (Este archivo): Define los metadatos y objetivos metodológicos cargables por agentes.
*   `scripts/`: Contiene los scripts interactivos ejecutables con gates de seguridad.
    - [instalar_entorno.sh](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/scripts/instalar_entorno.sh) (Aprovisionamiento del entorno macOS).
    - [optimizar_equipo.sh](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/scripts/optimizar_equipo.sh) (Optimizador con Premortem Gate).
*   `docs/`: Documentación teórica, manuales y auditorías de referencia.
    - [manual_terminal_antigravity.txt](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/manual_terminal_antigravity.txt) (Manual Técnico/Operativo).
    - [falsabilidad_premortem_terminal.md](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/falsabilidad_premortem_terminal.md) (Análisis de riesgos).
    - [doctrina_varela_puntualizada.md](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/doctrina_varela_puntualizada.md) (Decálogo CPMAI).
    - [auditoria_software_recomendado.md](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/auditoria_software_recomendado.md) (Diagnóstico de software).
    - [investigacion_mejoras_avanzadas.md](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/investigacion_mejoras_avanzadas.md) (Mejoras y configuraciones de macOS).
*   `examples/`: Versiones en formato de texto plano (`.txt`) para distribución y compartición segura por canales de mensajería o nube.
    - `instalar_entorno.txt`
    - `optimizar_equipo.txt`

---

## 2. Directrices de Uso de la Metodología

### 2.1. Aprovisionamiento Seguro (Fase I & II)
Al inicializar un entorno o aprovisionar una nueva máquina, debe utilizarse el instalador guiado interactivo para resolver las dependencias básicas del sistema, garantizando que el PATH y el gestor de paquetes (Homebrew) se configuren bajo un flujo secuencial libre de errores.

### 2.2. Optimización Semanal (Fase V / CPMAI)
El optimizador del equipo (`optimizar_equipo.sh`) debe ejecutarse de forma recurrente para depurar cachés temporales e innecesarias. Este script incluye:
1.  **Premortem Gate (Fase de Riesgos):** Revisa puertos en uso y entornos activos de desarrollo antes de borrar cachés críticas (npm, yarn) para prevenir bloqueos de proyectos activos.
2.  **Métricas Claras:** Calcula y expone los GB exactos de disco recuperados como evidencia de éxito de la tarea.

### 2.3. Autenticación y Seguridad (Fase IV)
Toda interacción con repositorios remotos debe realizarse estrictamente por SSH (criptografía Ed25519) enlazado al Llavero de macOS para evitar la exposición de credenciales y tokens en texto plano.
