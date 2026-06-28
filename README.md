# Metodología de Terminal macOS (CPMAI + Premortem)

Este repositorio contiene la **Metodología de Configuración, Optimización y Seguridad de la Terminal en macOS** implementada bajo los principios **CPMAI** y **Premortem Gates** de la Doctrina Varela.

Está estructurado como una **Skill de desarrollo activa y cargable** para ser utilizada por agentes inteligentes o desarrolladores de forma directa.

---

## 1. Estructura del Repositorio

*   [`SKILL.md`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/SKILL.md): Define las instrucciones y objetivos de la skill para agentes.
*   [`scripts/`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/scripts/): Scripts interactivos de automatización del entorno.
    - [`instalar_entorno.sh`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/scripts/instalar_entorno.sh): Script de aprovisionamiento guiado de dependencias (Xcode Tools, Homebrew, Git, Node, etc.).
    - [`optimizar_equipo.sh`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/scripts/optimizar_equipo.sh): Script de mantenimiento preventivo y limpieza segura con **Premortem Gate** y métricas de espacio liberado.
*   [`docs/`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/): Documentación teórica, decálogos operativos y análisis de riesgos.
    - [`manual_terminal_antigravity.txt`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/manual_terminal_antigravity.txt): Manual Técnico, Operativo y de Usuario integrado.
    - [`falsabilidad_premortem_terminal.md`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/falsabilidad_premortem_terminal.md): Análisis prospectivo de fallas del entorno de desarrollo.
    - [`doctrina_varela_puntualizada.md`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/doctrina_varela_puntualizada.md): Síntesis conceptual de la doctrina.
    - [`auditoria_software_recomendado.md`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/auditoria_software_recomendado.md): Diagnóstico de herramientas de desarrollo.
    - [`investigacion_mejoras_avanzadas.md`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/docs/investigacion_mejoras_avanzadas.md): Análisis de optimización avanzada de macOS.
*   [`examples/`](file:///Users/yarelyvarela/Code/metodologia-terminal-macos/examples/): Copias en formato de texto plano (`.txt`) para distribución externa rápida sin bloqueos de seguridad.

---

## 2. Cómo instalar esta Skill en tu Sistema

Para que tu agente (Antigravity o Claude) cargue de forma automática esta metodología en su contexto en cualquier nueva terminal o sesión, puedes copiar el archivo `SKILL.md` y sus subdirectorios en las carpetas de configuración global de tus agentes:

### Para Antigravity (Ruta global):
```bash
mkdir -p ~/.gemini/config/skills/metodologia-terminal-macos
cp -R * ~/.gemini/config/skills/metodologia-terminal-macos/
```

### Para Claude (Ruta global):
```bash
mkdir -p ~/.claude/skills/metodologia-terminal-macos
cp -R * ~/.claude/skills/metodologia-terminal-macos/
```

---

## 3. Instrucciones de Uso de los Scripts

### 3.1. Aprovisionamiento (Instalación de Entorno)
Para instalar Xcode Command Line Tools, Homebrew, Git, Node y configurar el PATH en una máquina macOS limpia:
```bash
chmod +x scripts/instalar_entorno.sh
./scripts/instalar_entorno.sh
```

### 3.2. Optimización y Purga Segura
Para realizar la limpieza de espacio en disco de forma segura utilizando validación de puertos y capturando métricas de rendimiento en vivo:
```bash
chmod +x scripts/optimizar_equipo.sh
./scripts/optimizar_equipo.sh
```
*(Nota: El script te mostrará una tabla final interactiva con la cantidad exacta de GB de disco liberados y MB de memoria RAM recuperados).*
