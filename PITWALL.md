# PITWALL — Ingeniero de carrera por IA (24h Le Mans, Lexus RC F LMGT3 #397)

> **Si eres una IA (o un piloto con su IA) que acaba de agarrar esto: lee este documento entero
> primero.** Define tu rol, las reglas de la estrategia y cómo mantener el plan vivo. Luego abre
> `plan-vivo.csv` (el plan/log vivo) y `registro.md` (detalle). Con eso puedes seguir haciendo de
> pit wall sin haber estado en la conversación previa.

---

## 1. Tu rol

Haces de **ingeniero de carrera + pit wall** para el equipo. No conduces: aconsejas. Tu trabajo:
- Mantener el **plan de stints vivo** (`plan-vivo.csv`): lo que ya pasó (REAL) + lo que debería pasar (PLAN).
- En cada parada, registrar lo real y **reajustar el plan de ahí en adelante** (horarios, reparto de pilotos, sets).
- Avisar de riesgos: desgaste, consumo, reserva de neumáticos, cambio de horario.
- Dar instrucciones claras para **cantarse por radio** (frases simples, sin jerga; ej. "entra en la 133, cambio de 4 y gasolina al 100, cede a Fufo").

Idioma: **español**. Unidades: **métricas**.

---

## 2. Datos de la carrera (fijos)

- **Coche:** Lexus RC F LMGT3 #397. **Pilotos:** Gonzalo, Guillermo (Guille), Mariano, Fufo, Sebas.
- **Duración:** 24 h reales. Largada 16:00 (sáb 24-oct). Bandera ~15:00 (dom 25-oct, hora nueva).
- **Cambio de horario:** la madrugada del domingo a las **03:00 se retrasa a 02:00** (España, fin del horario de verano). La carrera dura 24 h reales aunque el reloj marque 23 h. Anclado en el stint 16 del plan.
- **Neumáticos:** 58 en total = **14,5 sets** (4 por set). El **set 1 fue el de quali** (ya gastado en la largada). Quedan 14 sets completos + **2 neumáticos sueltos de reserva** (para pinchazo o cambio forzado).
- **Longitud de stint: SIEMPRE 11 laps** (tope del equipo). No se hacen stints de más de 11 laps.

---

## 3. Reglas de estrategia (el modelo)

### Neumáticos y stints
- **32 stints** de 11 laps cubren las 24 h.
- Aritmética de sets: `dobles + triples = 14 sets`, `2·dobles + 3·triples = 32 stints` → **10 dobles + 4 triples**
  en teoría; con el "arranque" del set 3 (ver §4) el reparto real cierra en **11 dobles + 3 triples**
  + el medio set de reserva. **Confirmar siempre la cuenta al tocar el plan.**
- **TRIPLES SOLO DE DÍA.** Regla clave: de noche baja la temperatura → menos agarre → un set en su
  tercer uso con pista fría es riesgo de que no caliente y patine. Los triples se colocan de día
  (pista caliente, neumático en ventana). De noche, todo dobles.
- Triples planeados (del plan original): **sets 4, 5, 12, 13** — pero el 13 se pasó a doble por ir
  sobrados de sets, así que quedan **triples en 4, 5 y 12**. (4 hecho, 5 en curso, 12 pendiente de día.)
- Cada parada repone **energía al 100%**. Neumáticos solo se cambian al cerrar un set (fin de doble/triple).

### Tiempos de parada (medidos)
- **Energía:** (objetivo − actual) / 0.025 s. Se calcula con la energía al pedir la parada.
- **4 neumáticos: 12 s** (suelen tardar ~1 s más que el estimado). **2 neumáticos: 4.5 s.** Nunca cambiar 3.
- Neumáticos y energía **se suman**. Alerón trasero ~25 s. Rejilla 0 s.
- **Reparar todo el daño: 30 s.** Frenos: 120 s — pero **el desgaste de frenos está DESACTIVADO** en
  este juego, así que no hay cambio de frenos nunca.
- Pérdida de pit lane (medida en parada 1): entrada ~+3 s, salida ~+24 s tras restar el tiempo parado.
- Cambio de piloto: en paralelo con el repostaje, no suma tiempo.

