---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 🏢 Enterprise KB

> Knowledge base de la industria **Enterprise** para Globant AI Studios.
> SAP, Salesforce, ServiceNow, HubSpot integrations, ERP/CRM agentico

## Estructura

```
enterprise-kb/
├── agents/        # Agentes AI open source de la industria
├── repos/         # Repos MIT/Apache como punto de partida
├── verticals/     # Plataformas verticales customizables con AI
├── intel/         # Mercado, players, tendencias
├── compose/       # Recetas: cómo componer soluciones
└── ingest/        # Scripts de actualización automática
```

## Uso

1. **Nuevo engagement**: leer `intel/market.md` + `repos/foundations.md`
2. **Proponer solución AI**: `agents/top.md` + `compose/patterns.md`
3. **Mantenerse al día**: correr `ingest/update.sh` semanalmente

## Estado de la KB — medido, no estimado (fifteenth pass, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Direcciones de repositorio distintas | **437** |
| …en `github.com` | 416 |
| …en `gitlab.com` | 21 |
| Nuevas direcciones este pase | **32**, todas con licencia, estrellas y fecha de push medidas |
| Recetas en `compose/patterns.md` | **29** |
| Tendencias numeradas en `intel/trends.md` | **33** (con una colisión de numeración registrada) |
| Clases de licencia registradas | **13** |
| Formas registradas de equivocarse | **33** |
| Proyectos archivados-pero-recomendados detectados | **11** |
| Preguntas registradas como **sin resolver** | 7 |

> **Lea esto antes de prometer una cifra de huella.** Catorce pases construyeron seis límites —
> lectura, escritura, procedencia, contención, borrado y accesibilidad — más la licencia de los
> **pesos**. Todos gobiernan lo que el agente **puede hacer**. El pase quince añade el séptimo: **lo
> que el agente gasta**, y es el primero que **no lo decide quien lo construye**. Medido antes de
> buscar, en los nueve archivos y **en los dos idiomas de la KB**: `carbon` 0, `kWh` 0, `emisión` 0,
> `CSRD` 0, `codecarbon` 0, `consumo` 0. Cero limpio. `FinOps` y `metering` **sí** estaban: esta capa
> no es FinOps con otro nombre — **FinOps mide dinero, esta mide julios, y el obligado a declararlos
> no es el CFO.**
>
> **Clase de licencia nº 13 — ODbL, y es la primera que no recae sobre código.**
> `thegreenwebfoundation/co2.js` figura como `NOASSERTION`; su `LICENSE` (12 678 bytes) contiene
> **dos licencias para dos activos**: el código es **Apache-2.0** y los **datos de intensidad de
> red** se republican de Electricity Maps bajo **Open Database License**, con ***share-alike***. Y
> muerde donde importa, porque **el factor de intensidad de red es justamente lo que convierte kWh
> en gCO₂e**. De ahí la regla:
>
> **el SPDX de un repo describe su código; no dice nada de los datos que empaqueta, los pesos que
> descarga ni el servicio al que llama.** Cuarta vez que esta KB encuentra el mismo patrón —
> pesos (pase 12), AUP (pase 12), SOM-1.0 (pase 13), **datos (pase 15)**.
>
> **Prueba de vendorización por la errata.** El mismo texto, con su errata (`"Licening for the
> CO2.js library"`), está dentro del `LICENSE` de `green-coding-solutions/green-metrics-tool`
> (35 429 bytes), **tres licencias en un archivo y con el encabezado contradiciendo a su cuerpo**: la
> sección titulada *"Apache License"* contiene la **AGPL-3.0**. Veredicto real: AGPL-3.0 (código) +
> ODbL (datos). Los tres proyectos de referencia de la capa son AGPL.
>
> **La única prueba de código del pase, y es la que habilita una receta.** El *scheduling*
> carbon-aware de `jobrunr/jobrunr` está en el **núcleo abierto** —91 coincidencias bajo
> `core/src/main/java/org/jobrunr/`, no en un módulo Pro— y por tanto es usable bajo
> **LGPL-3.0-or-later** (su archivo se llama **`License.md`**, y declara el proyecto
> *multi-licensed*: LGPL **o** comercial). Pero por defecto **llama a `https://api.jobrunr.io`** cada
> 5 minutos: una salida de red a un tercero, activada por defecto, en una librería de licencia
> impecable — y `carbonIntensityApiUrl` es configurable, así que la mitigación es una línea.
>
> **Dos obligaciones de EMEA se movieron en direcciones opuestas y deciden qué se vende.** El
> **CSRD se encogió** (Directiva (UE) **2026/470**: de ~50 000 a ~5 000 obligados, ≈90 % menos)
> mientras el deber de **centros de datos** de la **EED** (Reglamento Delegado (UE) **2024/1364**,
> ≥ **500 kW**, informe anual al **15 de mayo**) quedó intacto **y con un incumplimiento medido: 770
> centros reportaron, ≈36 % de los obligados**. Misma capa técnica, dos conversaciones comerciales
> opuestas. **Y la hipótesis con la que empezó el pase era falsa:** la obligación **no** está en el
> art. 40 del AI Act (normas armonizadas), está en la EED.
>
> **LATAM: Brasil derogó su propio mandato ISSB.** La **Resolución CVM 244 (mayo 2026)** revocó la
> obligatoriedad que la **193** había fijado desde el 1-ene-2026, y la dejó **voluntaria** — pero
> quien se adhiere queda atado a **tres ejercicios consecutivos con aseguramiento razonable**, que es
> un cliente **mejor**, no peor. **No cite el "65 % de empresas brasileñas no preparadas": es de
> 2024 y anterior a la reversión.** Pieza LATAM aprovechable y permisiva:
> `EquipoAnaliticaXM/API_XM` (**MIT**, SIMEM/XM Colombia).
>
> **Límite declarado y asimétrico, más marcado que en pases anteriores.** `arxiv.org` y los *hosts*
> legales y de analistas **no resuelven desde esta sesión** (comprobado una vez, no vuelto a
> sondear). Por eso **los hechos de código y licencia de este pase son byte a byte, y todos los
> regulatorios y de mercado son a nivel de snippet de búsqueda** — cada archivo lo dice donde
> aparece. Sin verificar en el primario, y marcadas como tales: ~**850×** la energía de un *token* de
> salida frente a uno de entrada (HotCarbon'26) y hasta **8,3×** de variación entre idiomas — lo
> segundo implicaría que **el mismo agente cuesta más energía por respuesta en español que en
> inglés**, y es una **hipótesis con fuente, no un hecho de esta KB** (open item 15-R1).
---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
