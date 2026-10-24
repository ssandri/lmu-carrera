# lmu-carrera

Pit wall en vivo para la **24h de Le Mans** (Lexus RC F LMGT3 #397), llevado por una IA que hace de
ingeniero de carrera.

**Punto de entrada: [`PITWALL.md`](PITWALL.md)** — rol del ingeniero, reglas de estrategia y como
mantener el plan vivo. Si retomas la carrera (otra IA, otro piloto con su IA, o tras un cuelgue),
empieza ahi.

- `PITWALL.md` — manual del ingeniero + estado actual (traspaso autosuficiente).
- `plan-vivo.csv` — plan/log vivo (pasado REAL + futuro PLAN). Fuente unica. Para Google Sheets (separador `;`).
- `registro.md` — bitacora narrada de la carrera (clima, pit lane, reconstrucciones).
- `Estrategia 24h lemans - Hoja 1.csv` — plan original de referencia.

La app de telemetria vive en un repo aparte: **lmu-app**.
