# Plan de desarrollo paso a paso
## Concepción: Las Heroínas del Mantaro — con sistema de combate ambicioso, costo cero

Este documento ordena todo el trabajo pendiente, desde la preparación técnica hasta el pulido final, integrando el sistema de combate que se decidió ampliar sobre el diseño original (documento base + escena "La Resistencia"). Pensado para ejecutarse en equipo con ayuda de Cowork (ya disponible, sin gasto adicional) y GDevelop (gratuito).

**Restricciones que gobiernan todo el plan:**
- Cero soles de gasto: solo assets CC0 o CC-BY-SA/GPL con atribución, solo comportamientos nativos de GDevelop, sin plugins ni packs de pago.
- Todo archivo de proyecto de GDevelop bajo control de versiones (git) antes de que cualquier IA lo edite directamente.
- La IA redacta lógica, documentación, diálogos y scripts de adaptación de assets. El equipo humano cura el arte final y prueba/balancea el combate — eso no se delega.

---

## Fase 0 — Preparar el terreno
- [ ] 0.1 Crear repositorio git para toda la carpeta del proyecto (proyecto GDevelop + documentos)
- [ ] 0.2 Apuntar Cowork a esa carpeta como su espacio de trabajo
- [ ] 0.3 Confirmar instalación de GDevelop y crear el proyecto base vacío

## Fase 1 — Diseño técnico del combate (documento, todavía sin código)
- [ ] 1.1 Especificar el sistema de combate: número de oleadas, enemigos por oleada, vida de jugador y enemigos, condición de victoria/derrota, controles
- [ ] 1.2 Traducir esa especificación a comportamientos nativos de GDevelop (movimiento top-down, variables de objeto para la vida, temporizadores) — sin extensiones de pago
- [ ] 1.3 Cerrar el flujo actualizado del Capítulo V: Camino al Mantaro → Río Mantaro → La Resistencia (combate) → Cortar las cuerdas → Liberar el soporte
- [ ] 1.4 Redactar `02-DIALOGOS-COMPLETOS.md`: todos los diálogos existentes más los nuevos de la escena de combate, incorporando la arenga real de Cleofé (parafraseada) y la mención del incendio del pueblo en el epílogo

## Fase 2 — Assets, en paralelo con la Fase 1
- [ ] 2.1 Descargar paquetes CC0 de Kenney para ambientes, efectos y UI (sin necesidad de atribución)
- [ ] 2.2 Descargar personajes base de la colección LPC en OpenGameArt (ya traen animación de caminata y ataque) — licencia CC-BY-SA + GPL, exige atribución y compartir bajo la misma licencia
- [ ] 2.3 Adaptar/recolorear los sprites al estilo andino-colonial de 1821 — pedirle a la IA un script de recoloreo en lote en vez de redibujar cuadro por cuadro
- [ ] 2.4 Buscar música instrumental andina libre de derechos para cada escena (Concepción, la amenaza, camino, puente, final)
- [ ] 2.5 Redactar la sección de créditos con las atribuciones que exige la licencia LPC

## Fase 3 — Base del juego (equivale a la Semana 1 del plan original)
- [ ] 3.1 Movimiento, colisiones, cambio entre escenarios
- [ ] 3.2 Sistema de diálogos con retrato, nombre y texto
- [ ] 3.3 Sistema base de combate: vida, daño, detección de oleada — la IA redacta la lógica de eventos, el equipo la verifica y ajusta directo en el editor de GDevelop

## Fase 4 — Jugabilidad completa (equivale a la Semana 2)
- [ ] 4.1 Misiones, objetos coleccionables, preguntas educativas, puntuación
- [ ] 4.2 Integrar la escena de La Resistencia con el sistema de combate ya construido
- [ ] 4.3 Balancear la dificultad de las oleadas (esto requiere jugarlo de verdad, no se delega a la IA)
- [ ] 4.4 Escena final del puente con el combate ya integrado, cuerdas cortadas y soporte liberado

## Fase 5 — Pulido (equivale a la Semana 3)
- [ ] 5.1 Animaciones, transiciones, efectos de sonido
- [ ] 5.2 Corrección de textos y errores de ortografía
- [ ] 5.3 Pruebas de principio a fin y ajuste final de balance
- [ ] 5.4 Preparar la build final para la presentación/concurso

---

Nota: si adoptan numeración secuencial para sus documentos, este puede ser el `00-PLAN-DE-DESARROLLO.md`, previo al `01` (diseño original, ya lo tienen) y al `02-DIALOGOS-COMPLETOS.md` (pendiente, ver Fase 1.4).