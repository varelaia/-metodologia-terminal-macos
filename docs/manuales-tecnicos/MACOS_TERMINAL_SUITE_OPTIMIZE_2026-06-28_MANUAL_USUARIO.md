# MANUAL DE USUARIO: MACOS_TERMINAL_SUITE_OPTIMIZE (2026-06-28)

Este manual te explica de forma muy sencilla y sin tecnicismos cómo utilizar las nuevas capacidades instaladas en tu terminal macOS Sonoma para tu trabajo diario.

---

## 1. ¿Cómo navegar y buscar más rápido?

*   **Salta a cualquier carpeta al instante (zoxide):**
    En lugar de escribir comandos largos de navegación, escribe simplemente `z` y una palabra de la carpeta a la que quieres ir.
    *Ejemplo:* `z Code` te llevará directamente a tu carpeta de desarrollo.
*   **Busca en tu historial en un segundo (fzf):**
    Presiona la combinación de teclas **`Ctrl + R`** en tu terminal. Se abrirá una barra de búsqueda visual en vivo. Escribe parte de un comando antiguo que usaste y selecciónalo con las flechas de tu teclado.

---

## 2. Herramientas útiles instaladas

*   **Ver contenidos con colores (`bat`):**
    Usa el comando `bat [nombre-archivo]` para leer textos y códigos en tu pantalla de forma ordenada y con colores interactivos.
*   **Listar archivos modernos (`eza`):**
    Escribe `eza -l --grid` para listar tus archivos con colores descriptivos y soporte visual.
*   **Monitoreo visual del sistema (`btop`):**
    Escribe `btop` para ver el uso en tiempo real de tu procesador (CPU), memoria RAM, discos y velocidad de internet en un panel de control muy estético.
*   **Ejemplos prácticos rápidos (`tldr`):**
    Escribe `tldr [comando]` (ejemplo: `tldr tar` o `tldr git`) para ver ejemplos rápidos de uso de comandos en una sola pantalla.

---

## 3. Descarga y manipulación de archivos

*   **Descargar videos de Internet (`yt-dlp`):**
    Escribe en tu terminal `yt-dlp` seguido de la dirección web del video de YouTube que desees descargar.
    *Ejemplo:* `yt-dlp https://www.youtube.com/watch?v=jNQXAC9IVRw`
*   **Optimización del equipo (`optimizar_equipo.sh`):**
    Ejecuta el comando `./optimizar_equipo.sh` en tu carpeta Code para liberar espacio en disco y recuperar memoria RAM inactiva de forma segura.
