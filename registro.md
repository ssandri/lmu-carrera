# Diario de decisiones y mediciones · 24 h Le Mans (Lexus RC F LMGT3 #397)

> **Qué es este archivo.** El *porqué* de la carrera: decisiones que toma el pit wall, mediciones
> puntuales y narración (clima, pit lane, incidentes, reconstrucciones) que no cabe en un campo de
> `carrera.json`. **No es la tabla de stints** — esa vive en `carrera.json` (fuente única). Aquí anoto
> el razonamiento antes/después de volcarlo al log. Para el plan original congelado: `plan-original.json`.

Ingeniero: pit wall IA. Pilotos: Gonzalo, Guillermo, Mariano, Fufo, Sebas.
Neumáticos: 58 (4 de quali al ~90 %) → 54 nuevos en carrera = 13.5 sets.

## Quali
- Mejor vuelta: 3:59.118. Neumáticos de quali al ~95 % → largamos con ellos (set 1, stints 1-2).

## Datos medidos (validados)
- **Ritmo base:** ~242.6 s/vuelta (4:02.5). Stint 1: 242.6 s. Stint 2: 242.9 s.
- **Consumo:** ~8.9 %/vuelta estable (medidas: 8.94 / 8.84 / 8.89 / 8.97 %/vuelta en stints 1-6).
  11 laps entran sobrados. **Energía validada → se dejó de trackear.**
- **Desgaste:** ~1.15 %/vuelta de día (promedio de los 4); menos con pista fría (~0.8 %/vuelta medido
  en stint 3 con pista más fría). Delanteros algo más rápidos que traseros.
- **Lift and coast** objetivo ×1 (1 vuelta): −4.5 % energía, ~0 s.

## Tiempos de parada (medidos, parado en box)
- Energía: (objetivo − actual) / 0.025 s (se calcula con la energía al pedir la parada).
- 4 neumáticos: 12 s (suelen tardar ~1 s más). 2 neumáticos: 4.5 s. **Nunca cambiar 3.**
- Neumáticos y energía se **suman**. Alerón trasero ~25 s. Rejilla 0 s.
- Reparar todo el daño: 30 s. Frenos: 120 s — pero **desgaste de frenos DESACTIVADO**, no hay cambio.
- **Pérdida de pit lane (parada 1):** entrada v11 = +3.2 s; salida v12 = +23.7 s tras restar 39.3 s
  parado. Total ~27 s.
- Cambio de piloto: en paralelo con el repostaje, no suma tiempo.

## Reglas de decisión
- **Neumáticos:** cambio de 4 al cerrar set (12 s); 2 solo si el desgaste va muy desigual.
  Triple solo si el agarre a ~64 % de vida es aceptable, y **solo de día** (pista caliente).
- **Reparar:** solo si el daño cuesta más de ~1.5 s/vuelta durante el stint siguiente (30 s). Estético: no.
- **Track limits:** contador **acumulativo de toda la carrera** (no se resetea). Al llegar a **12 avisos
  → DRIVE-THROUGH** (~20-25 s perdidos). En stint 14 vamos por 5.25/12. Recordar a cada piloto que no
  abuse de los límites — quedan muchos stints y es una penalización 100 % evitable.

## Experimento abierto: desgaste de noche
Medir si con pista fría el desgaste es menor que de día. Referencia de día (set 4, triple): proyectó
**59-63-73-71** al cierre (FL la peor). Vigilar el FL izquierdo.

- **Stint 13 (cierre triple set 5):** dato de cierre NO reportado → se perdió.
- **✅ Primer dato nocturno — stint 15 (cierre DOBLE set 6, v144):** desgaste restante
  **FL 78 · FR 86 · RL 82 · RR 85**. En 22 laps (doble) el FL perdió ~22 % → **~1.0 %/vuelta** frente a
  ~1.15 %/vuelta de día. **Confirma la hipótesis: de noche desgasta algo menos.** El FL a 78 % queda
  muy por encima del umbral (64 %), sin problema para un doble.
  ⚠️ **Dato algo contaminado:** Fufo tuvo un par de pérdidas (trompos/salidas) en este stint que pueden
  haber castigado los neumáticos de más — el desgaste "limpio" sería probablemente aún menor. Confirmar
  si esas pérdidas sumaron track limits (iba 5.25/12).

## Bitácora narrada (incidentes y reconstrucciones)

### Largada y primeros stints (stints 1-4)
- Largada P22, v3 en P25. Stint 1 parada solo energía ~39 s, sale v12 en P20.
- Clima tras stint 2 (~17:04): nubes ligeras, aire 29.3 °C, pista 46.3 °C, grip alto. Previsión: despejado, 24 °C.
- Stint 3: pista más fría, desgaste bajó a ~0.8 %/vuelta.

### CUELGUE DEL PC (tras la parada 4, ~19:05)
Justo tras la parada 4, Sebas había cambiado neumáticos (set 3 nuevo), dio 1 vuelta lenta y cedió a
Guille. **Se perdió la telemetría en vivo.** Los stints 5-7 se reconstruyeron a ciegas — de ahí los
`uso: arranque` y los desgastes `null` en esas filas de `carrera.json`. Reconstrucción:
- **Mini-stint del incidente (stint 5):** Sebas estrena el set 3 con un mini-stint de 1 lap por el
  incidente + parada en pits, cambio a Guille. Por eso el set 3 figura como `(arranque)`: lo estrenó
  sin contar como uso completo.
- **Stint 6 (Guille):** ~11 vueltas con set 3, entró en la v56 (no la 57), avisado L&C. Cede a Sebas.
- **Stint 7 (Sebas):** cerró el set 3 como DOBLE. Cambia a set 4 nuevo y sigue.

