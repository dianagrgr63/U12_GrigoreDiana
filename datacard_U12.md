# Data card · MEDE U12 · Statie × zi, Bucuresti, 2025

## Fisa 1: calitateaer.ro (RNMCA)

- **Provenienta:** rapoarte „Raport valori date" exportate de pe https://www.calitateaer.ro, pe statie (B-3, B-4, B-6), valori orare.
- **Tipul statiilor:** B-3: urban, B-4: industrial, B-6: trafic (din fisa fiecarei statii de pe portal). Coordonate: [lat/lon per statie].
- **Aparatura:** NO₂ cu analizor 42i, PM10 cu Sharp 5030, aceleasi la toate trei statiile.
- **Perioada:** 2025/01/01 – 2026/01/01.
- **Rezolutie temporala:** orara. Etichetele orare 01–24 inseamna sfarsit de ora; in procesare sunt mutate la inceputul orei.
- **Rezolutie spatiala:** punctuala (cate o statie).
- **Unitati:** µg/m³.
- **Goluri (ore lipsa, din 8.758 pe statie):**

| Statie | NO₂ lipsa | PM10 lipsa | Observatii |
|---|---|---|---|
| B-3 | 2,0% | 0,5% | PM10: goluri in aprilie–mai |
| B-4 | 0,0% | 4,8% | PM10: ~298 de ore in ianuarie, 88 in iulie |
| B-6 | 1,1% | 3,1% | PM10: goluri in mai–august |

- **Regula de zi valida:** cel putin 18 din 24 de ore valide. Altfel valoarea zilnica ramane goala.
- **Observatii tehnice:** ora locala cu schimbarea la ora de vara (pe 30 martie ziua are 23 de ore); raportul are 8.759 de randuri in loc de 8.760.
- **Licenta:** utilizare gratuita.

## Fisa 2: Open-Meteo Historical Weather API

- **Provenienta:** https://open-meteo.com/en/docs/historical-weather-api, descarcat in format Excel.
- **Puncte (`location_id`):**

| id | Latitudine | Longitudine | Altitudine | Statie asociata |
|---|---|---|---|---|
| 0 | 44,4640 | 26,0890 | 87 m | B3 |
| 1 | 44,3937 | 26,1868 | 83 m | B4 |
| 2 | 44,4640 | 26,0890 | 93 m | B6 |

- **Variabile:** temperatura la 2 m (°C), precipitatii (mm), viteza vantului la 10 m (km/h, convertita in m/s prin impartire la 3,6).
- **Perioada:** descarcat 2025/01/01 – 2026/01/01; pastrate doar orele din 2025, la ora locala.
- **Rezolutie temporala:** orara (8.760 de ore pe punct dupa eliminarea 1 ianuarie 2026).
- **Rezolutie spatiala:** grila de ordinul km-zecilor. Punctele 0 si 2 au aceleasi coordonate si serii identice.
- **Goluri:** niciunul.
- **Observatie tehnica:** timestamp-urile din fisier sunt in UTC+3 fix pe tot anul; in procesare sunt convertite la ora locala cu DST.
- **Licenta:** datele se descarca gratuit

## Fisa 3: tabelul aliniat

- **Fisiere:** `data/processed/hourly_aligned.csv` (statie × ora), `daily_aligned.csv` (statie × zi).
- **n:** 26.274 de randuri orare; 1.095 de randuri zilnice (3 statii × 365 de zile).
- **d:** 5 variabile (NO₂, PM10, temperatura, precipitatii, vant).
- **Agregare zilnica:** medie pentru NO₂, PM10 si temperatura; suma pentru precipitatii; maxim pentru vant.
- **Raport de acoperire:** 1.051 de zile cu ambii poluanti valizi.

| Statie | Zile valide NO₂ | Zile valide PM10 | Zile complete | Iarna | Primavara | Vara | Toamna |
|---|---|---|---|---|---|---|---|
| B-3 | 355 | 362 | 354 | 87 | 87 | 89 | 91 |
| B-4 | 365 | 346 | 346 | 77 | 92 | 88 | 89 |
| B-6 | 359 | 351 | 351 | 90 | 90 | 81 | 90 |

- **Split:** se decide la CP2.

## Limitari

- Statiile apropiate primesc meteo aproape identic (grila mare); doua dintre cele trei puncte au serii identice.
- B-4 are un gol de PM10 in ianuarie (iarna mai slab acoperita).
- Un singur an (2025).
- Precipitatiile sunt valori orare din reanaliza, nu masuratori locale.

## Reproducere

Notebook: `notebooks/01_load_align.ipynb`. Repo: https://github.com/dianagrgr63/U12_GrigoreDiana.