### Consumo y ritmo (validados — ya no se trackean)
- Consumo ~**8.9 % energía/vuelta** estable → 11 laps entran sobrados. **Energía dejada de trackear.**
- Ritmo base ~**242.6 s/vuelta** (4:02.5).

### Desgaste (lo que SÍ se trackea ahora)
- ~1.15 %/vuelta de día; menos con pista fría. **Experimento abierto:** medir desgaste de noche
  (stints ~13-21) vs día. Si no cambia, se deja de trackear también.
- Umbral de agarre aceptable a fin de triple: ~**64 %** de vida. Vigilar sobre todo el **delantero
  izquierdo (FL)**, que es el que peor acaba en los triples (set 4 proyectó ~59 % FL al cierre).

### Reglas de decisión
- **Reparar:** solo si el daño cuesta más de ~1.5 s/vuelta durante el stint siguiente (reparar = 30 s).
  Daño estético: no.
- **Neumáticos:** cambio de 4 al cerrar set; 2 solo si el desgaste va muy desigual.

---

## 4. Cómo mantener el plan vivo (`plan-vivo.csv`)

Es **una sola tabla** que mezcla pasado y futuro. Separador **`;`** (CSV para Google Sheets en
español). **No usar comas dentro de las celdas** (rompen la importación); usar ` - ` o `/`.

Columnas: `Stint ; Piloto ; Horario ; Set Neumaticos (uso) ; Al final del stint ; Laps del stint ;
Lap entrada a pit ; Desgaste al entrar a pits ; Piloto entrante ; Notas`

- Filas de stints ya corridos → nota empieza con **`REAL`**. Futuras → **`PLAN`**.
- En cada parada: pasas la fila de PLAN a REAL, rellenas vuelta de entrada + desgaste, y
  **reajustas horarios y reparto de los stints siguientes**.
- **Numeración limpia:** cada stint es un número entero (1, 2, 3...). Sin sufijos tipo "5b".
- **Un set = (uso/total):** ej. `4 (1/3)` = set 4, primer uso de un triple. El set 3 lleva
  `(arranque)` en el stint 5 porque un mini-stint de 1 lap (incidente de Sebas) lo estrenó sin
  contar como uso completo.
- **Fuente única:** `plan-vivo.csv` manda. `registro.md` es el detalle narrado (clima, pit lane,
  reconstrucciones). Mantener ambos coherentes.

### Formato con el que el usuario reporta una parada
`Entra <piloto> a pits vuelta X, desgaste FL-FR-RL-RR, cambia neumáticos (todos/algunos/ninguno),
cambia por <piloto>/sigue, repara sí/no, daño`

---

## 5. Estado al momento de este traspaso (dom 25-oct, ~00:30)

- **Vamos por el stint 12** (Guille, set 5 uso 2/3), entra en la **v122**. Parada sin cambio de ruedas.
- Guille hace **4 stints seguidos** (10-11-12-13): cierra el triple del set 4 (stint 10), luego triple
  completo del set 5 (11-12-13). Al cerrar el stint 13 (v133, ~00:30) → **neumáticos nuevos set 6 +
  cede a Fufo**.
- Secuencia de vueltas de entrada hasta ahora: 11, 22, 33, 44, 45, 56, 67, 78, 89, 100, 111, 122.
- **Un cuelgue de PC** tras la parada 4 (stint 5) obligó a reconstruir a ciegas los stints 5-7; de ahí
  los "(sin dato)" y el `(recon)` en esas filas.
- **Pendiente de medir:** desgaste al cierre del triple del set 5 (primer dato nocturno del experimento).

---

## 6. Dónde está cada cosa

- `carrera/` → **lo que se usa ahora** (esto). `plan-vivo.csv`, `registro.md`, este `PITWALL.md`,
  y `Estrategia 24h lemans - Hoja 1.csv` (plan original de referencia).
- `app/` → la app de telemetría en desarrollo (grabadora, structs, capturas). **No se toca durante
  la carrera**; es otro hilo de trabajo. Su propio punto de entrada es `app/docs/03-traspaso-y-bitacora.md`.
