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

## Estado de la KB — medido, no estimado (decimoctavo pase, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Direcciones de repositorio distintas | **546** (+29) |
| …en `github.com` | 525 |
| …en `gitlab.com` | 21 |
| Direcciones verificadas este pase | **34** (SPDX, estrellas, rama por defecto y último push medidos) |
| …de ellas **nuevas** para la KB | **29** |
| Recetas numeradas en `compose/patterns.md` | **35** |
| Tendencias numeradas en `intel/trends.md` | **39** (con una colisión de numeración heredada) |
| Clases de licencia registradas | **18** (+CC-BY-SA-4.0 sobre datos, +Unicode License V3) |
| Formas registradas de equivocarse | **48** |
| Proyectos archivados-o-desaconsejados pero recomendados | **14** |
| Preguntas registradas como **sin resolver** | **16** |

> **Lea esto antes de prometer que un agente cumple un plazo.** Diecisiete pases construyeron nueve
> límites —lectura, escritura, procedencia, contención, borrado, accesibilidad, pesos, idioma y el
> documento fiscal— más lo que el agente **gasta**. El pase diecisiete encontró **vencimientos**
> (India: **30 días** al IRP; las fechas de KSeF; los catálogos CFDI 2026). **Este pase preguntó si la
> KB podía contarlos y la respuesta fue no.** Medido antes de buscar, en los nueve archivos:
> `tzdata` **0** · `IANA` **0** · `ISO 8601` **0** · `calendario` **0** · `día hábil` **0** ·
> `business day` **0** · `business hours` **0** · `festivo` **0** · `cron` **0** · `RFC 5545` **0** ·
> `rrule` **0** · `CalDAV` **0** · `day count` **0** · `30/360` **0** · `holiday` **1** · `DST` **1**.
> **La KB tenía los plazos y no tenía el calendario con el que se cuentan.**
>
> **EL HALLAZGO DEL PASE, LEÍDO BYTE A BYTE EN `eggert/tz/NEWS` (266 065 B, el repositorio aguas
> arriba del tzdb, porque `data.iana.org` responde 403 por el proxy): LA BASE DE DATOS HORARIA ENVIÓ
> A PROPÓSITO DATOS QUE CONTRADICEN LA LEY.** «La hora correcta» no es una propiedad de su código: es
> una cadena de cinco eslabones —**ley → tzdb → CLDR/ICU → runtime → agente**—, cada uno con su
> versión y su cadencia. Cuatro jurisdicciones canadienses fijaron su reloj en 2026 y en los cuatro
> casos tzdb modeló la transición el **2026-11-01 a las 02:00** en lugar de la fecha legal: Columbia
> Británica (**2026-03-09**, release 2026b), Alberta (**2026-06-18**, 2026c), Territorios del Noroeste
> (**2026-08-21**, 2026d) y Manitoba (**2026-10-31**, 2026e). El motivo está escrito: «*This temporary
> hack works around limitations in Unicode CLDR and ICU*» (CLDR **48**-**48.2.2**, ICU **78**-**78.3**).
> **El dato autoritativo se dobló para acomodar a un consumidor aguas abajo.**
>
> **Y el parche se rompió a sí mismo.** Provoca que `zic` en tzcode **2023d-2026a**, en el modo
> `slim` **por defecto**, genere un TZif que **no conforma con RFC 9636 §3.3**, y que algunos lectores
> —«*including tzcode itself*»— **ignoren la transición real de `America/Vancouver`** del 2026-11-01
> 02:00. Remedio: **`zic -b fat`**. Los mismos apaños esquivan un fallo de `libstdc++ std::chrono` en
> **GCC 14.1-14.4, 15.1-15.2 y 16.1** (**bug 124851**, corregido en **16.2**). **Límite del daño,
> declarado por los mantenedores y por eso citable:** «*It does not affect UT offsets, and affects
> abbreviations and tm_isdst flags only*» — **aritmética de instantes a salvo; abreviatura de zona o
> rama sobre `isdst`, no**. La salida tiene un suelo de versión de un mes: el apaño se retira porque
> **CLDR 49 (2026-10-22)** lo corrigió, y «*users need CLDR 49+ anyway for timestamps starting on
> 11-01*». En la misma release **2026f** (2026-10-27), un cambio de época: **se acabaron los segundos
> intercalares** y las tablas **ya no caducan**.
>
> **El riesgo que está ocurriendo ahora mismo es cubano, y es silencioso.** 2026f: «*Cuba will not
> fall back to -05 on 2026-11-01 and instead plans to maintain -04 through 2027-11-07*». Los cambios
> canadienses **adelantan** algo que el sistema desactualizado aplicará igual; el cubano es una
> **no-transición**: un sistema con tzdata anterior al **2026-10-27 atrasó el reloj el 1 de noviembre
> y lleva 23 días una hora por detrás** de la hora legal, sin error y sin excepción. La ventana no
> cierra hasta el **2027-11-07**.
>
> **Clase de licencia nº 17, y recae sobre los datos, no sobre el código — séptima, octava y novena
> confirmación de la misma regla de esta KB.** (1) `commenthol/date-holidays` (1 122★) **declara él
> mismo** `"license": "(ISC AND CC-BY-SA-4.0)"`: el código es ISC y **los festivos de `holidays.yaml`
> son share-alike** porque derivan de Wikipedia — **el contraejemplo del pase diecisiete**, que
> observó que ningún repo de 200★+ publicaba una expresión compuesta, y **la tercera dirección de
> resolución para `NOASSERTION`: ni desidia ni permisivo oculto, sino honestidad compuesta**. (2)
> `unicode-org/cldr`: un repositorio con **dos regímenes** — UTS #35 «*may not … incorporate it … into
> any product … without the express written permission of Unicode*», mientras «*All other content in
> this repo is released under UNICODE LICENSE V3*»: **los datos de locale se empaquetan, el texto de
> la norma no**. (3) `eggert/tz`: `LICENSE` de **252 B**, dominio público **salvo** `date.c`,
> `newstrftime.3` y `strftime.c` (BSD-3) **si están presentes** — **la licencia depende de qué
> archivos copiaste**. Y el caso inverso: **`date-fns`, 36 663★, insignia `NONE`**, cinco rutas de
> `LICENSE` en **404** y una raíz de monorepo **sin campo `license`** — la insignia es *literalmente
> correcta* y la autoridad es el **registro**: `registry.npmjs.org/date-fns/latest` → `4.4.0`, **MIT**.
>
> **La esquina de las aplicaciones de calendario es estructuralmente copyleft, segunda aparición del
> patrón en dos pases.** Rallly (AGPL-3.0), Radicale (GPL-3.0), Easy!Appointments (GPL-3.0),
> Nextcloud Calendar (AGPL-3.0) y cal.com (AGPL-3.0): **cinco de cinco**. El pase diecisiete midió lo
> mismo en el transporte AS4/Peppol. **Dos capas sin relación, el mismo reparto: la biblioteca es
> permisiva y la aplicación de cara al usuario es recíproca.** La excepción permisiva es
> presentación, no servidor: `fullcalendar` (**MIT**, 20 790★).
>
> **Obsolescencia parlamentaria, un criterio nuevo para esta KB.** `workalendar` (**MIT**, 946★,
> último push **2024-04-12**) y `svendiedrichsen/jollyday` (**197★**, **2024-05-01**) **no están
> archivados**, así que la forja los muestra vivos; el fork mantenido `focus-shift/jollyday`
> (**Apache-2.0**) tiene **144★**, **menos que el abandonado**. **Un calendario de festivos sin
> mantenimiento no es código viejo: es código incorrecto**, porque los festivos los cambia un
> parlamento. **Ramas por defecto: el `main` ciego habría fallado 19 de 34 veces** (`dev`, `develop`,
> `trunk`, **`20.0`** y trece `master`), frente a 6/46 en el pase diecisiete.
>
> **Límite declarado, y la asimetría de siempre.** Todo lo de **tzdb, licencias y código es byte a
> byte**; todo lo **regulatorio y de mercado es a nivel de snippet de búsqueda** y va marcado donde
> aparece. **No se pudieron leer en primario** `data.iana.org` (403 por el proxy) ni
> `www.rfc-editor.org` (no resuelve), así que **RFC 9636 y RFC 9557 NO se leyeron**: las referencias a
> §3.2 y §3.3 son **citas textuales del `NEWS`**, primario para la cita y secundario para la norma.
> **Conflictos sin resolver:** si Ontario noroccidental seguirá a Manitoba en el -05 anual (tzdb
> asumió que sí «*to avoid creating new zones*») y las condiciones del **servicio alojado** de
> Nager.Date, distintas de su biblioteca MIT. **Corrección de método reutilizable por la flota:** el
> resumen de búsqueda atribuyó a **2026c** el fin del DST en Samoa y el cambio de Jordania; ambos son
> de **2021b (2021-09-24)** — **cinco años de error**. **Un resumen de búsqueda acierta el hecho y
> falla la versión, y en esta capa la versión *es* el hecho.** **Hueco declarado:** **APAC** no tuvo
> **ningún** cambio de calendario civil en las seis releases de 2026 —cero **medido**, no silencio— y
> su riesgo es estructural: `Australia/Lord_Howe` salta **30 minutos** de DST (`Rule LH 2008 max - Oct
> Sun>=1 2:00 0:30`), Nepal está en **+05:45** y la India en **+05:30** sin DST. El próximo pase debe
> preguntar en japonés, coreano y chino por **día hábil** (`営業日`, `祝日`), no por zonas horarias.

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
