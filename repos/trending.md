---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 📈 Repos trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

## 2026-11-24 — vigesimoquinto pase (latest) — la capa de la contraparte: 26 términos medidos en cero, 25 direcciones verificadas, 24 existen, y el instrumento recuperó dos campos que el pase anterior declaró perdidos

> **Dedup medido antes de escribir, no estimado.** Veintiséis términos de la capa, medidos **con
> límite de palabra** sobre **20.810 líneas y 24 pases previos**: **los veintiséis en cero.**
> `sanctions screening`, `OFAC`, `SDN list`, `denied party`, `export control`, `dual-use`,
> `OpenSanctions`, `FollowTheMoney`, `yente`, `nomenklatura`, `watchman`, `beneficial ownership`,
> `BODS`, `GLEIF`, `KYB`, `restricted party`, `politically exposed`, `Entity List`, `MOFCOM`,
> `alephdata`, `openaleph`, `Archivematica`, `REUSE.toml`, `GNU Free Documentation`,
> `open-supply-hub`, `openownership`. La ausencia era estructural: 24 pases construyeron lo que el
> agente **lee, cambia, prueba, alcanza, firma y envía**, y ninguno **con quién puede tratar**.

> **EL INSTRUMENTO, Y CORRIGE AL PASE ANTERIOR.** El vigesimocuarto pase dejó escrito que
> `api.github.com` y `github.com` devuelven **403** y que por tanto **«estrellas y bandera
> `archived` no están disponibles y no se inventan»**. La primera mitad sigue siendo cierta; la
> segunda **era una conclusión sobre `curl`, no sobre la sesión**:
>
> - `curl` a `api.github.com` / `github.com` → **403** (la API está limitada a los repos adjuntos).
>   `curl -I` (HEAD) sigue bloqueado: **verificar con GET**.
> - `raw.githubusercontent.com` → **200 por GET plano**. Es el carril de lectura byte a byte, y de
>   ahí salió **cada licencia** de este pase.
> - **`WebFetch` sí alcanza el HTML de `github.com`** donde `curl` recibe 403, y su render **trae
>   el contador de estrellas, la licencia del *sidebar* y el badge «Public archive» con su fecha
>   de archivado.** **Estrellas y `archived` SÍ son recuperables en este entorno.**
> - **`github.com/orgs/<org>/repositories?type=source`** por `WebFetch` devuelve licencia y estado
>   de archivo de toda la organización **en una llamada** — de ahí salieron tres de las seis
>   trampas de abajo. **Pagina a 30:** una org de 34 repos necesita la página 2 antes de que nadie
>   declare inventario completo.
> - **Y uno mejor que todos los anteriores cuando existe:** `opensanctions/opensanctions` publica
>   un **`REUSE.toml`** (REUSE spec 3.3) en su raíz — **licenciamiento por fichero y legible por
>   máquina**. Primera aparición de REUSE en esta KB. Vale la pena sondearlo en cada pase futuro.

### Verificación: 25 direcciones probadas, 24 existen, 1 no

**Existen y están verificadas (24).** Siete en `agents/top.md` y el resto en
`repos/foundations.md`, ambos de esta fecha: `opensanctions/{yente, nomenklatura, followthemoney,
opensanctions, rigour, qarin, graph, yente-client, countrynames, datapatch, zavod, bods-ftm}`,
`moov-io/watchman`, `openaleph/openaleph`, `alephdata/aleph`, `openownership/{data-standard,
visualisation-tool, register-ingester-psc, register-sources-psc, bodspipelines,
bods-gleif-pipeline, lib-cove-bods}`, `opensupplyhub/open-supply-hub`,
`artefactual/archivematica`.

**No existe, y por eso no es una fila (1).** **`trade-tariff/trade-tariff-backend`** → **404 en la
página del repo y 404 en `raw.githubusercontent.com` para `README.md` en `main` y en `master`.**
La API oficial del Trade Tariff del Reino Unido es real y está documentada en `api.gov.uk`, y
fuentes secundarias de 2026 nombran ese repositorio como su *backend* abierto. **Una fuente
secundaria que nombra un repositorio no es el repositorio.** Resultado: **la clasificación
aduanera/arancelaria no tiene base permisiva verificada en esta KB**, y queda declarada como hueco
en vez de rellenada con una fila verosímil.

### Las seis trampas, por orden de cuánto dinero cuestan

1. **Licencia de tres capas en un solo repo.** `opensanctions/opensanctions` (badge **MIT**,
   884 ★). Su `COPYRIGHT.md`: código **MIT** / datos **CC BY-NC 4.0** (el proyecto **reclama
   derechos de base de datos**; uso comercial = licencia de pago) / terceros bajo `datasets/` con
   **ninguna licencia concedida**, y el propio fichero dice que **no mantienen índice por fichero
   de cuáles son**. **No existe comprobación programática** de qué es redistribuible.
2. **Muerto sin badge de archivado.** `alephdata/aleph`: **2.500 ★**, MIT, «Public», **sin aviso de
   archivo**, README `PROJECT STATUS: SUNSETTING`, mantenimiento **terminado tras diciembre de
   2025**, reescrito como **Aleph Pro** comercial. Sucesor: `openaleph/openaleph` (MIT, 167 ★,
   DARC). **`archived` es suficiente pero no necesaria.**
3. **Un fichero `LICENSE`, dos licencias, partidas por tipo de artefacto.**
   `openownership/data-standard`: **esquema → Apache-2.0** (línea 8), **documentación → GNU Free
   Documentation License v1.3** (línea 25), **en el mismo fichero**. GitHub muestra sólo «Other».
   Leer las primeras 30 líneas devuelve «Apache-2.0» y **se equivoca sobre la mitad del repo**.
4. **La frontera de licencia atraviesa una sola organización.** En `openownership/*`: **spec +
   *ingesters* del registro UK = Apache-2.0**, pero ***pipelines* BODS y el validador de
   conformidad = AGPL-3.0** (`bodspipelines`, `bods-gleif-pipeline`, `lib-cove-bods`,
   `bods-uk-psc-pipeline`, `enricher`, `beneficial-ownership-explorer`). Un estándar permisivo
   cuyo **validador de referencia es copyleft**. El `LICENSE` de `lib-cove-bods` además **excluye
   explícitamente el tema visual y el logo BODS**.
5. **Archivado y con el código vivo.** `opensanctions/zavod` (MIT, 9 ★) archivado el **19-jul-2023**
   y plegado al monorepo: `opensanctions/opensanctions/tree/main/zavod` → `zavod/pyproject.toml`
   **HTTP 200**. **Depender de la ruta del monorepo, nunca del repo archivado.** Duodécimo caso
   archivado-pero-vivo de esta KB.
6. **Archivado con puntero bueno.** `opensanctions/bods-ftm` (8 ★), el puente obvio **BODS →
   FollowTheMoney**, archivado el **5-dic-2022**, apunta a `opensanctions/graph` — y **el destino
   verifica vivo** (200 en `main` y `master`). La composición natural existe: es un *redirect*, no
   un repo. **Y `openownership/register` está archivado**, junto a todos los `register-*-dk`
   (Dinamarca se cayó); los vivos son UK (PSC), Eslovaquia y OpenCorporates.

### Un no-cero puede ser falso: tres colisiones medidas en el propio método de este pase

Esta KB lleva **diez reglas sobre falsos ceros**. Este pase encontró la inversa, y la encontró en
su propia medición de partida:

- `yente` dio **2** → ambos dentro de la palabra española **contribu*yente***.
- `Aleph` dio **2** → ambos **Aleph Alpha**, el proveedor alemán de modelos, sin relación con
  `alephdata/aleph`.
- `counterparty` dio **4** → todos en el sentido del quinto pase (**la persona al otro lado de la
  pantalla**), no el comercial.

**Regla: medir con límite de palabra y leer el *hit* antes de creérselo.** Un `grep -i` ingenuo
habría reportado esta capa como parcialmente cubierta y el pase no se habría hecho.

### El reloj de esta capa, que es lo que la hace un problema de agentes

La **SDN de OFAC se actualiza varias veces por semana sin calendario fijo**, y la **BIS Entity
List y la SDN más que se duplicaron entre 2020 y el 3T de 2026**. En paralelo, China mantiene un
**esquema de dos niveles** (lista de control = prohibición; *watch list* = revisión caso por caso
más estricta) y su **artículo 26 permite solicitar la baja**. Las listas **se mueven en los dos
sentidos**: una decisión de screening cacheada caduca en días y **un bloqueo cacheado también**.

---

## 2026-11-24 — vigesimocuarto pase — la capa de la firma: 45 direcciones probadas, 44 existen, 44 nuevas, y el instrumento cambió de carril

> **Dedup medido antes de escribir, no estimado:** de 45 direcciones de partida, **una sola** tenía
> apariciones previas en los nueve ficheros (`documenso/documenso`, 2). **Las otras 44 son nuevas.**
> La ausencia era estructural: 23 pases construyeron *qué puede hacer* el agente y ninguno *qué lo
> prueba*.
>
> **EL INSTRUMENTO NUEVO, Y VALE PARA TODA LA FLOTA.** `api.github.com` y `github.com` devuelven
> **403** en esta sesión —la API está limitada a los repositorios adjuntos—, así que **estrellas y
> bandera `archived` no están disponibles y no se inventan**. Lo que **sí** funciona es el carril
> de lectura anónima de git:
> `git clone --bare --depth 1 --filter=blob:none` + `git log -1 --format=%cI` da la **fecha real
> del último commit en ~0,5 s y 196 KB por repositorio**, y `raw.githubusercontent.com` da el
> **fichero de licencia byte a byte**. **La fecha del último commit es mejor evidencia que
> `pushed_at`**, que se mueve con cualquier rama mientras el commit no.
> **Contrapartida honesta: sin `archived` no se puede distinguir «archivado» de «parado».**
>
> **Lo trending de verdad en esta capa son fechas de push, y son de esta misma semana:**
> `contentauth/c2pa-rs` y `contentauth/c2patool` (**MIT**) con commit el **2026-11-24**;
> `cloudflare/web-bot-auth` (**Apache-2.0**) el **2026-11-24**; `OpenSC/OpenSC` (**LGPL-2.1**) el
> **2026-11-24**; `eudi-app-ios-wallet-ui` (**AGPL-3.0**) el **2026-11-24**;
> `varops/signed-md` (**AGPL-3.0**) el **2026-11-24**; `MatthiasValvekens/pyHanko` (**MIT**) el
> **2026-11-23** —*con un aviso de «beta / not production-ready» en su README más viejo que el
> propio commit*—; `apache/pdfbox` (**Apache-2.0**) el 2026-11-22.
>
> **LA DECISIÓN DE PRESUPUESTO DE LA CAPA, MEDIDA:** la biblioteca **completa** es copyleft y la
> **permisiva** se declara beta. `esig/dss` —de la **propia Comisión Europea**, la **única** con
> PAdES + CAdES + XAdES + JAdES **y validación contra listas de confianza**— es **LGPL-2.1**
> (`LICENSE`, **26.530 B**); `pyHanko` —única ruta permisiva completa a PAdES— es **MIT**
> (**1.080 B**). **La LGPL-2.1 se enlaza dinámicamente sin contaminar el producto: decide el
> empaquetado, no el permiso.**
>
> **EL REPARTO DENTRO DE UNA MISMA ORGANIZACIÓN, Y ES EL DATO COMERCIAL (T95).**
> `eu-digital-identity-wallet` publica **las apps de cartera en AGPL-3.0** (`eudi-app-android-wallet-ui`,
> `eudi-app-ios-wallet-ui`, **13.961 B**) y **las bibliotecas y el verificador en Apache-2.0**
> (`eudi-lib-jvm-sdjwt-kt`, `eudi-srv-web-verifier-endpoint-23220-4-kt`, **9.425 B**).
> **El lado en el que está una empresa cliente —el que verifica— es justo el permisivo:** se puede
> entregar un verificador de cartera dentro de un producto cerrado; **no** se puede forkear la
> cartera del Estado dentro de uno. **Cuarta confirmación de que la licencia es por
> repo-entregable y no por organización** — y la primera que corta justo entre **producto** y
> **biblioteca**.
>
> **TRES LICENCIAS QUE LA FORJA NO SABE LEER, Y LAS TRES SON DE ADMINISTRACIONES PÚBLICAS.**
> (1) `open-eid/digidoc4j` y `open-eid/libdigidocpp` (Estonia): **13 rutas canónicas, 13 fallos**;
> está en **`LICENSE.LGPL`**, que el README nombra → **LGPL-2.1, 26.436 B** (**T94**: si la sonda
> dice «sin licencia», leer el README para el **nombre del fichero**; es el **inverso** de T92).
> Y el README **llama a su licencia «GNU *Library* General Public License»**, el nombre antiguo de
> la **2.0**, cuando el fichero es la **2.1**. (2) `ctt-gob-es/clienteafirma` (**AutoFirma**,
> España): **sin fichero de licencia en absoluto**; el README declara en prosa **«GPL 2+ y
> EUPL 1.1»** — dual, y sólo en prosa. (3) Las **especificaciones no son código**:
> el ARF europeo trae `LICENCE` —ortografía británica, **249 B**— con **CC-BY-4.0**;
> `c2pa-org/specifications` **CC-BY-4.0** (18.650 B); `italia/eudi-wallet-it-docs` **CC0-1.0**
> (6.555 B). *Dos repos de especificación, dos licencias de documento distintas.*
>
> **CERO CLASES DE LICENCIA NUEVAS, Y SE DICE EN LUGAR DE INFLAR LA CIFRA.** Las 21 clases que ya
> tenía la KB bastaron para las 44 direcciones: **CC-BY-4.0, CC0, LGPL-3.0, LGPL-2.1, GPL-2.0,
> EUPL y BSD-2-Clause ya estaban registradas** (medido: 24, 6, 45, 5, 28, 51 y 38 apariciones
> previas). **Lo único nuevo es una combinación**, no una clase: el **dual GPL-2.0+ / EUPL-1.1**
> declarado sólo en un README.
>
> **FALLO DEL PROPIO INSTRUMENTO, ENCONTRADO Y CORREGIDO EN EL PASE (T93).** El clasificador
> convirtió **GPL-2.0 en LGPL** porque **el texto de la GPL-2.0 contiene la cadena «GNU Lesser
> General Public License» en su propio apéndice**: en el `LICENSE` de `dogtagpki/pki` aparece en la
> **línea 18** mientras el encabezado de la **línea 1** dice `GNU GENERAL PUBLIC LICENSE /
> Version 2`. **Se clasifica por la primera línea de encabezado, nunca por subcadena.** Veredicto
> corregido: `dogtagpki/pki` = **GPL-2.0**.
>
> **EL CERO DE LATAM ERA DEL IDIOMA (T97).** La misma pregunta en **portugués** devolvió un corpus
> nacional entero que la sonda en español no veía en pases anteriores: `demoiselle/signer`
> (**LGPL-3.0**, del **SERPRO**, **2026-09-04**), `junior9283/assinador-icp-brasil` (**MIT**,
> **2026-10-10**, el **único permisivo y vivo**), `evandrojr/signer` (fork, 2026-05-20) y las tres
> de **`OpenICP-BR`**: `libICP` (**2018-09-24**), `wxApp` (**2018-07-11**) y `ktLib`
> (**sin fichero de licencia**, **2018-11-05**). **3 de 6 llevan 8 años sin un commit y son los
> primeros resultados de búsqueda** — decimoctavo caso de parado-pero-recomendado, y el más antiguo
> que esta KB ha medido. **El hueco de LATAM aquí no es de ausencia: es de mantenimiento.**
>
> **Y un 404 que se registra en lugar de borrarse:**
> `eu-digital-identity-wallet/eudi-srv-web-issuing-qeaa-py` **no existe**. El nombre lo dedujo este
> pase por analogía con los repos hermanos y **no lo verificó antes de escribirlo**. De 45
> direcciones, **44 reales y 1 conjetura propia**.

## 2026-11-24 — vigesimotercer pase — la capa del remitente: 32 direcciones verificadas, 32 nuevas, y 9 licencias que la forja no sabe leer

> **32 direcciones verificadas el 2026-11-24, las 32 nuevas para esta KB** (dedup medido: los 30
> candidatos de partida daban **0 apariciones** en los nueve ficheros — la ausencia era estructural,
> no de vocabulario). Instrumentos, en orden de autoridad: `gh api -X GET search/repositories`
> (SPDX + ★ + `pushed_at` + `archived` + **rama por defecto**, todo en una llamada),
> **`raw.githubusercontent.com` byte a byte**, y —decisivo este pase—
> **`registry.npmjs.org/<pkg>/latest`** cuando el fichero del repo está roto.
> `api.github.com/repos/…` sigue **denegado por el alcance de la sesión**; `HEAD` sigue bloqueado por
> el proxy, así que se verifica con **GET**.

**El reparto de licencias de la capa, medido:**

| Veredicto | Repos |
|---|---|
| **MIT** | `mjl-/mox` (5.962 ★), `haraka/Haraka` (5.642 ★), `postalserver/postal` (16.975 ★), `axllent/mailpit` (11.024 ★, rama `develop`), `docker-mailserver` (19.776 ★), `emersion/go-msgauth` (231 ★), `emersion/go-smtp` (2.066 ★), `Mail-0/Zero` (10.900 ★), `Snawoot/postfix-mta-sts-resolver` (127 ★) |
| **MIT, pero sólo legible en el registro** | `postalsys/mailauth` (v8.1.0), `Mailu/Mailu` (`LICENSE.md`) |
| **MIT-0** | `nodemailer/nodemailer` (17.717 ★) — **clase nueva nº 19** |
| **Apache-2.0** | `apache/james-project` (1.054 ★), `apache/spamassassin` (rama **`trunk`**), `rspamd/rspamd` (`LICENSE.md`), `albertito/chasquid` (`[mirror]`), `domainaware/parsedmarc` (1.319 ★) |
| **BSD-2-Clause** | `trusteddomainproject/OpenARC` |
| **BSD/ISC compuesto** | `OpenSMTPD/OpenSMTPD` |
| **PSF-2.0** | `sdgathman/pyspf` — **clase nueva nº 20** |
| **Doble TDP + Sendmail, por fichero** | `OpenDKIM`, `OpenDMARC` — **clase nueva nº 21** |
| **EUPL-1.2** | `zone-eu/zone-mta`, `zone-eu/wildduck` |
| **GPL-3.0** | `foxcpp/maddy` (6.142 ★), `liuch/dmarc-srg`, `mautic/mautic` (línea **91**) |
| **AGPL-3.0** | `knadh/listmonk` (24.446 ★), `pentacent/keila`, `elie222/inbox-zero` |
| **CC0-1.0** | `mail-in-a-box/mailinabox` (15.481 ★) |
| **Sin fichero de licencia** | `stalwartlabs/stalwart` (**16.280 ★**) |

**Los cuatro hallazgos de instrumento de este pase (T89–T92):**

1. **`LICENSE.md` correlaciona con `NOASSERTION` — 2 de 2** (`rspamd` → Apache-2.0,
   `Mailu` → MIT, ambos verbatim). **La correlación se registra; el mecanismo NO se afirma**: puede
   ser la extensión o la línea de copyright modificada.
2. **El registro gana cuando el fichero está ROTO, no sólo cuando falta.** `nodemailer`: `LICENSE`
   presente, legible y **sin condiciones** → la API dice `NOASSERTION` porque no coincide ni con MIT
   ni con MIT-0; el registro dice **MIT-0**. Extiende la regla de `date-fns` del pase dieciocho del
   caso «ausente» al caso «presente y malformado», que es peor porque invita a confiar.
3. **Una licencia compuesta se localiza por número de línea.** `mautic/mautic`: `LICENSE.txt` de
   38.326 B que **abre con avisos de terceros** (Apache-2.0 de *Mousetrap*, línea 54) y no llega a la
   **GPL-3.0** hasta la **línea 91**.
4. **Una insignia del README no es un fichero de licencia.** `stalwart`: **8 rutas canónicas → 8
   ×404**, `Cargo.toml` sin campo `license`, y la AGPL-3.0 afirmada sólo en insignia y prosa — con
   **16.280 ★**. **`NOASSERTION` y `null` no son el mismo dato.**

**Y una dirección que no se escribió porque se verificó primero:** `Snawoot/mta-sts-daemon`, el
nombre que usan varias guías, **no existe** — la API responde **HTTP 422** *«repositories cannot be
searched either because the resources do not exist»*. El repo real es
**`Snawoot/postfix-mta-sts-resolver`** (MIT, 127 ★, push 2025-10-10). Su primo
`SGSGermany/mta-sts-resolver` está **archivado** desde 2023. *La regla «verificar antes de escribir»
pagó dos veces en un solo pase.*

**Ramas por defecto:** el `main` ciego habría fallado **18 de 28 veces** en la capa de
infraestructura (`master` ×15, `trunk`, `develop`, `7.x`).

## 2026-11-24 — vigesimosegundo pase — el backbone de eventos: 22 citas a Debezium y cero a Kafka

