# La Metodología Core de Varela (CPMAI + ISO 42001) Puntualizada

Esta es la síntesis de la doctrina y metodología que gobierna tu flota agéntica y tus flujos de desarrollo (vibecoding) en Mandalore, extraída de tus archivos oficiales en [`claude-skills`](file:///Users/yarelyvarela/Code/claude-skills).

---

## 1. Arquitectura y Gobernanza del Agente (ISO 42001 A.6)
*   **Autonomía Gobernada:** El orquestador autónomo no opera sin control; se considera a sí mismo un sistema agéntico regulado bajo la cláusula **ISO 42001 A.6**.
*   **Trazabilidad:** Debe dejar siempre un rastro de su razonamiento (`orchestrator_usage.jsonl`) y respetar de forma estricta los límites de su alcance y el botón de parada de emergencia (*kill-switch*).

---

## 2. Decálogo de Principios Operativos (CPMAI)

### I. Asignación Inteligente de Recursos
*   **Principio:** *7 Patterns of AI*.
*   **Regla:** Identificar el patrón del problema antes de asignar recursos. No usar multi-agentes por defecto; usar el agente correcto para el patrón correcto, prefiriendo la eficiencia al tamaño del modelo.

### II. Separación de Deberes (ISO §5)
*   **Regla:** Quien construye o reporta no autoriza. Un agente de desarrollo (*worker*) puede declarar que un código está listo, pero el orquestador o el director del proyecto es el único que puede autorizar cambios en producción.

### III. Análisis de Impacto en Alertas (ISO A.5)
*   **Regla:** Toda alerta destructiva, irreversible o que toque producción de un cliente requiere confirmación. Acciones reversibles y seguras pueden ser auto-resueltas y notificadas posteriormente.

### IV. Viabilidad Comercial Primero (CPMAI Fase I)
*   **Regla:** Priorizar tareas que generen o retengan ingresos recurrentes (MRR). Evitar el perfeccionismo técnico en infraestructura que no agregue valor comercial. Si el mantenimiento de infraestructura consume más del 70% del tiempo, se activa el límite.

### V. Definición de "Listo" (Done) (CPMAI Fase V / ISO §9)
*   **Regla:** Ninguna tarea se considera terminada basándose únicamente en la memoria de la sesión. Se requiere una prueba en vivo de extremo a extremo (E2E) con evidencia empírica comprobable.

### VI. Veracidad antes que Volumen (CPMAI - Veracity)
*   **Regla:** Validar la veracidad y consistencia de los datos proporcionados por un modelo antes de integrarlos a un plan. Datos sin verificar propagados en cascada generan fallos a gran escala (*Garbage at Scale*).

---

## 3. Disciplina de Gestión de Riesgos (Premortem)
*   **Pensamiento Prospectivo:** Antes de realizar cualquier cambio importante, se asume que el despliegue **ya explotó en producción**. Se buscan las causas del fallo en tiempo pasado para engañar positivamente al cerebro y encontrar fallas silenciosas.
*   **Estratificación del Control (Altura del Control):**
    1.  **Bloqueo Duro (a):** Reglas rígidas en código/sistema para evitar fallos catastróficos (ej. no subir secretos, validar códigos de error HTTP, controlar comandos destructivos).
    2.  **Nudge Suave (b):** Recordatorios y advertencias en lenguaje natural para vigilar estados (ej. alertas de estado "listo").
    3.  **Disciplina / Juicio (c):** Evaluaciones subjetivas de diseño que no se automatizan y recaen sobre el criterio del desarrollador.
*   **Rollback Mandatorio:** Toda acción crítica debe tener un plan de retorno al estado anterior viable y estimado en tiempo. Si no es posible definir un rollback, la tarea es declarada temporalmente inviable.