### Set 4 pasa a TRIPLE (stints 8-10)
- Stint 8: Sebas 11 v con set 4 nuevo, cede a Mariano **sin cambiar ruedas** → set 4 va a TRIPLE.
  Desgaste al inicio del triple: 15-13-11-11 %.
- Stint 9: Mariano 11 v (desgaste −13/−12/−8/−9).
- Stint 10: Guille cierra el triple del set 4 y estrena el set 5. Proyección fin de triple: **59-63-73-71**
  (FL la peor). Sin dato de desgaste real por el cuelgue.

### Triple del set 5 — Guille 4 stints seguidos (stints 10-13)
- Guille encadena 10-11-12-13. Stints 11 y 12 sin dato de desgaste (seguimos a ciegas tras el cuelgue).
- **Stint 13 (cierre triple set 5):** Guille cumplió el plan, entró v133, neumáticos nuevos (set 6),
  cedió a Fufo que sale v134. **El desgaste de cierre NO se reportó** → el primer dato nocturno del
  experimento se perdió. Queda pendiente pedirlo en la próxima entrada (stint 15).

### Pista cauchada — máximo agarre (stint 14, ~01:07, pos 24)
- Con Fufo ya en pista (set 6 nuevo), la pista está en **Saturated Grip** = **seca y con el MÁXIMO
  agarre posible** (goma bien asentada/cauchada, no es lluvia). Clock in-game 01:07. Clima: nubes
  ligeras, aire 17 °C, pista 20.2 °C. Track limits 5.25/12.
- **Implicación estratégica:** condiciones óptimas. Pista fría de noche (20.2 °C) + máximo agarre →
  escenario favorable para **menor desgaste**, justo lo que queríamos medir en el experimento nocturno.
  No toca nada del plan: seguimos con el reparto de sets. Confirmar al próximo reporte el ritmo real de
  Fufo y, sobre todo, pedir el **desgaste FL-FR-RL-RR al cerrar el set 6 (stint 15)** para tener por fin
  un dato nocturno limpio.

## Reorganización de archivos (dom 25-oct ~00:30)
Se pasó de CSV a JSON como formato fuente:
- `plan-original.json` ← conversión del CSV original (foto congelada).
- `carrera.json` ← **fuente única viva** (reemplaza `plan-vivo.csv`): plan + real + lo que queda.
- `registro.md` (este archivo) ← solo diario de decisiones/mediciones/narración.
- La exportación a Google Sheets (CSV `;`, 10 columnas de siempre) se genera a demanda desde `carrera.json`.

## Sincronización matutina (stints 22-26, ~10:37 dom 25-oct)
- **Stints 22-23 (Mariano, set 10 doble):** v232 (85-86-90-89) y v243 (72-73-78-77). Degradación FL ~1.27 %/v. Cierre impecable con 72 % restante en FL. Monta set 11 nuevo, cede a Gonzalo.
- **Stints 24-25 (Gonzalo, set 11 doble):** v254 (84-87-87-87) y v265 (70-75-77-77). Degradación FL ~1.36 %/v. Cierre con 70 % restante en FL. Monta set 12 nuevo, cede a Mariano.
- **Stint 26 (Mariano, set 12 uso 1/3 de triple):** v276 a las 10:17 (86-88-88-89). Solo energía.
- **Stint 27 (Mariano):** Entró clavado a las 11:02 en **v287** con desgaste **75-78-79-80** (~1.0 %/v en FL). Desgaste espectacular tras 22 laps, llega con 75 % de vida al 3er uso. Solo energía.
- **Stint 28 (Guille):** Entró clavado a las 11:47 en **v298** con desgaste **58-64-70-70**. El FL bajó al 58 % provocando fuerte subviraje en pista (tal como se calculó), pero el neumático aguantó físicamente sin incidentes cerrando con éxito el último triple planeado de la carrera. **Track limits impecables:** se mantuvieron en **8.5 / 12** (0 avisos sumados en 11 vueltas críticas).
- **Box v298:** Monta **Set 13 nuevo** (4 neumáticos) + energía. Sigue Guille.
- **Stint 29 (Guille):** Entró clavado a las 12:32 en **v309** con desgaste **84-87-89-89** (~1.45 %/v en FL). Degradación estándar y uniforme para un primer stint diurno.
- **Box v309:** **Solo energía**, sin cambio de ruedas (Set 13 va a doble). Sigue Guille.
- **Stint 30 (Guille en pista):** Arranca v310 con Set 13 (uso 2/2). Es el último stint de Guille tras una tanda impecable de 3 stints (28, 29, 30). Próxima entrada en v320 (~13:17) para montar el **Set 14 (último set nuevo)** y ceder a Gonzalo.

- **Inventario:** Quedan 6 neumáticos nuevos (Set 14 de 4 ruedas para la parada en v320 + 2 de reserva de emergencia).

- **Estrategia neumáticos:** Set 12 confirmado a TRIPLE de día (26 Mariano, 27 Mariano, 28 Guille). Restan 10 neumáticos nuevos (sets 13 y 14 de 4 ruedas + 2 de reserva de emergencia). Cuadra al milímetro con el plan original.
- **⚠️ Track Limits:** Subió a **8.5 / 12** en v281. Restan ~63 vueltas y solo 3.5 avisos de margen antes del Drive-Through. Alerta roja a los pilotos para que aseguren el trazado sin pisar líneas.
- **Regla última parada (Stint 31 en v331):** Carga de energía calculada a medida = `(vueltas restantes estimadas + 2 de margen) × 8.9%`. No llenar al 100% para rascar segundos parados en box. Set 14 sigue puesto y Gonzalo remata a meta.

