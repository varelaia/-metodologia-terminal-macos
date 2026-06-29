# MANUAL TÉCNICO: MACOS_TERMINAL_SUITE_OPTIMIZE (2026-06-28)

Este manual documenta la arquitectura técnica, variables de entorno, configuraciones del sistema operativo y scripts de aprovisionamiento y optimización segura implementados en el entorno de macOS.

---

## 1. Arquitectura y Variables del Sistema

El entorno operativo se basa en la shell nativa **Zsh** en macOS Sonoma. Toda la inicialización y dependencias se cargan a través del archivo de perfil `~/.zshrc`.

### 1.1. Modificaciones en `.zshrc`
Se añadieron los siguientes bloques para inicializar las herramientas en cada sesión:
```zsh
# Enlace de Python 3.12 (Homebrew)
export PATH="/usr/local/opt/python@3.12/libexec/bin:$PATH"

# Inicialización de zoxide (Navegación inteligente de carpetas)
eval "$(zoxide init zsh)"

# Inicialización de fzf (Buscador difuso interactivo)
source <(fzf --zsh)

# Plugins de Zsh (Autosuggestions & Syntax Highlighting)
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# Abrir siempre en la carpeta de trabajo especificada
cd /Users/yarelyvarela/Code
```

---

## 2. Configuraciones de Defaults de macOS
Se aplicaron preferencias del sistema mediante el comando nativo `defaults write` para aumentar el rendimiento y accesibilidad en el desarrollo:

```bash
# Mostrar siempre archivos ocultos en Finder (incluye dotfiles)
defaults write com.apple.finder AppleShowAllFiles -bool true

# Mostrar siempre las extensiones de archivos en Finder
defaults write NSGlobalDomain AppleShowAllExtensions -bool true

# Configurar velocidad máxima de repetición de teclas (Key Repeat Rate)
defaults write NSGlobalDomain KeyRepeat -int 1
defaults write NSGlobalDomain InitialKeyRepeat -int 10

# Desactivar la autocorrección global de ortografía de macOS
defaults write NSGlobalDomain NSAutomaticSpellingCorrectionEnabled -bool false
```

---

## 3. Suite de Herramientas Instaladas

### 3.1. Homebrew (Fórmulas)
*   **zoxide (v0.9.9):** Reemplazo inteligente de `cd`.
*   **fzf (v0.73.1):** Fuzzy Finder interactivo.
*   **git-delta (v0.19.2):** Paginador y visualizador de diffs premium.
*   **bat (v0.26.1):** Clon de `cat` con resaltado de sintaxis.
*   **ripgrep (v15.1.0):** Buscador de texto en archivos ultra veloz.
*   **fd (v10.4.2):** Buscador interactivo de archivos.
*   **eza (v0.23.4):** Sucesor moderno de `ls` con colores.
*   **httpie (v3.2.4):** Cliente HTTP CLI.
*   **ffmpeg (v8.1.2):** Procesador de audio y video.
*   **imagemagick (v7.1.2):** Manipulador de imágenes.
*   **yt-dlp (v2026.6.9):** Descargador multimedia.

### 3.2. Python 3.12 (Librerías de Oficina/Multimedia)
Instaladas en el espacio de usuario (`~/.local/lib/python3.12`) y enlazadas con soporte de compatibilidad para Python 3.13+:
*   `pandas` (v3.0.4) y `openpyxl` (v3.1.5) para manipulación de XLSX.
*   `reportlab` (v5.0.0) y `pypdf` (v6.14.2) para creación y edición de PDFs.
*   `pillow` (v12.2.0) para procesamiento de PNG/JPG.
*   `pydub` (v0.25.1) para corte y edición de MP3/WAV.
*   **`audioop-lts` (v0.2.2) (Fix de compatibilidad):** Parche para proveer el módulo `audioop` que fue removido en la librería estándar de las versiones de Python 3.13 y 3.14.

---

## 4. Evidencia Verbatim de Funcionamiento (E2E)

### 4.1. Descarga E2E con `yt-dlp`
```text
[youtube] Extracting URL: https://www.youtube.com/watch?v=jNQXAC9IVRw
[youtube] jNQXAC9IVRw: Downloading webpage
[youtube] [jsc:deno] Solving JS challenges using deno
[download] Destination: Me at the zoo [jNQXAC9IVRw].mp4
[download] 100.0% of  614.43KiB at    5.07MiB/s ETA 00:00
[download] 100% of  614.43KiB in 00:00:00 at 1.62MiB/s
```

### 4.2. Validación de Carga de Librerías Python
```text
$ python3 -c "import pandas, openpyxl, reportlab, pypdf, PIL, pydub; print('=== PYTHON LIBRARIES: OK ===')"
=== PYTHON LIBRARIES: OK ===
```

### 4.3. Resultado de Optimización de Sistema (`optimizar_equipo.sh`)
```text
======================================================================
  INFORME DE MÈTRICAS DE OPTIMIZACIÓN
======================================================================
Espacio en Disco Liberado: 3 GB  (Antes: 394 GB | Ahora: 397 GB)
Memoria RAM Recuperada:    122 MB  (Antes: 64 MB  | Ahora: 186 MB)
======================================================================
```
