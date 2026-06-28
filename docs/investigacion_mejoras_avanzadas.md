# Investigación de Mejoras Avanzadas para Entornos macOS y Terminal

Esta investigación recopila mejoras profundas y configuraciones recomendadas para potenciar tu productividad, optimizar el rendimiento del sistema y afinar la experiencia de desarrollo interactivo en macOS.

---

## 1. Herramientas Modernas para Línea de Comandos (CLI)

Estas utilidades reemplazan comandos clásicos de Unix por alternativas optimizadas en velocidad y visualización:

| Comando Clásico | Alternativa Moderna | Beneficio | Comando de Instalación |
| :--- | :--- | :--- | :--- |
| `cat` | **`bat`** | Muestra el contenido de archivos con resaltado de sintaxis, números de línea e integración directa con Git. | `brew install bat` |
| `grep` | **`ripgrep` (`rg`)** | Buscador de texto dentro de archivos extremadamente rápido (el estándar usado por agentes de IA). Respeta `.gitignore` por defecto. | `brew install ripgrep` |
| `find` | **`fd`** | Buscador de archivos intuitivo, rápido y con colores por defecto. Mucho más simple de usar que `find`. | `brew install fd` |
| `ls` | **`eza`** | Reemplazo moderno de `ls` con soporte para colores, visualización de metadatos de Git y estructura de árbol integrada. | `brew install eza` |
| `curl` | **`httpie`** | Cliente HTTP interactivo amigable para probar APIs directamente desde la terminal con formato JSON automático. | `brew install httpie` |

---

## 2. Plugins de Consola para Zsh (Productividad Visual)

Podemos añadir inteligencia visual directamente a tu Zsh instalando estos plugins populares con Homebrew e integrándolos en tu `.zshrc`:

1.  **`zsh-autosuggestions` (Sugerencias Inteligentes):**
    *   *Qué hace:* Sugiere comandos basados en tu historial a medida que escribes en un color gris atenuado. Presionas la flecha derecha para completarlo.
    *   *Instalación:* `brew install zsh-autosuggestions`
2.  **`zsh-syntax-highlighting` (Resaltado en Vivo):**
    *   *Qué hace:* Resalta en verde los comandos válidos antes de presionar Enter, y en rojo los comandos erróneos o inexistentes.
    *   *Instalación:* `brew install zsh-syntax-highlighting`

---

## 3. Ajustes de Sistema Ocultos de macOS (Defaults)

Puedes afinar el comportamiento de macOS ejecutando estos comandos de configuración del sistema (`defaults write`) para acelerar la experiencia de usuario:

### 3.1. Mostrar siempre archivos ocultos en Finder
Útil para ver archivos de configuración (como `.git`, `.zshrc`, `.ssh`) sin presionar combinaciones de teclado:
```bash
defaults write com.apple.finder AppleShowAllFiles -bool true && killall Finder
```

### 3.2. Mostrar siempre las extensiones de archivos en Finder
Previene la confusión de abrir archivos ejecutables pensando que son de texto:
```bash
defaults write NSGlobalDomain AppleShowAllExtensions -bool true && killall Finder
```

### 3.3. Aumentar la velocidad de repetición de teclas (Key Repeat)
Indispensable para programadores que navegan por el código usando el teclado (hace que el cursor se mueva mucho más rápido al mantener presionadas las teclas direccionales):
```bash
# Establecer un retraso de repetición de tecla muy bajo (mínimo de macOS)
defaults write NSGlobalDomain KeyRepeat -int 1
defaults write NSGlobalDomain InitialKeyRepeat -int 10
```
*Nota: Requiere cerrar sesión y volver a iniciar para que aplique en todo el sistema.*

### 3.4. Desactivar la corrección automática de texto a nivel global
Evita que macOS intente corregir o cambiar palabras técnicas o código mientras escribes en editores sencillos o terminales:
```bash
defaults write NSGlobalDomain NSAutomaticSpellingCorrectionEnabled -bool false
```
