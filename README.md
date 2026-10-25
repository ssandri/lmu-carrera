# lmu-carrera

Pit wall en vivo para la **24h de Le Mans** (Lexus RC F LMGT3 #397), llevado por una IA que hace de
ingeniero de carrera.

**Punto de entrada: [`PITWALL.md`](PITWALL.md)** — rol del ingeniero, reglas de estrategia y como
mantener el plan vivo. Si retomas la carrera (otra IA, otro piloto con su IA, o tras un cuelgue),
empieza ahi.

- `PITWALL.md` — manual del ingeniero + estado actual (traspaso autosuficiente).
- `carrera.json` — plan/log vivo (pasado `estado:real` + futuro `estado:plan`). **Fuente unica.**
- `plan-original.json` — plan original congelado (referencia plan-vs-realidad).
- `registro.md` — diario de decisiones, mediciones y narracion (clima, pit lane, reconstrucciones).
- `Estrategia 24h lemans - Hoja 1.csv` — CSV original (ya volcado a `plan-original.json`; respaldo).

Exportar a Google Sheets: el pit wall imprime en pantalla una tabla (`;`, 10 columnas) a demanda; se copia a mano.

La app de telemetria vive en un repo aparte: **lmu-app**.
