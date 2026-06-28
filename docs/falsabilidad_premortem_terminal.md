# Análisis de Falsabilidad y Premortem en la Configuración de Entornos

Este documento aplica dos marcos analíticos críticos de la filosofía científica y la gestión de proyectos de ingeniería (la **Falsabilidad** y el **Análisis Premortem**) a la arquitectura de terminal macOS y Git que hemos configurado.

---

## 1. Falsabilidad (¿Cómo demostramos que nuestro sistema puede fallar?)
La **falsabilidad** (concepto de Karl Popper) establece que para que una hipótesis o sistema sea válido y robusto, debe ser posible diseñar una prueba que demuestre su fallo. En desarrollo de entornos, esto se traduce en **pruebas de estrés y límites**.

### Falsabilidad aplicada a nuestra configuración:
1.  **Redirección automática de la Shell (`cd` en `.zshrc`):**
    *   *Hipótesis:* "La terminal siempre se abre en `/Users/yarelyvarela/Code`".
    *   *Prueba de Falsabilidad:* ¿Qué pasa si el directorio `Code` es renombrado o eliminado? 
    *   *Resultado:* La shell lanzará un error silencioso `cd: no such file or directory` y se quedará en el directorio raíz.
    *   *Mitigación:* El script debería validar la existencia de la carpeta antes de cambiar de directorio (ej: `[ -d ~/Code ] && cd ~/Code`).
2.  **Script de Instalación (`instalar_entorno.sh`):**
    *   *Hipótesis:* "El script configura todo de forma desatendida".
    *   *Prueba de Falsabilidad:* Ejecutar el script sin conexión a internet o sin permisos de administrador (`sudo`).
    *   *Resultado:* El instalador fallará al descargar Homebrew o instalar paquetes via `curl`/`brew`.
    *   *Mitigación:* Se agregaron validaciones de estado y conectividad antes de iniciar las descargas críticas en el script.
3.  **Conexión SSH a GitHub:**
    *   *Hipótesis:* "La llave SSH conecta con GitHub de manera segura y definitiva".
    *   *Prueba de Falsabilidad:* Ejecutar `ssh -T git@github.com`. Si la llave pública en GitHub es eliminada, el comando debe fallar inmediatamente con `Permission denied (publickey)`.
    *   *Resultado:* Falsable y verificado. La prueba falló originalmente hasta que agregaste la llave pública, validando la seguridad del canal.

---

## 2. Análisis Premortem (Adelantarse al desastre)
El **Análisis Premortem** (Gary Klein) consiste en asumir que el proyecto o sistema **ha fallado de forma catastrófica en el futuro**, y trabajar hacia atrás para identificar qué causó dicho desastre y cómo evitarlo hoy.

### "Premortem": Imaginemos que es mañana y todo ha fallado. ¿Qué pasó?

#### Escenario de Fallo A: La terminal no responde o lanza errores al abrirse.
*   **Causa de Muerte:** Corrupción en el archivo [`.zshrc`](file:///Users/yarelyvarela/.zshrc). Esto ocurre cuando múltiples herramientas escriben en él de forma descontrolada, generando bucles infinitos de redirección o rutas duplicadas en `$PATH`.
*   **Prevención:** Mantener copias de seguridad de los archivos dotfiles (`.zshrc`, `.bash_profile`) y usar comentarios claros para delimitar qué herramienta escribió qué bloque.

#### Escenario de Fallo B: Git rechaza las subidas de código (Access Denied).
*   **Causa de Muerte 1 (Permisos de llave):** Los permisos de la carpeta `.ssh/` o el archivo de llave privada `id_ed25519` cambiaron accidentalmente. El protocolo SSH exige que la llave privada sea legible únicamente por el propietario (permisos `600`). Si los permisos son muy abiertos (como `777`), SSH bloquea el uso de la llave por seguridad.
    *   *Prevención:* Ejecutar `chmod 700 ~/.ssh` y `chmod 600 ~/.ssh/id_ed25519`.
*   **Causa de Muerte 2 (Llavero macOS desvinculado):** Tras reiniciar la Mac, el sistema no recuerda la llave SSH y pide la clave constantemente.
    *   *Prevención:* Asegurarse de tener configurado `UseKeychain yes` y `AddKeysToAgent yes` en el archivo [`~/.ssh/config`](file:///Users/yarelyvarela/.ssh/config).

#### Escenario de Fallo C: Herramientas instaladas por Homebrew dejan de funcionar.
*   **Causa de Muerte:** Incompatibilidad de arquitecturas tras una actualización de macOS (por ejemplo, pasar de Rosetta a nativo de Apple Silicon o viceversa), o rutas de `$PATH` que apuntan al directorio incorrecto de brew (Intel usa `/usr/local/bin/brew` y Apple Silicon usa `/opt/homebrew/bin/brew`).
    *   *Prevención:* Utilizar la detección dinámica de arquitectura en la asignación del `PATH` (como lo implementamos en el script `instalar_entorno.sh`).