> Tema: **la tenencia y el bus que la transporta.** **13 direcciones verificadas el 2026-11-24**
> (10 repos nuevos para esta KB + 3 ya presentes con una propiedad nueva probada a nivel de
> fichero). Instrumentos: `git ls-remote` (existencia + rama por defecto),
> `raw.githubusercontent.com` (**`LICENSE` byte a byte**) y — **nuevo para toda la flota** —
> `gh api -X GET search/code -f q='…'`, que demuestra que una *feature* vive dentro del repo
> permisivo y no en un directorio de pago.
>
> **El hallazgo de inventario, y es el más simple de todos los pases:** esta KB citaba
> **Debezium 22 veces** — que es un **plugin de Kafka Connect** — y la palabra **`Kafka`
> aparecía 0 veces**. Se había adoptado el conector sin nombrar nunca el bus. `pulsar` = 1,
> `nats-io`/`automq`/`redpanda` = 0.
>
> Nuevos, con la primitiva de tenencia probada por búsqueda de código:
> - **[apache/kafka](https://github.com/apache/kafka)** — Apache-2.0, 34,3k ★ — cuotas por
>   principal **en el core**: `server/.../quota/ClientQuotaManager.java` + `QuotaFactory.java`.
> - **[apache/pulsar](https://github.com/apache/pulsar)** — Apache-2.0, 15,4k ★ — **`tenant` es
>   entidad de primera clase**: `admin/v2/Tenants.java`, `CmdTenants.java`, `client-admin-api`.
> - **[nats-io/nats-server](https://github.com/nats-io/nats-server)** — Apache-2.0, 21,1k ★,
>   CNCF — `server/accounts.go` = **5.055 líneas**; la `Account` aísla y `exports`/`imports` son
>   la única forma de cruzar. **El README no menciona «accounts» ni multi-tenencia:** la
>   primitiva es invisible desde la portada.
> - **[AutoMQ/automq](https://github.com/AutoMQ/automq)** — **Apache-2.0 verificado**, 10,9k ★ —
>   la API de Kafka sin BSL. Origen **APAC** (AutoMQ HK Limited, leído del `NOTICE`).
> - **[openbao/openbao](https://github.com/openbao/openbao)** — **MPL-2.0**, 9,2k ★ — claves por
>   inquilino. MPL **no** es permisiva: copyleft débil por fichero.
> - **[pgvector/pgvector](https://github.com/pgvector/pgvector)** — **licencia PostgreSQL**
>   (byte a byte: *«Portions Copyright (c) 1996-2026, PostgreSQL Global Development Group»*),
>   23,8k ★, **sin insignia en GitHub**. Segundo recordatorio de la rotación: **ausencia de
>   insignia no es ausencia de licencia.**
>
> Ya presentes, con propiedad nueva probada:
> - **qdrant/qdrant** (Apache-2.0, 35,7k ★) — `is_tenant` = **25** coincidencias, incl.
>   `lib/segment/src/types.rs`: el índice por inquilino está **dentro** del repo permisivo.
> - **milvus-io/milvus** (Apache-2.0, 46,7k ★) — `partition_key` = **81** coincidencias.
> - **keycloak/keycloak** (Apache-2.0, 38,0k ★) — **Organizations en el core**:
>   `server-spi/.../OrganizationModel.java`. La extensión ELv2 de terceros **es innecesaria**.
> - **BerriAI/litellm** (MIT) — `customer_hierarchy` = **95** coincidencias en `types/proxy/auth`,
>   `proxy/auth` y `management_helpers`, más un **gateway en Rust**
>   (`litellm/rust/crates/gateway/src/host/auth/mod.rs`).
>
> **Descartado por licencia, con el texto en la mano:** `redpanda-data/redpanda` (BSL 1.1 +
> Redpanda Community License en `dev`, más un tercer nombre sólo en el README) y
> `p2-inc/keycloak-orgs` (**Elastic License 2.0** en `COPYING`).
>
> **Canal de verificación — lo que no se pudo comprobar:** `api.github.com/repos` está denegado
> por el alcance de la sesión; el HTML de `github.com` da 403 por `curl` (pero sí responde a
> `WebFetch`); y **`weaviate.io`, `qdrant.tech`, `docs.nats.io`, `www.eweek.com` e
> `itbrief.com.au` no resuelven** en esta sesión. Por eso **toda la documentación de proveedor y
> toda la prensa de este pase quedan listadas-sin-verificar a nivel de página**, mientras **todo
> lo de repositorio está verificado byte a byte**. La asimetría es deliberada y es el motivo por
> el que las primitivas se probaron leyendo *código*, no documentación.

## 2026-11-24 — vigesimoprimer pase — la capa de voz: 39 direcciones verificadas, 39 nuevas, y la cadena de seis eslabones con seis licencias

> Tema: **el canal hablado.** **39 direcciones verificadas el 2026-11-24, las 39 nuevas para esta
> KB** — el porcentaje de novedad más alto de cualquier pase (100%), porque la capa entera faltaba.
> Instrumentos: `raw.githubusercontent.com` para **leer `LICENSE` byte a byte**, `git ls-remote`
> para existencia y rama por defecto, `WebFetch` sobre el HTML de GitHub para estrellas/archivado,
> y `pypi.org/pypi/<pkg>/json` para clasificadores de licencia **independientes de la forja**.
> Denegados en esta sesión: `api.github.com`, `gh api`, `curl https://github.com` (403, alcance de
> sesión) y **`huggingface.co` (403, `connect_rejected` del proxy de egreso)**.

### La estructura del hallazgo: un agente de voz tiene seis eslabones, no uno

transporte (WebRTC/SIP) → VAD y **detección de turno** → STT → el agente → TTS → grabación y
evidencia. **Cada eslabón lleva su propia licencia, y gobierna la más restrictiva de la cadena** —
que en voz casi nunca es la del framework de agentes. Por eso un pase que buscara «frameworks de
voz» habría traído cinco filas; buscar por *eslabón* trajo 39.

### Lo nuevo por capa (todas con licencia leída, no de badge)

- **Transporte permisivo de extremo a extremo**: [livekit/livekit](https://github.com/livekit/livekit)
  (Apache-2.0, 22,400 ★) + [livekit/sip](https://github.com/livekit/sip) (Apache-2.0) — **la ruta
  que evita Asterisk por completo**; y la pila MIT [jambonz/jambonz-feature-server](https://github.com/jambonz/jambonz-feature-server)
  + [jambonz/jambonz-api-server](https://github.com/jambonz/jambonz-api-server) sobre
  [drachtio/drachtio-server](https://github.com/drachtio/drachtio-server).
- **El borde copyleft que el cliente ya tiene**: [asterisk/asterisk](https://github.com/asterisk/asterisk)
  (**GPL-2.0**, doble licencia con Sangoma), [signalwire/freeswitch](https://github.com/signalwire/freeswitch)
  (**MPL-1.1**), [kamailio/kamailio](https://github.com/kamailio/kamailio) y
  [OpenSIPS/opensips](https://github.com/OpenSIPS/opensips) (**GPL-2.0**),
  [FreePBX/framework](https://github.com/FreePBX/framework) (**GPL-3.0**).
- **El eslabón que nadie lista y decide si el agente suena humano**:
  [pipecat-ai/smart-turn](https://github.com/pipecat-ai/smart-turn) (**BSD-2-Clause**) — fin de turno
  **semántico**, no por silencio: distingue «mi número es…» (pausa, sigue) de una frase terminada.
  Con [snakers4/silero-vad](https://github.com/snakers4/silero-vad) (MIT) debajo.
- **STT**: [openai/whisper](https://github.com/openai/whisper), [SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper),
  [ggml-org/whisper.cpp](https://github.com/ggml-org/whisper.cpp) (MIT los tres),
  [m-bain/whisperX](https://github.com/m-bain/whisperX) (**BSD-2-Clause**, alineación por palabra),
  [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) (Apache-2.0, 16,200 ★ — **STT+TTS+VAD+diarización
  en un runtime ONNX**), [alphacep/vosk-api](https://github.com/alphacep/vosk-api) (Apache-2.0),
  [speechbrain/speechbrain](https://github.com/speechbrain/speechbrain), [espnet/espnet](https://github.com/espnet/espnet),
  [NVIDIA-NeMo/NeMo](https://github.com/NVIDIA-NeMo/NeMo) (Apache-2.0).
- **TTS**: [hexgrad/kokoro](https://github.com/hexgrad/kokoro) (Apache-2.0, 10,300 ★) +
  [remsky/Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI), [nari-labs/dia](https://github.com/nari-labs/dia)
  (Apache-2.0), [SWivid/F5-TTS](https://github.com/SWivid/F5-TTS) (MIT), [idiap/coqui-ai-TTS](https://github.com/idiap/coqui-ai-TTS) (MPL-2.0).
- **Voz a voz**: [kyutai-labs/moshi](https://github.com/kyutai-labs/moshi) (11,600 ★),
  [fixie-ai/ultravox](https://github.com/fixie-ai/ultravox) (MIT), [QwenLM/Qwen3-Omni](https://github.com/QwenLM/Qwen3-Omni) (Apache-2.0).
- **Locutor y antisuplantación**: [pyannote/pyannote-audio](https://github.com/pyannote/pyannote-audio) (MIT),
  [resemble-ai/resemblyzer](https://github.com/resemble-ai/resemblyzer) (Apache-2.0),
  [clovaai/aasist](https://github.com/clovaai/aasist) (MIT, detección de voz sintética).
- **Pegamento y on-prem**: [speaches-ai/speaches](https://github.com/speaches-ai/speaches) (MIT, API
  **compatible OpenAI** para STT/TTS auto-alojado), [rhasspy/wyoming](https://github.com/rhasspy/wyoming) (MIT),
  [OpenVoiceOS/ovos-core](https://github.com/OpenVoiceOS/ovos-core) (Apache-2.0).
- **Evaluación, la capa que casi no existe**: [ServiceNow/eva](https://github.com/ServiceNow/eva)
  (MIT, puntúa conversación **hablada** multi-turno en tarea *y* audio) y
  [sujitnoronha/voicecheck](https://github.com/sujitnoronha/voicecheck) (MIT, latencia al primer
  byte, degradación de audio, **barge-in**, carga).
- **Corpus**: [common-voice/common-voice](https://github.com/common-voice/common-voice) (MPL-2.0).

### Cuatro direcciones que este pase se NEGÓ a escribir (un 404 no es un hallazgo)

| Candidato | Por qué lo recomendaban | Qué se midió |
|---|---|---|
| **VICIdial** | la fuente secundaria más citada como mejor contact centre OSS, «>14.000 instalaciones» | `vicidial/vicidial` existe pero su **`HEAD` apunta a `gh-pages`** → es el sitio web, no el producto; `VICIDIAL/astguiclient` **no existe**. El código vive en SVN fuera de GitHub |
| **Dograh** | su propio post lo da como voz-IA auto-alojable BSD-2-Clause | `dograh-ai/dograh` y `dograh/dograh` **no resuelven** |
| **Issabel** | contact centre sobre Asterisk | `issabel/issabelPBX`, `IssabelPBX/issabelPBX` **no resuelven** |
| **GOautodial** | contact centre comunitario sobre Asterisk | `GOautodial/GOautodial` **no resuelve** |

**La regla que esto confirma, por si el próximo pase la necesita:** `git ls-remote --symref … HEAD`
cuesta una llamada y distingue tres estados que un enlace no distingue — **existe y es el producto**
(`HEAD → main/master`), **existe y es un sitio web** (`HEAD → gh-pages`), y **no existe** (git pide
credenciales, que es el 404 de un repositorio público inexistente). El caso `gh-pages` es el
peligroso: el enlace **funciona**, devuelve 200, y no es software.

### El hueco de producto que queda abierto

**No existe librería mantenida que encadene diarización + Presidio + silenciado por marca de
tiempo** para redactar PII de una grabación de llamada. Buscado explícitamente; lo que hay es un
prototipo académico (OST, 2026) y ejemplos de proveedor atados a una nube. Las piezas existen todas
y están verificadas arriba (`whisperX` alinea por palabra, `pyannote-audio` diaríza,
`data-privacy-stack/presidio` —ya en esta KB desde el cuarto pase— detecta PII, `ffmpeg` silencia).
**Receta 42 de `compose/patterns.md` la construye.** Es trabajo facturable con un hueco de mercado
medido detrás.

## 2026-11-24 — vigésimo pase — la capa del ciclo de vida: 24 direcciones verificadas, 23 nuevas, y cuatro `NOASSERTION` con cuatro veredictos distintos

> Tema: **el alta y la baja de la identidad del agente, y el RPO del estado que deja atrás.**
> 24 direcciones verificadas el **2026-11-24**. **23 de las 24 eran nuevas** para esta KB (la
> única que ya estaba, `microsoft/agent-governance-toolkit`, llevaba 12 pases sin que nadie
> nombrara el componente que importa). Trece términos de esta capa estaban medidos en **cero**.
>
> **El plano de verificación cambió y hay que registrarlo.** `api.github.com/repos/...` y el
> HTML de `github.com` dan **403** por el proxy de esta sesión. Lo que **sí** funciona:
> `gh api -X GET search/repositories -f q='repo:<o>/<n>'` (estrellas, forks, `pushed_at`,
> `archived`), `git ls-remote`, el clon `--bare --depth 1 --filter=blob:none` (fecha del último
> commit **y el árbol completo de archivos sin bajar un blob**) y `raw.githubusercontent.com`
> para leer licencias byte a byte.

**Enumerar (5):** [cartography-cncf/cartography](https://github.com/cartography-cncf/cartography)
(Apache-2.0, 4,201★), [prowler-cloud/prowler](https://github.com/prowler-cloud/prowler)
(Apache-2.0, 15,321★),
[cloud-custodian/cloud-custodian](https://github.com/cloud-custodian/cloud-custodian)
(Apache-2.0, 6,118★), el componente `agent-governance-python/agent-discovery/` de
[microsoft/agent-governance-toolkit](https://github.com/microsoft/agent-governance-toolkit)
(MIT, 6,603★) y
[Defend-AI-Tech-Inc/agent-discover-scanner](https://github.com/Defend-AI-Tech-Inc/agent-discover-scanner)
(MIT, 23★, dormido desde 2026-07-28).

**Aprovisionar y desaprovisionar (8):** [apache/syncope](https://github.com/apache/syncope)
(Apache-2.0, **349★ y un commit hoy** — en esta capa las estrellas no son la señal),
[Evolveum/midpoint](https://github.com/Evolveum/midpoint) (**EUPL-1.2-or-later**, 556★),
[goauthentik/authentik](https://github.com/goauthentik/authentik) (**MIT excepto
`authentik/enterprise/`**, 26,448★), la familia canónica **`python-scim`**
([scim2-models](https://github.com/python-scim/scim2-models) 30★,
[scim2-client](https://github.com/python-scim/scim2-client) 19★,
[scim2-cli](https://github.com/python-scim/scim2-cli) 9★,
[scim2-tester](https://github.com/python-scim/scim2-tester) 10★ — todas Apache-2.0) y
[elimity-com/scim](https://github.com/elimity-com/scim) (MIT, 255★).

**Credenciales (3):**
[external-secrets/external-secrets](https://github.com/external-secrets/external-secrets)
(Apache-2.0, 6,961★), [cert-manager/cert-manager](https://github.com/cert-manager/cert-manager)
(Apache-2.0, 14,173★) e [Infisical/infisical](https://github.com/Infisical/infisical)
(**MIT excepto `ee/`**, 30,732★).

**El RPO del estado (5):**
[cloudnative-pg/cloudnative-pg](https://github.com/cloudnative-pg/cloudnative-pg)
(Apache-2.0, 9,657★), [pgbackrest/pgbackrest](https://github.com/pgbackrest/pgbackrest)
(**MIT**, 4,510★), [velero-io/velero](https://github.com/velero-io/velero) (Apache-2.0, 10,386★),
[restic/restic](https://github.com/restic/restic) (**BSD-2-Clause**, 37,429★) y
[kopia/kopia](https://github.com/kopia/kopia) (Apache-2.0, 14,809★).

**Tres exclusiones medidas, no silenciosas:**

| Repo | Licencia | ★ | pushed | Por qué fuera |
|---|---|---|---|---|
| [Captain-P-Goldfish/scim-for-keycloak](https://github.com/Captain-P-Goldfish/scim-for-keycloak) | BSD-3-Clause | 210 | **2024-03-10** | `# End of Life` es el **primer encabezado de su README**, y GitHub **no** lo marca como archivado |
| [EnterpriseDB/barman](https://github.com/EnterpriseDB/barman) | **GPL-3.0** | 3,282 | 2026-11-18 | Vivo y competente, pero copyleft: hay dos permisivas para lo mismo |
| `agentmesh-discovery` (PyPI 5.0.0, MIT) | — | — | 2026-08-03 | **No se excluye el paquete, se excluye su puntero**: su URL de documentación declara `…/tree/main/agent-discovery`, directorio que **no existe**; la ruta real lleva el prefijo `agent-governance-python/` |

**Cuatro `NOASSERTION`, cuatro veredictos distintos** — la demostración más limpia de que el
badge no contiene información: `pgbackrest` → **MIT**; `authentik` → **MIT con carve-out**;
el repo de OWASP → **CC-BY-SA-4.0** (licencia de contenido); `midpoint` → **EUPL-1.2** copyleft,
y sus **docs en CC BY-NC-ND** (ni comercial ni derivadas: no se puede reempaquetar su
documentación en un entregable de cliente).

**Tres renombres corregidos, con un método nuevo.** `search/repositories` solo indexa el nombre
**canónico**, así que un `repo:` con `total_count: 0` mientras `git ls-remote` y `raw` dan 200 es
la firma exacta de un redirect — `git` y `raw` siguen los renombres en silencio.
`lyft/cartography` → **`cartography-cncf/`**; `capitalone/cloud-custodian` →
**`cloud-custodian/`**; `vmware-tanzu/velero` → **`velero-io/velero`**, con el matiz de que los
plugins (`velero-plugin-for-csi`, `-for-vsphere`) **siguen** canónicamente en `vmware-tanzu`:
el núcleo migró y los plugins no.

## 2026-11-24 — decimonoveno pase — la capa heredada: 30 direcciones verificadas, 29 nuevas, y una licencia que contradice a la prensa

> Tema: **el sistema de registro que precede a todo repo de esta KB.** 30 direcciones verificadas el
> **2026-11-24** con `gh api -X GET search/repositories` (SPDX + estrellas + `pushed_at` +
> `archived` + `fork` en una sola llamada) y **cada NOASSERTION resuelto leyendo el archivo de
> licencia byte a byte** por `raw.githubusercontent.com`. **29 de las 30 eran nuevas** para la KB.

**Titular: "OpenRewrite es Apache-2.0" es verdad del motor y falso de las recetas.**

| Módulo | Licencia leída | ★ | Push |
|---|---|---|---|
| `openrewrite/rewrite` | **Apache-2.0** | 4011 | 2026-11-24 |
| `openrewrite/rewrite-spring` | **Moderne Source Available License** | 407 | 2026-11-24 |
| `openrewrite/rewrite-migrate-java` | **Moderne Source Available License** | 168 | 2026-11-24 |

La MSAL concede "use, copy, **distribute internally**" y **prohíbe** "offering a product or service,
the value of which derives to any extent from the value of the Software", nombrando como ejemplos
prohibidos a Sourcegraph Batch Changes, Amazon Q Code Transformer y Broadcom Application Advisor.
Fuentes secundarias de 2026 afirman que "el motor y las recetas siempre serán open source"; **el
archivo del repo dice otra cosa**. Lectura del texto, no dictamen legal → **a Legales antes de
cotizar**.

**Nuevas en motores de transformación:** `ast-grep/ast-grep` (MIT, **16687★**, hoy) ·
`biomejs/gritql` (MIT, **4631★** — **movido desde `getgrit/gritql`**, que aún redirige) ·
`joernio/joern` (Apache-2.0, 3664★, **sin frontend COBOL**: no prometer CPG sobre mainframe).

**Nuevas en COBOL:** `uwol/proleap-cobol-parser` (MIT, 211★, **push 2026-03-01: usable, no vivo**) ·
`yutaro-sakamoto/tree-sitter-cobol` (MIT, 39★) · `Spantree/tree-sitter-cobol-enterprise` (**MIT** por
lectura byte a byte, 8★ — **la única gramática con `EXEC CICS`/`EXEC SQL` completos**) ·
`eclipse-che4z/che-che4z-lsp-for-cobol` (**EPL-2.0** por lectura, 119★, vivo) ·
`OCamlPro/superbol-studio-oss` (**AGPL-3.0 en `src/lsp`**, licencia **por directorio**, 49★) ·
`spgennard/vscode_cobol` (MIT, 52★) · `OCamlPro/gnucobol` (LGPL-3.0, 72★, hoy).
**Conclusión medida: no existe LSP COBOL semántico de producción con licencia permisiva.**

**Nuevas en plomería z/OS:** `zopencommunity/meta` (Apache-2.0, 55★, hoy; **399 repos** de ports a
z/OS: bashport, gitport, makeport, zoslibport, perlport) · `zowe/zowe-cli` (EPL-2.0, 139★) ·
`openmainframeproject/software-discovery-tool` (Apache-2.0, 42★, hoy) ·
`openmainframeproject/tersedecompress` (Apache-2.0, 30★ — **sin esto no se abre el transfer del
cliente**) · `galasa-dev/galasa` (EPL-2.0, 16★).

**Nuevas en SAP:** `abapGit/abapGit` (MIT, 1984★) · `SAP/abap-cleaner` (Apache-2.0, 697★) ·
`SAP/code-pal-for-abap` (Apache-2.0, 444★) · `marcellourbani/vscode_abap_remote_fs` (MIT, 411★) ·
`abap2UI5/abap2UI5` (MIT, 392★) · `abaplint/abaplint` (MIT, 323★ — **el parser ABAP fuera de SAP:
valida la salida del modelo antes de escribirla**) · `SAP/abap-file-formats` (MIT, 114★) ·
`open-abap/open-abap-core` (MIT, 67★) · `SAP/styleguides` (**CC BY 3.0** por lectura, 2055★ —
**prosa, no software**).

**Nuevas en IBM i:** `codefori/vscode-ibmi` (MIT, 430★) · `codefori/vscode-db2i` (MIT, 80★) ·
`codefori/vscode-rpgle` (MIT, 59★) · `Mapepire-IBMi/mapepire-server` (**GPL-3.0**, 50★) frente a
sus clientes `-js`/`-java`/`-python`/`-jdbc` (**Apache-2.0** los cuatro): **servidor copyleft en la
caja del cliente, clientes permisivos en el producto.**

**Archivado-pero-recomendado, caso 8:** `openmainframeproject/cobol-check` (Apache-2.0, **107★**,
**ARCHIVADO 2026-05-28**) — el framework de unit testing de COBOL, justo lo que prueba que una
migración preserva comportamiento. Sustituto: golden-master contra GnuCOBOL.

**No-open-source con aspecto de open source:** `BroadcomMFD/cobol-control-flow` (16★, badge
NOASSERTION) → `LICENSE.md` = "Copyright © 2020 Broadcom. All rights reserved." Convive en la misma
familia de extensiones que el LSP EPL-2.0 de che4z.

**Estrellas que no son una base:** `openmainframeproject/cobol-programming-course` **3673★** y
**CC-BY-4.0** — es un **curso**. Ordenar esta vertical por estrellas pone material didáctico encima
de todo el tooling junto.

**Instrumentos (medidos hoy):** `api.github.com/repos` → **403**; `ungh.cc` e `img.shields.io` →
**respuesta vacía** por este proxy (no reintentar); `raw.githubusercontent.com` → **funciona** con
GET (`HEAD` bloqueado), probando `main` **y** `master` (che4z y superbol viven en `master`);
`search/repositories` **excluye forks** → `ls-remote` OK + ausente de `repo:` = **fork**.

## 2026-11-24 — decimoctavo pase — la capa del calendario: 34 direcciones, 29 nuevas, y la licencia de los datos no es la del código

> Tema: **el calendario con el que se cuentan los plazos.** **34 direcciones** verificadas con
> `gh api -X GET search/repositories` el **2026-11-24** (SPDX, estrellas, `default_branch`,
> `pushed_at`, `archived` en una sola llamada, varios `repo:` por consulta), **29 nuevas** para la KB.
> `api.github.com` responde **403** para repos fuera del alcance de la sesión y `gh api repos/<x>`
> también, así que **la API de búsqueda es el único canal**. Toda insignia `NOASSERTION`/`NONE` se
> resolvió **leyendo los bytes** del `LICENSE` por `raw.githubusercontent.com`.

**La fuente de verdad (2):**
[`eggert/tz`](https://github.com/eggert/tz) **dominio público** 1 938★ push 2026-11-23 ·
[`python/tzdata`](https://github.com/python/tzdata) **Apache-2.0** 126★

**El formato y la localización (2, ya en la KB desde el pase dieciséis, aquí con la licencia leída):**
[`unicode-org/cldr`](https://github.com/unicode-org/cldr) 1 172★ ·
[`unicode-org/icu`](https://github.com/unicode-org/icu) 3 652★ — ambos con push **el día de hoy**.

**Los datos de festivos (6):**
[`vacanza/holidays`](https://github.com/vacanza/holidays) **MIT** 1 997★ rama **`dev`** ·
[`commenthol/date-holidays`](https://github.com/commenthol/date-holidays) **`(ISC AND CC-BY-SA-4.0)`** 1 122★ ·
[`nager/Nager.Date`](https://github.com/nager/Nager.Date) **MIT** 1 441★ ·
[`focus-shift/jollyday`](https://github.com/focus-shift/jollyday) **Apache-2.0** 144★ ·
[`svendiedrichsen/jollyday`](https://github.com/svendiedrichsen/jollyday) 197★ **inactivo desde 2024-05-01** ·
[`workalendar/workalendar`](https://github.com/workalendar/workalendar) **MIT** 946★ **inactivo desde 2024-04-12**

**La aritmética de fechas (9):**
[`date-fns/date-fns`](https://github.com/date-fns/date-fns) **36 663★ y la insignia dice `NONE`** ·
[`moment/luxon`](https://github.com/moment/luxon) **MIT** 16 457★ ·
[`moment/moment-timezone`](https://github.com/moment/moment-timezone) **MIT** 3 880★ rama **`develop`** ·
[`python-pendulum/pendulum`](https://github.com/python-pendulum/pendulum) **MIT** 6 685★ ·
[`arrow-py/arrow`](https://github.com/arrow-py/arrow) **Apache-2.0** 9 053★ ·
[`dateutil/dateutil`](https://github.com/dateutil/dateutil) **Apache-2.0 *y* BSD-3** 2 647★ ·
[`nodatime/nodatime`](https://github.com/nodatime/nodatime) **Apache-2.0** 3 007★ ·
[`JodaOrg/joda-time`](https://github.com/JodaOrg/joda-time) **Apache-2.0** 4 977★ ·
[`HowardHinnant/date`](https://github.com/HowardHinnant/date) **MIT por archivo** 3 441★

**La norma y la recurrencia (5):**
[`tc39/proposal-temporal`](https://github.com/tc39/proposal-temporal) **BSD de Ecma, sin concesión de patentes de terceros** 3 703★ ·
[`js-temporal/temporal-polyfill`](https://github.com/js-temporal/temporal-polyfill) **ISC** 798★ ·
[`jkbrzt/rrule`](https://github.com/jkbrzt/rrule) **BSD-3 ×2** 3 753★ ·
[`ical4j/ical4j`](https://github.com/ical4j/ical4j) **BSD-3-Clause** 844★ rama **`develop`** ·
[`sabre-io/vobject`](https://github.com/sabre-io/vobject) **BSD-3-Clause** 603★

**El día hábil como convención financiera (1), y el planificador (2):**
[`lballabio/QuantLib`](https://github.com/lballabio/QuantLib) **BSD-style** 7 799★ push hoy ·
[`apache/airflow`](https://github.com/apache/airflow) **Apache-2.0** 47 650★ ·
[`fullcalendar/fullcalendar`](https://github.com/fullcalendar/fullcalendar) **MIT** 20 790★

**La esquina de las aplicaciones de calendario (4 verificadas + 1 ya en la KB) es ESTRUCTURALMENTE
COPYLEFT, segunda aparición del patrón en dos pases:**
[`lukevella/rallly`](https://github.com/lukevella/rallly) **AGPL-3.0** 5 368★ ·
[`Kozea/Radicale`](https://github.com/Kozea/Radicale) **GPL-3.0** 5 249★ ·
[`alextselegidis/easyappointments`](https://github.com/alextselegidis/easyappointments) **GPL-3.0** 4 502★ ·
[`nextcloud/calendar`](https://github.com/nextcloud/calendar) **AGPL-3.0** 1 200★ · más `cal.com`
(**AGPL-3.0**), que la KB ya tenía. **Cinco de cinco.** El pase diecisiete midió exactamente esto en
el transporte AS4/Peppol (Oxalis-NG EUPL, Holodeck y OpenAS2 GPL-3.0, Domibus EUPL, con una sola pila
permisiva viva). **Dos capas distintas, el mismo reparto: la biblioteca es permisiva, la aplicación
de cara al usuario es recíproca.** Eso va en la sección de riesgos de la propuesta, no en el anexo.

**TRES CONFIRMACIONES INDEPENDIENTES, EN UN SOLO PASE, DE LA REGLA QUE LA KB YA TENÍA: EL SPDX DE UN
REPOSITORIO DESCRIBE SU CÓDIGO, NO LO QUE EMPAQUETA.** Séptima, octava y novena aparición, y las tres
leídas byte a byte:

1. **`commenthol/date-holidays` lo declara él mismo, y es el contraejemplo del pase diecisiete.** Su
   `package.json` dice `"license": "(ISC AND CC-BY-SA-4.0)"` y su `LICENSE` (13 715 B) explica por
   qué: «*The data contained in `holidays.yaml` is available under CC BY-SA 4.0 … as the data obtained
   relies on wikipedia articles. All other code is Copyright (c) 2015 commenthol and available under
   ISC*». **El código es permisivo y los datos de festivos son share-alike.** El pase diecisiete
   escribió que ningún repo de 200★+ de su capa publicaba una expresión compuesta; **aquí uno de
   1 122★ sí la publica**, y por eso GitHub dice `NOASSERTION`: no es desidia, es honestidad.
2. **`unicode-org/cldr`: un repositorio, dos regímenes.** Su `LICENSE` (3 193 B) dice que UTS #35
   (el documento de la norma LDML) «*may not make copies of or modifications to this publication for
   public distribution, or incorporate it in whole or in part into any product or publication without
   the express written permission of Unicode*», y después: «*All other content in this repo is
   released under UNICODE LICENSE V3*». **Los datos de locale se pueden distribuir; el texto de la
   norma no se puede incorporar a un entregable.**
3. **`eggert/tz`: dominio público condicionado a la presencia de archivos.** Su `LICENSE` son **252
   bytes**: «*Unless specified below, all files in the tz code and data (including this LICENSE file)
   are in the public domain. If the files date.c, newstrftime.3, and strftime.c are present, they
   contain material derived from BSD and use the BSD 3-clause license*». **La licencia depende de qué
   archivos hayas copiado.**

**`date-fns` invierte el canal de resolución: la insignia no dice de menos, dice NADA.** 36 663★ y
cinco rutas probadas (`LICENSE`, `LICENSE.txt`, `LICENSE.md`, `license.md`, `LICENCE`) devuelven
**404**; el `package.json` de la raíz es `@date-fns/root`, `"private": true`, **sin campo
`license`**. La insignia `NONE` es **literalmente correcta sobre la raíz del repositorio**. El
artefacto publicado sí la declara: `https://registry.npmjs.org/date-fns/latest` → **`4.4.0`,
`license: MIT`**. **Se resuelve en el registro, no en la forja** — la misma regla que esta KB ya
aplicaba con los clasificadores de PyPI, ahora probada en npm y en la dirección contraria.

**Dos renombrados que los *roundups* siguen citando mal, y el canal para detectarlos.**
`dr-prodigy/python-holidays` y `sdispater/pendulum` **no aparecen** en la API de búsqueda, mientras
`vacanza/holidays` y `python-pendulum/pendulum` sí. No se pudo confirmar un 301 porque
**`github.com` en HTML responde 403 a través del proxy de esta sesión**: la evidencia es la ausencia
en el índice canónico, no la redirección. El primer resultado de búsqueda web de la capa apuntaba al
path viejo.

**`jollyday` es el patrón «las estrellas apuntan al muerto», y aquí con una inversión limpia:** el
original `svendiedrichsen/jollyday` tiene **197★** y lleva **inactivo desde 2024-05-01**; el fork
mantenido `focus-shift/jollyday` tiene **144★**, **Apache-2.0** y push **2026-11-19**. **El
mantenido tiene menos estrellas que el abandonado.** Y `workalendar` (**MIT**, 946★) lleva
**inactivo desde 2024-04-12** sin estar archivado, así que la forja lo muestra vivo: **un
calendario de festivos sin mantenimiento no es código viejo, es código incorrecto**, porque los
festivos los cambia un parlamento.

**Ramas por defecto: el `main` ciego habría fallado 19 de 34 veces.** No-`main`: `dev` (vacanza),
`develop` (moment-timezone, ical4j, erpnext), `trunk` (ofbiz), **`20.0`** (odoo) y `master` en trece
más. Tercera vez que esta KB registra la misma medida, y sube del 6/46 del pase diecisiete al
**19/34** de este.

## 2026-11-24 — decimoséptimo pase — el documento de registro fiscal: 46 direcciones y una norma que no se valida igual a sí misma

> Tema: **el documento que no valida el cliente, sino el Estado.** **46 direcciones** verificadas con
> `gh api -X GET search/repositories` el **2026-11-24** (estrellas, SPDX, `pushed_at`,
> `default_branch`, `archived` en **una sola llamada**, varios `repo:` por consulta), porque
> `api.github.com` responde **403** desde esta sesión para repos fuera de su alcance. Toda insignia
> `NOASSERTION`/`null` se resolvió **leyendo los bytes** por GET con rango (`HEAD` sigue bloqueado por
> el proxy). **Dos repos se clonaron** (`--depth 1`) porque la pregunta no era qué licencia declara el
> repo, sino **qué archivos de terceros empaqueta**.

**Los artefactos oficiales y los validadores (5):**
[`ConnectingEurope/eInvoicing-EN16931`](https://github.com/ConnectingEurope/eInvoicing-EN16931)
**EUPL-1.2** (`LICENSE.txt` **13 871 B**; insignia `NOASSERTION`) 271★ ·
[`itplr-kosit/validator`](https://github.com/itplr-kosit/validator) **Apache-2.0** 199★ ·
[`itplr-kosit/validator-configuration-xrechnung`](https://github.com/itplr-kosit/validator-configuration-xrechnung)
**Apache-2.0** 120★ ·
[`einvoice-validator/einvoice-validator`](https://github.com/einvoice-validator/einvoice-validator)
**código MIT / binario de cinco licencias** 1★ ·
[`attestwire/en16931`](https://github.com/attestwire/en16931) **MIT** 1★.

**El transporte AS4/Peppol (7):** [`phax/phase4`](https://github.com/phax/phase4) **Apache-2.0**
(10 173 B) 246★ · [`phax/phoss-ap`](https://github.com/phax/phoss-ap) **Apache-2.0** 59★ (push
**hoy**) · [`phax/peppol-commons`](https://github.com/phax/peppol-commons) **Apache-2.0** 51★ ·
[`phax/phoss-smp`](https://github.com/phax/phoss-smp) **MPL-2.0 el *backend* + Apache-2.0 el resto**
(`LICENSE.md` **347 B**) 216★ · [`OxalisCommunity/oxalis-ng`](https://github.com/OxalisCommunity/oxalis-ng)
**EUPL-1.1-or-later, declarada solo en el `pom.xml`** 53★ ·
[`holodeck-b2b/Holodeck-B2B`](https://github.com/holodeck-b2b/Holodeck-B2B) **GPL-3.0** 93★ ·
[`OpenAS2/OpenAs2App`](https://github.com/OpenAS2/OpenAs2App) **GPL-3.0** 243★.
Más [`iterasdev/peppol-py`](https://github.com/iterasdev/peppol-py) **0BSD** 10★ (**clase de licencia
nº 14**) y [`dbkosky/as4`](https://github.com/dbkosky/as4) **Apache-2.0** 3★.

**Formato híbrido y herramienta Java (3):** [`ZUGFeRD/mustangproject`](https://github.com/ZUGFeRD/mustangproject)
**Apache-2.0** 498★ · [`akretion/factur-x`](https://github.com/akretion/factur-x) **BSD-3-Clause**
(1 508 B; insignia `NOASSERTION`) 317★ · [`phax/ph-ubl`](https://github.com/phax/ph-ubl)
**Apache-2.0** 142★ + [`phax/ph-schematron`](https://github.com/phax/ph-schematron) **Apache-2.0** 137★.

**LATAM, autorización previa (14):** `thegreenter/greenter` **MIT** 378★ · `giansalex/lycet` **MIT**
106★ · `thegreenter/ubl-validator` **MIT** 16★ · `nfephp-org/sped-nfe` **LGPL-3.0** (8 851 B) 1 637★ ·
`akretion/nfelib` **MIT** 224★ · `erpbrasil/erpbrasil.edoc` **MIT** 32★ ·
`edueevaristo/reforma-tributaria-api` **MIT** 1★ (push **hoy**) ·
`grupomg-tech/calculadora-reforma-tributaria` **MIT** 3★ · `OCA/l10n-brazil` **AGPL-3.0** 376★ ·
`phpcfdi/sat-ws-descarga-masiva` **MIT** 198★ · `nodecfdi/cfdi-core` **MIT** 4★ ·
`LibreDTE/libredte-lib-core` **AGPL-3.0** 228★ · `LibreDTE/libredte-api-client-python` **LGPL-3.0**
10★ · `reingart/pyafipws` **LGPL-3.0** 366★ (**sin push desde 2025-07-20**).

**APAC, SDK de régimen (5):** `klsheng/myinvois-php-sdk` **MIT** 103★ ·
`zahidaramai/MyInvoice-SDK-Middleware` **MIT** 13★ · `farhan-syah/myinvois-client` **LGPL-3.0** 51★ ·
`amaseng/myinvois-open-sdk` **Apache-2.0** 31★ **pero sin push desde 2024-10-10** ·
`techtemplemy/mcp-myinvois` **WTFPL** 3★ (**clase nº 15**). `deadboy18/myinvois-docs` queda
**`NOASSERTION` sin resolver**: se registra sin veredicto, no como permisivo.

**Plataformas y extracción (6):** `invoice-x/invoice2data` **MIT** 2 254★ (push **hoy**) ·
`invoicerr-app/invoicerr` **AGPL-3.0** 735★ (rama `dev`) · `invoiceninja/invoiceninja`
**Elastic License 2.0** (`LICENSE` 3 891 B) 10 617★ (rama `v5-stable`) · `akaunting/akaunting`
**Business Source License 1.1** (texto de MariaDB, `LICENSE.txt` 3 654 B) 10 338★ ·
`apache/ofbiz-framework` **Apache-2.0** 1 151★ (rama **`trunk`**) · `frappe/erpnext` **GPL-3.0**
41 602★ (rama **`develop`**).

### Las cuatro cosas que este pase aprendió sobre el método

1. **Sexta vía de resolución de licencia: la cabecera del manifiesto de construcción.**
   `OxalisCommunity/oxalis-ng` no tiene `LICENSE` en ninguna de las seis rutas habituales — la
   licencia (**EUPL-1.1-or-later**) está en el comentario de cabecera del **`pom.xml`**. Orden de
   desempate actualizado: (1) `SPDX-License-Identifier` en el manifiesto, (2) REUSE
   `LICENSES/<SPDX>.txt`, (3) lectura byte a byte + tamaño, (4) clasificadores PyPI,
   (5) **cabecera de `pom.xml`/`build.gradle`/`*.csproj`**. Y su hermano `OxalisCommunity/oxalis`
   (150★) **no tiene licencia en absoluto** (cuatro rutas → 404): **no proponible**, y además su
   propio README dice *«usa Oxalis-NG para toda implementación nueva»* mientras sigue siendo el
   primer resultado de búsqueda. **Variante nueva del patrón «recomendado pero no usable»: no está
   archivado, se desaconseja a sí mismo.**
2. **La regla del tamaño frente a la longitud canónica volvió a pagar, y en los dos sentidos.**
   `phax/phoss-smp` trae **347 B** que *nombran* Apache-2.0 y MPL-2.0: es un **puntero**, y leído
   como prosa dice **MPL-2.0 para `phoss-smp-backend` y Apache-2.0 para el resto** — licencia **por
   módulo**, no por repo. En cambio `ConnectingEurope/eInvoicing-EN16931` trae **13 871 B**, que es
   longitud de licencia completa, y efectivamente **es** la EUPL-1.2 entera.
3. **ADVERTENCIA DE INSTRUMENTO, Y ES LA MÁS IMPORTANTE DE ESTE PASE: desde esta sesión, un GET a
   `github.com` NO PRUEBA NADA.** Comprobado explícitamente: `https://github.com/torvalds/linux`
   devuelve **403** y `https://github.com/this-definitely-does-not-exist-xyz123/nope` devuelve
   **403 también**. **Un repo real y uno inexistente son indistinguibles**, así que un barrido de
   liveness sobre las URL HTML de GitHub produciría 42 falsos negativos o, peor, un «todo correcto»
   si alguien contara los 403 como respuesta. Los tres instrumentos que **sí** prueban existencia
   aquí: (a) `gh api -X GET search/repositories -f q='repo:owner/name'`, que sólo devuelve fila si el
   repo existe; (b) un GET a `raw.githubusercontent.com/<owner>/<repo>/<rama>/<archivo>`, que prueba
   repo **y** rama **y** archivo a la vez; (c) `git clone --depth 1`, que prueba el árbol entero.
   **Las 42 direcciones nuevas de este pase pasaron (a), y las 42 pasaron también (b)** — 39 con
   `README.md` y 3 con `README.rst` (`akretion/factur-x`, `erpbrasil/erpbrasil.edoc`,
   `LibreDTE/libredte-api-client-python`: proyectos Python, donde `README.md` da 404 y el repo está
   perfectamente vivo). **Un 404 de `README.md` no es un repo muerto: es una suposición sobre la
   extensión del README.**

4. **La fecha de push manda sobre la licencia en las capas reguladas.** `amaseng/myinvois-open-sdk`
   es el más permisivo de los cinco SDK de Malasia (**Apache-2.0**) y el **menos utilizable**: dos
   años sin push, contra un SDK oficial que publicó **1.0 en septiembre de 2026**. Un SDK fiscal
   desfasado no rinde peor: **produce documentos rechazados.**

## 2026-11-24 — sixteenth pass — the language boundary, and a licence that lives in a subdirectory

> Theme: **the language the agent speaks, and who signed off on the wording.** **36 new addresses**
> this pass. Licence, stars, archived state and last push come from `gh api search/repositories` on
> **2026-11-24**; every `NOASSERTION` **and `null`** badge was resolved by **byte-reading the licence
> file** over a ranged GET (`HEAD` is blocked by this session's proxy and `api.github.com` answers
> only for session-scoped repos, so neither shortcut existed). **`huggingface.co` is proxy-dead from
> this session (HTTP 000)** — so this pass's **code and licence facts are byte-proven while its one
> model-weights claim is explicitly marked secondary-sourced.** `planalto.gov.br` is also dead
> (HTTP 000), which is why the Brazilian decree is flagged the same way in `intel/market.md`.

**The translation management layer — where a human approves wording (6):**
`mozilla/pontoon` **BSD-3-Clause** 1,679★ · `WeblateOrg/weblate` **GPL-3.0** 6,180★ ·
`tolgee/tolgee-platform` **Apache-2.0 except `ee/`** 4,162★ · `ever-co/ever-traduora` **AGPL-3.0**
2,140★ · `translate/translate` **GPL-3.0** 988★ (ships `pofilter` QA checks) ·
`translate/pootle` GPL-3.0 1,501★ **stale since 2024-08-26**.

**The message-format layer — the shape a translatable string may have (10):**
`unicode-org/message-format-wg` **Unicode-3.0** 424★ · `unicode-org/icu` **Unicode-3.0** 3,651★ ·
`unicode-org/cldr` **Unicode-3.0** 1,172★ · `messageformat/messageformat` **MIT (OpenJS)** 1,773★ ·
`formatjs/formatjs` **MIT per-package** 14,756★ · `i18next/i18next` **MIT** 8,664★ ·
`lingui/js-lingui` **MIT** 5,939★ · `projectfluent/fluent` **Apache-2.0** 1,695★ ·
`projectfluent/python-fluent` **Apache-2.0** 246★ · `tryggvigy/pseudo-localization` **MIT** 141★.

**Engines and weights (7):** `OpenNMT/CTranslate2` **MIT** 4,764★ · `argosopentech/argos-translate`
**MIT** 6,691★ · `LibreTranslate/LibreTranslate` **AGPL-3.0** 17,840★ ·
`Helsinki-NLP/Opus-MT` **code MIT / models CC-BY-4.0** 880★ · `OpenNMT/OpenNMT-py` **MIT** 7,023★ ·
`marian-nmt/marian` **MIT in `LICENSE.md`** 1,475★ **stale since 2023-08-25** ·
`facebookresearch/stopes` **MIT** 315★.

**Evaluation (3):** `Unbabel/COMET` **Apache-2.0** 791★ · `mjpost/sacrebleu` **Apache-2.0** 1,266★ ·
`google-research/mt-metrics-eval` **Apache-2.0** 141★.

**Language identification (4) — and three of the four are dead:** `pemistahl/lingua-py`
**Apache-2.0** 1,822★ ✅ · `pemistahl/lingua` **Apache-2.0** 831★ ✅ ·
`facebookresearch/fastText` MIT **26,502★ ARCHIVED 2024-03-22** ❌ ·
`google/cld3` Apache-2.0 886★ **ARCHIVED 2023-05-24** ❌.

**Regional assets (3 + one measured gap):** `AI4Bharat/IndicTrans2` **MIT** 500★ — all **22
scheduled languages of India**, i.e. exactly the set DPDP §5(3) names (**APAC**) ·
`masakhane-io/masakhane-mt` **MIT** 334★ **stale since 2022-06-14** (**EMEA**) ·
`SakuraLLM/SakuraLLM` **GPL-3.0** 4,865★ (**APAC**, not recommended) ·
`facebookresearch/flores` 770★ **ARCHIVED 2023-11-20**. **LATAM: nothing found** — the region's
open-language repos already in this KB are corpus-cleaning tools, not translation tooling.

**Agent rows (3):** `lingodotdev/lingo.dev` **Apache-2.0** 5,397★ ·
`andrewyng/translation-agent` **MIT** 5,817★ **stale** · `SakuraLLM/SakuraLLM` (above).

### The headline, and it is a licence inside a directory

**`tolgee/tolgee-platform` is not Apache-2.0.** Its root `LICENSE` is a *multi-licence declaration*:
everything under **`ee/`** and **`/webapp/src/ee`** falls under **"Tolgee EE License version 1"** —
*"non-commercial purposes only"*, plus *"you may not provide the software to third parties as a
hosted or managed service"* and *"you may not … circumvent the license key functionality"*. Only
the content **outside** those directories defaults to Apache-2.0. **The onyx pattern of the seventh
pass, second occurrence** — and the method consequence is sharp: byte-reading the first 400 bytes of
`LICENSE` returns the string `Apache License` and is **wrong**. When a root licence names a
*directory*, the probe is not finished until that directory's licence is read too.

### Four more traps from this pass

- **Weblate is GPL-3.0.** Two aggregators returned **MIT** this pass. Byte-read says
  `GNU GENERAL PUBLIC LICENSE Version 3`. Fine as a hosted internal TMS, **not** a component to
  link into a client product.
- **In two of six layers the most-starred option is the copyleft one.** LibreTranslate (17,840★,
  AGPL-3.0) and Weblate (6,180★, GPL-3.0) top their categories; the permissive answers are quieter —
  `argos-translate` (MIT, 6,691★) **is** LibreTranslate's engine without the AGPL wrapper, and
  **Pontoon** (BSD-3-Clause, 1,679★) is the TMS. **Sorting by stars sorts away from what Globant can
  ship.**
- **`traduora/traduora` does not exist** — the aggregator path **422s**. Real owner:
  **`ever-co/ever-traduora`**. Eighth rename-ledger entry.
- **`NOASSERTION`/`null` resolved four different ways in one pass:** `marian` → MIT in
  **`LICENSE.md`** (wrong filename) · `icu`/`cldr`/`message-format-wg` → **Unicode-3.0** (real,
  permissive, simply unbadged) · `python-fluent` → Apache-2.0 · `formatjs` → **no root licence file
  at all**, MIT declared per package, which is why its badge is `null` rather than `NOASSERTION`.

### Primary source of the pass — read from the spec repo because `unicode.org` is unreachable

`unicode-org/message-format-wg`'s own README: the **Unicode MessageFormat Standard is a stable part
of CLDR**, **approved by the CLDR Technical Committee** and **recommended for implementation**,
and it **replaces earlier message formatting built into ICU** — while *"some default functions and
items in the `u:` namespace are **still in Draft status**."* All three are true at once: MF2 is no
longer a preview to wait out, every existing ICU-syntax estate has a migration ahead of it, and the
surface is **not** fully frozen. Quoting only the first sentence is how a 2028 rewrite gets sold.


## 2026-11-24 — fifteenth pass — el límite del consumo, y una licencia que recae sobre datos

> Tema: **lo que el agente gasta y lo que hay que declarar sobre ese gasto.** **33 direcciones
> nuevas** este pase. Toda licencia con `NOASSERTION` fue resuelta por **lectura byte a byte** del
> archivo de licencia (GET con rango; `HEAD` está bloqueado por el proxy de esta sesión), y
> licencia, estrellas, último push, estado de archivado y `default_branch` salen de
> `gh api search/repositories` del **2026-11-24**. Los hechos de **código y licencia de este pase
> son más fuertes que sus hechos regulatorios**: `arxiv.org` y los *hosts* legales no resuelven
> desde esta sesión, así que toda cifra de energía y toda fecha normativa queda **a nivel de
> snippet**, nunca como bibliografía.

**Motores de medición (permisivos, los proponibles):** `hubblo-org/scaphandre` (Apache-2.0, 2018★,
2026-07-19, RAPL por proceso) · `sustainable-computing-io/kepler` (Apache-2.0, **1606★**,
2026-11-24, eBPF+RAPL **por pod** de Kubernetes → Prometheus) · `…/kepler-operator` (Apache-2.0,
40★) · `mlco2/codecarbon` (MIT, **1951★**, 2026-11-22, `default_branch=master`) ·
`ml-energy/zeus` (Apache-2.0, 390★, GPU, mide **y optimiza**) · `saintslab/carbontracker` (MIT,
489★) · `powerapi-ng/powerapi` (**BSD-3-Clause**, 255★) ·
`cloud-carbon-footprint/cloud-carbon-footprint` (Apache-2.0, 1054★, **push 2026-04-23** —el más
antiguo de la tabla, verificar actividad—, `default_branch=trunk`).

**Decisión y planificación:** `Green-Software-Foundation/carbon-aware-sdk` (MIT, 600★,
`default_branch=**dev**`) · `Green-Software-Foundation/if` (MIT, 184★ — declara el cálculo como
manifiesto YAML, que es lo que lo hace auditable) · `thegreenwebfoundation/grid-intensity-go`
(Apache-2.0, 84★) · `kube-green/kube-green` (MIT, 1390★ — apaga lo no productivo por horario: el
ahorro más barato y el menos citado).

**Declaración legible por máquina — el patrón de OSCAL otra vez:** `Arelle/Arelle` —
**Apache-2.0 por byte-read** (la API dice `NOASSERTION`; el preámbulo *"# License / Copyright ©
2011-present Workiva, Inc."* desactiva al clasificador), **261★**, push **2026-11-24**. Procesador
XBRL open source: cuando la obligación pasa de *"publique un informe"* a *"publique estos campos"*,
**la herramienta que importa es un procesador de esquema de hace una década, no un modelo**. Arelle
es a ESRS/XBRL lo que `oscal-cli` es a FedRAMP. Más `os-climate/physrisk` (Apache-2.0, 72★) y
`os-climate/osc-transformer-presteps` (Apache-2.0, **1★** — infraestructura de consorcio, no
producto).

### *** EL HALLAZGO DEL PASE: UNA LIBRERÍA PERMISIVA PUEDE ENTREGARTE UNA BASE DE DATOS CON COPYLEFT ***

`thegreenwebfoundation/co2.js` (499★, push 2026-11-17) figura como `NOASSERTION`. Su `LICENSE`
—12 678 bytes— contiene **dos licencias para dos activos distintos**: el **código** es
**Apache-2.0**, y los **datos de intensidad de red** empaquetados se republican de **Electricity
Maps bajo la Open Database License (ODbL)**, con las obligaciones enumeradas en el propio archivo:
*"Attribute: Credit Electricity Maps as the source"*, *"Share-Alike: Keep derivative works under
the same license"*, *"Keep open: Provide unrestricted versions if using DRM"*.

**Clase de licencia nº 13 de esta KB: ODbL — la primera que no recae sobre código.** Y muerde donde
duele: el factor de intensidad de red es **justamente** lo que convierte kWh en gCO₂e, o sea el dato
sin el cual toda la capa de medición no produce la cifra que el informe exige. Quien lo toma por esta
vía hereda **share-alike sobre la base de datos derivada**, y eso **sobrevive a una librería
Apache-2.0**. El SPDX del repo describe el código; **no dice nada de los datos que el repo
empaqueta**.

**Prueba de vendorización, por la errata.** El mismo texto, **con su errata incluida**
(`"Licening for the CO2.js library"`), reaparece dentro del `LICENSE` de
`green-coding-solutions/green-metrics-tool` (260★, push 2026-11-24, 35 429 bytes). Ese archivo es
**tres licencias en uno y su encabezado contradice su propio cuerpo**: en la línea 7 el título dice
*"Apache License"* y lo que sigue (líneas 10–652) es la **AGPL-3.0**; en la línea 673 llega la
sección **ODbL** de los datos. Veredicto real: **AGPL-3.0 (código) + ODbL (datos)**.

**Los tres grandes de la capa son AGPL**, y conviene saberlo antes de prometer: `green-metrics-tool`
(AGPL-3.0), `Boavizta/boaviztapi` (AGPL-3.0, 102★), `Boavizta/cloud-scanner` (AGPL-3.0, 43★), más la
fuente original `electricitymaps/electricitymaps-contrib` (AGPL-3.0, **4057★**) con la misma forma:
**código AGPL, datos ODbL**. Y una **MPL-2.0** que no es permisiva aunque se parezca:
`mlco2/ecologits` (364★), la vía para medir GenAI **por API** cuando no hay acceso al host.

### La única prueba de código del pase: `jobrunr/jobrunr`

3112★, push 2026-11-24, `NOASSERTION`. Resuelto con **dos oráculos no equivalentes**: su archivo de
licencia **no se llama `LICENSE`** (404 en `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `COPYING`) sino
**`License.md`**, que declara el software **`multi-licensed`** —**LGPL-3.0-or-later** *o* comercial
por suscripción, a elección del receptor—; y el POM de Maven Central
(`org/jobrunr/jobrunr/8.0.0`) declara **solo** *"GNU Lesser General Public License v3.0 or later"*,
apuntando a `License.md#lgpl-v3-license`, **un ancla**, porque el archivo tiene varias secciones.
→ **Un manifiesto puede estar correcto y ser incompleto**: en una oferta multi-licencia nombra *una*
de las opciones.

**¿Y el *scheduling* carbon-aware está en el núcleo abierto o en la edición de pago?** Contestado
leyendo el código: `gh api search/code` sobre `repo:jobrunr/jobrunr carbonaware` da **91
coincidencias**, en **`core/src/main/java/org/jobrunr/scheduling/carbonaware/`** y
`…/server/carbonaware/` — **módulo `core`, fuente `main`, no un módulo Pro**. Es **usable bajo
LGPL-3.0-or-later**, y es el único planificador de esta KB que desplaza trabajo diferible a ventanas
de red limpia. El agente enterprise está lleno de trabajo diferible: reindexado, *batch* de
*embeddings*, evaluaciones nocturnas, reentrenos.

**La dependencia que hay que declararle al cliente**, leída de
`CarbonAwareJobProcessingConfiguration.java`: por defecto llama a **`https://api.jobrunr.io`** cada
**5 minutos**, con *timeouts* de **3 s** y **3 reintentos**. `carbonIntensityApiUrl`, `areaCode` y
`dataProvider` **son configurables**, así que la mitigación es una línea. Misma forma que la SOM-1.0
del pase trece —*la cláusula que decide está fuera de la licencia*— un nivel más abajo: aquí lo que
está fuera es una **salida de red a un tercero, activada por defecto**, en una librería de licencia
impecable.

### Trampa de nombre, y falsable en 30 segundos de README

`crbnos/carbon` — 2860★, push 2026-11-24, primero en cualquier búsqueda de `carbon` + ERP. **No mide
carbono:** es un **ERP/MES/QMS de manufactura** (MRP, inventario, planta, trazabilidad por
lote/serie sobre Postgres, con API REST y servidor MCP). Su `LICENSE` dice **AGPL-3.0-*only*** para
todo **salvo** los *Enterprise files*, bajo **Carbon Commercial License**. Dos formas de equivocarse
en un repo. Como *vertical agentizable* de manufactura sí es candidato; como capa ambiental, no.

### Suites: cuatro ramas por defecto y ninguna es `main`

`odoo/odoo` **LGPL-3.0 por byte-read** (la API dice `NOASSERTION`; el preámbulo *"For copyright
information, please see the COPYRIGHT file"* la oculta), 56 065★, `default_branch=**20.0**` ·
`frappe/erpnext` GPL-3.0, 41 597★, `develop` · `cortezaproject/corteza` **Apache-2.0**, 2192★,
`2026.9.x` · `apache/ofbiz-framework` **Apache-2.0**, 1151★, `trunk`. **Ninguna module ESG nativo**
— ver `verticals/solutions.md`. Confirma T86 fuera de su industria: iterar `main`/`master` a ciegas
falla en las cuatro, y la rama viene en la **misma** llamada que la licencia.

### LATAM, medido y con un hallazgo real

Sonda en **español y portugués** sobre nombre, descripción y README (`huella de carbono`,
`emisiones gases efecto invernadero`, `pegada de carbono`, `inventario de emisiones`): los primeros
resultados por estrellas son **listas *awesome*, catálogos de datos y proyectos de curso** — ningún
motor de contabilidad de carbono LATAM mantenido y con licencia permisiva. **Cero medido, no
silencioso.** Pero la sonda devolvió una pieza que sí sirve:
**`EquipoAnaliticaXM/API_XM`** — **MIT, 75★, push 2026-11-10, `default_branch=master`** — librería
Python de **SIMEM.co** y **SINERGOX/XM**, los sistemas de información del operador del sistema
eléctrico **colombiano**. No es contabilidad de carbono: es **dato de red nacional con licencia
permisiva**, que es exactamente lo que falta para calcular un factor de intensidad local **sin
heredar ODbL**.

### Direcciones verificadas en este pase — 33, con licencia, estrellas y último push medidos el 2026-11-24

| Repo | Licencia | ★ | Último push | Nota |
|---|---|---|---|---|
| [sustainable-computing-io/kepler](https://github.com/sustainable-computing-io/kepler) | Apache-2.0 | 1606 | 2026-11-24 | eBPF+RAPL por pod |
| [sustainable-computing-io/kepler-operator](https://github.com/sustainable-computing-io/kepler-operator) | Apache-2.0 | 40 | 2026-11-23 | operador K8s/OpenShift |
| [hubblo-org/scaphandre](https://github.com/hubblo-org/scaphandre) | Apache-2.0 | 2018 | 2026-07-19 | potencia por proceso |
| [mlco2/codecarbon](https://github.com/mlco2/codecarbon) | MIT | 1951 | 2026-11-22 | `default_branch=master` |
| [mlco2/agentic-footprint](https://github.com/mlco2/agentic-footprint) | MIT | 8 | 2026-11-23 | Rust, específico de agentes |
| [mlco2/ecologits](https://github.com/mlco2/ecologits) | **MPL-2.0** | 364 | 2026-11-23 | GenAI por API; no permisiva |
| [ml-energy/zeus](https://github.com/ml-energy/zeus) | Apache-2.0 | 390 | 2026-11-17 | GPU, mide y optimiza |
| [ml-energy/leaderboard](https://github.com/ml-energy/leaderboard) | **NONE** | 14 | 2026-09-23 | sin archivo de licencia |
| [saintslab/carbontracker](https://github.com/saintslab/carbontracker) | MIT | 489 | 2026-11-05 | la ruta `lfwa/…` no existe |
| [powerapi-ng/powerapi](https://github.com/powerapi-ng/powerapi) | BSD-3-Clause | 255 | 2026-11-24 | única BSD-3 de la capa |
| [cloud-carbon-footprint/cloud-carbon-footprint](https://github.com/cloud-carbon-footprint/cloud-carbon-footprint) | Apache-2.0 | 1054 | 2026-04-23 | `default_branch=trunk`; push más antiguo |
| [thegreenwebfoundation/co2.js](https://github.com/thegreenwebfoundation/co2.js) | **Apache-2.0 + ODbL (datos)** | 499 | 2026-11-17 | byte-read; API dice NOASSERTION |
| [thegreenwebfoundation/grid-intensity-go](https://github.com/thegreenwebfoundation/grid-intensity-go) | Apache-2.0 | 84 | 2026-05-11 | cliente Go |
| [Green-Software-Foundation/if](https://github.com/Green-Software-Foundation/if) | MIT | 184 | 2026-10-24 | cálculo como manifiesto YAML |
| [Green-Software-Foundation/carbon-aware-sdk](https://github.com/Green-Software-Foundation/carbon-aware-sdk) | MIT | 600 | 2026-11-04 | `default_branch=dev` |
| [kube-green/kube-green](https://github.com/kube-green/kube-green) | MIT | 1390 | 2026-09-02 | apaga lo no productivo |
| [jobrunr/jobrunr](https://github.com/jobrunr/jobrunr) | **LGPL-3.0-or-later O comercial** | 3112 | 2026-11-24 | `License.md`; carbon-aware en `core` |
| [Arelle/Arelle](https://github.com/Arelle/Arelle) | **Apache-2.0** | 261 | 2026-11-24 | byte-read; procesador XBRL; © Workiva |
| [os-climate/physrisk](https://github.com/os-climate/physrisk) | Apache-2.0 | 72 | 2026-11-23 | riesgo físico climático |
| [os-climate/osc-transformer-presteps](https://github.com/os-climate/osc-transformer-presteps) | Apache-2.0 | 1 | 2026-11-23 | infraestructura de consorcio |
| [Boavizta/boaviztapi](https://github.com/Boavizta/boaviztapi) | **AGPL-3.0** | 102 | 2026-11-24 | trampa de licencia |
| [Boavizta/cloud-scanner](https://github.com/Boavizta/cloud-scanner) | **AGPL-3.0** | 43 | 2026-06-04 | trampa de licencia |
| [green-coding-solutions/green-metrics-tool](https://github.com/green-coding-solutions/green-metrics-tool) | **AGPL-3.0 + ODbL (datos)** | 260 | 2026-11-24 | byte-read; encabezado contradice cuerpo |
| [electricitymaps/electricitymaps-contrib](https://github.com/electricitymaps/electricitymaps-contrib) | **AGPL-3.0** | 4057 | 2026-11-24 | fuente original; datos ODbL |
| [Breakend/experiment-impact-tracker](https://github.com/Breakend/experiment-impact-tracker) | MIT | 293 | 2024-01-30 | **`archived=true`** — caso nº 11 |
| [VeiledTee/agent-energy-profiler](https://github.com/VeiledTee/agent-energy-profiler) | MIT | 0 | 2026-10-24 | separa medido de estimado |
| [geoz-lab/swe_token_energy](https://github.com/geoz-lab/swe_token_energy) | MIT | 0 | 2026-11-02 | artefacto de investigación |
| [Enterprise-DNA-OS/carbon-accounting-for-claude-code](https://github.com/Enterprise-DNA-OS/carbon-accounting-for-claude-code) | MIT | 0 | 2026-10-18 | sesiones de agente sobre Postgres |
| [lxzxl/carbonink](https://github.com/lxzxl/carbonink) | MIT | 4 | 2026-10-09 | GHG local-first, ISO 14064-1, MCP |
| [crbnos/carbon](https://github.com/crbnos/carbon) | **AGPL-3.0-only + comercial** | 2860 | 2026-11-24 | **trampa de nombre: es un ERP** |
| [cortezaproject/corteza](https://github.com/cortezaproject/corteza) | Apache-2.0 | 2192 | 2026-11-19 | `default_branch=2026.9.x` |
| [apache/ofbiz-framework](https://github.com/apache/ofbiz-framework) | Apache-2.0 | 1151 | 2026-11-24 | `default_branch=trunk` |
| [EquipoAnaliticaXM/API_XM](https://github.com/EquipoAnaliticaXM/API_XM) | MIT | 75 | 2026-11-10 | **LATAM**: SIMEM/XM Colombia, `master` |

**Ya estaban en la KB y se reconfirman con licencia leída:**
[odoo/odoo](https://github.com/odoo/odoo) **LGPL-3.0** (byte-read; API dice NOASSERTION), 56 065★,
`default_branch=20.0` · [frappe/erpnext](https://github.com/frappe/erpnext) GPL-3.0, 41 597★,
`develop` · [opencost/opencost](https://github.com/opencost/opencost) Apache-2.0, 6831★, `develop`.

**Ruta medida como inexistente:** `lfwa/carbontracker` y `carbon-aware-computing/CarbonAwareComputing`
— ambas **descartadas en silencio** por la llamada por lotes, que es la señal de que no existen.

## 2026-11-24 — fourteenth pass — the accessibility boundary

> Theme: **whether the agent's interface can be used by the people the client must serve.**
> 15 new repository addresses this pass. Every licence is a **byte-read** of the repository's own
> `LICENSE` file, every dependency a byte-read of its `package.json`, every star count a WebFetch
> of github.com HTML, every version and publish date from `registry.npmjs.org` — because
> `api.github.com`, `img.shields.io` and `repos.ecosyste.ms` are all **403** for this session.

**Engines (2).** `dequelabs/axe-core` **MPL-2.0**, 7.9k★, npm 4.14.1 published 2026-11-16 —
the engine the whole layer runs on. `IBMa/equal-access` **Apache-2.0**, 788★, default branch
`main-4.x`, **zero axe dependencies** — the only fully permissive engine in the layer.

**Tools (4).** `microsoft/accessibility-insights-web` MIT 966★ (pins `axe-core` 4.11.3, dated
2026-04-13 — seven months behind); `microsoft/accessibility-insights-service` MIT 79★ (needs Azure
resources); `GoogleChrome/lighthouse` Apache-2.0 31.2k★ (pins `axe-core` 4.14.1);
`pa11y/pa11y` **LGPL-3.0-only** 4.6k★ (Pa11y 10 current, **Pa11y 9 support ended 2026-02-27**).

**Screen-reader automation (3) — the category this KB had never held.**
`guidepup/guidepup` MIT 604★, npm 0.40.0 (2026-11-01), **drives real VoiceOver and NVDA** from
Playwright/Jest. `guidepup/virtual-screen-reader` MIT 158★, npm 0.33.0 (2026-09-20), simulates a
screen reader over a DOM in unit tests with **no real screen reader**. `nvaccess/nvda`
**GPL-2.0-or-later with two exceptions** — the AT itself; driven, never linked.

**MCP servers (3).** See `agents/trending.md` for the full reading. Short version:
`JustasMonkev/mcp-accessibility-scanner` MIT 59★ npm 2026-11-16 (**use**);
`priyankark/a11y-mcp` MPL-2.0 53★ (npm **provenance**, Dependabot);
`ronantakizawa/a11ymcp` MIT 97★ npm last published 2026-03-01 pinning `puppeteer` **13.5.0 of
2022-03-07** (**avoid**).

**Not software, despite being on GitHub (3).** `w3c/wcag` — W3C **Document** Licence.
`act-rules/act-rules.github.io` — W3C **Community Contributor License Agreement**.
`ryersondmp/sa11y` — **GPL-2.0**, and its own `LICENSE.md` records that **versions ≤ 2.0 were
MIT**: a licence tightening documented inside the repository.

**Three measurements worth carrying forward.**
1. **The permissive badge is the wrapper's.** 5 of 6 tools tested bundle MPL-2.0 `axe-core`,
   including Microsoft's MIT one and Google's Apache-2.0 one.
2. **Star rank inverted maintenance rank perfectly** across the three MCP servers (97★ stalest,
   59★ freshest, 53★ most hygienic).
3. **Zero non-US origin** in the whole layer — measured with the Spanish and Portuguese short
   instruments as well as English.

## 2026-11-24 — thirteenth pass — the erasure boundary

> Theme: **where a delete actually has to land**. 24 new repository addresses, every licence, star
> count, push date, archival state and default branch measured in this pass. The twelfth pass could
> not measure stars at all; the instrument note at the bottom is why this one could.

### The archived and the renamed — read this part first

| Repo | Licence | Stars | Last push | State |
|---|---|---|---|---|
| [ethyca/fides](https://github.com/ethyca/fides) | Apache-2.0 | 483 | 2026-08-06 | **ARCHIVED** — the open-source DSAR engine every roundup still recommends |
| [ethyca/fidesops](https://github.com/ethyca/fidesops) | Apache-2.0 | 49 | 2022-11-30 | **ARCHIVED** |
| [amundsen-io/amundsen](https://github.com/amundsen-io/amundsen) | Apache-2.0 | 4,780 | 2026-09-10 | **ARCHIVED** — still listed in catalog comparisons |
| [ethyca/janus-sdk-android](https://github.com/ethyca/janus-sdk-android) | **NOASSERTION** | 0 | 2026-11-20 | live — the vendor's active line, **no licence declared** |
| [ethyca/fides-helm](https://github.com/ethyca/fides-helm) | Apache-2.0 | 4 | 2026-10-02 | live — **the chart outlived the product** |

### New permissive rows — the cascade substrate

| Repo | Licence | Stars | Push | The erasure property |
|---|---|---|---|---|
| [trinodb/trino](https://github.com/trinodb/trino) | Apache-2.0 | 13,542 | 2026-11-24 | Will happily read a snapshot you thought you deleted |
| [delta-io/delta](https://github.com/delta-io/delta) | Apache-2.0 | 9,085 | 2026-11-24 | `DELETE` then `VACUUM` — **the retention window is the erasure SLA** |
| [apache/hudi](https://github.com/apache/hudi) | Apache-2.0 | 6,395 | 2026-11-24 | First-class **record-level deletes**; lead with it when erasure is the driver |
| [chroma-core/chroma](https://github.com/chroma-core/chroma) | Apache-2.0 | 29,739 | 2026-11-20 | The one major permissive vector store this KB lacked |
| [MarquezProject/marquez](https://github.com/MarquezProject/marquez) | Apache-2.0 | 2,311 | 2026-11-23 | OpenLineage reference server — **lineage is the prerequisite for erasure** |
| [apache/atlas](https://github.com/apache/atlas) | Apache-2.0 | 2,163 | 2026-11-20 | Classification propagation: the tag follows the data |
| [apache/polaris](https://github.com/apache/polaris) | Apache-2.0 | 2,124 | 2026-11-24 | Iceberg catalog — central place for table retention policy |
| [OpenMined/PySyft](https://github.com/OpenMined/PySyft) | Apache-2.0 | 10,064 | 2026-11-24 | Data that was never copied needs no cascade |
| [google/differential-privacy](https://github.com/google/differential-privacy) | Apache-2.0 | 3,380 | 2026-11-20 | DP primitives to cite in a DPIA |
| [opendp/opendp](https://github.com/opendp/opendp) | **MIT** | 450 | 2026-11-24 | Permissive privacy accountant that can ship in a deliverable |
| [orestbida/cookieconsent](https://github.com/orestbida/cookieconsent) | **MIT** | 5,782 | 2026-11-22 | Dependency-free consent UI |
| [EdyVision/pii-codex](https://github.com/EdyVision/pii-codex) | BSD-3-Clause | 102 | 2026-02-15 | Risk-scores detected PII |
| [danyuchn/pii-guard](https://github.com/danyuchn/pii-guard) | **MIT** | 257 | 2026-11-15 | Reversible zh-TW de-identification — **first non-English row in this layer** |
| [SuiteCRM/SuiteCRM](https://github.com/SuiteCRM/SuiteCRM) | AGPL-3.0 | 5,877 | 2026-11-04 | Default branch **`hotfix`**; `mark_deleted()` is an `UPDATE` |
| [axelor/axelor-open-suite](https://github.com/axelor/axelor-open-suite) | **AGPL-3.0** (byte-read) | 989 | 2026-11-24 | The one suite shipping a GDPR module with a processing register |

### Licences resolved from bytes — one badge, three classes, one pass

| Repo | Badge | Bytes say |
|---|---|---|
| [kiprotect/klaro](https://github.com/kiprotect/klaro) | `NOASSERTION` | **BSD-3-Clause** (permissive) |
| [axelor/axelor-open-suite](https://github.com/axelor/axelor-open-suite) | `NOASSERTION` | **AGPL-3.0** (copyleft) |
| [pgvector/pgvector](https://github.com/pgvector/pgvector) | `NOASSERTION` | **PostgreSQL License** (permissive) |
| [vec2text/vec2text](https://github.com/vec2text/vec2text) | `NOASSERTION` | **SOM-1.0** — publishes your model weights |
| [weaviate/weaviate](https://github.com/weaviate/weaviate) | `NOASSERTION` | *"variously licensed under BSD-3-Clause, or the Weaviate License"* — **split inside one repo** |

### Unlearning, measured

[`OPTML-Group/Unlearn-Sparse`](https://github.com/OPTML-Group/Unlearn-Sparse) MIT **90★**;
[`locuslab/tofu`](https://github.com/locuslab/tofu) MIT **30★**, **idle since 2025-02-25**. There is
no production unlearning tooling. The architecture must therefore keep personal data **out of the
weights** — which is a design rule with a legal basis, not a preference.

### Instrument — stars are measurable again

`api.github.com/repos/{o}/{r}` is **403** out of scope, but
`gh api -X GET search/repositories -f q='repo:a/b repo:c/d …'` **ORs** multiple `repo:` qualifiers
and returns `license.spdx_id`, `stargazers_count`, `pushed_at`, `archived` **and `default_branch`**
in one request. **How it lies:** an invalid `repo:` is **silently dropped** when valid ones remain
(ask 8, get 6, no error), but if *all* are invalid the query returns **422** — which is positive
evidence a path is gone, and how both the Presidio and Casbin moves were detected. Default branches
met this pass: `master`, **`hotfix`**, `develop`, `20.0`, `main`.

## 2026-11-24 — twelfth pass — the weights boundary

> Theme: pass 7 asked what the agent may **read**, pass 8 what it may **change**, pass 9 whether its
> components **are what they claim to be**, pass 10 what it may **reach**, pass 11 **where this KB had
> looked**. This pass asks the question none of them did: **under what licence does the model itself
> arrive?** Fifteen repositories, every licence byte-verified from `raw.githubusercontent.com` on
> 2026-11-24. Full tables in `repos/foundations.md`, analysis in `intel/trends.md` (trends 27–28).

> **No star counts in this section.** `api.github.com` answered **403 for every repository outside
> this session's scope**, so stars and push dates **could not be measured**. Each row carries the
> licence and the byte-verified evidence instead. An omitted number is a refused measurement, not a
> small project.

### New to this KB — the licence instruments

| Repo | Licence | Byte-verified evidence | Note |
|---|---|---|---|
| [OpenMDW/OpenMDW](https://github.com/OpenMDW/OpenMDW) | OpenMDW-1.1 text; docs CC-BY-4.0 | `1.1/LICENSE.OpenMDW-1.1` **2,619 B**; `FAQ.md` a **171-byte stub** | **Eleventh licence class in this KB, first one written for weights.** Model + data + docs + code in one grant; **database and trade-secret** rights named; **outputs unrestricted**; **not OSI-approved, no SPDX ID** |
| [meta-llama/llama-models](https://github.com/meta-llama/llama-models) | Per-model Llama Community Licenses | Root `LICENSE` **78 B — a bare URL**; `models/llama4/LICENSE` **7,603 B**; `models/llama4/USE_POLICY.md` **5,824 B** | The licence source of truth for the family most enterprise agents run on. **The EU carve-out is in the AUP at line 71, not in any `LICENSE`** |
| [spdx/spdx-3-model](https://github.com/spdx/spdx-3-model) | Community-Spec-1.0 | `model/AI/Classes/AIPackage.md` **1,687 B** | The SPDX 3.0 **AI profile** — and it is **not** in `spdx/spdx-spec`. Every property is `minCount: 0`, so a conformant AI SBOM may be silent about training data |
| [CycloneDX/specification](https://github.com/CycloneDX/specification) | Apache-2.0 | `LICENSE` **11,341 B**; `schema/bom-1.6.schema.json` **262,666 B** with `machine-learning-model`, `modelCard`, `modelParameters` | **ML-BOM confirmed in the published schema by byte-read.** The AI-BOM most client toolchains can already emit |

### New to this KB — model sources, licence verified from a reachable primary

| Repo | Weights licence | Byte-verified evidence | Note |
|---|---|---|---|
| [langtech-bsc/salamandra](https://github.com/langtech-bsc/salamandra) | **Apache-2.0** | `LICENSE` **11,357 B** | EMEA sovereign (Barcelona Supercomputing Center). No AUP, no gate, no inheritance. **The clean European option** |
| [allenai/OLMo](https://github.com/allenai/OLMo) · [allenai/OLMo-core](https://github.com/allenai/OLMo-core) | **Apache-2.0** | `LICENSE` **11,359 B** both | The only family probed where code and weights agree **and** both are permissive |
| [QwenLM/Qwen3](https://github.com/QwenLM/Qwen3) | **Apache-2.0** | **No `LICENSE` (404 at `main` and `master`)**; `README.md:397` states it | APAC, frontier-class, permissive — and a **false negative** for every scanner |
| [aisingapore/sealion](https://github.com/aisingapore/sealion) | **Varies by base model** | `README.md:88` | APAC regional model. README contradicts its own arXiv paper's "fully open MIT" claim |
| [NVIDIA/Cosmos](https://github.com/NVIDIA/Cosmos) | **OpenMDW-1.1** | `LICENSE` **2,619 B**, byte-identical to canonical | First major adoption, confirmed from the vendor's repo |
| [NVIDIA-NeMo/Nemotron](https://github.com/NVIDIA-NeMo/Nemotron) | Repo is **Apache-2.0** (code) | `LICENSE` **11,358 B** | Held beside Cosmos as the **two-document rule inside one vendor** |
| [google-deepmind/gemma](https://github.com/google-deepmind/gemma) | Code Apache-2.0; **weights UNRESOLVED** | `LICENSE` **11,358 B**; `README.md` has **zero** licence statements | The canonical false positive. `ai.google.dev` does not resolve from this session, so the weights question stays open |

### New to this KB — weights inspection tooling

| Repo | Licence | Byte-verified evidence | Note |
|---|---|---|---|
| [mmaitre314/picklescan](https://github.com/mmaitre314/picklescan) | **MIT** | `LICENSE` **1,072 B** | The permissive pickle scanner — ship this one |
| [trailofbits/fickling](https://github.com/trailofbits/fickling) | **LGPL** | `master/LICENSE` **7,652 B** | The better-known one, and **copyleft**. Standalone CI binary only |
| [protectai/modelscan](https://github.com/protectai/modelscan) | **Apache-2.0** | `LICENSE` **10,754 B** | Admission scanning for third-party weights across formats |
| [huggingface/safetensors](https://github.com/huggingface/safetensors) | **Apache-2.0** | `LICENSE` **11,357 B** | Removes the code-execution problem rather than scanning for it. **Require the format, keep the scanner** |
| [ossf/ai-ml-security](https://github.com/ossf/ai-ml-security) | **Apache-2.0** | `LICENSE` **11,356 B** | OpenSSF AI/ML security WG — whose guidance the gate implements |

### Paths probed and not found — recorded so absence is not read as non-existence

`swiss-ai/apertus`, `utter-project/EuroLLM`, `OpenGPT-X/Teuken`, `sarvamai/sarvam-1`, `lfai/mof`, and
`aisingapore/sea-lion` (correct path: `aisingapore/sealion`). **Apertus, EuroLLM, Teuken and Sarvam
are real projects whose repository addresses this pass failed to locate** — an open inventory item
for pass 13, not a measured zero.

## 2026-11-24 — eleventh pass — the forge boundary

> Theme: pass 7 asked what the agent may **read**, pass 8 what it may **change**, pass 9 whether its
> components **are what they claim to be**, pass 10 what it may **reach**. This pass asks the
> question all four assume an answer to: **how does this KB know what exists?** The answer was one
> forge, and it had never been stated. Full tables in `repos/foundations.md`.

### The headline is a number about this KB, not about the industry

| Measurement, 2026-11-24 | Value |
|---|---|
| Distinct repository addresses in this KB | **314** |
| …on `github.com` | **314** |
| …on `gitlab.com`, `sourceforge.net`, `codeberg.org`, `bitbucket.org`, `git.sr.ht`, `gitee.com`, `huggingface.co` | **0** |

Not 314 of 320. **314 of 314.** Ten passes of research, eight thousand lines, one forge.

### The eight forges that refused, and why "unmeasured" is the only honest word

| Forge | Why it would have mattered | Probe result |
|---|---|---|
| `gitlab.com` | GitLab CE, Mayan EDMS, Flectra, GitLab's own AI work | **Reachable**, API `200` unauthenticated |
| `gitee.com` | the dominant **APAC** forge | `CONNECT tunnel failed, 403` |
| `atomgit.com` | OpenAtom-hosted Chinese projects | `CONNECT tunnel failed, 403` |
| `gitlab.opencode.de` | **openCoDE**, the German public-sector forge | `CONNECT tunnel failed, 403` |
| `foss.heptapod.net` | **Tryton**, a full ERP, canonical home | `CONNECT tunnel failed, 403` |
| `codeberg.org` | Forgejo and the Gitea-fork ecosystem | `CONNECT tunnel failed, 403` |
| `git.openldap.org` | OpenLDAP, the directory under the estate | `CONNECT tunnel failed, 403` |
| `pagure.io` | Fedora/RHEL-adjacent enterprise tooling | `CONNECT tunnel failed, 403` |
| `invent.kde.org`, `salsa.debian.org` | upstream packaging of estate components | `CONNECT tunnel failed, 403` |

**A `403 CONNECT` is the instrument failing, not the subject being empty.** The APAC consequence is
the sharpest: this KB cannot currently see the forge most Chinese enterprise projects publish on, so
every APAC inventory statement it makes carries that caveat whether or not it is written down. From
this pass on, it is written down.

### New repository rows — enterprise platforms

| Repo | Licence | Stars | Branch | Last activity | What it is |
|---|---|---|---|---|---|
| [mayan-edms/mayan-edms](https://gitlab.com/mayan-edms/mayan-edms) | **GPL-2.0-only** (byte-read; API said `other`) | **683** | `master` | **2026-11-24** | *"Advanced enterprise … DMS"* — most-starred enterprise platform found off GitHub, active the day it was found |
| [gitlab-org/gitlab](https://gitlab.com/gitlab-org/gitlab) | **MIT** | **6,209** | `master` | 2026-11-24 | GitLab CE — permissive, and already self-hosted at many clients |
| [flectra-hq/flectra](https://gitlab.com/flectra-hq/flectra) | GPL-3.0 | 252 | **`3.0`** | 2026-07-15 | Odoo-lineage ERP+CRM; ~4 months idle |
| [dokos/dokos](https://gitlab.com/dokos/dokos) | GPL-3.0-or-later | 39 | **`develop`** | 2026-11-24 | French ERPNext derivative on Dodock/Frappe |

### New repository rows — the workplace estate, which was missing on *both* forges

| Repo | Licence | Stars | Last push | What it is |
|---|---|---|---|---|
| [nextcloud/server](https://github.com/nextcloud/server) | **AGPL-3.0** | **37,621** | 2026-11-24 | The default self-hosted file/groupware platform in EMEA public sector |
| [opf/openproject](https://github.com/opf/openproject) | GPL-3.0 | **17,676** | 2026-11-24 | Project/portfolio management, German-origin, regulated estates |
| [xwiki/xwiki-platform](https://github.com/xwiki/xwiki-platform) | **LGPL-2.1** | 1,336 | 2026-11-24 | Enterprise wiki — **fewest stars, best licence** of the three |

This trio was absent for ten passes while 314 GitHub addresses accumulated, which shows the bias was
never *only* about forges: the KB had covered chat and document repositories and skipped the suite
in between. **A forge audit finds gaps a keyword audit does not, because a URL has no vocabulary.**

### The air-gap reference implementation — MIT IaC, proprietary payload

[gitlab-com/public-sector/offline-lab](https://gitlab.com/gitlab-com/public-sector/offline-lab) —
**MIT**, 4★, active **2026-11-24**, owned by GitLab's Public Sector group. Topology:
**GitLab → AI Gateway → LiteLLM → AWS Bedrock**, Alloy → Loki → Grafana.

Four facts from its runbook worth more than the repository:

1. It owns *"the canonical list of external dependencies you must mirror internally"* — the artefact an
   air-gapped engagement needs and almost nobody writes.
2. Images pinned by tag **and digest**, with the rule stated: *"an air-gapped mirror plus a moving tag
   cannot be reproduced."* The ninth pass's provenance boundary, reached from the deployment side.
3. The AI Gateway image *"includes the Duo Workflow service as a sub-process — mirroring this one image
   covers agentic flows; there is no separate workflow image."*
4. *"The default topology calls a hosted model provider"* — **the air gap is a separate track**. Third
   independent confirmation that "offline" always has an online bootstrap.

**And the split:** the IaC is MIT; the AI Gateway
([…/code-suggestions/ai-assist](https://gitlab.com/gitlab-org/modelops/applied-ml/code-suggestions/ai-assist),
64★, **GitLab EE licence** byte-read from `LICENSE`) and Orbit are not. Take the method, not the payload.

### Two migration remnants, and a rule about star-ranked forge listings

| Repo | Stars | Last activity | Its own description |
|---|---|---|---|
| [meltano/meltano](https://gitlab.com/meltano/meltano) (GitLab) | **554** | **2024-09-11** | *"[This project was migrated to GitHub]"* |
| [gitlab-org/duo-workflow/duo-workflow-service](https://gitlab.com/gitlab-org/duo-workflow/duo-workflow-service) | 10 | 2026-10-23 | *"This project is migrated to …/ai-assist"* |

Stars accumulate and never decay, so **a star-sorted forge listing surfaces dead mirrors near the
top.** Both of these announce their own death in the description field — the cheapest possible check,
and exactly the one a star-sorted list invites you to skip. Meltano is already in this KB at its live
GitHub address; ranking by stars would have added a duplicate pointing at a two-year-old corpse.

### A rename that moved the product and left the path alone

[gitlab-org/cluster-integration/gitlab-agent](https://gitlab.com/gitlab-org/cluster-integration/gitlab-agent)
— MIT, 113★, `master`, active 2026-11-24 — now describes itself as **"GitLab Relay — host for various
GitLab Features such as: Workflow Engine (AutoFlow / autocore), GitLab CD, Job Router and Runner
Controller."** The ninth pass built a detector for renames that move **owner and path**. This is the
variant that defeats it: **URL stable, licence stable, product replaced.** Diff the description against
your own one-line summary, not just the HTTP status.

### LATAM — a first, and a measured zero beside it

| Repo | Licence | Stars | Last activity | What it is |
|---|---|---|---|---|
| [dansanti/facturacion_electronica](https://gitlab.com/dansanti/facturacion_electronica) | **GPL-3.0** | 11 | 2026-10-31 | **Chilean** e-invoicing library — first LATAM-origin, licence-resolved, non-GitHub repo in this KB |
| [odoocoop/facturacion_electronica](https://gitlab.com/odoocoop/facturacion_electronica) | **unresolved — `429` twice** | 4 | 2026-11-01 | Odoo-cooperative LATAM localisation. **A rate limit is not a licence verdict** |
| [torresoftware/apidian2020](https://gitlab.com/torresoftware/apidian2020) | **NONE** | 11 | 2026-06-23 | **Colombian DIAN** e-invoicing API — no licence file, **not proposable** |

Spanish probes for `agente IA`, `empresa gestion` and `nomina` returned a **measured zero** (and
`nomina` collided with `nominatim` — the search is accent-insensitive). `facturacion` did not. The
zero was in the **technology** vocabulary; the content was in the **domain** vocabulary.

## 2026-11-24 — tenth pass — the containment boundary

> Theme: pass 7 asked what the agent may **read**, pass 8 what it may **change**, pass 9 whether its
> components **are what they claim to be**. This pass asks the question all three leave open —
> **what can the agent reach, and what physically stops it?** The layer scored a true zero:
> `cilium`, `istio`, `linkerd`, `kyverno`, `gatekeeper`, `falco`, `tetragon`, `gVisor`,
> `Firecracker`, `Kata`, `eBPF`, `mTLS`, `NetworkPolicy`, `service mesh`, `Agent Sandbox` and
> `Prempti` → **0 hits across all nine files**. `egress` → 8 hits, **all prose, none a tool**.
> Full tables in `repos/foundations.md`; the build is Receta 20.

### The headline is an asymmetry: the most complete architecture in this layer has 46 stars

| Repo | ★ | Controls implemented | Status |
|---|---|---|---|
| [Azure/kars](https://github.com/Azure/kars) (MIT) | **46** | **All four** — sandbox, governed egress, tool policy, hash-chained audit | `v1alpha1`, *"Not an officially supported Microsoft product"* |
| [cilium/cilium](https://github.com/cilium/cilium) | 25,896 | One (egress/network) | CNCF **Graduated** |
| [firecracker-microvm/firecracker](https://github.com/firecracker-microvm/firecracker) | 38,192 | One (kernel isolation) | Production, AWS-operated |
| [falcosecurity/prempti](https://github.com/falcosecurity/prempti) | 234 | One (request interception) | **Experimental Preview**, idle since 2026-09-21 |

This is **trend 11 running in reverse**. That trend said star count has decoupled from enterprise
suitability, and every prior instance was *popular but unsuitable*. `Azure/kars` is the first
instance of the opposite: **architecturally complete and commercially unusable as a dependency**.
The correct use of a 46-star reference implementation is to **read it and reproduce its shape** on
components that are graduated — which is exactly what Receta 20 does.

### Three independent sources say the same thing, and none of them is marketing

Each of these is a project or body explaining the limits of *its own* control:

- [falcosecurity/prempti](https://github.com/falcosecurity/prempti)'s README: it is *"not a sandbox,
  OS-level security, or a substitute for least-privilege environments"*, and it governs *"the
  commands the agent requests, not the side effects those commands produce at runtime."*
- Vercel's gVisor-vs-microVM comparison: neither *"automatically denies outbound network access or
  enforces business permissions."*
- Cloud Security Alliance, Oct 2026, reviewing a July 2026 incident: **no sandbox was technically
  broken** — an agent **wrote a file that a trusted, unsandboxed component later executed.**

**That third one is the write-then-execute confused deputy, and it is the same shape as pass 7's
permission-sync finding and pass 8's write-boundary finding.** Three passes, three layers, one
failure mode: the boundary held and the thing *across* the boundary did the work. State it to a
client that way, because it is the argument for buying the whole sequence rather than one control.

### New this pass — the standard arrived while nobody in this KB was looking

[kubernetes-sigs/agent-sandbox](https://github.com/kubernetes-sigs/agent-sandbox) (Apache-2.0,
4,703 ★, pushed 2026-11-23) is a **Kubernetes SIG Apps subproject** that is already **past 1.0** —
its README pins `v1.0.2` for production/GitOps. It is a *sandbox orchestrator*: it delegates
isolation to gVisor or Kata via `RuntimeClass` and adds `Sandbox`, `SandboxTemplate`,
`SandboxClaim` and `SandboxWarmPool` on `agents.x-k8s.io/v1beta1`. The warm-pool claim is the part
with commercial consequence — it is what makes per-task sandboxes affordable instead of theoretical.

**It is not a CNCF project yet.** Google's announcement says *"building Agent Sandbox as a CNCF
project"*, future tense. Do not write "CNCF" next to it in a deliverable.

### Trap — a 0-star personal fork that the search channel cannot warn you about

A web search for the project returned [grosser/agent-sandbox](https://github.com/grosser/agent-sandbox)
**in the same result list** as the real one. It is a fork: 0 stars, 0 forks, 0 watchers, an
Apache-2.0 badge, and a README whose **first line is byte-identical to upstream's**.

**Two things make this worse than the owner/owner collisions already recorded** (`complytime/complytime`
vs `complytime/complyctl`):

1. **README text cannot identify the canonical repo.** A fork inherits the description, the badge and
   the prose. The *only* reliable signal on the page is the **"forked from"** line.
2. **`gh api search/repositories` cannot see it at all** — forks are excluded from the search index,
   so the API channel this KB trusts most returns **nothing** for `repo:grosser/agent-sandbox` and
   therefore raises no flag. The channel that *surfaced* the risk (web search) is the channel that
   cannot verify, and the channel that verifies is blind to the risk.

**Method rule 14:** for any repo that arrived via web search, check the **"forked from"** line before
the licence. Existence, licence and even a plausible star count can all be inherited from a parent.

### Licence finding — a ninth class, and the first that is split by component

[cilium/cilium](https://github.com/cilium/cilium)'s badge says `Apache-2.0` and is **correct but
incomplete**. Its own `README.rst`, byte-read: *"The Cilium user space components are licensed under
the Apache License, Version 2.0. The BPF code templates are dual-licensed under the General Public
License, Version 2.0 (only) and the 2-Clause BSD License (you can use the terms of either license,
at your option)."* `bpf/COPYING` → 200; top-level `LICENSE.BSD-2-Clause` → 404.

**This one resolves in Globant's favour** — take the BSD-2-Clause option and no GPL enters the
deliverable — but the election must be **performed and recorded in the SBOM**, because the licence of
the artefact you ship is not the licence on the page describing the repository. Same shape in
`cilium/tetragon`.

### Correction resolved against a primary source — CNCF maturity

A 2026 comparison blog says Kyverno **graduated** in March 2026; another lists it **Incubating**.
[kyverno/kyverno](https://github.com/kyverno/kyverno)'s own README says *"CNCF Incubating project"*.
**The repository wins.** Falco and Cilium both carry *graduated* badges in their own READMEs, so the
difference is real self-description, not inconsistency. Quote maturity from the README — procurement
documents cite it.

### Verification channel for this pass — what worked and what is 403

| Channel | Result |
|---|---|
| `git ls-remote --symref` | **Works** — existence + real default branch |
| `raw.githubusercontent.com/<r>/<br>/LICENSE` | **Works** — the byte-read licence, and the only way the Cilium split was found |
| `gh api -X GET search/repositories -f q=repo:<o>/<n>` | **Works** — exact stars, SPDX, `archived`, last push. **Blind to forks.** Returned **HTTP 422** for `google/gvisor` specifically |
| `api.github.com/repos/<o>/<n>` | **403** for every repo not attached to this session, authenticated or not |
| `github.com` HTML via `curl` | **403**; the same URL via the fetch tool **works** |
| `kubernetes.io`, `agent-sandbox.sigs.k8s.io` | **Do not resolve** — outside this session's network policy. Cost one unverifiable finding, recorded as such |

---

## 2026-11-24 — ninth pass — the provenance boundary

> Theme: the seventh pass asked what the agent may **read**, the eighth what it may **change**
> and what **proves** it. This one asks the question both of those assume an answer to —
> **are the components what they claim to be, and who signs for them?** The layer was
> measurably empty: `sigstore`, `cosign`, `in-toto`, `SLSA`, `attestation`, `syft`, `grype`,
> `trivy`, `dependency-track`, `guac` and `model card` all scored **zero across all nine files**,
> while `SBOM` scored 24 hits purely as a compliance noun. Full tables and the method notes are
> in `repos/foundations.md`. Verified 2026-11-24: `git ls-remote --symref` for existence and
> **real default branch**, licence **byte-read** from each `LICENSE`, last-commit date from a
> shallow bare clone, and stars/`archived`/SPDX from `gh api search/repositories` — which works here
> even though `gh api repos/<owner>/<repo>` and `api.github.com` are both **403**.

### The headline is a die-off, and it inverts this KB's own detection rule

Both reference SLSA tools now say in their own READMEs, at line 11: *"This project is **no longer
actively maintained**."* Neither is archived; both carry recent release tags and look alive on their
repo pages.

| Repo | Measured state | Successor the README names |
|---|---|---|
| [slsa-framework/slsa-verifier](https://github.com/slsa-framework/slsa-verifier) | Apache-2.0, **352 ★**, `main` last commit **2026-08-06** — that commit being *"docs: Add maintenance status"*. Tags to `v2.7.1`. **`HEAD` resolves to `refs/heads/Hayden-IO-patch-1`**, a personal patch branch at a different sha from `main`. | `gh attestation verify` |
| [slsa-framework/slsa-github-generator](https://github.com/slsa-framework/slsa-github-generator) | Apache-2.0, **610 ★**, `main` last commit **2026-08-06**. README: last release **v2.1.0, Feb 2025**; existing provenance stays valid and workflows keep working, but will not be updated **"including for GitHub Actions runtime deprecations."** | GitHub artifact attestations |

**Five prior passes learned "trust the repo page over the docs" from seven archived-but-silent
projects. This is the exact inverse. Read both directions, every pass.** And the strategic point:
the CI-agnostic open-source provenance path has been retired in favour of **a single vendor's
platform feature**. A GitLab/Jenkins/self-hosted estate has no successor named by the project —
this pass searched and **found none** (recorded as an open gap).

### New rows — signing, and the one that signs a model

| Repo | Licence (byte-read) | ★ | Last commit | Why it is new here |
|---|---|---|---|---|
| [sigstore/cosign](https://github.com/sigstore/cosign) | Apache-2.0 | 6.5k | 2026-11-22 | Keyless container/blob signing — the substitute for the retired SLSA generator on non-GitHub CI. |
| [sigstore/model-transparency](https://github.com/sigstore/model-transparency) | Apache-2.0 | **250** | 2026-11-09 | **Signs model weights.** Sigstore bundle → DSSE → in-toto statement listing every file as `(path, digest)`; verify recomputes hashes. Keyless OIDC, keys, or **PKCS#11 hardware**. The only permissive model-signing tool located, and this KB had nothing in the slot. |
| [in-toto/witness](https://github.com/in-toto/witness) | Apache-2.0 | 622 | 2026-09-21 | Per-step attestations with keyless signing via **Sigstore *and SPIFFE/SPIRE*** and an **embedded OPA Rego** engine — two components this KB already holds, each gaining a second job. |
| [guacsec/guac](https://github.com/guacsec/guac) | Apache-2.0 | 1.6k | 2026-11-24 | SBOMs **and** attestations into one graph (CycloneDX, SPDX, in-toto ITE6, DSSE, SLSA, CSAF/OpenVEX). Its own page warns identifiers are often missing and linking is **heuristic**. |
| [DependencyTrack/dependency-track](https://github.com/DependencyTrack/dependency-track) | Apache-2.0 | 4.5k | 2026-11-23 | The consumption half the AI-BOM section lacked: continuous re-evaluation and drift alerting. |
| [CycloneDX/cdxgen](https://github.com/CycloneDX/cdxgen) | Apache-2.0 | 1.1k | 2026-11-24 | `aibom` command over **prompt files, AI services, MCP configs and model metadata**, Hugging Face purls and `.gguf`; submits straight to Dependency-Track. Gotcha: `--component-type` alone does not enable model discovery. |

### Measured, not cited: "offline verification" has an online bootstrap

```
$ gh attestation trusted-root
tuf refresh failed: Get "https://tuf-repo-cdn.sigstore.dev/14.root.json": Forbidden
exit=1, 0 bytes
```

`gh` 2.89.0 is present and the documented air-gap path is *fetch the root once, verify offline with
`--custom-trusted-root`*. In this session's restricted network the fetch **fails closed**. So the
trusted root can be **used** offline but not **obtained** offline: allowlist
`tuf-repo-cdn.sigstore.dev` from one permitted host, pin the root, ship it inward as a controlled
artefact, and give its refresh an owner — a forgotten refresh is an outage, because verification
correctly fails closed.

### Archived yesterday, recommended to this pass today

[NimbleBrainInc/mpak](https://github.com/NimbleBrainInc/mpak) (Apache-2.0, 14 ★) — MCP package
registry with bundle signing, GitHub-OIDC provenance and an **L1–L4 trust ladder** topping out at
"Attested" — was **archived by its owner 2026-11-23**, one day before this pass, `registry.mpak.dev`
to be shut down. A search engine returned it as a live finding. **Eighth archived-but-recommended
project in nine passes.** 163 commits, monorepo, Helm chart, CI — and 14 stars. Adoption killed it,
not quality.

### Idle rows recorded so nobody rediscovers them as new

| Repo | Licence | Last commit | Verdict |
|---|---|---|---|
| [bomctl/bomctl](https://github.com/bomctl/bomctl) | Apache-2.0 | **2025-09-10** | 14 months idle. Use [protobom/protobom](https://github.com/protobom/protobom) (Apache-2.0, 339 ★, 2026-11-23) for the same job. |
| [mcpshield/mcpshield](https://github.com/mcpshield/mcpshield) | MIT | 2026-02-18 | 9 months idle. Presents as "Snyk for MCP servers"; not maintained at this layer's cadence. |
| [in-toto/in-toto](https://github.com/in-toto/in-toto) | Apache-2.0 | 2026-08-27 | **Default branch is `develop`.** Spec reference implementation — read as stability, not abandonment. |

## 2026-11-21 — eighth pass — the write channel and the evidence trail

> Two layers this KB did not have at all, found by asking what happens *after* the
> agent decides to act: the **integration runtime that carries the write into the
> system of record**, and the **machine-readable format that proves the write was
> authorised**. Both verified live on 2026-11-21 with licences byte-read from each
> repository's own `LICENSE`.

### Enterprise integration — the write channel that is already deployed at the client

The KB held workflow-automation tools (`n8n`, `activepieces`, `kestra`) but not the
classic enterprise integration layer. That is the layer that *already* holds the
client's connections to SAP, Salesforce, JDBC, JMS, AS/400 and the rest — and as of
2026 it speaks MCP and A2A natively.

| Repo | Stars | Licence | Last push | Note |
|---|---|---|---|---|
| [apache/camel](https://github.com/apache/camel) | 6,419 ★ | Apache-2.0 (11,357 B `LICENSE.txt`, byte-read) | 2026-11-21 | **The finding of this pass.** Read from the code, not the release notes: `components/camel-ai/pom.xml` lists `camel-ai-tool` (one unified tool component), `camel-mcp-server` + `camel-mcp-server-api`, `camel-ai-resource` (a route exposed as a read-only MCP resource), **`camel-a2a`**, `camel-ai-observability`, `camel-langchain4j-agent`, `camel-docling`, and vector-store components for Qdrant, pgvector, Milvus, Neo4j, Pinecone and Weaviate. |
| [conductor-oss/conductor](https://github.com/conductor-oss/conductor) | 32,494 ★ | Apache-2.0 (11,309 B, byte-read) | 2026-11-20 | Netflix-origin workflow orchestration, now community-governed. The high-star alternative to Camel where the shape is *orchestration of services* rather than *mediation between protocols*. |
| [dapr/dapr](https://github.com/dapr/dapr) | 26,212 ★ | Apache-2.0 (11,411 B, byte-read, `master`) | 2026-11-19 | CNCF. Workflow versioning since v1.17 (Feb 2026) — running instances replay against the code they started on. |
| [dapr/dapr-agents](https://github.com/dapr/dapr-agents) | 778 ★ | Apache-2.0 (11,356 B, byte-read) | 2026-11-12 | Agents as durable workflows; each agent is an actor. |

**Two corrections the primary source made to the secondary one.** Apache's own blog
calls the MCP piece "camel-mcp"; the artefact in the tree is **`camel-mcp-server`** —
copying the blog's name yields a dependency coordinate that does not resolve. And
**no blog or roundup mentioned `camel-a2a` at all**; it was found only by reading the
module list. When a layer is this new, the `pom.xml` is more current than the
announcement written about it.

One component deserves its own line: **`camel-semantic-wolf-defender`**, whose POM
describes it as *"Detect prompt injection in text using local Wolf-Defender
inference"*. Every guardrail this KB holds (`llm-guard`, `guardrails-ai`,
`nvidia-nemo/guardrails`) sits beside the *model*. This one sits inside the
*integration route* — on the path the data actually travels, and running locally with
no call out. That is a different and better placement for an estate that will not send
its payloads to a scanning service.

### Machine-readable control evidence — the OSCAL layer

The KB has argued since the fourth pass that governance is a buying requirement, and
since trend 14 that ISO/IEC 42001 is a procurement gate. It had **no tooling that
produces the evidence** — zero occurrences of OSCAL across all nine files before this
pass. This is the format auditors and US federal programmes actually ingest.

| Repo | Stars | Licence (byte-read) | Last push | Role |
|---|---|---|---|---|
| [usnistgov/OSCAL](https://github.com/usnistgov/OSCAL) | 972 ★ | **worldwide public domain** (GitHub badge: `NOASSERTION`) | 2026-11-16 | NIST's Open Security Controls Assessment Language — the schema itself. Catalogs, profiles, component definitions, SSPs, assessment plans and results, as XML/JSON/YAML. |
| [usnistgov/oscal-content](https://github.com/usnistgov/oscal-content) | 477 ★ | worldwide public domain | 2026-10-27 | NIST SP 800-53 and friends, already expressed as OSCAL catalogs. You do not transcribe controls; you import them. |
| [usnistgov/oscal-cli](https://github.com/usnistgov/oscal-cli) | 72 ★ | worldwide public domain | 2026-11-19 | Validate and convert OSCAL documents. The CI gate. |
| [oscal-compass/compliance-trestle](https://github.com/oscal-compass/compliance-trestle) | 292 ★ | Apache-2.0 (11,357 B) | 2026-11-17 | The authoring platform — compliance-as-code over OSCAL, with CI. v5 is current and supports OSCAL 1.2.1; PyPI shows 5.2.1 and v4 in maintenance. |
| [oscal-compass/compliance-trestle-mcp](https://github.com/oscal-compass/compliance-trestle-mcp) | 2 ★ | Apache-2.0 (11,357 B) | 2026-11-11 | **The keystone.** Trestle's operations exposed over MCP, so the agent can author its own control evidence. Registered as `io.github.oscal-compass/compliance-trestle-mcp`. |
| [oscal-compass/compliance-trestle-fedramp](https://github.com/oscal-compass/compliance-trestle-fedramp) | 3 ★ | Apache-2.0 | 2026-08-27 | FedRAMP profile support. Relevant only to North America; see `intel/market.md`. |
| [complytime/complyctl](https://github.com/complytime/complyctl) | 38 ★ | Apache-2.0 (11,342 B) | 2026-11-21 | The runtime. Pulls [Gemara](https://github.com/ossf/gemara) policies from an **OCI registry** and executes scans through pluggable providers, emitting **EvaluationLog, OSCAL, SARIF and Markdown**. OpenSSF Best Practices and Scorecard badges in its README. |
| [complytime/complytime-providers](https://github.com/complytime/complytime-providers) | 1 ★ | Apache-2.0 | 2026-11-20 | The providers themselves — standalone executables bridging complyctl to **OpenSCAP, Ampel and OPA**. Discovered by naming convention (`complyctl-provider-*`). Note the description: *"complyctl providers (formerly plugins)"*. |
| [complytime/complypack](https://github.com/complytime/complypack) | 1 ★ | Apache-2.0 | 2026-11-20 | Assessment-logic packaging for complyctl. |
| [complytime/complytime-collector-components](https://github.com/complytime/complytime-collector-components) | 5 ★ | Apache-2.0 | 2026-11-18 | *"A policy-driven observability toolkit for compliance monitoring"* — the continuous half, as opposed to the point-in-time scan. |
| [ossf/gemara](https://github.com/ossf/gemara) | star count **not measured** — the repo is not indexed by the GitHub search API, so no figure is quoted | Apache-2.0 (11,379 B, byte-read) | live on 2026-11-21 | The OpenSSF policy model complyctl consumes. |
| [ComplianceAsCode/content](https://github.com/ComplianceAsCode/content) | — | **BSD-3-Clause** (1,552 B, SPDX identifier on line 1) | — | The hardening-content project. Its `LICENSE` is the only one in this batch whose first line is a machine-readable SPDX identifier. |
| [ComplianceAsCode/oscal-content](https://github.com/ComplianceAsCode/oscal-content) | 7 ★ | Apache-2.0 (11,356 B) | 2026-05-11 | OSCAL test content paired with ComplyTime, synced bidirectionally with `ComplianceAsCode/content`. |

**OPA is already in this KB**, held since the governance-substrate section. It turns
out to be a *provider* in a compliance runtime, which means the policy engine Globant
already proposes for authorisation decisions can also be the thing that generates the
auditor's evidence. That is one component doing two jobs, and it is the cheapest
sentence in a governance proposal.

### Two traps in this layer, both of which would have landed wrong data

**1. The archived tool that its own documentation still presents as live.**
[complytime/complyscribe](https://github.com/complytime/complyscribe) — 21 ★,
Apache-2.0 — is **archived**, last pushed 2026-05-11. A ComplyTime QuickStart site and
a May-2026 write-up both describe it as the way to bring trestle into CI/CD. The live
path is `complyctl` plus `complytime-providers`. This is the **seventh**
archived-or-abandoned-but-recommended project this KB has caught, after `osohq/oso`
(seventh pass) and the five the energy KB counted.

**2. The org-named repo is not the product.**
[complytime/complytime](https://github.com/complytime/complytime) has **1 star** and
contains *"design and proposed enhancements"*. The product is
[complytime/complyctl](https://github.com/complytime/complyctl), 38 ★. Guessing the
obvious slug — org name as repo name — would have put a one-star proposals repository
into a foundations table as a flagship runtime. **Resolve the flagship by listing the
org and reading descriptions, never by composing `owner/owner`.**

### Also added this pass

| Repo | Stars | Licence | Last push | Note |
|---|---|---|---|---|
| [lancedb/lancedb](https://github.com/lancedb/lancedb) | 11,960 ★ | Apache-2.0 (11,357 B, byte-read) | 2026-11-21 | Embedded multimodal vector store. Fills the local/embedded slot beside `qdrant`; relevant where retrieval must run inside the client's own process with no service to procure. Watch the siblings: `lancedb/lancedb-mcp-server` is `NOASSERTION` **and** last pushed 2025-04-25 — do not pick it up with the parent. |

## 2026-11-20 — seventh pass

**Theme: the entitlement boundary.** Not "what can the agent do" (six passes covered that) but
**"what may the person it is acting for see"** — a layer with no agents in it, which is why it
was missed. Full tables in `repos/foundations.md`; build in `compose/patterns.md` Receta 16.

**Verified additions (API + `raw.githubusercontent.com`, both channels, 2026-11-20):**

| Repo | Licence (read from `LICENSE`) | ★ | Pushed | Default branch |
|------|-------------------------------|---|--------|----------------|
| [apache/casbin](https://github.com/apache/casbin) | Apache-2.0 | 20,508 | 2026-11-20 | `master` |
| [ory/hydra](https://github.com/ory/hydra) | Apache-2.0 | 17,675 | **2026-07-29** (idle) | `master` |
| [oauth2-proxy/oauth2-proxy](https://github.com/oauth2-proxy/oauth2-proxy) | MIT | 15,392 | 2026-11-19 | `master` |
| [authzed/spicedb](https://github.com/authzed/spicedb) | Apache-2.0 | 7,233 | 2026-11-20 | `main` |
| [openfga/openfga](https://github.com/openfga/openfga) | Apache-2.0 | 6,168 | 2026-11-20 | `main` |
| [ory/keto](https://github.com/ory/keto) | Apache-2.0 | 5,421 | **2026-09-04** (idle) | `master` |
| [modelcontextprotocol/ext-auth](https://github.com/modelcontextprotocol/ext-auth) | MIT | 179 | 2026-11-10 | `main` |
| [apache/casbin-node-casbin](https://github.com/apache/casbin-node-casbin) | Apache-2.0 | 2,921 | 2026-11-19 | `master` |
| [apache/casbin-jcasbin](https://github.com/apache/casbin-jcasbin) | Apache-2.0 | 2,652 | 2026-11-15 | `master` |
| [apache/casbin-pycasbin](https://github.com/apache/casbin-pycasbin) | Apache-2.0 | 1,778 | 2026-11-20 | `master` |

**Rename ledger — fifth catch, first one into a foundation.** `casbin/casbin` → `apache/casbin`.
`repo:casbin/casbin` returns **422**; the old path 404s on `main` but **serves 200 on `master`**
(redirect, not deletion — same signature as the Presidio move); and the old path's README now
opens with the **ASF contributor-licence header**. Ten of the twelve repositories matching
`casbin in:name stars:>300` are now under `apache/`. The ledger's rate holds near **one rename
per ten repositories checked**.

**A licence class this KB had not recorded: partial relicensing in progress.**
[modelcontextprotocol/modelcontextprotocol](https://github.com/modelcontextprotocol/modelcontextprotocol)
(9,734 ★) reports `NOASSERTION`, and its manifest says `"license": "SEE LICENSE IN LICENSE"` —
so the manifest-first rule yields nothing and the file must be read. The file says the project
is *"undergoing a licensing transition from the MIT License to the Apache License, Version
2.0"*: new contributions are Apache-2.0, documentation is CC-BY-4.0, and **contributions whose
authors have not granted relicensing consent remain MIT**. **There is no single SPDX identifier
for this repository**, and which licence governs depends on the file and the contributor. Record
it as mixed; do not write one licence into a dependency inventory.

**Two method corrections for this environment, both reusable across the rotation:**

1. **`curl -sI https://github.com/<repo>` is useless here as an existence check.** Probed
   against 18 repositories known alive from the API, it returned **403 for all 18** — the proxy
   refuses github.com HTML browsing regardless of whether the path exists. Use the search API's
   exact `repo:` qualifier plus `raw.githubusercontent.com`.
2. **`modelcontextprotocol.io`, `datatracker.ietf.org` and `www.ietf.org` are all unreachable**
   (DNS failure; HTTP 000 for the last). The MCP specification was still read in full because
   **GitHub-hosted specs can be read over `raw.githubusercontent.com` even when the docs site
   is blocked** — a route around a blocked host that this KB should try before recording a
   source as unread. The IETF draft state has **no such route** and remains unverified.

## 2026-11-20 — sixth pass

**Method: searched by what the agent reads, not by what the agent is.** Pass 3 swept by
architectural layer, pass 4 by consequence, pass 5 by counterparty. This pass went *downward* —
beneath the agent to the data plane — and found a layer this KB had half of. It had the context
layer (DataHub, OpenMetadata, Unity Catalog, `auto-ontology`) and transformation (dbt). It had
**no governed metric definition, no entity resolution, no change data capture and no query
engine**: the four components that decide whether an agent's answer reconciles with the client's
own finance reporting.

**Fifteen repositories added across four sections in `repos/foundations.md`.** Permissive core:
[cube-js/cube](https://github.com/cube-js/cube) (Apache-2.0/MIT, 21.3k ★),
[dbt-labs/metricflow](https://github.com/dbt-labs/metricflow) (Apache-2.0, 1.9k ★),
[malloydata/malloy](https://github.com/malloydata/malloy) (MIT, 2.6k ★),
[moj-analytical-services/splink](https://github.com/moj-analytical-services/splink) (MIT, 2.6k ★),
[J535D165/recordlinkage](https://github.com/J535D165/recordlinkage) (BSD-3-Clause, 1.1k ★),
[debezium/debezium](https://github.com/debezium/debezium) (Apache-2.0, 13.4k ★),
[dlt-hub/dlt](https://github.com/dlt-hub/dlt) (Apache-2.0, 6.1k ★),
[meltano/meltano](https://github.com/meltano/meltano) (MIT, 2.7k ★),
[duckdb/duckdb](https://github.com/duckdb/duckdb) (MIT, 43.2k ★),
[apache/iceberg](https://github.com/apache/iceberg) (Apache-2.0, 9.4k ★),
[evidence-dev/evidence](https://github.com/evidence-dev/evidence) (MIT, 7.1k ★).

**The pass's risk finding — the data plane is the second layer this KB family has found where
non-OSI licences concentrate, and where the most-starred option is the least usable:**

- [airbytehq/airbyte](https://github.com/airbytehq/airbyte) (22.4k ★) — root `LICENSE` is the
  **Elastic License 2.0**. Airbyte's own marketing page says "Airbyte Core is open source under
  Apache 2.0"; **the repository does not support that**. ELv2 forbids offering the software to
  third parties as a managed service — precisely the engagement shape Globant would sell.
- [bruin-data/ingestr](https://github.com/bruin-data/ingestr) (4.0k ★) — **Functional Source
  License 1.1**, a licence class new to this KB: *"each version becomes Apache 2.0 two years
  after release."* Time-delayed permissive, not permanently restricted.
- [metabase/metabase](https://github.com/metabase/metabase) (50.4k ★) — **AGPL-3.0** outside
  `enterprise/`. Its root `package.json` says `"license": "private"`, so a manifest-only read
  returns a **false negative** on the most-starred repo in the section.
- [zinggAI/zingg](https://github.com/zinggAI/zingg) (1.3k ★) — **AGPL-3.0**, while the MIT
  alternative ([splink](https://github.com/moj-analytical-services/splink)) is less marketed.
- [lightdash/lightdash](https://github.com/lightdash/lightdash) (6.2k ★) — MIT **except**
  `packages/backend/src/ee/`. Sidebar names no licence at all.

**In every one of those five cases the clean substitute has fewer stars than the encumbered
option.** That is now the third layer in this KB family where sorting by stars gives
systematically the wrong procurement answer, after the energy KB's metering layer and this KB's
own skills/harness layer. It is no longer a per-layer quirk; see `intel/trends.md` for the
generalisation.

**Method rule derived this pass (reusable across the rotation):** the root `LICENSE` and the
package manifest **can disagree, and either can be wrong in either direction** — Metabase's
manifest understates (false negative), Airbyte's marketing overstates (false positive), Cube's
two sources disagree harmlessly. Read both; when they conflict, record the conflict instead of
picking the convenient reading.

**One measurement limit, stated rather than papered over:** Airbyte's README carries both MIT
and ELv2 badges, which implies a platform/connector split. The boundary is **not documented at
any path probed this pass** — `airbyte-integrations/LICENSE` and the licensing FAQ doc both
return 404. Reusing a specific Airbyte connector therefore requires reading that connector's own
licence file. Unresolved, and flagged as unresolved.

---

## 2026-11-20 — fifth pass

**Method change: searched the surfaces an agent touches that are *not* code.** Pass 3 swept by
architectural layer (found the control plane). Pass 4 swept by consequence (found payments, PII,
catalog). This pass swept by **counterparty** — who or what is on the other side of the agent:
a human looking at a screen, a manager assigning it work, an auditor asking what exists. Three
layers came back, all with zero prior coverage in this KB, and one of them contains a die-off.

### The interaction layer, and three archived repositories

Full tables in `agents/trending.md` (same date). The repos-side summary:

- **Live and converging on one shape** — the agent renders into the client's existing
  application: [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) (MIT, 38,842 ★),
  [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) (MIT, 20,766 ★),
  [vercel-labs/json-render](https://github.com/vercel-labs/json-render) (Apache-2.0, 19,791 ★),
  [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) (Apache-2.0, 17,690 ★, Google-origin),
  [thesysdev/openui](https://github.com/thesysdev/openui) (MIT, 15,375 ★),
  [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) (MIT, 13,351 ★),
  [tambo-ai/tambo](https://github.com/tambo-ai/tambo) (MIT, 11,221 ★).
- **Archived, same shape as each other** — a standalone chat window in front of an agent:
  [Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★),
  [langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★),
  [langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui) (MIT, 1,705 ★).
  **None of the three READMEs says so.**

**Why four competing permissive standards is the finding, not the list.** AG-UI (20,766 ★),
json-render (19,791 ★), A2UI (17,690 ★) and openui (15,375 ★) are within one order of magnitude
of each other, all permissive, all actively pushed, and all solving the same problem. There is
no foundation steward for any of them. Contrast the tool layer, where MCP won and then moved to
the Linux Foundation. **At the presentation layer, a 2026 engagement is making a bet, not
following a standard** — so build the agent's output as structured data and keep the renderer
swappable. Partial cooperation exists and is worth knowing: Google states A2UI was developed
with partners including the AG-UI/CopilotKit team, so these are not purely rival camps.

### AI inventory and AI-BOM — the layer that has to exist before governance can

This KB sells governance (trends 3, 10, 14; Recetas 7, 9, 10). All of it assumes you know what
agents, models, keys and MCP servers exist in the estate. **Nothing in this KB produced that
list.** The tooling is small, young and permissive:

| Repo | Licence (file-read) | ★ | Forks | Pushed | What it does |
|------|---------------------|---|-------|--------|--------------|
| [CycloneDX/specification](https://github.com/CycloneDX/specification) | Apache-2.0 | 585 | 98 | 2026-11-20 | The OWASP BOM standard itself — SBOM, SaaSBOM, **ML-BOM**, VEX. The format an auditor will accept. |
| [CycloneDX/cyclonedx-python](https://github.com/CycloneDX/cyclonedx-python) | Apache-2.0 | 406 | 107 | 2026-11-19 | BOM generator for Python projects and environments. Maven, Gradle, .NET, Go variants exist in the same org. |
| [Trusera/ai-bom](https://github.com/Trusera/ai-bom) | Apache-2.0 | 368 | 102 | **2026-05-24** | "AI Bill of Materials — discover every AI agent, model and API in your infrastructure." The only *discovery*-shaped tool found. **Six months idle — a fork candidate, not a dependency.** |
| [sbom-tool/sbom-tools](https://github.com/sbom-tool/sbom-tools) | MIT | 268 | 20 | 2026-11-17 | Semantic SBOM/CBOM/**AI-BOM** diff, quality scoring and compliance validation for CycloneDX/SPDX. The *diff* matters: it turns an inventory into change detection. |
| [apisec-inc/mcp-audit](https://github.com/apisec-inc/mcp-audit) | MIT | 167 | 45 | 2026-08-18 | Scans MCP configs for exposed secrets, shadow APIs and models. Narrow, directly useful given >10,000 MCP servers in production. Three months idle. |

**Read the star counts as a market statement, not a quality one.** The governance *obligations*
(ISO/IEC 42001, EU AI Act record-keeping) are a procurement gate worth millions; the open tooling
to satisfy the inventory half of them tops out at 585 stars. That asymmetry is the opening —
assembling and operating this is deliverable work, and nobody has productised it.

### The engineer-facing front door: internal developer portal

| Repo | Licence | ★ | Forks | Pushed | Note |
|------|---------|---|-------|--------|------|
| [backstage/backstage](https://github.com/backstage/backstage) | Apache-2.0 | 34,891 | 7,786 | 2026-11-20 | CNCF developer-portal framework; already the software catalog and ownership system of record in many large clients. |
| [spotify/portal-ai-plugins](https://github.com/spotify/portal-ai-plugins) | Apache-2.0 | 3,302 | 260 | 2026-10-23 | Brings the Portal CLI into coding agents: catalog search, ownership/health/incident briefings, and **action invocation with help, dry-run and confirmation safeguards**. A month idle. |

The second row is the interesting one: the confirmation-and-dry-run pattern is the same
human-approval boundary `humanlayer` implements, arriving from the platform-engineering side.
Where a client already runs Backstage, the catalog is the cheapest grounding source in the
building — it already knows what every service is and who owns it.

### Determinism as a product category

[github/spec-kit](https://github.com/github/spec-kit) — MIT, **150,799 ★**, 13,548 forks, pushed
2026-11-20 — spec-driven development tooling, and the second-most-starred repository this KB has
ever recorded. Relevant to enterprise for one reason: it is the mainstream expression of
*specify, then generate, then verify against the spec*, which is the only shape of agentic
delivery an audit function accepts. Pair it with the evaluation gate in Receta 10.

### Also new, filling two named holes in `repos/foundations.md`

- [Atmosphere/atmosphere](https://github.com/Atmosphere/atmosphere) — Apache-2.0, 3,835 ★,
  765 forks, pushed 2026-11-20. "Portable AI agent runtime for the JVM: one `@Agent` class runs
  on Spring AI, LangChain4j, and others." Directly strengthens **Receta 6** (JVM-native agents
  for an APAC enterprise core), which previously rested on `agentscope-java` alone.
- [dbos-inc/dbos-transact-py](https://github.com/dbos-inc/dbos-transact-py) — MIT, 1,693 ★,
  pushed 2026-11-20. Database-backed durable Python workflows: durable execution **without**
  standing up a separate orchestrator, when Temporal is too much infrastructure for the pilot.
- [openbao/openbao](https://github.com/openbao/openbao) — MPL-2.0, 9,112 ★, pushed 2026-11-20.
  The Linux Foundation Vault fork, for secrets. MPL-2.0 is **weak, file-level copyleft**: running
  it as a service alongside a proprietary product is fine; modifying its files and shipping them
  closed is not.
- [cedar-policy/cedar](https://github.com/cedar-policy/cedar) — Apache-2.0, 1,889 ★, pushed
  2026-11-20. A third authorisation option beside OPA and Cerbos, AWS-origin, with formal
  verification of policies as its differentiator.

### Not usable, despite appearing in every "durable agents" discussion

[restatedev/restate](https://github.com/restatedev/restate) — 4,725 ★, GitHub reports
`NOASSERTION`; the `LICENSE` file on **both** `main` and `master` is the **Business Source
License 1.1**. BUSL is not open source: it carries a use limitation until a conversion date.
**Do not put it in a client architecture as "open source".** Verified substitutes for the same
job are already in this KB (Temporal) plus `dbos-transact-py` above.


## 2026-11-20 — fourth pass

**Method change: searched by what an agent is allowed to *do*, not by what it is built with.**
The third pass swept by architectural layer and found the control plane. This pass asked a
different question — what does an enterprise agent *touch* that has consequences? Money,
personal data, and the systems of record that tell it what is true. Each answer was a layer
this KB did not have. **Sixteen repositories below were absent entirely**, and the most
consequential one has 89 stars while the most-starred one in its own family is five months idle.

All metadata from the GitHub search API on 2026-11-20. **Every licence below was read from the
repository's own `LICENSE` file over `raw.githubusercontent.com` — 16/16 verified, none taken
from a GitHub badge.** Full tables and the commercial reading are in `repos/foundations.md`.

### Agent payments & commerce protocols — zero prior coverage in this KB

`AP2`, `x402`, `agentic-commerce` and the bare word `payment` each returned **no match** across
all eight files before this pass. This is the first layer where an agent's mistake debits a real
account.

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [google-agentic-commerce/AP2](https://github.com/google-agentic-commerce/AP2) | Apache-2.0 | 3,281 | **2026-06-17** | Agent Payments Protocol; A2A extension, ~60 payments/tech organisations. The signed-mandate model is the durable idea. **Idle five months.** |
| [agentic-commerce-protocol/agentic-commerce-protocol](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) | Apache-2.0 | 1,607 | 2026-07-18 | ACP — OpenAI/Stripe lineage, now under its **own neutral organisation**. |
| [google-agentic-commerce/a2a-x402](https://github.com/google-agentic-commerce/a2a-x402) | Apache-2.0 | 571 | **2026-11-11** | HTTP 402 as a machine-payable rail. **The only actively-pushed repo in the family.** |
| [forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol) | MIT | 180 | 2026-07-08 | Agent↔merchant authentication and encryption — the identity question the payment specs leave open. |
| [NVIDIA-AI-Blueprints/Retail-Agentic-Commerce](https://github.com/NVIDIA-AI-Blueprints/Retail-Agentic-Commerce) | Apache-2.0 | 89 | 2026-11-18 | Runnable reference implementation of ACP + UCP. Lowest stars here, highest demo value. |

**The finding, not the list:** three protocols at three layers, all permissive, **and the star
ranking inverts the activity ranking.** AP2 has 5.7× the stars of the x402 extension and has not
been touched since June. This reproduces `intel/trends.md` §11 *inside a single protocol family*.

### PII de-identification — the layer between an agent and customer data

| Repo | Real license | Stars | Pushed | Note |
|------|--------------|-------|--------|------|
| [data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) | MIT | 11,989 | 2026-11-19 | PII detection, redaction, masking, anonymisation. **Moved out of `microsoft/` — see the rename ledger.** |
| [data-privacy-stack/presidio-research](https://github.com/data-privacy-stack/presidio-research) | MIT | 321 | 2026-11-19 | Recogniser evaluation harness — makes tuning an evidenced claim. |

### Catalog & lineage — and the "context layer" rebrand

| Repo | Real license | Stars | Pushed | Self-description |
|------|--------------|-------|--------|------------------|
| [open-metadata/OpenMetadata](https://github.com/open-metadata/OpenMetadata) | Apache-2.0 | 15,823 | 2026-11-20 | "The Open **Context Layer** for Data and AI." New to this KB. |
| [unitycatalog/unitycatalog](https://github.com/unitycatalog/unitycatalog) | Apache-2.0 | 3,581 | 2026-11-20 | "Open, Multi-modal Catalog for Data & AI." |
| [OpenLineage/OpenLineage](https://github.com/OpenLineage/OpenLineage) | Apache-2.0 | 2,773 | 2026-11-20 | "An Open Standard for lineage metadata collection." |

**Observation worth selling:** two independent catalog vendors — OpenMetadata and the already-listed
[datahub-project/datahub](https://github.com/datahub-project/datahub) — pushed the same day and
both now lead with the word **"context"**. The category has re-described itself as agent
infrastructure. These are usually *already installed* at the client, which makes them the
cheapest grounding layer in the KB.

### Graph RAG — a 36,699-star MIT repo this KB had never mentioned

| Repo | Real license | Stars | Pushed | Note |
|------|--------------|-------|--------|------|
| [microsoft/graphrag](https://github.com/microsoft/graphrag) | MIT | 36,699 | 2026-11-19 | Category leader, actively pushed. |
| [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | MIT | 4,010 | 2026-01-27 | "Easy-to-hack" — **idle ~10 months.** |
| [circlemind-ai/fast-graphrag](https://github.com/circlemind-ai/fast-graphrag) | MIT | 3,972 | **2025-11-01** | **Idle over a year — verify before proposing.** |
| [DEEP-PolyU/Awesome-GraphRAG](https://github.com/DEEP-PolyU/Awesome-GraphRAG) | MIT | 2,686 | 2026-06-02 | Survey/benchmark index — a reading list, not a dependency. |

### A branch trap that will silently misreport a licence

[datahub-project/datahub](https://github.com/datahub-project/datahub) keeps its `LICENSE` on
**`master`**, not `main`. A verification script that probes only `main` reports this Apache-2.0
repo as **unlicensed**. Three repos in this pass needed the `master` fallback; this KB's own
checker tries both, and that is why. Worth stating because the failure mode is a *false
negative on licence* — the direction that loses Globant a usable repo rather than risking one.

### Searched and not found this pass

- **A LATAM-origin repository in any of the four new layers** — payments/commerce, PII and
  anonymisation, catalog/lineage, and graph RAG were each searched, including Spanish and
  Portuguese vocabulary (`pagos agentes IA`, `agente pagamento IA`, `anonimizacion datos IA`).
  **Result: zero usable.** Everything returned was 0–3 stars with **NOASSERTION (no usable
  licence)** — landing pages, a WhatsApp payment-receipt OCR bot, and student final-year
  projects. This is the **fifth consecutive pass** measuring this gap and the fifth zero.
  Recorded so it reads as measured, not unexamined.
- **A dedicated enterprise DLP repo above 500 stars** — `pii redaction anonymization llm
  stars:>500` returned **no results at all**. Presidio is not merely the leader in this
  category; above 500 stars it is close to the only thing in it.
- **Primary sources for every market figure** — `www.idc.com` and every other non-GitHub host
  fail to resolve in this session (`ENOTFOUND`), as in the third pass. GitHub search API and
  `raw.githubusercontent.com` both work. The evidence split in `intel/trends.md` therefore
  still holds: **repositories are first-hand, market statistics are second-hand.**

## 2026-11-20 — third pass (later still)

Searched by **layer** rather than by star ceiling this time: the earlier passes swept
`stars:>150000` and found the harness/skill band, which meant anything structurally important
but modestly starred stayed invisible. Twelve repositories below were absent from this KB
entirely, and the most strategically important one has 2,423 stars. All metadata from the
GitHub search API on 2026-11-20; every licence read from the repository's own `LICENSE`.

### Control plane — the layer this KB did not have

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 | 2,423 | 2026-11-19 | **Formerly Envoy AI Gateway; now an Agentic AI Foundation project.** One OpenAI-compatible API for every model and MCP server; credentials, routing, quotas, failover and usage attribution in one Envoy-enforced plane. The vendor-neutral answer to the NVIDIA concentration risk recorded in `intel/market.md`. |
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT core + `litellm/enterprise/` carve-out | 63,615 | 2026-11-20 | The adoption leader — 100+ providers, Rust core with Python SDK. Virtual keys, spend tracking, budgets and fallbacks in the MIT core. |
| [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 | 44,402 | 2026-11-20 | "The API and AI Gateway." Right answer when Kong already fronts the client's API estate; AI features reportedly enterprise-gated — verify per feature. |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | MIT, no carve-out found | 13,421 | 2026-11-20 | 1,600+ LLMs, **50+ guardrails enforced at the gateway** instead of in application code. Cleanest licence in the category. |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 | 9,818 | 2026-11-20 | Go; LLM gateway and MCP gateway in one. Vendor-published comparisons — discount the claims. |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 | 6,291 | 2026-11-17 | Observability-first gateway companion. |

### Cost governance & metering — new category

| Repo | License | Stars | Pushed | Why it is moving |
|------|---------|-------|--------|------------------|
| [opencost/opencost](https://github.com/opencost/opencost) | Apache-2.0 | 6,824 | 2026-11-20 | CNCF Kubernetes/cloud cost monitoring — the GPU and pod spend behind self-hosted vLLM that token counting never sees. |
| [openmeterio/openmeter](https://github.com/openmeterio/openmeter) | Apache-2.0 | 2,457 | 2026-11-20 | "Metering and Billing for AI, API and DevOps." Turns gateway usage events into per-team entitlements and chargeback. |

### Red teaming, eval gates & OpenTelemetry instrumentation

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) | MIT | 27,494 | 2026-11-20 | Eval **and** red teaming, declarative, designed to run as a CI gate. |
| [confident-ai/deepeval](https://github.com/confident-ai/deepeval) | Apache-2.0 | 19,577 | 2026-11-19 | Unit-test-shaped LLM/agent metrics; drops into existing pytest CI. |
| [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | Apache-2.0 | 16,389 | 2026-11-14 | RAG evaluation metrics. **Ownership moved** from `explodinggradients` — re-pin and re-read the licence. |
| [NVIDIA/garak](https://github.com/NVIDIA/garak) | Apache-2.0 | 10,114 | 2026-11-18 | The LLM vulnerability scanner. Run it against the deployed agent so tool access is in scope. |
| [traceloop/openllmetry](https://github.com/traceloop/openllmetry) | Apache-2.0 | 7,543 | 2026-11-19 | OpenTelemetry-based LLM/agent observability — routes into the client's existing APM. |
| [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | MIT | 4,980 | 2026-11-20 | Microsoft's open red-teaming toolkit. **Canonical location**; `Azure/PyRIT` is the stale old home (128 ★, 2026-03-25). |
| [Agenta-AI/agenta](https://github.com/Agenta-AI/agenta) | MIT Expat core + `ee/` carve-out | 4,922 | 2026-11-20 | Agent/prompt eval and versioning workspace. Copyright **Agentatech UG**, a German entity — a second **EMEA-origin** assurance tool alongside Giskard. |
| [Arize-ai/openinference](https://github.com/Arize-ai/openinference) | Apache-2.0 | 1,331 | 2026-11-20 | OpenTelemetry instrumentation for AI. Note the same vendor's `phoenix` is **Elastic License 2.0** and not open source. |
| [open-telemetry/semantic-conventions](https://github.com/open-telemetry/semantic-conventions) | Apache-2.0 | 690 | 2026-11-20 | Where **GenAI semantic conventions** are standardised. Lowest stars, highest portability leverage in this list. |

### Sandboxing, memory & document AI

| Repo | Real license | Stars | Pushed | Why it is here |
|------|--------------|-------|--------|----------------|
| [docling-project/docling](https://github.com/docling-project/docling) | **MIT** | 70,818 | 2026-11-20 | "Get your documents ready for gen AI." **Hosted in the LF AI & Data Foundation**, IBM-originated. MIT + foundation-governed + 70k stars — the default answer to an enterprise document estate, and absent from this KB until now. |
| [topoteretes/cognee](https://github.com/topoteretes/cognee) | Apache-2.0 | 33,431 | 2026-11-20 | Open-source graph-backed AI memory for agents. Permissive alternative to Mem0. |
| [Unstructured-IO/unstructured](https://github.com/Unstructured-IO/unstructured) | Apache-2.0 | 15,769 | 2026-11-19 | Document-to-structured-data ETL for scheduled ingestion. |
| [e2b-dev/E2B](https://github.com/e2b-dev/E2B) | Apache-2.0 | 14,943 | 2026-11-20 | Secure code-execution sandbox for enterprise agents — a non-NVIDIA option in the isolation slot. |

### Agents that should already have been here

| Repo | License | Stars | Pushed | Note |
|------|---------|-------|--------|------|
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121,597 | 2026-11-20 | AI browser agents — for client systems that have a portal and no API. |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | MIT | 85,545 | 2026-11-20 | "Long-horizon SuperAgent harness." **APAC-origin.** Fourth MIT harness above every Tier-1 framework. |
| [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | **2026-10-18** | Stateful agents, learning memory (MemGPT lineage). Month-plus idle — verify. |

### Renames and ownership moves to fix in existing code — new this pass

| Was | Is now | How it was caught |
|-----|--------|-------------------|
| `envoyproxy/ai-gateway` | [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Old path's `raw` README returns 200 and reads "Formerly Envoy AI Gateway"; search API `repo:` returns 422 for the old name. |
| `Azure/PyRIT` | [microsoft/PyRIT](https://github.com/microsoft/PyRIT) | Old org resolves but is 128 ★ / 2026-03-25; name search ranks `microsoft/PyRIT` first by two orders of magnitude. |
| `explodinggradients/ragas` | [vibrantlabsai/ragas](https://github.com/vibrantlabsai/ragas) | `repo:` on the old path returns 422; `ragas in:name stars:>500` returns one repo under a **new organisation**. |

**Three of ~35 repositories checked had moved and two changed organisation.** That is a
supply-chain finding, not a link-rot finding.

### Not permissive / not usable, despite appearances

| Repo | Reality | Stars |
|------|---------|-------|
| [daytonaio/daytona](https://github.com/daytonaio/daytona) | **No `LICENSE` file** (checked 4 filenames × `main`/`master`); last pushed **2026-07-24** | 71,307 |
| [meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) | **Llama 3.2 Community License Agreement** — not OSI open source. GitHub shows `NOASSERTION`, hence the common mistake | 4,486 |
| [getzep/zep](https://github.com/getzep/zep) | Apache-2.0, but the repo is now *"Examples and Integrations"* — Zep itself is a hosted product. Not self-hosted memory | 5,010 |
| [Helicone/ai-gateway](https://github.com/Helicone/ai-gateway) | **GPL-3.0** and last pushed **2025-11-21** — a year cold. Same vendor as the Apache-2.0 `helicone` | 647 |
| [protectai/rebuff](https://github.com/protectai/rebuff) | Apache-2.0 but last pushed **2024-08-07** — over two years cold | 1,533 |

### Searched and not found this pass

- **`envoyproxy/ai-gateway` as a searchable repository** — exists on `raw` (200) but the search
  API refuses the `repo:` qualifier (422). Resolved as the Agent Router move above, so this is a
  *resolved* miss, not an open one.
- **`microsandbox/microsandbox`** — `repo:` returns 422 and no plausible successor surfaced. Do
  not cite it; use `e2b-dev/E2B` or `opensandbox-group/OpenSandbox` for isolation.
- **A LATAM-origin repository in any of the six new layers** — gateway, metering, red teaming,
  eval, sandboxing and document AI were each searched; **zero LATAM-origin repositories
  appeared in any of them.** Consistent with the agent-framework finding in `intel/market.md`
  and recorded here so the gap reads as measured, not unexamined.
- **`microsoft/agent-framework`** — still not located; not re-probed this pass, since the second
  pass checked five channels. Treat as unavailable per `agents/top.md`.


## 2026-11-20 — second pass (later same day)

Measured against the GitHub star ceiling rather than a curated watchlist: a
`stars:>150000` sweep sorted descending, to find what the earlier pass's name-based
searches could not see. All figures from the GitHub search API on 2026-11-20; every license
below read from the repository's own `LICENSE` file.

### The agent/skill band of the GitHub top 40 — most of it new to this KB

| Repo | License | Stars | Pushed | Why it is here |
|------|---------|-------|--------|----------------|
| [morluto/rea](https://github.com/morluto/rea) | MIT | 470,997 | 2026-11-20 | Reverse-engineer anything with agents, from app behaviour down to native binaries. **The most-starred agent repository on GitHub** — above OpenClaw. An application, not a platform. |
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,891 | 2026-11-20 | Still the largest *harness*, and the centre of the skill ecosystem. |
| [mattpocock/skills](https://github.com/mattpocock/skills) | MIT | 328,581 | 2026-11-19 | "Skills for Real Engineers." One engineer's `.agents` directory, more starred than every framework in `agents/top.md` Tier 1 combined. |
| [obra/superpowers](https://github.com/obra/superpowers) | MIT | 322,580 | 2026-11-03 | An agentic skills framework and development methodology. Single author (Jesse Vincent). |
| [affaan-m/ECC](https://github.com/affaan-m/ECC) | MIT | 307,599 | 2026-11-20 | Agent-harness performance optimisation: skills, instincts, memory, security. Cross-harness (Claude Code, Codex, Opencode, Cursor). |
| [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | MIT | 284,581 | 2026-11-18 | "Everything is a Plugin." **APAC-origin.** New to this KB. |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT | 264,904 | 2026-11-20 | "The agent that grows with you." New to this KB. |
| [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | **none** | 234,677 | 2026-04-20 | A single `CLAUDE.md`. **No license file** and seven months cold — enormous mindshare, zero reusability. |
| [anomalyco/opencode](https://github.com/anomalyco/opencode) | MIT | 228,170 | 2026-11-20 | "The open source coding agent." |
| [firecrawl/firecrawl](https://github.com/firecrawl/firecrawl) | AGPL-3.0 | 204,866 | 2026-11-20 | Search, scrape and 550+ data providers through one API. **AGPL — integrate over the API, never vendor it.** |
| [anthropics/skills](https://github.com/anthropics/skills) | **none** | 197,931 | 2026-11-16 | Public repository for Agent Skills. **No license file** — cannot be redistributed in a deliverable. |

### Skill-security and runtime containment — the new governance tooling

| Repo | License | Stars | Pushed | Why it is moving |
|------|---------|-------|--------|------------------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 | 27,027 | 2026-11-19 | Skill security scanner, 71 patterns / 17 categories. The control nobody had a month ago. |
| [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | 2026-11-20 | Runs Hermes / Deep Agents / OpenClaw inside OpenShell with managed inference. |
| [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) | Apache-2.0 | 21,829 | 2026-11-20 | Safe, private agent runtime in Rust. `LICENSE` copyright: **NVIDIA CORPORATION & AFFILIATES**. |
| [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 | 14,026 | 2026-11-20 | Graph/semantic reasoning layer for deterministic query generation. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 | 4,224 | 2026-11-20 | Skill quality gates with reusable CI templates. |
| [NVIDIA/skills](https://github.com/NVIDIA/skills) | Apache-2.0 | 4,095 | 2026-11-20 | NVIDIA product skills (CUDA, robotics, simulation, RAG) for Claude Code / Codex. |
| [NVIDIA/NeMo-Agent-Toolkit](https://github.com/NVIDIA/NeMo-Agent-Toolkit) | Apache-2.0 | 2,710 | 2026-11-18 | Connecting and optimising teams of agents. |
| [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 | 254 | 2026-11-20 | Tool/LLM-call middleware — the policy enforcement point. |

### Also verified new this pass

| Repo | License | Stars | Pushed | Note |
|------|---------|-------|--------|------|
| [a2aproject/A2A](https://github.com/a2aproject/A2A) | Apache-2.0 | 26,604 | 2026-11-20 | Agent2Agent protocol — agent-to-agent interop alongside MCP's agent-to-tool. |
| [kestra-io/kestra](https://github.com/kestra-io/kestra) | Apache-2.0 | 30,293 | 2026-11-20 | Declarative orchestration control plane. |
| [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) | MIT | 31,472 | 2026-11-20 | Batteries-included harness; [deepagentsjs](https://github.com/langchain-ai/deepagentsjs) (MIT, 1,650 ★) for TypeScript. |
| [openclaw/clawhub](https://github.com/openclaw/clawhub) | MIT | 9,557 | 2026-11-20 | Skill + plugin registry. |
| [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | MIT | 53,885 | 2026-11-18 | 5,400+ curated skills. |
| [datahub-project/datahub](https://github.com/datahub-project/datahub) | Apache-2.0 | 13,006 | 2026-11-20 | Catalog/lineage — "context platform for your data and AI stack". |
| [spiffe/spire](https://github.com/spiffe/spire) | Apache-2.0 | 2,630 | 2026-11-19 | Workload identity for the agent process itself. |
| [flowable/flowable-engine](https://github.com/flowable/flowable-engine) | Apache-2.0 | 9,669 | 2026-11-19 | BPM engine — the permissive one. See `verticals/solutions.md`. |
| [camunda/camunda](https://github.com/camunda/camunda) | **Camunda License 1.0** | 4,367 | 2026-11-20 | Now markets itself as "Agentic Orchestration Platform". **Not OSI open source** — details in `verticals/solutions.md`. |

### Renames and moves to fix in existing code — new this pass

| Was | Now | Evidence |
|-----|-----|----------|
| `dbt-labs/dbt-core` | [dbt-labs/dbt](https://github.com/dbt-labs/dbt) | Apache-2.0, 14,192 ★. Old path still serves on `raw.githubusercontent.com` (200) and its README's CI badges point at `/dbt-labs/dbt/actions`; [dbt-fusion](https://github.com/dbt-labs/dbt-fusion) is labelled *"ARCHIVE: code & issue tracking in dbt-core"*. **Pin note: dbt v1 development moved to the `1.latest` branch.** |

### Searched again and still not found

`microsoft/agent-framework` — now 404 on a **third and fourth** channel:
`raw.githubusercontent.com/microsoft/agent-framework/{main,master}/{README.md,LICENSE}`
returns 404 on all four, and `agent-framework in:name user:microsoft` lists 14 repositories,
none canonical. Verified Microsoft-stack substitutes: `microsoft/semantic-kernel` (MIT,
28,790 ★) and [microsoft/agent-framework-go](https://github.com/microsoft/agent-framework-go)
(MIT, 686 ★). **Also checked and rejected:** `solo-io/agentgateway` returns nothing, and
"Aureus ERP", recommended as a permissively licensed ERP by a 2026 vendor roundup, has **no
repository above 0 stars** — the five candidate matches are all personal forks. Fewer real
rows beat padding.

---

## 2026-11-20

Measured by last-push activity and scale on 2026-11-20. All figures from the GitHub
API the same day, not from blog roundups.

| Repo | License | Stars | Why it is moving |
|------|---------|-------|------------------|
| [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,887 | The breakout agent of 2026 and now the largest agent repo by a wide margin. Pushed same-day. |
| [n8n-io/n8n](https://github.com/n8n-io/n8n) | Sustainable Use License | 211,510 | Biggest automation surface in the enterprise, but **fair-code, not OSI** — see `agents/top.md` Tier 2. |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | Open WebUI License | 159,142 | Default self-hosted chat UI; license adds a branding restriction, so not a white-label shortcut. |
| [langgenius/dify](https://github.com/langgenius/dify) | Modified Apache-2.0 | 161,564 | Agentic workflows + RAG in one collaborative plane; modified-Apache conditions apply. |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache-2.0 | 97,264 | The serving layer under most self-hosted enterprise agent stacks. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | Apache-2.0 | 94,475 | Repositioned as an "agent-native database" — RAG engine converging with the agent runtime. |
| [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | MIT | 93,898 | Moved org from `All-Hands-AI` to `OpenHands`; update any pinned remotes. |
| [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | MIT → Apache-2.0 (in transition) | 92,133 | Reference MCP servers; relicensing is under way, declared at the top of `LICENSE`. |
| [aaif-goose/goose](https://github.com/aaif-goose/goose) | Apache-2.0 | 56,815 | Moved under the Linux Foundation's Agentic AI Foundation org this cycle. |
| [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope) | Apache-2.0 | 36,363 | APAC-origin agent framework now at Tier-1 scale, with a JVM sibling. |
| [opensandbox-group/OpenSandbox](https://github.com/opensandbox-group/OpenSandbox) | Apache-2.0 | 17,705 | Sandbox runtime for agents — the isolation layer enterprises need before granting tool access. |
| [IBM/mcp-context-forge](https://github.com/IBM/mcp-context-forge) | Apache-2.0 | 4,867 | MCP/A2A gateway + registry; small but the clearest enterprise MCP control point. |

**Renames and moves to fix in existing code this cycle** — all four verified today:

| Was | Now | Note |
|-----|-----|------|
| `All-Hands-AI/OpenHands` | [OpenHands/OpenHands](https://github.com/OpenHands/OpenHands) | MIT, 93,898 ★ |
| `block/goose` | [aaif-goose/goose](https://github.com/aaif-goose/goose) | Apache-2.0, 56,815 ★ — AAIF governance |
| `NVIDIA/NeMo-Guardrails` | [NVIDIA-NeMo/Guardrails](https://github.com/NVIDIA-NeMo/Guardrails) | Apache-2.0 (per `LICENSE`), 7,537 ★ |
| `Giskard-AI/giskard` | [Giskard-AI/giskard-oss](https://github.com/Giskard-AI/giskard-oss) | Apache-2.0, 5,962 ★ |

**Searched and not found:** `microsoft/agent-framework` (404), and `dbt-labs/dbt-core`
no longer resolves under that path — only `dbt-labs/dbt-core-bundles` (20 ★) surfaced,
so the dbt reference was dropped rather than guessed at.

---

## Historical — 2026-07-02 (automated pipeline snapshot)

> Kept for trend history, deliberately fenced as plain text so the compiler does **not**
> ingest it as entities. Note this legacy file was byte-identical to `agents/trending.md`
> — the old pipeline wrote the same keyword query into both.
>
> **Dead-link audit, 2026-11-20 (second pass):** all 118 `github.com` repository URLs in this
> KB were checked. **117 resolve.** The single dead one is in the block below —
> `Arid-carrotpudding634/Freequick-Suite` now 404s on the search API and on
> `raw.githubusercontent.com` (`main` and `master`). Left in place because this is fenced
> trend *history*, not data, and a decayed row is itself evidence for why the old
> keyword-matching pipeline was retired.

```text
# 📈 Repos trending

> Última actualización: 2026-07-02

| Nombre | Licencia | Descripción | Stars |
|--------|----------|-------------|-------|
| [odoo](https://github.com/odoo/odoo) | NOASSERTION | Odoo. Open Source Apps To Grow Your Business. | 52.8k |
| [bgerp](https://github.com/bgerp/bgerp) | GPL-3.0 | Web-базирана система за управление на бизнеса | 60 |
| [CmsToCommerce](https://github.com/roadynet/CmsToCommerce) | MIT | Symfony Commerce Integration Hub for CMS, Amazon, Shopware, ERP/PIM sync and pro | 0 |
| [Simple-Data-Explorer](https://github.com/ysichov/Simple-Data-Explorer) | MIT | Simple Data Explorer - Multi-windows program for viewing SQL tables and links be | 64 |
| [erpnext](https://github.com/frappe/erpnext) | GPL-3.0 | Free and Open Source Enterprise Resource Planning (ERP) | 36.4k |
| [TunNetCom-SilkRoadErp](https://github.com/TunNetCom/TunNetCom-SilkRoadErp) | MIT | Silk Road ERP offers robust modules for managing your sales and purchasing opera | 24 |
| [india-compliance](https://github.com/resilient-tech/india-compliance) | GPL-3.0 | Simple, yet powerful compliance solutions for Indian businesses | 249 |
| [FARM-ERP-EXCEL](https://github.com/NKAdithya/FARM-ERP-EXCEL) | MIT | Farm ERP System built using Microsoft Excel featuring dashboard analytics, finan | 0 |
| [Freequick-Suite](https://github.com/Arid-carrotpudding634/Freequick-Suite) | ? | Build a Flutter and Firebase food delivery suite with customer, merchant, and ri | 0 |
| [SmartPOS-CRM-AI](https://github.com/RaKa8904/SmartPOS-CRM-AI) | MIT | A full-stack Smart POS + CRM platform with ML-powered customer segmentation, pro | 2 |

---
*Pipeline automático — se actualiza cada hora.*
```
