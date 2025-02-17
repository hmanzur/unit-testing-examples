# React + Vitest Examples

## Componente usa timeout

No hay ejemplos porque usar `setTimeout` en React puede ser problemático por varias razones:

1. Si un componente se desmonta antes de que el `setTimeout` se ejecute, la función aún intentará ejecutarse, lo que puede generar errores o actualizaciones de estado en componentes desmontados.
2. `setTimeout` opera fuera del modelo reactivo de React. Si el estado cambia antes de que se ejecute, la lógica puede quedar desincronizada.
3. Si usas `setTimeout` para animaciones o cambios de UI, puedes notar retrasos o inconsistencias porque React ya maneja actualizaciones de estado de forma eficiente.

Timeout mal gestionados o usados para "animar" la carga inicial de un sitio web no son consideradas buenas prácticas.
