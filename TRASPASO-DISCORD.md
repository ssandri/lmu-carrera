# 🏁 Traspaso pit wall · 24h Le Mans · Lexus RC F LMGT3 #397

> **Mensaje para pegar en Discord** y que otro tome el papel de ingeniero/pit wall con una IA.
> El bloque **ESTADO ACTUAL** se actualiza justo antes de cada traspaso (ver aviso ahí).
> Todo lo demás es fijo. La fuente de verdad siempre es el repo, no este resumen.

---

## 📂 Repo (fuente de verdad)

**https://github.com/ssandri/lmu-carrera** (privado)

Clonar y leer **en este orden**:
1. `PITWALL.md` → rol, reglas de estrategia, cómo mantener el plan
2. `carrera.json` → **FUENTE ÚNICA VIVA** (plan + real + lo que queda)
3. `registro.md` → diario de decisiones, mediciones y narración

(`plan-original.json` = plan original congelado, referencia plan-vs-realidad.)

La IA que tome el relevo: **lee `PITWALL.md` entero primero**. Es autosuficiente.

---

## 🎯 Tu rol (resumen para la IA)

Ingeniero de carrera + pit wall. No conduces: aconsejas.
- Mantener `carrera.json` vivo (`estado: real` = pasado, `plan` = futuro).
- En cada parada: pasar el stint de `plan`→`real`, rellenar vuelta de entrada + desgaste,
  reajustar horarios/reparto de los stints siguientes.
- Dar la frase para cantar por radio (simple, sin jerga).
- Idioma **español**, unidades **métricas**.

---

## 📋 Datos fijos de la carrera

- **Pilotos:** Gonzalo, Guillermo (Guille), Mariano, Fufo, Sebas.
- Largada sáb 16:00. Bandera ~dom 15:00 (hora nueva). **24 h reales.**
- **CAMBIO HORARIO:** dom 03:00 CEST → 02:00 CET (fin horario verano). La carrera dura
  24 h reales aunque el reloj marque 23 h. Anclado en el stint 16.
- **Neumáticos:** 58 uds = 14,5 sets. Set 1 fue quali (gastado en largada). Quedan 14 sets
  completos + 2 neumáticos sueltos de reserva (pinchazo).
- **Stint SIEMPRE 11 laps** (tope del equipo). Nunca más.
- **Track limits:** contador acumulativo de toda la carrera (no se resetea). Al llegar a **12 → DRIVE-THROUGH**. Avisar a los pilotos.

---

## ⚙️ Reglas de estrategia

- 32 stints de 11 laps cubren las 24 h. Reparto: **11 dobles + 3 triples + ½ set reserva**.
- **TRIPLES SOLO DE DÍA** (de noche la pista fría no calienta el neumático → patina).
  Triples: sets 4 (hecho), 5 (en curso), 12 (pendiente, de día).
- Cada parada repone energía al 100%. Ruedas solo se cambian al cerrar un set.

**Tiempos de parada (medidos):**
- Energía: `(objetivo − actual) / 0.025` s.
- 4 ruedas: 12 s (suelen tardar ~1 s más). 2 ruedas: 4.5 s. **Nunca cambiar 3.**
- Ruedas y energía se **suman**. Alerón trasero ~25 s. Rejilla 0 s.
- Reparar todo el daño: 30 s. **Frenos DESACTIVADOS** (no hay cambio de frenos nunca).
- Pérdida pit lane: entrada ~+3 s, salida ~+24 s. Cambio de piloto: en paralelo, 0 s.

**Consumo y ritmo (validados, ya NO se trackean):**
- Consumo ~8.9 %/vuelta → 11 laps entran sobrados. Ritmo base ~242.6 s/vuelta (4:02.5).

**Desgaste (lo que SÍ se trackea ahora):**
- ~1.15 %/vuelta de día; menos con pista fría.
- Umbral de agarre a fin de triple: ~64 % de vida.
- Vigilar sobre todo el **DELANTERO IZQUIERDO (FL)**, el que peor acaba en triples.
- **Experimento abierto:** medir si de noche (stints ~13-21) desgasta menos que de día.

**Decisión:**
- Reparar: solo si el daño cuesta >1.5 s/vuelta en el stint siguiente. Estético: no.
- Ruedas: cambio de 4 al cerrar set; 2 solo si el desgaste va muy desigual.

---

## 📍 ESTADO ACTUAL

> ⚠️ **ACTUALIZAR ESTE BLOQUE JUSTO ANTES DE CADA TRASPASO.** Lo de abajo refleja el último
> momento guardado y puede estar desfasado. El estado real siempre está en `carrera.json`
> (`meta.estado_actual`). Al pasar el relevo, poner aquí: stint en curso, piloto, set/uso,
> próximo evento y qué medir.

```
Momento:        (rellenar: ej. dom ~07:00, fin de mi último stint)
Stint en curso: (rellenar)
Piloto:         (rellenar) — set X (uso Y/Z)
Próximo evento: (rellenar: qué pasa en la próxima parada)
A medir:        (rellenar: qué desgaste/dato pedir en la próxima entrada)
Reserva sets:   (rellenar si cambió)
```

Mientras tanto, el estado más reciente guardado está en `carrera.json`.

---

## ✍️ Cómo reportar una parada a la IA

```
Entra <piloto> a pits vuelta X, desgaste FL-FR-RL-RR, cambia neumáticos
(todos/algunos/ninguno), cambia por <piloto>/sigue, repara sí/no, daño
```

La IA entonces: pasa el stint a `real` en `carrera.json`, registra el dato, reajusta el plan
siguiente, y te da la frase para cantar por radio. Para volcar al Google Sheet, pedile
"imprimime la tabla" (o "desde el stint N") y te la saca en pantalla para copiar a mano.

---

## 🔭 Plan de stints (puede moverse con cada parada)

```
13 Guille  00:30-01:17  set 5 (3/3)  → nuevos set 6, cede a Fufo  [v133]
14 Fufo    01:17-02:03  set 6 (1/2)  noche
15 Fufo    02:03-02:50  set 6 (2/2)  → nuevos set 7, cede a Sebas
16 Sebas   02:50→02:36  set 7 (1/2)  ⏰ CAMBIO HORARIO 03:00→02:00
17 Sebas   02:36-03:23  set 7 (2/2)  → nuevos set 8, cede a Fufo
18 Fufo    03:23-04:09  set 8 (1/2)
19 Fufo    04:09-04:56  set 8 (2/2)  → nuevos set 9, cede a Sebas
20 Sebas   04:56-05:42  set 9 (1/2)
21 Sebas   05:42-06:29  set 9 (2/2)  → nuevos set 10, cede a Mariano
22 Mariano 06:29-07:15  set 10 (1/2) amanece - desgaste debería subir
23 Mariano 07:15-08:01  set 10 (2/2) → nuevos set 11, cede a Gonzalo
24 Gonzalo 08:01-08:48  set 11 (1/2)
25 Gonzalo 08:48-09:34  set 11 (2/2) → nuevos set 12, cede a Mariano
26 Mariano 09:34-10:21  set 12 (1/3) TRIPLE de día
27 Mariano 10:21-11:07  set 12 (2/3) → cede a Guille
28 Guille  11:07-11:54  set 12 (3/3) → nuevos set 13
29 Guille  11:54-12:40  set 13 (1/2)
30 Guille  12:40-13:27  set 13 (2/2) → nuevos set 14 (último), cede a Gonzalo
31 Gonzalo 13:27-14:13  set 14 (1/2)
32 Gonzalo 14:13-15:00  set 14 (2/2) → bandera a cuadros ~15:00
```
