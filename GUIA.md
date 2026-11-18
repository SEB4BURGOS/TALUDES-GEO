# Guía paso a paso: usar la página desde cero (Ejercicios de ayudantía)

Página: https://claude.ai/artifact/R8AJFx6ttUT8XD1zRWXeHd  (versión 2.2)
Convenciones: punto decimal; X horizontal, Z cota; unidades kN, kPa, m.

## Atajo
En "Interfaz (terreno)" → "Cargar ejemplo" → Ej. 1 o Ej. 2 carga todo lo de abajo. Los pasos explican cada dato por si lo ingresas a mano.

## Paso 1. Interfaz (equivale a Paso 3–4 de la guía GEO5)
Pega los puntos del terreno (uno por línea, X,Z), con la base del terraplén en Z=0.
- Ej. 1 (H 6 m, corona 5 m, 1V:1H):  0,0 / 10,0 / 16,6 / 21,6 / 27,0 / 37,0     X inicial 0, X final 37, Cota inferior −10
- Ej. 2 (H 8 m, corona 9 m, 2V:3H):  0,0 / 15,0 / 27,8 / 36,8 / 48,0 / 63,0     X inicial 0, X final 63, Cota inferior −15

## Paso 2. Suelos (Paso 5–6)
Unidad de γ: kN/m³. Orden de arriba hacia abajo; todos menos el último llevan su base (X,Z).
- Ej. 1: Terraplén SP-SM γ17 φ30 c2.9, base "0,0 / 37,0".  Fundación GW γ19 φ36 c0.
- Ej. 2: Terraplén GP-GM γ20 φ37 c0, base "0,0 / 63,0".  Fundación CH (no drenada) γ14.5 φ0 c18.5 (c = su = qu/2, análisis en tensiones totales).

## Paso 3. Agua y sobrecarga (Paso 7)
Nivel freático Z = 0. Sobrecarga q: Ej.1 50 kPa de X=16 a 21; Ej.2 30 kPa de X=27 a 36 (sobre la corona).

## Paso 4. Criterio y sismo (Paso 8–9)
- Situación "Permanente": FS admisible 1.5.  Situación "Sísmico": FS 1.1 y Kh (Ej.1 0.267; Ej.2 0.20). Kv = 0.
- Al cambiar la situación, la página pone 1.5 o 1.1 (editable). Con "Permanente" Kh se ignora, igual que en GEO5.

## Paso 5. Grilla de búsqueda (Paso 10)
Ej.1: X 18–34, Z 8–24. Ej.2: X 24–58, Z 4–45. 33×25 centros, 60 radios, 60 dovelas, Radio mínimo 2 m. Marca "Refinar fuera de los nodos" (equivale a la "Optimización"). Si el aviso dice que el centro queda en el borde, amplía la grilla.

## Paso 6. Analizar (Paso 10–11)
Elige Método (Bishop o Spencer) → Analizar. Repite para cada situación. Lee: FS vs admisible (ACEPTABLE / NO ACEPTABLE), Fa, Fp, Ma, Mp, pestaña Métodos (los cuatro métodos sobre la misma superficie) y Dovelas.

## Resultados de la página
| Caso | Bishop | Spencer | Exigido | Veredicto |
|---|---|---|---|---|
| Ej.1 estático | 0.84 | 0.83 | 1.5 | No cumple |
| Ej.1 sísmico (Kh 0.267) | 0.62 | 0.62 | 1.1 | No cumple |
| Ej.2 estático | 0.56 | 0.57 | 1.5 | No cumple |
| Ej.2 sísmico (Kh 0.20) | 0.38 | 0.38 | 1.1 | No cumple |

## Origen de la falla y soluciones
**Ej.1.** La superficie crítica es un círculo de pie dentro del terraplén; el nivel freático no influye (con o sin agua da lo mismo). Causa: talud a 45° con relleno φ30° y 50 kPa en la corona. Solución probada en la página: tender a 1V:4H (estático 2.42/2.47, sísmico 1.16/1.20: cumple). Con 1V:3H queda en 1.45/1.67 estático y 1.06/1.09 sísmico: no cumple sísmico. Alternativas de refuerzo (geomallas, muro al pie) no se modelan en la página.

**Ej.2.** Dos causas: (1) talud 2V:3H (56°) mayor que φ=37° del relleno; (2) arcilla blanda (su 18.5 kPa) bajo 8 m de relleno más 30 kPa: falla profunda de fundación. Aplanar el talud solo no basta (0.59–0.64) y reemplazar o mejorar la arcilla solo tampoco (≈0.9–1.15 estático). Combinación probada: talud 1V:3H + arcilla mejorada a su ≈ 60 kPa (precarga con drenes, columnas, etc.): estático 1.50/1.61, sísmico 1.13. Con su 40 sísmico queda en 0.76. Reemplazo de 8–10 m con 1V:3H cumple estático (1.50/1.61) pero no sísmico en Bishop (0.95–0.98).

## Notas y límites
- 2V:3H se interpretó como 2 verticales por 3 horizontales. Confirma con tu profesor.
- Los resultados de estos ejercicios no se han comparado con GEO5 (solo el caso de la tarea, con diferencias de 0.1–0.3 %).
- Sismo: Fi = Kh·W por dovela sobre el peso del suelo (sin la sobrecarga), brazo medido hasta el centroide de la dovela.
- Las soluciones propuestas son verificaciones de la página, no un diseño: validar con el profesor y la normativa.
