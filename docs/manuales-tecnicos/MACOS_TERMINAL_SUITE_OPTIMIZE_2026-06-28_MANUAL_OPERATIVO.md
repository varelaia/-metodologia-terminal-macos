# MANUAL OPERATIVO: MACOS_TERMINAL_SUITE_OPTIMIZE (2026-06-28)

Este manual detalla las tareas de mantenimiento rutinario, ramas de decisión y resolución de problemas para operar el entorno de desarrollo y productividad en macOS de forma segura.

---

## 1. Mantenimiento Periódico del Entorno

### 1.1. Tarea Semanal: Optimización de Almacenamiento y RAM
Ejecutar el script de optimización de forma semanal para purgar cachés acumuladas y archivos temporales de compilación.
```bash
cd /Users/yarelyvarela/Code
./optimizar_equipo.sh
```

### 1.2. Tarea Quincenal: Actualización de Homebrew y Paquetes
Para garantizar parches de seguridad activos en tus dependencias locales:
```bash
brew update && brew upgrade
```

---

## 2. Ramas de Decisión y Resolución de Errores

### 2.1. Incidentes de Python (PEP 668: Externally Managed Environment)
*   **Problema:** Al intentar instalar un paquete de Python de forma global (`pip3 install xyz`), Python bloquea la acción indicando que el entorno está gestionado por Homebrew.
*   **Decisión/Solución:**
    1.  Si es un script local de desarrollo y requieres la librería globalmente en tu espacio de usuario, pasa el flag de exclusión seguro:
        ```bash
        pip3 install --user --break-system-packages xyz
        ```
    2.  Si es un proyecto estructurado, inicializa y activa un entorno virtual (`venv`):
        ```bash
        python3 -m venv .venv
        source .venv/bin/activate
        pip install xyz
        ```

### 2.2. Error de audioop en `pydub` (Python 3.13+)
*   **Problema:** Al importar `pydub` o manipular MP3/WAV, el script falla con `ModuleNotFoundError: No module named 'audioop'`.
*   **Decisión/Solución:** El módulo `audioop` fue removido en la librería estándar de Python 3.13+. Instala el paquete de reemplazo compatible:
    ```bash
    pip3 install --user --break-system-packages audioop-lts
    ```

### 2.3. Fallo de Enlace en Homebrew (`brew link` error)
*   **Problema:** Homebrew instala una fórmula pero da error de enlace porque ya existe un binario manual previo en `/usr/local/bin`.
*   **Decisión/Solución:** Ejecutar el enlace con sobreescritura de forma forzada:
    ```bash
    brew link --overwrite <nombre-paquete>
    ```
    *Ejemplo para yt-dlp:* `brew link --overwrite yt-dlp`

---

## 3. Errores a NO cometer (Anti-patrones)

1.  **NO usar `sudo pip`:** Nunca ejecutes instalaciones de Python con `sudo`. Esto corrompe los permisos del sistema de archivos de tu usuario. Usa siempre `--user --break-system-packages` o entornos virtuales.
2.  **NO ignorar el Premortem Gate:** No borres cachés de desarrollo (`npm cache clean`, `.yarn-cache`) si tienes servidores de Node o bases de datos corriendo activamente en tu Mac, ya que interrumpirá y corromperá el flujo de tus proyectos.
