# Diseño técnico — Escena "La Resistencia"
## Fase 1.1 y 1.2 del plan de desarrollo

Este documento traduce la escena de combate a algo que se puede construir directamente en el editor de eventos de GDevelop, sin extensiones de pago. Pensado para que Cowork (o cualquiera del equipo) lo implemente paso a paso dentro del proyecto.

---

## 1.1 — Especificación de diseño

**Objetivo del jugador:** mientras Cleofé prepara el corte de las amarras, María e Higinia (con apoyo de los pobladores ya avisados en el Capítulo II) deben resistir el avance de los soldados realistas lanzándoles piedras, sin dejarlos cruzar hacia el puente.

**Duración objetivo:** 45–60 segundos (para no romper el ritmo de 15-25 min total del juego).

**Estructura:**
- 2 oleadas de soldados. Oleada 1: 3 soldados. Oleada 2: 4 soldados. (Total 7 — deliberadamente pocos, no es "muchos enemigos").
- Cada soldado avanza en línea recta desde un punto de entrada hacia una "línea límite" cerca del puente.
- El jugador dispara piedras hacia el soldado más cercano dentro de un rango, parado junto a un montón de piedras (punto de munición).
- Cada soldado tiene 2 puntos de resistencia — 2 impactos y cae.
- Si un soldado cruza la línea límite sin haber sido detenido, resta 1 punto a una barra compartida de "Aguante del pueblo" (empieza en 3).
- **Victoria:** sobrevivir ambas oleadas → desbloquea "Cortar las cuerdas".
- **Derrota:** el Aguante del pueblo llega a 0 → se reinicia la escena, sin penalización narrativa (es un juego educativo, no se busca castigar).
- El jugador no recibe daño directo — no hay "vida del personaje" ni posibilidad de que María muera. Se mantiene el espíritu de "sin combate complejo" del diseño original: es una defensa de oleada, no un duelo cuerpo a cuerpo.

---

## 1.2 — Traducción a GDevelop (sin extensiones de pago)

### Objetos necesarios
| Objeto | Tipo | Comportamiento | Notas |
|---|---|---|---|
| `Soldado` | Sprite | Ninguno especial — movimiento por evento | Variable de objeto `Vida` = 2 |
| `Piedra` | Sprite | "Movimiento en línea recta" (nativo) | Se destruye al salir de pantalla o al impactar |
| `PuntoMunicion` | Sprite (o punto invisible) | — | Marca desde dónde dispara el jugador |
| `LineaLimite` | Sprite invisible (o solo coordenada) | — | Referencia de posición, no necesita sprite visible |

### Variables de escena
- `AguanteDelPueblo` (número) = 3 al iniciar
- `OleadaActual` (número) = 1
- `SoldadosRestantesOleada` (número)

### Lógica de eventos (en orden)

1. **Al empezar la escena:** crear los 3 soldados de la Oleada 1 con un pequeño retraso entre cada uno (usar un Temporizador nativo de GDevelop, ej. cada 2 segundos aparece uno nuevo, en vez de los 3 de golpe).
2. **Cada fotograma:** mover cada `Soldado` hacia la `LineaLimite` (evento simple de "acercar objeto a posición" o cambiar X/Y según una velocidad fija — no hace falta pathfinding, es línea recta).
3. **Al presionar E cerca de `PuntoMunicion`:** crear una `Piedra` que se mueve en línea recta hacia el `Soldado` más cercano dentro de un rango (condición "Soldado más cercano a PuntoMunicion").
4. **Si `Piedra` colisiona con `Soldado`:** restar 1 a `Vida` del Soldado, eliminar la Piedra.
5. **Si `Vida` del Soldado llega a 0:** eliminar el Soldado, sumar puntos, restar 1 a `SoldadosRestantesOleada`.
6. **Si un `Soldado` cruza la posición de `LineaLimite` sin haber sido eliminado:** restar 1 a `AguanteDelPueblo`, eliminar ese Soldado.
7. **Si `AguanteDelPueblo` = 0:** mostrar mensaje de reintento y reiniciar la escena.
8. **Si `SoldadosRestantesOleada` = 0 y `OleadaActual` = 1:** esperar 2 segundos, subir `OleadaActual` a 2, generar los 4 soldados de la Oleada 2 (mismo patrón que el paso 1).
9. **Si `SoldadosRestantesOleada` = 0 y `OleadaActual` = 2:** mostrar "Resistencia lograda", pasar a la escena "Cortar las cuerdas".

Todo esto usa únicamente: Sprites, variables de objeto/escena, el comportamiento nativo "Movimiento en línea recta", condiciones de colisión y temporizadores — nada que no venga ya incluido en GDevelop.

---

## 1.3 — Flujo del Capítulo V (referencia)

```
Camino al Mantaro → Llegada al río → La Resistencia (esta escena) → Cortar las cuerdas → Liberar el soporte → Escena final
```

---

## Siguiente paso: Fase 1.4

Falta redactar `03-DIALOGOS-COMPLETOS.md` con todos los diálogos del juego, incluyendo los nuevos de esta escena (gritos de aliento, la arenga de Cleofé antes de empezar, reacciones al perder/ganar cada oleada).