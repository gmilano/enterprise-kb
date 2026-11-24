---
industry: enterprise
region: Global
updated: 2026-11-24
---

# 📈 Agentes trending — Enterprise

> **APPEND-ONLY.** Newest dated section first; history is kept below it.

## 2026-11-24 — vigesimoquinto pase (latest) — el límite de la contraparte: la capa sí tiene agentes, y el más estrellado de todos está muerto sin decirlo

> Tema: **con quién puede operar el agente.** Veintiséis términos medidos **con límite de palabra**
> sobre **20.810 líneas y 24 pases previos**, y los veintiséis en cero: `sanctions screening` = 0,
> `OFAC` = 0, `SDN list` = 0, `denied party` = 0, `export control` = 0, `dual-use` = 0,
> `OpenSanctions` = 0, `FollowTheMoney` = 0, `yente` = 0, `nomenklatura` = 0, `watchman` = 0,
> `beneficial ownership` = 0, `BODS` = 0, `GLEIF` = 0, `KYB` = 0, `restricted party` = 0,
> `politically exposed` = 0, `Entity List` = 0, `MOFCOM` = 0, `alephdata` = 0, `openaleph` = 0,
> `Archivematica` = 0, `REUSE.toml` = 0, `GNU Free Documentation` = 0, `open-supply-hub` = 0,
> `openownership` = 0.
>
> **El séptimo pase dio para quién actúa el agente; el octavo, qué puede cambiar; el noveno, qué
> puede probar; el décimo, qué puede alcanzar. Este da con quién puede tratar** — y es el primero
> de la serie cuya regla **no la escribe el cliente**, sino listas de terceros que se mueven varias
> veces por semana.

### Lo nuevo de la semana, y es una inversión de método

**El repo más estrellado de toda la capa está muerto y la página no lo dice.**
[alephdata/aleph](https://github.com/alephdata/aleph) — **2.500 ★, MIT, «Public», sin badge de
archivado** — lleva en su README `PROJECT STATUS: SUNSETTING` y la frase de que el mantenimiento
**terminó después de diciembre de 2025** (sin updates, sin fixes, sin soporte desde el 31-12-2025).
Se reescribió como **Aleph Pro**, comercial. Su sucesor abierto,
[openaleph/openaleph](https://github.com/openaleph/openaleph) (MIT, **167 ★**, mantenido por
**DARC**, *soft fork* declarado y compatible con el esquema FtM), tiene **menos de una quinceava
parte de las estrellas del cadáver**.

Durante ocho pases esta KB usó **la bandera `archived`** como el *tell* de un proyecto muerto.
Aquí no hay bandera. **Regla nueva: `archived` es suficiente, no necesaria — hay que leer la línea
de estado del README.** Cualquier ranking de 2026 que ordene esta capa por estrellas recomienda
Aleph, y recomienda mal.

### Las filas nuevas (7 verificadas el 2026-11-24, licencia leída del fichero)

| Repo | Licencia | ★ | Papel |
|---|---|---|---|
| [moov-io/watchman](https://github.com/moov-io/watchman) | Apache-2.0 | 527 | Descarga y parsea **US CSL (con BIS Entity List), OFAC, EU CSL, UK CSL, FinCEN 311**. La única fila con listas oficiales y **sin dueño comercial del dato** |
| [opensanctions/nomenklatura](https://github.com/opensanctions/nomenklatura) | MIT | 274 | Resolución de entidades; aristas **igual / distinto / sin decidir** + inferencia transitiva |
| [opensanctions/yente](https://github.com/opensanctions/yente) | MIT | 189 | API de casado de entidades; **corre on-premise como *KYC appliance*** |
| [openaleph/openaleph](https://github.com/openaleph/openaleph) | MIT | 167 | Búsqueda sobre documentos + datos estructurados, enlazando entidades (DARC) |
| [opensanctions/qarin](https://github.com/opensanctions/qarin) | MIT | 18 | Investigación **financiada por la UE (NGI Search)** sobre **calidad del casado de nombres** |
| [opensanctions/graph](https://github.com/opensanctions/graph) | MIT | — | Datasets adyacentes → FtM; destino del puntero de un repo archivado |
| [opensanctions/yente-client](https://github.com/opensanctions/yente-client) | MIT | — | SDK/CLI cliente de yente |

### El dato que convierte esto en un problema de agentes y no de *compliance*

**La regla del 50 % de OFAC:** una entidad participada en **≥50 % en agregado** por partes
sancionadas **está bloqueada aunque no aparezca en ninguna lista**. El conjunto de contrapartes
prohibidas es **estrictamente mayor** que la unión de las listas publicadas, y la diferencia sólo
se calcula **recorriendo el grafo de titularidad**.

Y el reloj: **la SDN de OFAC se actualiza varias veces por semana, sin calendario fijo**, y la
**BIS Entity List y la SDN más que se duplicaron entre 2020 y el 3T de 2026**. Una decisión de
screening cacheada **caduca en días**, no en trimestres. Eso es diseño de agente —
reverificación, no un *job* nocturno.

### Lo que NO es un agente en esta capa, dicho para que nadie lo busque aquí

`followthemoney` (modelo de datos), `rigour` (limpieza/validación), `countrynames`, `datapatch`,
el estándar **BODS** y las *pipelines* de `openownership`, **GLEIF/LEI** (API CC0 sin
autenticación) y `opensupplyhub/open-supply-hub` (MIT, 23 ★) son **cimientos**, no agentes: están
en `repos/foundations.md` de esta misma fecha, con la frontera de licencia **Apache-2.0 (spec y
*ingesters* UK) vs AGPL-3.0 (*pipelines* y el validador de conformidad)** explicada ahí.

### La trampa de licencia, y es la razón por la que el presupuesto se parte en dos

`opensanctions/opensanctions` (884 ★) lleva badge **MIT** y su `COPYRIGHT.md` parte el repo en
**tres**: código **MIT**, datos **CC BY-NC 4.0** (uso comercial = licencia de pago; el proyecto
reclama **derechos de base de datos**), y material de terceros bajo `datasets/` con **ninguna
licencia concedida y sin índice por fichero de cuáles son**. Es decir: **no hay comprobación
programática** posible de qué se puede redistribuir.

**Consecuencia comercial:** el *KYC appliance* on-premise que ofrece el README de yente es legal
**sólo con licencia de datos**. Dos presupuestos: software permisivo (Globant construye) y datos
(contrato del cliente con un tercero).

### Colisión de nombre, declarada

`counterparty` ya aparecía 4 veces desde el quinto pase, **en otro sentido**: la persona al otro
lado de la pantalla. Aquí es **la entidad comercial del otro lado de la transacción**. Además
`yente` dio 2 falsos positivos (dentro de *contribu**yente***) y `Aleph` otros 2 (**Aleph Alpha**,
el proveedor alemán de modelos). **Un no-cero puede ser falso**: medir con límite de palabra y
leer el *hit* antes de creerlo.

---

## 2026-11-24 — vigesimocuarto pase — el límite de la firma: la capa sí tiene agentes, y lo nuevo de la semana es que el único bien diseñado pone la puerta en el servidor

> Tema: **qué hace que lo que el agente produjo se sostenga.** Veintidós términos medidos en cero
> antes de empezar, sobre **20.141 líneas y 23 pases previos**: `eIDAS` = 0, `PAdES` = 0,
> `CAdES` = 0, `e-signature` = 0, `firma electrónica` = 0, `qualified signature` = 0,
> `RFC 3161` = 0, `sello de tiempo` = 0, `no repudio` = 0, `non-repudiation` = 0,
> `trust list` = 0, `TSP` = 0, `certificate authority` = 0, `C2PA` = 0, `RFC 9421` = 0,
> `Web Bot Auth` = 0, `verifiable credential` = 0, `SD-JWT` = 0, `EUDI` = 0, `mDL` = 0,
> `pyHanko` = 0, `EJBCA` = 0 — y `XAdES` = **2**, `DocuSign` = **4**.
> **El pase noveno dio a esta KB la firma de un *build* (sigstore/SLSA/in-toto: 46, 54 y 44
> apariciones). Firmar un build no es sellar un documento, y en 23 pases nadie preguntó qué prueba
> que el contrato que el agente acaba de redactar vale ante un juez.**
>
> **EL HALLAZGO: UN AGENTE NO PUEDE FIRMAR; SÓLO PUEDE SELLAR.** El Reglamento (UE) 910/2014
> separa la **firma** cualificada —**persona física**, acredita **voluntad**, Art. 25 y ss., **no
> automatizable por definición**— del **sello** cualificado —**persona jurídica**, acredita
> **origen e integridad y no voluntad**, Arts. 35–40, **automatizable: es su caso de uso**—.
> Meter el certificado de firma de una persona en una tubería automática **no es un atajo: es una
> atribución falsa de voluntad**. *(Nivel resumen; y una de las fuentes que lo explica **sitúa mal
> el articulado**, lo etiqueta «Art. 25» en vez de 35–40: la capa se documenta mal incluso donde
> acierta.)*
>
> **LO NUEVO DE LA SEMANA, Y ESTA VEZ SÍ ES UN AGENTE.** Al contrario que la tenencia (pase 22) y
> el remitente (pase 23), **esta capa tiene cuatro agentes reales**, verificados el 2026-11-24 con
> licencia leída byte a byte: `varops/signed-md` (**AGPL-3.0**, 34.020 B, commit **2026-11-24**),
> `imagine-ai-inc/sign` (**MIT**, 1.072 B, 2026-11-16), `hanzoai/sign` (**AGPL-3.0**, 2026-11-21) y
> `signbee/skill` (**MIT**, 1.064 B, 2026-10-31) —que no es un servidor sino una *skill*, y por eso
> **traslada el límite al proveedor en vez de resolverlo**—.
>
> **Y el patrón no es cuántos son, sino dónde ponen la puerta.** El README de `varops/signed-md`,
> **leído en primario (12.754 B)**: *«Your agents handle the paperwork. **People approve and
> sign**»* · *«Only a person approves a template, and an agent can only send the exact revision a
> person saw»* · *«**Guardrails the agent can't talk its way around. These live in the server, not
> in a prompt**»* · *«there is no AI inside Signed.md itself»*. **Eso es el reparto firma/sello del
> Reglamento sin citarlo**: primera vez en 24 pases que esta KB encuentra una herramienta cuyo
> diseño coincide con una obligación jurídica que la herramienta no menciona.
>
> **El reparto cruel de la capa:** **lo que se puede entregar no tiene la puerta, y lo que tiene la
> puerta no se puede entregar.** La pieza permisiva (`imagine-ai-inc/sign`, MIT) es la proponible y
> **no** documenta puerta humana; la que la tiene es **AGPL-3.0**, que alcanza al servicio en red.
> Se copia el **diseño**, no el código (Receta 49).
>
> **CORRECCIÓN QUE SE APUNTA CONTRA UNO MISMO (T96).** El resumen de búsqueda de este pase afirmó
> que *«none of these projects documents a human-approval gate»*. **El byte a byte dice lo
> contrario**, y de haber creído al resumen este pase habría descartado **el único proyecto bien
> diseñado de la capa**. **La afirmación negativa de un resumen no es un cero medido.**
>
> **La tercera firma, que es otro acto y conviene no confundir:** `cloudflare/web-bot-auth`
> (**Apache-2.0**, commit **2026-11-24**) hace que el agente firme **cada petición HTTP** con
> **RFC 9421** (Ed25519 por agente, cabecera `Signature-Agent`, directorio en
> `/.well-known/http-message-signatures-directory`). **RFC 9421 es un RFC; Web Bot Auth no lo es**
> —grupo IETF constituido en 2026 y **sin documentos adoptados a agosto**, así que un RFC es cosa
> de 2027 como muy pronto—. **Establece identidad, no permiso** (el permiso es el pase 7). Visa
> **TAP** y Mastercard **Agent Pay** lo usan como capa de autenticación *(secundario)*.
> **Esta KB ya sabe distinguir tres firmas: un *build* (pase 9), una *petición* (este pase) y un
> *documento* (este pase). Las tres se llaman «firma» en una reunión.**
>
> **Trampa de la semana, decimoséptima de la serie:** `Sphereon-Opensource/eidas-signature-client`
> es la **primera recomendación** de la búsqueda de bibliotecas eIDAS y **no recibe un commit desde
> el 2024-04-09** (19 meses), con **LGPL-3.0**. El delator es el de siempre: lo recomienda la
> documentación adyacente al propio ecosistema.
>
> **Límite del instrumento, declarado:** en esta sesión `api.github.com` **y** `github.com` dan
> **403**, así que **no hay ni una estrella ni una bandera `archived` en este pase** y no se finge
> que las haya. Este pase **no puede distinguir «archivado» de «parado»** y por eso dice siempre
> **«sin commit desde X»**.

## 2026-11-24 — vigesimotercer pase — el límite del remitente: la novedad de la semana es que la implementación de referencia no se ha movido desde 2024

> Tema: **con qué dominio firma el agente.** Catorce términos medidos en cero antes de empezar,
> sobre **19.436 líneas y 22 pases previos**: `DMARC` = 0, `DKIM` = 0, `SPF` = 0, `ARC` = 0,
> `BIMI` = 0, `MTA-STS` = 0, `SMTP` = 0, `IMAP` = 0, `phishing` = 0, `suplantación` = 0,
> `rebote`/`bounce` = 0, `unsubscribe` = 0, `buzón` = 0, `correo electrónico` = 0 —
> y `remitente` = **1**, que era de **voz** (la pre-declaración de CLI de TRAI del pase veintiuno).
> **El pase veintiuno dio a esta KB el canal hablado; el canal escrito nunca se hizo.**
>
> **Lo nuevo de la semana en esta capa no es un agente: es una fecha de push.**
> `trusteddomainproject/OpenARC` —la implementación de referencia de **ARC**, el mecanismo que hace
> que el correo reenviado y las listas sobrevivan a DMARC— **no recibe un commit desde el
> 2024-04-19**, tiene **150 ★** (el más estrellado de los tres hermanos del Trusted Domain Project)
> y **no está archivada**, así que la forja la muestra viva. Al lado: `OpenDKIM` sigue en
> **`2.11.0~beta2`** y `OpenDMARC` en **1.4.2 desde 2021** (*ambos secundarios*).
> **Mientras tanto el estándar se reescribió**: DMARCbis salió el **2026-05-19** como **RFC 9989**
> (deja obsoletos el **RFC 7489** y el **RFC 9091**), con **RFC 9990** y **RFC 9991**, y **eliminó
> `pct`** en favor de un indicador binario `t=`. *El estándar es de mayo de 2026; el código que lo
> ejecuta, de antes.*
>
> **Agentes reales encontrados: 2. Manos de buzón encontradas: 2, y las dos están muertas o
> paradas.** `Mail-0/Zero` (**MIT**, 10.900 ★, push 2026-11-15) y `elie222/inbox-zero`
> (**AGPL-3.0** leída byte a byte en 36.236 B, 13.112 ★) son los únicos agentes de correo con IA
> de peso; el servidor MCP de Gmail más recomendado de los listados,
> `GongRzhe/Gmail-MCP-Server` (**MIT**, 1.173 ★), está **ARCHIVADO** desde el 2025-08-06
> —**decimosexto archivado-pero-recomendado de esta KB**— y su alternativa,
> `MarkusPfundstein/mcp-gsuite` (**MIT**, 492 ★), lleva **19 meses sin un commit** sin estar
> archivada. **La capa tiene infraestructura viva y manos agénticas muertas.**
>
> **La trampa de la semana, y es la biblioteca de envío más usada del mundo.**
> `nodemailer/nodemailer` (**17.717 ★**) trae un `LICENSE` de 935 B que es un **MIT truncado**:
> promete *«subject to the following conditions:»* y **no enumera ninguna condición**. El registro
> resuelve lo que el fichero no puede: `registry.npmjs.org/nodemailer/latest` → **v10.6.1,
> `license: "MIT-0"`**. **Clase de licencia nº 19 de esta KB.** Y en el otro extremo del tamaño,
> `stalwartlabs/stalwart` (**16.280 ★**) **no tiene fichero de licencia en absoluto** —8 rutas
> canónicas, 8 respuestas 404, y ningún campo `license` en su `Cargo.toml`—: su AGPL-3.0 vive en
> **una insignia del README**, que también declara que **multi-tenencia y aprovisionamiento SCIM
> son de la edición Enterprise**.

## 2026-11-24 — vigesimosegundo pase — el límite de la tenencia: una capa entera sin un solo agente dentro

> Tema: **de quién es la respuesta.** Diez términos medidos en cero (o casi) antes de empezar:
> `tenancy` = 0, `BYOK` = 0, `tenant_id` = 0, `row level security` = 0, `Kafka` = 0,
> `nats-io` = 0, `automq` = 0, `redpanda` = 0, `multi-tenant` = 1, `pulsar` = 1 — **sobre 21
> pases previos de esta KB**. La novedad de la semana en esta capa **no es un agente nuevo**:
> es que la capa no tiene agentes. Diez repos verificados el 2026-11-24, **cero son agentes**.
>
> **Lo que sí se mueve esta semana, y es de licencias, no de código:**
> - **`p2-inc/keycloak-orgs` (546 ★) es Elastic License 2.0**, leído byte a byte de su `COPYING`.
>   Su propio README: *«We've changed the license of our core extensions from the AGPL v3 to the
>   Elastic License v2»* — **AGPL-3.0 → ELv2**, sin pasar por permisiva, mientras sigue hablando
>   de *«making its core extensions open source»*. **Octava trampa «recomendado por documentación
>   adyacente al proyecto»** de esta rotación.
> - **`weaviate/weaviate` (17,0k ★) partió su licencia dentro del repo el 26 de agosto de 2026**
>   (fecha leída de `wl/LICENSE-WEAVIATE`): BSD-3-Clause fuera de `wl/`, *all rights reserved* +
>   clave de licencia dentro. GitHub sigue mostrando la insignia **«BSD-3-Clause»** a secas.
>   **Medido, no supuesto:** `wl/` son **29 ficheros** y el límite entre inquilinos **no** está
>   ahí — 84 ficheros con `tenant` en la ruta y 147 con `namespace` están **fuera**, incluido
>   `adapters/handlers/mcp/read/tenants.go`. Lo de pago es **operar** muchos inquilinos
>   (suspender, rebalancear, deduplicar backups, auto-recuperar, expirar credenciales).
> - **`redpanda-data/redpanda` (12,7k ★) tiene tres nombres de licencia y ninguno es permisivo**:
>   `licenses/bsl.md` (BSL 1.1) + `licenses/rcl.md` (Redpanda Community License) en la rama `dev`,
>   y un README que nombra una *«Redpanda Community Edition License»* **cuyo texto no está en el
>   repositorio**. Sin `LICENSE` en la raíz → **sin insignia en GitHub**.
> - **El sustituto permisivo existe y está verificado: `AutoMQ/automq` (10,9k ★, Apache-2.0** leído
>   byte a byte en `LICENSE` **y** `NOTICE`, cero menciones a BSL), API de Kafka sobre S3.
>   `NOTICE`: *Copyright 2023-2025, AutoMQ HK Limited* → **origen APAC verificado por licencia.**
>
> **Incidente de la ventana (fuente secundaria, página no verificable en esta sesión):** se
> reporta que **155 respuestas** del modelo GLM-5.3 en **Cloudflare Workers AI** contenían
> información de *otros* clientes entre el **2026-08-27 y el 2026-09-09**, investigado por
> Knostic. Un episodio atribuido a la API de Claude el 2026-06-05 aparece en una sola fuente y
> **está explícitamente sin confirmar**; se registra como no confirmado, no como hecho.

## 2026-11-24 — vigesimoprimer pase — el límite de la voz: el agente que habla, y la licencia que ningún listado de 2026 menciona

> Tema: **cuando el agente atiende el teléfono.** Veintiocho términos medidos en cero antes de
> empezar (`livekit`, `pipecat`, `asterisk`, `freeswitch`, `jambonz`, `vocode`, `whisper`, `piper`,
> `coqui`, `kokoro`, `silero`, `speech`, `telephony`, `contact centre`, `TTS`, `SIP`, `WebRTC`,
> `diarization`, `barge-in`, `robocall`, `TCPA`…). **Ninguno aparecía tras veinte pases de
> frontera.** Los únicos aciertos de `voice` en los ocho ficheros eran subcadenas de **`invoice`**.
> El canal por el que la mayoría de las empresas atiende a sus clientes no estaba en la KB.

**Las cinco filas reales de agente de voz** (licencia leída byte a byte el 2026-11-24):
[pipecat-ai/pipecat](https://github.com/pipecat-ai/pipecat) (**BSD-2-Clause**, 17,400 ★ — primera
BSD-2 de esta KB),
[livekit/agents](https://github.com/livekit/agents) (Apache-2.0, 15,300 ★),
[kyutai-labs/unmute](https://github.com/kyutai-labs/unmute) (MIT),
[vocodedev/vocode-core](https://github.com/vocodedev/vocode-core) (MIT, 3,800 ★) y
[openai/openai-realtime-agents](https://github.com/openai/openai-realtime-agents) (MIT).

### El hallazgo de licencia del pase, y es el peor que esta KB ha encontrado *para un integrador*

[TEN-framework/ten-framework](https://github.com/TEN-framework/ten-framework) (11,200 ★) aparece en
al menos tres comparativas de 2026 como «Apache-2.0, open-source voice agent framework», **sin
salvedad**. Su fichero `LICENSE` pesa **2,234 B** y dice «Apache License v2.0 … **with the following
additional conditions**» (© 2025 Agora):

- cláusula **1(i)**: prohíbe alojarlo «on any **End User devices**, including … **mobile terminal
  devices**» → **prohíbe la voz en el móvil**;
- cláusula **1(ii)**: prohíbe desplegarlo de forma que «**allows others to compete** with Agora's
  offerings, **including without limitation enabling any third party to develop or deploy
  Applications**»;
- cláusula **2**: sólo se puede desplegar «**solely for your benefit** and the benefit of your
  **direct** End Users».

Dify, Camunda y Mattermost restringían *revender el producto*. Esta cláusula restringe **el modelo
de negocio de un estudio**: construir un agente de voz *para un cliente* es, en la letra de 1(ii),
habilitar a un tercero. **No es base para trabajo de cliente.** Tier 2, y hay que decirlo en la
semana 0.

### Instrumento nuevo, reutilizable por toda la flota

**El enlace «License» de la barra lateral de GitHub *sin nombre SPDX* es el delator de una licencia
modificada**, y el **tamaño en bytes** es el segundo delator: **Apache-2.0 íntegra pesa ~11,3 kB**.
Medido en el mismo pase: `livekit/agents` → «Apache-2.0 license», 11,356 B (real);
`pipecat-ai/pipecat` → «BSD-2-Clause», 1,300 B (real); `ten-framework` → **«License»** sin tipo,
2,234 B (modificada). Es la **inversa complementaria** de la regla `NOASSERTION` del sexto pase:
allí la ausencia de veredicto escondía licencias *permisivas*; aquí esconde una *restrictiva*. La
ausencia de nombre SPDX **no informa en ninguna dirección** — obliga a leer, y en ambos sentidos.

### Tres trampas de mantenimiento, y las tres son de una especie distinta

| Proyecto | ★ | Lo que muestra GitHub | La realidad leída |
|---|---|---|---|
| [rhasspy/piper](https://github.com/rhasspy/piper) | 11,300 | **«Public archive … archived by the owner on Oct 6, 2025»** | MIT, congelado, y el README apunta al sucesor **[OHF-Voice/piper1-gpl](https://github.com/OHF-Voice/piper1-gpl)**, que es **GPL-3.0** |
| [resemble-ai/chatterbox](https://github.com/resemble-ai/chatterbox) | 28,100 | **Sin banner de archivado** | El README dice «**As of August 2026, Chatterbox is retired research and is no longer maintained**» |
| [coqui-ai/TTS](https://github.com/coqui-ai/TTS) | 46,300 | **Sin banner y sin puntero a fork** | MPL-2.0; el fork mantenido es [idiap/coqui-ai-TTS](https://github.com/idiap/coqui-ai-TTS) y el original no lo menciona |

**Es el octavo proyecto archivado-pero-estrellado de esta KB, y añade dos especies nuevas al
catálogo.** Hasta ahora el patrón era «archivado y recomendado por su propia documentación». Las dos
nuevas son peores porque **ninguna herramienta automática las detecta**: *retirado sin archivar*
(el campo `archived` es `false`, sólo lo dice el README en prosa) y *huérfano sin puntero* (46,3k
estrellas, empresa desaparecida, cero señal en el repositorio). Y Piper añade un tercer eje que la
KB no tenía: **el sucesor cambió la licencia**. La elección no es «mantenido o no»; es **MIT
archivado o GPL-3.0 mantenido**, y eso es una decisión de contrato, no de ingeniería.

### Una trampa fresca

[fishaudio/fish-speech](https://github.com/fishaudio/fish-speech) no es código abierto: su
**«FISH AUDIO COMMUNITY LICENSE AGREEMENT» v1.0 está fechada el 2026-10-13** (hace seis semanas),
limita el uso comercial a un umbral de ingresos y exige acuerdo escrito aparte para cualquier
*Hosted Service*.

### Lo que el pase *no* pudo medir, y por qué es la mitad del hallazgo

`huggingface.co` está **rechazado por el proxy de egreso** (`connect_rejected`, 403), y
`api.github.com`/`gh api`/`curl https://github.com` están **denegados por el alcance de sesión**.
Funcionan `raw.githubusercontent.com` (leer `LICENSE`), `git ls-remote` (existencia) y `WebFetch`
sobre el HTML de GitHub (estrellas, banner). Consecuencia que hay que escribir, no callar: **la
licencia del código de este pase es de primera mano; la de los *pesos* no lo es.** Y en voz **el
peso es el entregable** — la voz que sale por el teléfono del cliente. Primera vez que esta KB
necesita **dos columnas de licencia en la misma fila**: [kyutai-labs/moshi](https://github.com/kyutai-labs/moshi)
tiene código MIT + Apache-2.0 (ambos ficheros presentes, verificados) y **pesos CC-BY-4.0 según su
README** — atribución obligatoria en el producto del cliente, y **sin concesión de patentes**,
porque CC-BY no es Apache.

## 2026-11-24 — vigésimo pase — el límite del ciclo de vida: la identidad huérfana está en el esquema, no en el descuido

> Tema: **qué pasa con el agente cuando la persona que lo creó se va.** Trece términos
> medidos en cero antes de empezar (`SCIM`, `IGA`, `non-human identity`, `offboarding`,
> `decommission`, `provisioning`, `RPO`, `RTO`, `backup`, `disaster recovery`, `velero`,
> `restic`, `SailPoint`). No era una capa infrarrepresentada: **no estaba**. 24 repos
> verificados hoy, **ninguno es un agente** — quinta vez que el hallazgo es que las filas de
> agente no se mueven.

**Lo que sí pertenece a este archivo: la primera clase `Agent` que esta KB encuentra dentro de
un proveedor de identidad.** `authentik/enterprise/agents/models.py` (licencia **EE**, no MIT)
define al agente como cuenta de servicio con humano padre, token de API, contraseña
deshabilitada y caducidad propia. Y la decisión que hay que tomar en la semana 1 de un
engagement tiene tres valores y un nombre, `ActorPolicyInheritance`, en la parte **MIT**:

- `MIRROR` — defiere al padre en vivo, el agente **nunca excede** al humano; a cambio **acopla**
  los ciclos de vida, que es lo contrario de lo que piden los tenets del NIST.
- `COPY` — instantánea al crear. Falla en **dos direcciones**: el acceso que el humano tiene por
  **grupos no se copia** (infra-aprovisionamiento el día 1) y las asignaciones directas quedan
  **congeladas** (sobre-aprovisionamiento el día 100, cuando al humano ya se le revocó).
- `NONE` — no hereda; todo a mano.

**Y la línea que lo explica todo**, en `authentik/core/models.py`, MIT:
`parent = models.ForeignKey(User, on_delete=models.SET_DEFAULT, default=None, ...)`. Al borrar al
humano, **el vínculo se pone a NULL y el agente sobrevive**. La identidad huérfana está en el
esquema. Es OWASP **NHI1** demostrado en una línea.

**Confirmado en fuente primaria (el repo de OWASP, no un blog):** el árbol de
`OWASP/www-project-non-human-identities-top-10` tiene `2025/docs/1-improper-offboarding.md` …
`10-human-use-of-nhi.md`. **Improper Offboarding es el NHI1**, con *Detectability: Hard*. Y solo
existe el directorio `2025/` (último commit 2026-07-27): **no hay edición 2026**.

**Dos herramientas de inventario, ambas MIT:** el componente `agent-discovery` de
`microsoft/agent-governance-toolkit` (un repo que esta KB tenía desde el pase 8 **sin nombrar
nunca este componente**) y `Defend-AI-Tech-Inc/agent-discover-scanner` (23 estrellas, dormido
desde julio, se autodescribe "industry-standard"). Su README deja la frase que va en la
propuesta: *"you can't govern what you can't see."*

## 2026-11-24 — decimonoveno pase — el límite del sistema heredado: la reachability la decide una API vieja, no la edad del sistema

> Tema: **el sistema de registro que el cliente ya tiene corriendo.** Los dieciocho pases
> anteriores buscaron con vocabulario de cosas nuevas (frameworks, gateways, authz, OSCAL,
> observabilidad, consumo, idioma, documento fiscal, calendario). Ninguno buscó con el vocabulario
> de lo que el cliente **ya opera**. Verificado hoy sobre las 524 direcciones que ya tenía esta KB:
> `cobol`, `jcl`, `abap`, `as400`, `odata`, `idoc`, `zowe`, `abaplint`, `abapgit`, `openrewrite`,
> `tree-sitter` → **cero archivos**. Un agujero de 524 repos de ancho.

**El hallazgo que ordena el pase, medido no opinado.** La capa de acceso agéntico a un estate
heredado existe **solo donde el estate ya exponía una API remota antes de que existieran los
agentes**:

| Estate | API preexistente | Servidores MCP abiertos hallados | Tope de estrellas |
|---|---|---|---|
| SAP ABAP (ECC / S/4HANA) | ADT sobre HTTP | **4**, todos MIT/Apache-2.0 | 215★ |
| IBM i / Db2 for i | Mapepire | **1**, MIT | 30★ |
| IBM Z / z/OS | Zowe REST (z/OSMF) | **1**, EPL-2.0 | 25★ |

Siete filas nuevas en `agents/top.md`, todas con licencia leída y actividad medida el 2026-11-24:

- **`Azure-Samples/Legacy-Modernization-Agents`** — MIT, **234★**, push 2026-11-22. **Renombrado a
  "Project Starforge"** (URL del repo sin cambios). COBOL+copybooks+BMS+JCL → Java Quarkus/Spring o
  C#. Construye el grafo del estate en Neo4j **determinísticamente desde el fuente, sin llamadas al
  modelo**; el modelo solo convierte. Su AST Explorer trata los *parse gaps* como **riesgo de
  verificación**.
- **`mario-andreschak/mcp-abap-abap-adt-api`** — MIT, **215★**, push 2026-09-16.
- **`fr0ster/mcp-abap-adt`** — Apache-2.0, **111★**, push 2026-11-24 (hoy). BTP + on-premise,
  **CRUD completo**, JWT/XSUAA.
- **`marianfoo/abap-mcp-server`** — Apache-2.0, **99★**, push 2026-11-20.
- **`abap-ai/mcp`** — MIT, **88★**, push 2026-07-19. SDK para escribir el servidor MCP **dentro**
  de ABAP: la única fila que no exige un proceso fuera del sistema SAP.
- **`Strom-Capital/mcp-server-db2i`** — MIT, **30★**, push 2026-11-23. **Solo lectura**, login con
  el usuario IBM i de cada persona, allowlist de bibliotecas, enmascarado de columnas.
- **`zowe/zowe-mcp`** — **EPL-2.0**, **25★**, push 2026-11-24. El único del lado z/OS.

**Ceros medidos (no silencios).** `cobol modernization AI agent` = **un** proyecto con tracción y
una cola de POCs de ≤8★; `jcl parser mainframe` = 1★ y 1★; `rpgle language server` = **0**;
`natural adabas software ag parser` = **0**; `smojol` = **0** con este instrumento;
`cobol modernizacion legado` = **0**, `cobol analisis banco espanol` = **0**,
`mainframe modernizacao cobol` = 3 repos **todos de 0★ y sin licencia**.

**Trampa nueva de clase propia: el cluster de forks que gana al upstream en el buscador.** La
búsqueda web de "COBOL to Java AI agent" devuelve **seis** repos con el mismo README por encima del
original (`gkaleta/`, `shinya-ambient/`, `aplusdepseudo/`, `vjrithwik/`, `josh202310/`,
`renehonig/Legacy-Modernization-Agents`). Detector reutilizable: `search/repositories` **excluye
forks por defecto**, así que resolver con `git ls-remote` y **no** aparecer en una consulta `repo:`
prueba que es un fork.

**Lo que esto cambia para una propuesta.** La capa determinística de mainframe está madura y es
Apache-2.0/EPL-2.0; la capa agéntica encima está **vacía salvo un sample de Microsoft de 234★**. El
primer entregable vendible no es la conversión: es el **inventario y la extracción de reglas de
negocio** construidos sin modelo, que es exactamente lo que ISG reporta que ya compra el sector
público de EE. UU. (ver `intel/market.md`).

## 2026-11-24 — decimoctavo pase — el límite del calendario: el instante lo calcula una cadena de cinco eslabones, y en 2026 uno mintió a propósito

> Tema: **cuándo vence algo, en la hora de quién y en los días laborables de quién.** Los diecisiete
> pases anteriores cubrieron ocho límites —lectura, escritura, procedencia, contención, borrado,
> accesibilidad, pesos, idioma—, el consumo y el documento fiscal. El pase diecisiete encontró
> **plazos** (India: **30 días** al IRP; las fechas de KSeF; los catálogos CFDI 2026). Este pase midió
> si la KB podía **calcularlos** y la respuesta fue no. Medido antes de buscar, sobre los nueve
> archivos: `tzdata` **0** · `IANA` **0** · `ISO 8601` **0** · `calendario` **0** · `día hábil` **0** ·
> `business day` **0** · `business hours` **0** · `festivo` **0** · `cron` **0** · `RFC 5545` **0** ·
> `rrule` **0** · `CalDAV` **0** · `day count` **0** · `30/360` **0** · `holiday` **1** · `DST` **1**.
> **La KB tenía los vencimientos y no tenía el calendario con el que se cuentan.**

**Nuevo en la capa de agentes (1 fila real, y el cero se publica igual):**

- **`modelcontextprotocol/servers` → `src/time`** (`mcp-server-time`) — **MIT**, declarada en
  `pyproject.toml` como `license = { text = "MIT" }` (leído por bytes), versión **`2026.11.18`**
  —seis días— y `mcp>=2.3,<3`. Tres herramientas: `get_current_time`, `convert_time` y
  **`get_time_ago`**. Es el **único** elemento con forma de agente en toda la capa, y es un servidor
  de referencia, no un producto.

**Las dos frases de su README que deciden una integración, citadas:** «*The offset is elapsed time,
counted back from the current instant, so across a daylight-saving change "a day ago" is exactly 24
hours ago and its wall-clock reading can differ from now by an hour*» —**«hace un día» son 24 horas,
no «ayer a esta hora»**, y el servidor lo documenta porque son cosas distintas— y «*A timezone name
… must be an exact IANA key, case included: `Europe/Warsaw` is accepted and `europe/warsaw` is
rejected on every platform, including macOS, whose case-insensitive filesystem would otherwise
resolve it*». **Un LLM que normaliza a minúsculas el nombre de la zona recibe un error**, y una
implementación ingenua en macOS lo habría aceptado en silencio.

**EL HALLAZGO DEL PASE, LEÍDO EN EL `NEWS` DE `eggert/tz` (266 065 B, el repositorio aguas arriba del
propio tzdb): LA BASE DE DATOS HORARIA ENVIÓ A PROPÓSITO DATOS QUE CONTRADICEN LA LEY.** Cuatro
jurisdicciones canadienses fijaron su reloj de forma permanente en 2026 y en los cuatro casos tzdb
**modeló la transición el 2026-11-01 a las 02:00 en lugar de la fecha legal**: Columbia Británica
(legal **2026-03-09**, release **2026b**), Alberta (legal **2026-06-18**, **2026c**), Territorios del
Noroeste (legal **2026-08-21**, **2026d**, solo `America/Inuvik`) y Manitoba (legal **2026-10-31**,
**2026e**). El motivo está escrito: «*This temporary hack works around limitations in Unicode CLDR
and ICU*» —CLDR **48** (2025-10-29), **48.1** (2026-01-08), **48.2.1** (2026-07-08), **48.2.2**
(2026-09-21) e ICU **78** (2025-10-30), **78.2**, **78.3** (2026-03-17)—. **El dato autoritativo se
dobló para acomodar a un consumidor aguas abajo.**

**Y el parche se rompió a sí mismo.** La nota `NOTE FOR 2026 TEMPORARY HACK FOR CLDR AND CANADA` dice
que el apaño «*causes zic in tzcode **2023d through 2026a**, in the default **slim** mode, to generate
a TZif file that does not conform to Internet RFC 9636 §3.3*», y que ese archivo «*causes some TZif
readers, **including tzcode itself**, to ignore America/Vancouver's 2026-11-01 02:00 transition from
PDT (tm_isdst=1) to MST (tm_isdst=0)*». El remedio documentado es **`zic -b fat`**. Los mismos apaños
esquivan además un fallo de `libstdc++ std::chrono` en **GCC 14.1-14.4, 15.1-15.2 y 16.1** (**GCC bug
124851**), corregido en **GCC 16.2**.

**Límite del daño, declarado por los propios mantenedores y por eso citable ante un cliente:** «*It
does not affect UT offsets, and affects abbreviations and tm_isdst flags only*». **Un agente que solo
hace aritmética de instantes está a salvo; uno que muestra la abreviatura o ramifica sobre `isdst` no.**

**El apaño ya se está retirando** y la condición es una versión: el bloque `Unreleased` restituye las
fechas legales porque **CLDR 49 (2026-10-22)** lo corrigió, y añade que «*users need CLDR 49+ anyway
for timestamps starting on 11-01*». **El suelo de dependencia tiene un mes.**

**Cuatro aciertos de calendario civil de 2026, todos de fuente primaria y fechados:** **2026f**
(2026-10-27) — **Cuba no retrasa el reloj el 2026-11-01 y se queda en -04 hasta el 2027-11-07**— y,
en la misma release, **se acabaron los segundos intercalares**: «*No more leap seconds, and leap
second tables no longer expire*», `zic` ignora las líneas `Expires` y `localtime.c` baja de 49 a 27.
**2026c** — **Marruecos a +00 permanente el 2026-09-20**. **2026a** (2026-03-01) — Moldavia usa
horarios de transición de la UE desde 2022. **Unreleased** — **Groenlandia retrasa dos horas el
2027-10-31** para pasar de -02/-01 a -03/-02.

**Corrección de método, y es una enseñanza reutilizable por toda la flota.** El resumen de búsqueda
atribuyó a la release **2026c** el fin del horario de verano en **Samoa** y el cambio de Jordania.
Comprobado contra el archivo primario con `awk`, ambos son de la release **2021b (2021-09-24)**:
**cinco años de error de atribución**. Paraguay (-03 permanente) es de **2025a** e Irán (sin DST
desde 2022) de **2022b**. **Un resumen de búsqueda sabe los hechos y no sabe las versiones, y en esta
capa la versión *es* el hecho.**

## 2026-11-24 — decimoséptimo pase — el límite del documento fiscal: el agente no puede ser el emisor

> Tema: **lo que el agente puede emitir en nombre del Estado.** Ocho límites anteriores los decidía
> quien construye el sistema; este lo decide una autoridad tributaria. Medido antes de buscar, sobre
> los nueve archivos y en los dos idiomas: `Peppol` **0** · `AS4` **0** · `EN 16931` **0** ·
> `Factur-X` **0** · `ZUGFeRD` **0** · `Schematron` **0** · `CFDI` **0** · `NF-e` **0** ·
> `Verifactu` **0** · `KSeF` **0** · `FatturaPA` **0** · `ViDA` **0** · `SAF-T` **0** · `X12` **0**.
> **No fue cero limpio** y el residuo define el hueco: `facturacion` **25** y `e-invoic` **5**
> estaban desde el pase once — la KB tenía los **módulos de localización fiscal** de LATAM y no tenía
> **ni el formato, ni el validador, ni el transporte, ni el modelo de autorización**.

**Nuevo en la capa de agentes (4 filas, todas verificadas 2026-11-24):**

- **`techtemplemy/mcp-myinvois`** — **WTFPL**, **3★**, push 2026-09-05. Servidor **MCP** con
  ficheros `SKILL.md` para el régimen e-Invoice de Malasia (LHDN), *sandbox* por defecto y aviso
  explícito de no oficialidad. **Clase de licencia nº 15 de esta KB y la más problemática hasta la
  fecha**: permisiva en intención, **sin renuncia de garantía ni concesión de patentes**, no
  certificada por OSI. Se registra como **documentación ejecutable del flujo**, no como dependencia.
- **`giansalex/lycet`** — **MIT**, **106★**, push 2026-11-10. API REST sobre Greenter (SUNAT 🇵🇪):
  la manera de dar al agente **una herramienta fiscal determinista** en vez de una librería.
- **`einvoice-validator/einvoice-validator`** — **código MIT**, binario
  `MIT AND EUPL-1.2 AND LicenseRef-OASIS… AND LicenseRef-UN-CEFACT… AND W3C-19980720`, **1★**,
  push 2026-11-23. La **puerta de validación determinista** que el agente invoca. **Sin superficie
  MCP** (medido: 0 coincidencias de `mcp` en todo el repo) — se llama como proceso.
- **`invoice-x/invoice2data`** — **MIT**, **2 254★**, push **2026-11-24**. Extracción por plantillas,
  la capa anterior al documento estructurado.

**El cero que vale más que las cuatro filas.** No apareció **ningún agente open source específico de
cuentas por pagar o facturación electrónica**. Esa casilla es comercial (Basware InvoiceAI y su
*Supplier Agent* de feb-2026, Coupa↔Rossum may-2026, Tipalti, Stampli, Vic.ai, AppZen, Ramp).
⚠️ *Secundario: snippets, no verificado en primario.* **Lo abierto de este plano son las primitivas
de cumplimiento; el agente es la parte que se construye.**

**La restricción de diseño del plano, y contradice el reflejo habitual de los agentes.** El agente
**no puede ser el emisor**: MyInvois (*guideline* v4.8, ago-2026) exige firma digital del emisor o
de su proveedor acreditado; India impone **30 días** de ventana de reporte al IRP para
AATO ≥ ₹10 crore —de modo que **encolar y reintentar puede invalidar el documento para siempre**—;
y en los regímenes de **autorización previa** de LATAM un reintento **no es idempotente**: puede
crear un **segundo documento fiscal**. Idempotencia a nivel de **serie y número de documento**,
nunca a nivel de HTTP. ⚠️ *Las tres obligaciones, de fuente secundaria.*

**Hallazgo probado byte a byte, y es el del pase.** Los dos conjuntos **oficiales** de artefactos
EN 16931 (CEN/TC 434, versión **1.3.17**) **no validan igual**: `BR-CO-17` usa `<` en UBL y `<=` en
CII —una factura desviada **exactamente 1,00** pasa en CII y falla en UBL— y `BR-S-08` tiene
**tolerancia ±1** en UBL frente a **igualdad estricta** en CII. Una conversión UBL↔CII fiel **puede
invertir la validez sin tocar un número**. Detalle en `intel/trends.md` (tendencia 34).


## 2026-11-24 — sixteenth pass — the language boundary: three agent rows, and a metric that inverts

> Theme: **what the agent *says*, in which language, and who approved the wording.** Measured before
> searching, across all nine files and both of the KB's languages: **28 of 30 terms at a clean zero**
> — `weblate` 0 · `pontoon` 0 · `tolgee` 0 · `messageformat` 0 · `glossary` 0 · `terminolog` 0 ·
> `XLIFF` 0 · `sacrebleu` 0 · `COMET` 0 · `fasttext` 0 · `IndicTrans` 0 · `Bill 96` 0 ·
> `Eighth Schedule` 0. The two non-zero hits are the exact shape of the blind spot: `lingua` **1**
> (the *description* of a sovereign base model the KB already held) and `DPDP` **10** — India's
> statute was in this KB as a **privacy** instrument, with its **§5(3) language duty absent**. The
> KB had read the law and kept only the half that matched the pass it was running.

**New in the agent layer this week (3 rows, all verified 2026-11-24):**

- **`lingodotdev/lingo.dev`** — **Apache-2.0**, **5,397★**, push **2026-11-20**. Localisation
  engineering agent: extracts strings, translates, opens the PR. Config takes **your own model**
  (`model: "anthropic/claude-sonnet-4.5"`), so the translating step is BYO-key — the one row here
  that fits a client CI pipeline. Licence lives in **`LICENSE.md`**; the root `readme.md` is a
  **22-byte pointer file**, so a naive README fetch returns nothing.
- **`andrewyng/translation-agent`** — **MIT**, **5,817★**, push **2024-08-04**. The reflection loop:
  translate → self-critique → apply critique. **Two years stale — a pattern to copy, not a
  dependency to install.**
- **`SakuraLLM/SakuraLLM`** — **GPL-3.0**, **4,865★**, push 2026-07-23. APAC-origin JP→ZH
  translation LLM. **Recorded, not recommended**: copyleft, and the domain is light novels.

**Three rows, not five, and that is the finding.** This is the **fourth boundary in this KB that
turns out to be a component layer rather than an agent layer** (after containment, erasure and
consumption). The work here is done by a TMS, a message format, an engine, an evaluator and a
language detector — none of them agents. They are in `repos/foundations.md`; padding this file with
them would have produced five unusable rows.

**The strongest agentic result in the layer has no repository.** **AIDAterm** (ACL 2026, Industry
Track) is a four-agent pipeline — Analysis → Translation → Post-editing → Review — reporting
**99.4% terminology accuracy on WMT25**, which its authors say beat **all 20 submitted systems**.
No repo surfaced, so it is recorded as a **reproducible design** (Receta 30), not an inventory row.

**The sentence that should change an acceptance criterion**, from `translation-agent`'s own README:
translations its **human raters preferred** scored **lower on BLEU**. So BLEU can invert on exactly
the agentic pipelines this KB recommends — an SOW with "BLEU ≥ X" can reject the better system.
Rank with **COMET**/reference-free QE; keep sacreBLEU as a regression tripwire only. The benchmark
named in that sentence, **FLORES**, is **archived since 2023-11-20** with 770★.

**Trap carried over from the seventh pass, repeated exactly.** **Tolgee** was described by an
aggregator this pass as *"self-hosting is fully open-source"*. Its root `LICENSE` is a multi-licence
declaration: everything under **`ee/`** is **"Tolgee EE License version 1" — non-commercial only**,
no hosted service, no circumventing the licence key. The **onyx pattern**, second occurrence.


## 2026-11-24 — fifteenth pass — el límite del consumo: tres agentes reales y un cero medido

> Tema: **el límite del consumo** — lo que el agente **gasta** y lo que hay que **declarar** sobre
> ese gasto. Medido antes de buscar, sobre los nueve archivos y **en los dos idiomas de la KB**:
> `carbon` 0 · `kWh` 0 · `emision/emisión` 0 · `CSRD` 0 · `ESRS` 0 · `codecarbon` 0 · `kepler` 0 ·
> `consumo` 0 · `ambiental` 0 · `eficiencia energética` 0. Cero limpio en los nueve.
> Contraste que prueba que la capa es nueva y no un sinónimo: `FinOps`, `metering`, `OpenCost` y
> `SPIFFE` **ya estaban**. FinOps mide dinero; esta capa mide julios, y el obligado a declararlos no
> es el CFO.

**Nuevo esta semana en la capa de agentes (3 repos, verificados hoy 2026-11-24):**

- **`mlco2/agentic-footprint`** — MIT, **8★**, push **2026-11-23** (un día antes de este pase).
  Rust. De la organización que mantiene CodeCarbon (1951★, MIT). Huella específica de flujos
  agénticos: el único de los tres con una organización seria detrás.
- **`VeiledTee/agent-energy-profiler`** — MIT, **0★**, push **2026-10-24**. Python; perfila energía
  **por operación** en un flujo multi-paso y **separa explícitamente lo medido de lo estimado**, que
  es la distinción que hace auditable el número.
- **`Enterprise-DNA-OS/carbon-accounting-for-claude-code`** — MIT, **0★**, push **2026-10-18**.
  Contabilidad de carbono de sesiones de agente de código sobre Postgres.

**Se publican con 0★ a propósito.** La alternativa honesta era una sección vacía, y el hueco *es* el
hallazgo: **la atribución de consumo por tarea de agente no tiene producto maduro.** Un *prompt* se
expande en N llamadas al modelo, M invocaciones de herramienta y reintentos; ninguna sonda madura
(Kepler, Scaphandre, CodeCarbon, Zeus) sabe sumar eso a una unidad de negocio. La respuesta de hoy
es composición, no producto: `compose/patterns.md` **Receta 28**.

**Archivado-pero-recomendado, caso nº 11:** `Breakend/experiment-impact-tracker` — MIT, 293★,
**`archived=true`**, último push **2024-01-30**, y sigue en listados de herramientas de huella de ML.
Los once casos de esta KB llegaron por documentación adyacente al proyecto, nunca por el repo.

**Sin licencia, que no es lo mismo que archivado:** `ml-energy/leaderboard` — **`NONE`**, 14★, push
2026-09-23 — mientras su propio motor `ml-energy/zeus` es **Apache-2.0** (390★). La licencia no se
hereda dentro de una organización, ni hacia arriba ni hacia abajo.

**Ruta que los roundups citan y no existe:** `lfwa/carbontracker`. El proyecto real es
**`saintslab/carbontracker`** (MIT, 489★, push 2026-11-05). La llamada por lotes a
`gh api search/repositories` **descarta en silencio** un `repo:` inválido si quedan válidos — 14
pedidos, 13 devueltos — así que el descarte silencioso **es** la señal de que una ruta desapareció.

## 2026-11-24 — fourteenth pass — three agents in a layer with a measured zero, and the engine under all of them

> Theme: **the accessibility boundary** — whether the agent's own interface can be used by the
> people the client is legally obliged to serve, and whether an agent can test that. Measured
> before searching, across all nine files: `wcag` 0, `accessib` 0, `a11y` 0, `EN 301 549` 0,
> `VPAT` 0, `axe-core` 0. A clean zero in every file.

**New this week in the agent layer (3 repos, all verified today):**

- **`JustasMonkev/mcp-accessibility-scanner`** — MIT (byte-read), 59★, npm `5.0.1` published
  **2026-11-16** (eight days before this pass), `axe-core` 4.14.0 + `playwright` 1.65.1. WCAG
  2.0/2.1/2.2 at A/AA/AAA, multi-page crawl, keyboard-navigation checks, JSON reports, plus browser
  automation (click/hover/drag off accessibility snapshots, console and network capture).
  **The one to put in a client pipeline.**
- **`priyankark/a11y-mcp`** — **MPL-2.0** (byte-read *and* npm SPDX), 53★, npm `1.1.1` 2026-10-26.
  Audit → fix → re-audit loop. The **only** one of the three that publishes to npm **with
  provenance**, runs release-policy and real-Chrome smoke tests in CI, and has weekly Dependabot.
- **`ronantakizawa/a11ymcp`** (npm `a11y-mcp-server`) — MIT, **97★ — the most-starred**, and the
  one to avoid: npm `1.1.0` last published **2026-03-01**, and it pins **`puppeteer` 13.5.0, which
  npm dates to 2022-03-07**, against a current 25.18.1 of 2026-11-17.

**The measurement that matters more than the three rows.** Star rank is the exact inverse of
maintenance rank here: 97★ stalest, 59★ freshest, 53★ the only one with supply-chain hygiene. This
is the **third** measured instance in this KB of trend 11 ("star count has decoupled from
enterprise suitability"), and the first where the inversion is perfect across a whole category.

**The licence finding.** Every tool in this layer except IBM's is a wrapper around
`dequelabs/axe-core`, which is **MPL-2.0** — proved by reading `package.json` in each repository:
Microsoft's MIT tool, Google's Apache-2.0 tool and all three MCP servers carry it.
`IBMa/equal-access` (Apache-2.0, 788★) declares **zero** axe dependencies and ships its own engine.
So the permissive badge in this layer is the *wrapper's* badge; MPL-2.0 is file-level copyleft,
which is deliverable but belongs in the client's OSS review and in the AI-BOM.

**A dated licence-tightening instance, from the project's own LICENSE file.** `ryersondmp/sa11y`
states in `LICENSE.md`: released under **GPL-2.0**, and "previous versions of Sa11y (v2.0 and
below) were released under the MIT license." That is trend 7 ("licences are quietly tightening")
with the evidence inside the repository rather than in a blog post.

**Two repositories that look like rows and are not.** `w3c/wcag` is under the **W3C Document
Licence** and `act-rules/act-rules.github.io` under a **W3C Community Contributor License
Agreement** — neither is a software licence, so neither is something to "build on". They are
reference corpora; cite them, do not vendor them.

**Instruments proved or re-proved this pass** (useful to the whole rotation, not just enterprise):
`api.github.com` 403, `img.shields.io` 403, `repos.ecosyste.ms` 403, curl on github.com HTML 403 —
but **WebFetch reads github.com HTML fine** (stars, description, archived banner), and
`registry.npmjs.org/<pkg>` returns the SPDX licence of the latest version plus a **per-version
publish date**, which is how a pinned dependency gets dated and staleness gets measured without the
GitHub API. `raw.githubusercontent.com/<repo>/HEAD/LICENSE` returns licence **text** — stronger
than any badge — and `/HEAD/package.json` exposes the dependency chain.

## 2026-11-24 — thirteenth pass — the layer with no agents in it, and a licence that takes your weights

> Theme: **the erasure boundary** — what the agent must *forget*. Measured before searching: across
> 10,355 lines and 355 repository addresses, `erasure`, `retention`, `unlearn`, `DSAR` and
> `Article 17` returned **zero files**, and so did the Spanish forms (`borrado`, `supresión`,
> `retención`, `conservación`). `GDPR` appeared **twice**, both in passing. The gap survived its own
> audit in both of this KB's languages, which is the only reason it is reported as a gap.

### The news is a zero, and it is measured

```
gh api search/repositories  q='DSAR agent stars:>50'                      → 0
gh api search/repositories  q='GDPR erasure agent stars:>50'              → 0
gh api search/repositories  q='data subject request automation stars:>50' → 0
gh api search/repositories  q='privacy request agent LLM stars:>50'       → 1
```

**There is no agent for this layer**, and the one hit is a proxy. Second layer in six passes with
no agents in it — the first was the entitlement boundary. The pattern: *the layers a client's legal
and security functions care about most have the least open-source product in them.*

### The one new row

| Agent/component | Licence (byte-read) | Stars | Push | Note |
|---|---|---|---|---|
| [crp4222/PrivAiTe](https://github.com/crp4222/PrivAiTe) | **BSD-3-Clause** | 70 | 2026-11-22 | PII redaction proxy for LLM APIs **and agent CLIs** — scrubs **tool-call arguments**, then restores on reply. Sits exactly where Tier 0 of `agents/top.md` has no control. Created 2026-05-07, single-maintainer: a **pattern to adopt**, not a vendor |

### The archival that matters more than any new row

`ethyca/fides` (Apache-2.0, 483★) — the project every 2026 roundup names as the open-source DSAR
engine — is **archived**, last push 2026-08-06, along with `fidesops`, `fidesdemo`, `fideslib`,
`fides-CICD-Quickstart` and `fides-stats`. The only actively developed repositories in that
organisation are three mobile consent SDKs that **declare no licence**. First archival + **licence
regression** in one namespace that this KB has recorded. `fides-helm` is still maintained — **the
chart outlived the product**, which is a new way to misread a layer's health.

### A false finding this pass caught on itself

`repo:microsoft/presidio` is unsearchable (**422**) and `grep -ril presidio` matches **seven
files** — which looks exactly like a KB citing a dead owner. It is not: the **fourth pass already
caught the move** and rewrote every citation; the grep matched the **new** path. **Grep the old
owner path, never the bare project name.** Also: `raw.githubusercontent.com/microsoft/presidio/...`
still returns **200** via redirect, so **no liveness check can detect a rename** — only the search
API can, by refusing the path.

### Licence class nº 12 — and it reaches the weights

[`vec2text/vec2text`](https://github.com/vec2text/vec2text) (1,150★) reports `NOASSERTION`. Its
`LICENSE` is **SOM-1.0**, whose §3(A) requires anyone who uses the tool *"to create inferences with
a Model, whether or not you make the Model available to others"* to publish that model's **weights**.
The twelfth pass found the operative clause **outside** the licence (in an AUP); this one found it
**inside a tool's licence, reaching an asset the tool does not contain**. Use
[`jina-ai/embedding-inversion-demo`](https://github.com/jina-ai/embedding-inversion-demo)
(Apache-2.0) instead.

Full tables in `repos/foundations.md`; trends 29–30 in `intel/trends.md`; the builds are Recetas 25
and 26.

## 2026-11-24 — twelfth pass — the licence of the model the agent runs on

> Theme: **the weights boundary**. This KB holds 338 repository addresses and an eleven-class licence
> taxonomy, all of it built by reading `LICENSE` files in code repositories. This pass pointed that
> apparatus at the one artefact it had never been pointed at — **the model weights the agent
> actually runs on** — and found that the file every scanner reads is the wrong file.
>
> There is no new agent in this section. The news is that **the licence posture of every agent in
> `agents/top.md` is incomplete**, because an agent's MIT licence says nothing about the weights it
> loads. Full analysis in `intel/trends.md` trends 27–28; the gate to build is Receta 23.

### The measurement, in one block

```
grep -c 'European Union'  models/llama4/LICENSE        → 0
grep -c 'European Union'  models/llama3_3/LICENSE      → 0
grep -c 'European Union'  models/llama3_2/LICENSE      → 0
grep -c 'European Union'  models/llama3_1/LICENSE      → 0
grep -c 'European Union'  models/llama4/USE_POLICY.md  → 1   ← the clause lives here
```

`models/llama4/USE_POLICY.md:71`, read from Meta's own repository on 2026-11-24, withdraws the
**Section 1(a) rights** for multimodal Llama 4 from *"an individual domiciled in, or a company with a
principal place of business in, the European Union"*, while exempting **end users** of a product
incorporating such a model. **A document that is not the licence modifies the licence grant, and no
licence scanner reads it.**

### What moved this week in the weights layer

| What | Licence | Verified how, 2026-11-24 | Why it is this week's news |
|---|---|---|---|
| **OpenMDW-1.1** (Linux Foundation) | Permissive in substance; **not OSI-approved, no SPDX ID** | Canonical text `OpenMDW/OpenMDW` → `1.1/LICENSE.OpenMDW-1.1`, **2,619 bytes** | **An eleventh licence class, and the first written for weights rather than code.** One grant over model + data + docs + code, adding **database and trade-secret** rights; **outputs explicitly unrestricted**. OSI review still open at 2026-08-29 over termination reaching copyright claims |
| **NVIDIA Cosmos ships under it** | OpenMDW-1.1 | `NVIDIA/Cosmos` → `LICENSE`, **2,619 bytes — byte-identical to canonical** | First major adoption **confirmed from the vendor's own repository**, not a press release. By contrast `NVIDIA-NeMo/Nemotron` → `LICENSE` is **Apache-2.0** — the code, not the weights |
| **Latam-GPT** (CENIA, Chile), launched **2026-02-10** | **Llama 3.1 Community License** (secondary-sourced) | Published as `latam-gpt/Llama-3.1-70B-LatamGPT-SFT-1.0`; model card on a host this session cannot reach | **LATAM's sovereignty flagship is a Llama 3.1 70B derivative** and inherits Meta's AUP, naming obligation and 700M-MAU clause. The sovereignty is in the data and the language, **not in the licence** |
| **SEA-LION** (AI Singapore) | **Varies by base model** | `aisingapore/sealion` → `README.md:88` | The project's own README says MIT *"as much as possible… may be bound by the Llama3 License"*, while its arXiv paper (2504.05747) claims *"fully open MIT"*. **Paper and artefact disagree; the README sides with the artefact** |
| **Salamandra** (Barcelona Supercomputing Center) | **Apache-2.0** | `langtech-bsc/salamandra` → `LICENSE`, **11,357 bytes** | **EMEA's cleanest sovereign base model** — no AUP, no download gate, no inherited base licence. The one to put in front of a European client this week |
| **Qwen3** | **Apache-2.0** | `QwenLM/Qwen3` → `README.md:397`, with **no `LICENSE` file at `main` or `master`** | The most permissive frontier-class family verified this pass, and a **false negative** for any scanner: the repo looks unlicensed while the weights are Apache-2.0 |

### The licence trap of the week, and it is in the tooling

`trailofbits/fickling` — the best-known pickle-security tool — is **LGPL** (`master/LICENSE`, 7,652
bytes), not permissive. Its peer `mmaitre314/picklescan` is **MIT** (1,072 bytes). **Two tools, one
job, different licence classes.** Ship the MIT one; keep the LGPL one as a standalone CI binary.

### Declared gap for this section

`api.github.com` returns **403 for every repository outside this session's scope**, so **no star
counts or push dates appear in this pass's rows**. `huggingface.co` and `ai.google.dev` **do not
resolve from this session**, which is why two weights licences above are marked secondary-sourced and
**Gemma's is recorded as unresolved rather than guessed**. Absence of a number here means the
measurement was refused, not that the project is small.

## 2026-11-24 — eleventh pass — the agent layer on a forge nobody had searched

> Theme: **the instrument**. Passes 7 to 10 each measured a boundary of the agent — what it may
> read, change, prove and reach. This pass measured the **KB itself** and found that all 314 of its
> repository addresses sat on a single forge. The trending news is therefore not a new agent: it is
> six permissive agent components that existed all along, on `gitlab.com`, and were never seen.
> Full tables in `repos/foundations.md` and `agents/top.md`; the build is Receta 21.

### The measurement that produced this section

```
314 distinct github.com addresses in this KB · 0 on gitlab.com, sourceforge.net,
codeberg.org, bitbucket.org, git.sr.ht, gitee.com or huggingface.co
```

Nine alternative forges were then probed. **Eight refused at the network layer**
(`curl (56) CONNECT tunnel failed, response 403`), including `gitee.com` — the dominant APAC forge —
and `gitlab.opencode.de`, the German public-sector forge. One, `gitlab.com`, answered its API
unauthenticated. So the zero has two different causes, and only one of them was a research failure.

### `gitlab-org/orbit/knowledge-graph` — the week's most interesting agent product, and it is not open source

| Property | Value (verified 2026-11-24) |
|---|---|
| Repo | [gitlab-org/orbit/knowledge-graph](https://gitlab.com/gitlab-org/orbit/knowledge-graph) |
| Self-description | **"Software lifecycle context graph for AI agents"** |
| Licence reported by API | `other` |
| **Licence in the repository** | **GitLab Enterprise Edition licence** (byte-read from `LICENSE.md`) |
| Stars / last activity | 58 / **2026-11-24** |
| Maturity | `v1.9.1`, own Helm charts, release badge, `"private": true` in `package.json` |

Production use *"may only be used in production, if you … have a valid GitLab Enterprise Edition
subscription for the correct number of user seats."* Within the same `gitlab-org` namespace, GitLab
CE is **MIT** and this is not — **the namespace is not the licence**, and its community fork inherits
the EE terms rather than escaping them.

**The positioning sentence:** the proprietary option has the best marketing line in the category;
the four permissive options for the same job — OpenMetadata, DataHub, Unity Catalog, OpenLineage —
are already in this KB and are all Apache-2.0.

### New rows, and all six are MIT

| Repo | Licence | Stars | Last activity | One line |
|---|---|---|---|---|
| [fforster/gitlab-mcp](https://gitlab.com/fforster/gitlab-mcp) | MIT | **85** | 2026-11-24 | MCP server for GitLab — most-starred permissive agent component found off GitHub |
| [nagyv/gitlab-opencode](https://gitlab.com/nagyv/gitlab-opencode) | MIT | 59 | 2026-09-17 | Any LLM in GitLab CI with explicit **tool permissions** |
| [lx-industries/rmcp-openapi](https://gitlab.com/lx-industries/rmcp-openapi) | MIT | 13 | 2026-11-24 | **OpenAPI endpoints → MCP tools** on the official Rust SDK |
| [lx-industries/rmcp-actix-web](https://gitlab.com/lx-industries/rmcp-actix-web) | MIT | 6 | 2026-11-23 | `actix-web` transport for the same SDK |
| [lx-industries/openblob](https://gitlab.com/lx-industries/openblob) | MIT | 4 | 2026-11-24 | *"Distributed agentic workloads, no one in charge, everything under control"* |
| [gitlab-org/ai-engineering/agent-foundations/agentic-productivity](https://gitlab.com/gitlab-org/ai-engineering/agent-foundations/agentic-productivity) | MIT | 6 | 2026-10-01 | GitLab's own *"agentic configs, skills, agents and workflows"* |

**And one refusal that matters:** [gitlab-org/ai/lazy-mcp](https://gitlab.com/gitlab-org/ai/lazy-mcp)
(20★, 2026-11-08) has **no licence file in its root** — verified by listing the tree, not by trusting
an empty API field. GitLab Inc.'s own MCP project is not proposable.

### Why the gap lasted ten passes — a vocabulary collision measured on a second forge

Searching `gitlab.com` for **`agent`** returns, in star order, a browser user-agent switcher, a
Kubernetes cluster agent, `fetchmail`, a network telemetry agent and a VPN client. On this forge the
word still carries its **pre-LLM meaning**. The sweep that worked searched the **domain** — `erp`,
`crm`, `facturacion`, `mcp` — not the technology. `mcp` worked precisely because it is a new word
with nothing to collide with.

### The sixth consecutive pass in which no agent row changed — and that is now the finding

For the sixth pass running the shortlist above did not move. What moved this pass is the KB's
ability to say **why** it believes the shortlist is complete, and to name the edge of that belief:
one forge measured, one reachable, seven refused and therefore **unmeasured rather than empty**.

## 2026-11-24 — tenth pass — a guardrail that runs inside the agent's own hook loop

> Theme: **containment** — what the agent may *reach*, and what stops it. For the **fifth
> consecutive pass no agent row changed**, and for the fifth consecutive pass the news is one layer
> below the agent. What belongs *here* is the one component found this pass that is not beside the
> agent but **inside it**: it runs on the agent's own hook API and answers every tool call before it
> executes. Full tables in `repos/foundations.md`; the build is Receta 20.

### `falcosecurity/prempti` — Falco moved into the agent's tool-call lifecycle

| Property | Value (verified 2026-11-24) |
|---|---|
| Repo | [falcosecurity/prempti](https://github.com/falcosecurity/prempti) |
| Licence | Apache-2.0 (byte-read from `LICENSE`) |
| Stars | **234** |
| Last push | **2026-09-21** — roughly two months idle |
| Status | **"Experimental Preview"**, stated in its own README |
| Owner | `falcosecurity` — the **CNCF-graduated** Falco project's own organisation, not a vendor fork |

**How it works, and why the mechanism is the interesting part:** a hook fires **before** each tool
call; the interceptor passes the event over a **Unix socket** to a broker embedded in a **Falco
plugin**; Falco's rule engine evaluates it and returns **allow / deny / ask**; the interceptor
delivers that verdict back to the agent. Default mode is `guardrails` (verdicts enforced);
`monitor` mode observes and logs only. Supported agents: **Claude Code** (Linux/macOS/Windows) and
**Codex** (experimental, Linux only).

**This is the first component in this KB that enforces policy at the agent's decision point rather
than at a network, API or admission boundary.** Everything else the KB holds sits *outside* the
agent and sees a request that has already been formed. Prempti sees the intent.

### The sentence from its README that should be in the deliverable, not buried

> *"not a sandbox, OS-level security, or a substitute for least-privilege environments"* — and it
> governs *"the commands the agent requests, **not the side effects those commands produce at
> runtime**."*

A project disclosing the exact shape of its own blind spot is rare enough to be worth quoting
directly to a client. It also **completes an argument this KB has been assembling for three
passes**: hook interception sees the request but not the effect; kernel isolation stops host escape
but not network egress (Vercel, on gVisor and microVMs); and the July 2026 incident class reviewed
by the Cloud Security Alliance in October bypassed both — **no sandbox was broken, an agent wrote a
file that a trusted unsandboxed component later executed.**

**Four controls, not one: intercept the request, isolate the kernel, restrict the egress, detect at
runtime.** No single project provides all four. Sell the set.

### How to position it despite "Experimental Preview" and two months idle

Do **not** put a 234-star experimental preview on a client's critical path. Do use it as the
**pattern**, because the pattern is portable and the pattern is the billable insight:

- The agent's **hook API is a policy enforcement point** — on Claude Code it exists, is documented,
  and fires before tool execution. That is true whether or not Prempti is the thing attached to it.
- The **rules can be Falco rules**, which means the detection content a client already owns for
  their Kubernetes estate becomes reusable against agent tool calls. Sysdig's commercial Falco Feeds
  are reported to ship agent-specific rules mapped to **MITRE ATLAS** (MCP tool poisoning, prompt-
  injection exfiltration, coding-agent credential theft) — **a paid layer on the open engine; priced
  separately, and that should be said out loud in an estimate.**
- `monitor` mode first, `guardrails` second. The same two-phase rollout the KB already recommends
  for Tetragon enforcement and for OPA: **observe, build the allowlist from what you observed, then
  enforce.** Enforcing a policy you have not first measured takes down legitimate work.

### Also new, and it names agents this KB already holds

[Azure/kars](https://github.com/Azure/kars) (MIT, 46 ★) is a Microsoft **reference implementation**
for running agents safely on Kubernetes, and its supported-runtime list is a useful external check
on this KB's Tier 0/Tier 1: **OpenClaw** and **Hermes** (Nous Research) are 2 of its 8, beside
OpenAI Agents SDK, Microsoft Agent Framework, LangGraph, Claude Agent SDK and Pydantic-AI. **Every
one of those eight is already in `agents/top.md`** — the first time an external architecture has
independently reproduced this KB's agent inventory rather than adding to it. Its disqualifiers
(`v1alpha1`, *"Not an officially supported Microsoft product"*) are in `repos/foundations.md`.

---

## 2026-11-24 — ninth pass — the agent's own security tool changed hands

> Theme: **provenance** — not what the agent may read or change, but **what the agent is made of
> and who signs for it.** For the fourth consecutive pass **no agent row changed**, and for the
> fourth consecutive pass the news is one layer below the agent. The full provenance layer is in
> `repos/foundations.md` and `repos/trending.md`; what belongs *here* is that a tool this KB
> already recommends has changed owner, name, install path and business model at once.

### `mcp-scan` → `snyk/agent-scan`: a rename that is also an acquisition and a meter

| Cited as | Canonical 2026-11-24 | Evidence |
|---|---|---|
| `invariantlabs-ai/mcp-scan` | [snyk/agent-scan](https://github.com/snyk/agent-scan) | Both paths return the **identical HEAD sha `a8561271`** under `git ls-remote` — GitHub serves the old address as an alias, which is exactly why no roundup notices. Apache-2.0, 3,300 ★, last commit 2026-11-23. Now scans "AI agents, MCP servers **and agent skills**". |
| `mcp-scan` on PyPI | `snyk-agent-scan` | PyPI `mcp-scan` 0.4.3 is a **redirect shim** — summary says so and `requires_dist: ['snyk-agent-scan']`. Target is at 0.7.0, Apache-2.0, 46 releases. |
| `mcp-scan` on npm | **Unrelated project** | npm `mcp-scan` 2.3.0, MIT, maintainer `rodolfboctor`, repo [Abanoub-Rodolf/mcp-scan](https://github.com/Abanoub-Rodolf/mcp-scan). `snyk/agent-scan`'s README: **"there is no npm package."** |

**`uvx mcp-scan` and `npx mcp-scan` install different vendors' software.** Name the registry and pin
the version in every deliverable: `uvx snyk-agent-scan@<version>`.

### Two properties to quote before recommending it

1. **Permissive licence, metered capability.** `SNYK_TOKEN` must be exported *before* any scan; the
   free tier stops at a **daily usage limit**; v0.5.x drives a dated analysis API (`2025-09-02`) that
   is **planned for deprecation**. The analysis is **not local** — so for the egress-restricted or
   sovereign estate in `intel/market.md`, assume it does not run until proven otherwise.
   **Licence governs redistribution; it says nothing about whether the capability is local.**
2. **Scanning untrusted MCP config is a privileged act.** To read tool descriptions it **executes the
   commands in the config** and calls remote MCP URLs **with their configured headers** — the client's
   own credentials. It refuses link-local and cloud-metadata targets (`169.254.0.0/16`, `fe80::/10`,
   `fd00:ec2::254`, `100.100.100.200`), does not follow redirects, validates DNS per request, and then
   states plainly that re-resolution at connect time leaves a **DNS-rebinding window**. Sandbox it;
   never pass `--dangerously-run-mcp-servers` outside a disposable environment. *A tool that documents
   its own residual vulnerability is behaving better than one that does not — quote both halves.*

### The locally-runnable alternative, which is the commercially useful finding

[cisco-ai-defense/mcp-scanner](https://github.com/cisco-ai-defense/mcp-scanner) (Apache-2.0, 1.1k ★,
2026-11-19): per its README the Cisco API key is required **only for the API analyzer** — YARA,
readiness, prompt-defense, static-JSON and vulnerable-package scans need **no key**, and the LLM
analyzer accepts **a local endpoint such as Ollama** with a placeholder key. For a client who cannot
send MCP configuration to a vendor endpoint, this is the candidate to pilot. Test it; do not assume it.

### Publisher identity for MCP servers — preview, but the primitive is real

[modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry) (7.5k ★, 2026-11-23)
validates **namespace ownership at publish time** via GitHub OAuth, GitHub OIDC, **DNS** and HTTP
verification. DNS verification — proving control of a domain and its subdomains — is the difference
between "a server named `acme-crm`" and "a server published by whoever controls `acme.com`". It is
**still a preview release, not GA**, with the API frozen at v0.1 pending v1.

**Licence note, and it is a new class for this KB.** Its `LICENSE` byte-reads as a *licensing
transition*: new contributions Apache-2.0, but contributions whose authors have not consented to
relicensing **remain MIT**. The repo is a **per-contribution MIT/Apache-2.0 mixture** — both
permissive, so not a blocker, but *"the MCP registry is Apache-2.0"* is false and so is *"it is MIT"*.
The transition is **partial across the org**: same notice on `modelcontextprotocol/modelcontextprotocol`
and `/servers`, while [`/python-sdk`](https://github.com/modelcontextprotocol/python-sdk) is **still
plain MIT**. Record licences per repository and per date, never per organisation.

## 2026-11-21 — eighth pass — the write boundary

> Theme: the seventh pass asked *what may the agent read*. This one asks **what may the
> agent change**, and **what proves afterwards that it was allowed to**. Every row
> verified live on 2026-11-21 (`git ls-remote`) with the licence read byte-for-byte from
> the repository's own `LICENSE`, never from GitHub's SPDX badge — this pass found
> **four repositories where that badge is wrong**, and in all four it was wrong in the
> *permissive* direction, which is the opposite of every previous pass.

### The inventory hole: the KB held three of the four hyperscaler agent frameworks

A KB with 234 distinct repository addresses was missing **Google's**. Not a judgement
call, not a licence exclusion — simply absent, through eight passes, while
`microsoft/agent-framework`, `openai/openai-agents-python` and the Anthropic-adjacent
harness layer were all present and tiered.

| Repo | Stars | Licence | Last push | Why it belongs in an enterprise KB |
|---|---|---|---|---|
| [google/adk-python](https://github.com/google/adk-python) | 22,295 ★ | Apache-2.0 (11,357 B, byte-read) | 2026-11-21 | Google's Agent Development Kit, the reference implementation of the A2A protocol this KB already tracks via [a2aproject/a2a](https://github.com/a2aproject/a2a). Pushed the day of this pass. |
| [google/adk-go](https://github.com/google/adk-go) | 8,992 ★ | Apache-2.0 (11,340 B, byte-read) | 2026-11-20 | Go runtime. Matters where the agent must ship as a single static binary into a locked-down estate. |
| [google/adk-java](https://github.com/google/adk-java) | 1,778 ★ | Apache-2.0 (11,357 B, byte-read) | 2026-11-20 | The JVM option beside `agentscope-java` and `camel-langchain4j-agent`. Relevant to Receta 6 (APAC enterprise core). |
| [google/adk-python-community](https://github.com/google/adk-python-community) | 188 ★ | Apache-2.0 | 2026-11-20 | Community extension surface, held separately from the supported core — the same split Microsoft uses for `agent-framework-samples`. |

**The lesson is about method, not about Google.** This KB's discovery instrument is
queries about *problems* ("entitlement", "the data plane", "cost governance"). An
artefact that answers no single problem — a general framework from a vendor whose
protocol work was already held — falls through every one of them. **A problem-shaped
instrument cannot find a category-shaped object.** Any KB in this fleet that has run
more than three passes should spend one query per pass on a flat inventory check
against the obvious incumbents, not on a problem.

### Durable agents: the write path's recovery story

| Repo | Stars | Licence | Last push | Notes |
|---|---|---|---|---|
| [dapr/dapr-agents](https://github.com/dapr/dapr-agents) | 778 ★ | Apache-2.0 (11,356 B, byte-read) | 2026-11-12 | `DurableAgent` runs as a Dapr Workflow instance; every LLM and tool interaction is persisted to a durable state store, so a half-finished write survives a restart. v1.0 GA March 2026 per Diagrid's announcement (vendor source — the GA *date* is attributed, the repo and licence are verified). |
| [dapr/dapr](https://github.com/dapr/dapr) | 26,212 ★ | Apache-2.0 (11,411 B, byte-read, `master` branch) | 2026-11-19 | CNCF. The substrate underneath the above. **Workflow versioning landed in v1.17 (February 2026)**: running instances keep replaying against the code they started on while new instances use the updated code. For an agent that is mid-write when you deploy, this is the difference between a resumed transaction and a corrupted one. |

### Trending this week, filtered to what an enterprise would actually run

| Repo | Stars | Licence | Last push | Note |
|---|---|---|---|---|
| [block/buzz](https://github.com/block/buzz) | 37,646 ★ | Apache-2.0 (11,337 B, byte-read) | 2026-11-21 | "A hive mind communication platform" — a self-hostable workspace where agents are first-class members beside people, on Nostr. Relevant to the *agent-to-user layer* this KB opened in the sixth pass; self-hostable matters for the sovereignty cases in EMEA and APAC. Pre-1.0 per its own ecosystem. |
| [Tencent/LoopForge](https://github.com/Tencent/LoopForge) | 5,481 ★ | **MIT** — GitHub reports `NOASSERTION`; see the trap below | 2026-11-21 | Self-hosted workflows for coding-agent delivery, orchestrating CodeBuddy, Codex and others. **APAC-origin supply with a byte-read permissive licence.** Notably it vendors a Tencent-modified copy of [obra/superpowers](https://github.com/obra/superpowers), which this KB already tracks in the skill supply chain — a Big Tech delivery tool shipping a modified community skill framework is exactly the supply-chain shape trend 10 describes. |
| [openai/codex-security](https://github.com/openai/codex-security) | 14,249 ★ | Apache-2.0 (10,925 B, byte-read) | 2026-11-21 | Security CLI and TypeScript SDK for finding, validating and fixing vulnerabilities. Sits beside `NVIDIA/SkillSpector` and `nvidia/garak` in the red-team section. |
| [SWE-agent/SWE-agent](https://github.com/SWE-agent/SWE-agent) | 20,845 ★ | MIT (1,146 B, byte-read) | 2026-11-16 | **Rename.** Every roundup still cites `princeton-nlp/SWE-agent`; the canonical owner is now the `SWE-agent` org. See the rename ledger in `repos/foundations.md`. |
| [SWE-agent/mini-swe-agent](https://github.com/SWE-agent/mini-swe-agent) | 9,925 ★ | MIT | 2026-11-16 | The stripped-down sibling. Useful as a *readable* reference when a client asks what an agent loop actually is. |

### The licence trap of this pass, and it runs the opposite way to all seven before it

Every previous pass found repositories that **looked permissive and were not**
(Permify AGPL-3.0, `osohq/oso` archived, FSL, BSL 1.1, the "MIT incipit" impostor).
This pass found four that **look restricted and are not**:

| Repo | GitHub badge | Byte-read reality |
|---|---|---|
| [usnistgov/OSCAL](https://github.com/usnistgov/OSCAL) | `NOASSERTION` | `LICENSE.md`, 5,254 B, first line *"This project is in the worldwide public domain"* |
| [usnistgov/oscal-cli](https://github.com/usnistgov/oscal-cli) | `NOASSERTION` | `LICENSE.md`, 3,540 B, worldwide public domain |
| [usnistgov/oscal-content](https://github.com/usnistgov/oscal-content) | `NOASSERTION` | `LICENSE.md`, 2,105 B, worldwide public domain |
| [Tencent/LoopForge](https://github.com/Tencent/LoopForge) | `NOASSERTION` | `LICENSE`, 3,516 B — *"LoopForge is licensed under MIT, except for the third-party components listed below"*, then the full MIT grant |

**`NOASSERTION` is not a verdict. It is the absence of one.** It means GitHub's
classifier did not recognise the file, and the two commonest reasons are a
US-Government public-domain dedication and a corporate preamble above an otherwise
standard grant. This KB — and, per `rotation.json`, the energy KB last run — has been
treating `NOASSERTION` as a hard exclusion. That rule produces **false exclusions**,
and it excluded the entire NIST compliance stack until this pass.

See `repos/foundations.md` for the full new sections, and `intel/trends.md` for the
three method rules this pass added.

## 2026-11-20 — seventh pass

**No new agents. The newsworthy thing in the agent category this pass is a category that
contains no agents** — and three archived or copyleft surprises inside it.

**What was searched:** the entitlement boundary — relationship-based authorization, delegated
identity, permission-aware retrieval. Chosen because it is the first question a client's
security team asks and this KB had **zero** coverage of it (`OpenFGA`, `Casbin`, `OAuth`, token
exchange: no matches in any of the eight files).

**New this pass, all verified against the GitHub API and `raw.githubusercontent.com`:**

| Piece | Licence | ★ | Pushed | Note |
|-------|---------|---|--------|------|
| [apache/casbin](https://github.com/apache/casbin) | Apache-2.0 | 20,508 | 2026-11-20 | **Moved to the Apache Software Foundation.** The most-starred authorization library in open source. Family re-homed under `apache/casbin-*` (jcasbin, pycasbin, node-casbin, Casbin.NET, casbin-rs). **Lives on `master`, not `main`.** |
| [authzed/spicedb](https://github.com/authzed/spicedb) | Apache-2.0 | 7,233 | 2026-11-20 | Zanzibar-style permission database; the store behind permission-aware retrieval. |
| [openfga/openfga](https://github.com/openfga/openfga) | Apache-2.0 | 6,168 | 2026-11-20 | CNCF-hosted, Auth0 origin, best-documented for the agent/RAG case. |
| [modelcontextprotocol/ext-auth](https://github.com/modelcontextprotocol/ext-auth) | MIT | 179 | 2026-11-10 | Specification repo — rank by provenance, not stars. Carries the enterprise MCP authorization profile, revision `2026-07-28`. |

**Three traps in the same category, which is the trend worth recording:**

- [osohq/oso](https://github.com/osohq/oso) — Apache-2.0, 3,480 ★, **ARCHIVED 2026-10-22**, its
  own description now reading *"Legacy Oso open source library (archived)"*. **This is the fifth
  archived-but-highly-starred project this KB has found in six passes** (three chat UIs → Vanna
  at 23.8k ★ → now Oso). The pattern has graduated from observation to standing check.
- [Permify/permify](https://github.com/Permify/permify) — **AGPL-3.0**, 5,975 ★, confirmed by
  reading `LICENSE`. Markets itself in the same sentence as Apache-2.0 SpiceDB and OpenFGA.
- [zitadel/zitadel](https://github.com/zitadel/zitadel) — **AGPL-3.0**, 15,622 ★. Commonly
  suggested as the modern alternative to Keycloak, which is **Apache-2.0**.

**And a negative result worth more than the positives — six repositories that do not count.**
A search for the exact pattern name returned six GitHub projects all named essentially
`permission-aware-rag`, with confident READMEs (*"0 restricted chunks leaked in 330 adversarial
tests"*, *"a benchmark of three filtering strategies on 50K chunks"*). Their real star counts:
**1, 0, 0, 19, 0, 0**, and **three have no licence file**. They are personal demos. The cause is
structural: **web search ranks on README semantics, so when the search phrase *is* the
repository name, the result page fills with zero-traction look-alikes.** A results page whose
entries all share one repository name is a warning, not a confirmation.

## 2026-11-20 — sixth pass

**Headline: the agent an enterprise asks for first was missing from this file entirely, and its
second most-starred implementation has been archived since March.**

Five passes catalogued the agent as a *general* thing — harnesses, frameworks, UI surfaces,
governance. This pass searched by **first client request** instead: what does an enterprise ask
for in meeting one? The answer is always some version of *"let us ask our data a question in
English."* That is a distinct agent category with its own benchmark literature and its own
licence traps, and this KB had none of it.

**New this pass — four live data agents (full table in `agents/top.md`, Tier 2):**

| Agent | Licence | ★ | Origin |
|-------|---------|---|--------|
| [mindsdb/mindsdb](https://github.com/mindsdb/mindsdb) | MIT | 39.9k | North America |
| [eosphoros-ai/DB-GPT](https://github.com/eosphoros-ai/DB-GPT) | MIT | 20.3k | APAC (China) |
| [Canner/WrenAI](https://github.com/Canner/WrenAI) | Apache-2.0 (all code paths) | 18.4k | APAC (Taiwan) |
| [XGenerationLab/XiYan-SQL](https://github.com/XGenerationLab/XiYan-SQL) | Apache-2.0 | 1.0k | APAC (China) |

**Three of the four are APAC-origin.** That is the second time this KB has measured APAC as the
origin region for a whole agent category (the third pass found `deer-flow` the same way), and it
is now a pattern worth stating in a capability deck rather than a coincidence.

**The die-off, continuing last pass's finding:** [vanna-ai/vanna](https://github.com/vanna-ai/vanna)
(MIT, 23.8k ★) was **archived by its owner on 29 March 2026 and is read-only** — nearly eight
months. It is the second most-starred project in the category. Last pass found three archived
chat-UI repositories whose READMEs did not disclose it; this pass found a fourth archived
project in a different layer. **Standing method change: `archived` status is now checked for
every repository this KB recommends, every pass.** Stars do not decay when a project dies, so
star-sorted search actively leads a client to dead code.

**Licence finding — WrenAI, and a correction to the public record.** Secondary sources describe
WrenAI as "Apache 2.0 core with AGPL modules" and some mirrors report it as AGPL-3.0 outright.
**Neither is accurate today.** Its `LICENSE` is an explicit path→licence map: `core/**`,
`sdk/**`, `skills/**`, `examples/**` and the root files are **all Apache-2.0**; `docs/**` is
CC-BY-4.0; the AGPL-3.0 text is shipped **pre-emptively and currently applies to zero paths**.
So: Globant can build on all of it today, *and* the path map is the thing to re-read each pass,
because the project has told us in writing that it intends to add AGPL modules later. That is
the honest statement, and it is neither of the two wrong ones. WrenAI's licence file also states
that **the package manifest is authoritative where it disagrees with the licence file** —
independent corroboration of the manifest-first rule this KB's energy pass derived.

**What did not change:** Tier 0 and Tier 1 are untouched again — the fourth consecutive pass
where the framework choice did not move. The agent is still the least consequential decision
on the page.

---

## 2026-11-20 — fifth pass

**Headline: three of this layer's best-known repositories are archived, and their READMEs do not
say so.** This pass searched the one surface the previous four never touched — **where the agent
meets the human** — and the first thing it measured was a die-off. The GitHub search API reports
`archived: true` for [Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0,
12,498 ★ — the most-recommended Python conversational-AI shell in the market),
[langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★) and
[langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui) (MIT, 1,705 ★).
LangChain has archived **both** of its agent UI repositories.

**Evidence quality, stated because the conclusion is strong:** the `archived` flag comes from the
GitHub search API, re-queried twice. The github.com HTML page returns **403 from this
environment**, so that channel could not cross-check it, and **none of the three READMEs carries
a deprecation notice** — an engineer reading the README would not know. Corroborating signal for
Chainlit only: a PyPI fork surfaced in this pass's web search states the original Chainlit team
is no longer maintaining the project. Treat "archived" as well-founded; treat "and therefore
dead" as a judgement.

**What the pattern means, and it is not a coincidence.** Sort this layer by shape rather than by
stars and the archived repos are all the *same* shape — a **standalone chat window placed in
front of an agent**. Every live, actively-pushed repository in the layer is the *other* shape:
the agent **renders into the client's existing application** using that application's own
components. The chat shell as a product category is being abandoned in favour of in-app
generative UI. For an engagement this is the difference between a deliverable the client's users
must navigate to and one that appears inside the screen they already work in.

### The agent-to-user interaction layer — zero prior coverage in this KB

Verified today against the GitHub API; every licence below was additionally **read from the
repository's `LICENSE` file**, not taken from the badge.

| Repo | Licence (file-read) | ★ | Forks | Pushed | What it is |
|------|---------------------|---|-------|--------|------------|
| [CopilotKit/CopilotKit](https://github.com/CopilotKit/CopilotKit) | MIT | 38,842 | 4,839 | 2026-11-20 | The frontend stack for agents and generative UI (React, Angular, mobile, Slack). Authors of the AG-UI protocol. |
| [ag-ui-protocol/ag-ui](https://github.com/ag-ui-protocol/ag-ui) | MIT | 20,766 | 2,129 | 2026-11-20 | **AG-UI: the Agent-User Interaction Protocol.** The third leg of the protocol triad — MCP for tools, A2A for agent-to-agent, AG-UI for agent-to-user. |
| [vercel-labs/json-render](https://github.com/vercel-labs/json-render) | Apache-2.0 | 19,791 | 1,059 | 2026-11-19 | "The Generative UI framework" (Vercel). |
| [a2ui-project/a2ui](https://github.com/a2ui-project/a2ui) | Apache-2.0 | 17,690 | 1,432 | 2026-11-20 | **A2UI — Google-origin**, announced 15 Dec 2025, 1.0 released. Agent streams **layout data, not code**; the client holds a catalog of pre-approved components and the agent may only request from it. |
| [thesysdev/openui](https://github.com/thesysdev/openui) | MIT | 15,375 | 1,026 | 2026-11-20 | "The Open Standard for Generative UI" — a third contender for the same slot. |
| [assistant-ui/assistant-ui](https://github.com/assistant-ui/assistant-ui) | MIT | 13,351 | 1,353 | 2026-11-20 | TypeScript/React library for AI chat; the live option where the archived LangChain UIs used to be. |
| [tambo-ai/tambo](https://github.com/tambo-ai/tambo) | MIT | 11,221 | 577 | 2026-11-18 | Generative UI SDK for React. |
| [CopilotKit/openfuse](https://github.com/CopilotKit/openfuse) | MIT | 6,544 | 964 | 2026-11-20 | Reference personal agent (browser, terminal, files) built on CopilotKit — a worked example, not a platform. |
| [flyerhq/flutter_chat_ui](https://github.com/flyerhq/flutter_chat_ui) | Apache-2.0 | 2,381 | 864 | 2026-11-19 | The mobile answer: Flutter chat/agent SDK. Relevant wherever the client's workforce is phone-first. |

**Archived — do not start here, and check whether a client already did:**
[Chainlit/chainlit](https://github.com/Chainlit/chainlit) (Apache-2.0, 12,498 ★,
**archived**, last push 2026-09-18, Paris-origin),
[langchain-ai/agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) (MIT, 3,253 ★,
**archived**), [langchain-ai/deep-agents-ui](https://github.com/langchain-ai/deep-agents-ui)
(MIT, 1,705 ★, **archived**). Also stale but not archived:
[agno-agi/agent-ui](https://github.com/agno-agi/agent-ui) (MIT, 1,879 ★, last push
**2026-05-08** — six months).

### Human approval as a component, not a code review habit

| Repo | Licence | ★ | Pushed | Note |
|------|---------|---|--------|------|
| [humanlayer/humanlayer](https://github.com/humanlayer/humanlayer) | Apache-2.0 (file-read) | 12,919 | 2026-11-16 | Approval/escalation layer: the agent requests a human decision as a typed call rather than a prompt asking nicely. |
| [humanlayer/12-factor-agents](https://github.com/humanlayer/12-factor-agents) | **Apache-2.0 — read from the file; GitHub reports `NOASSERTION`** | 27,343 | 2025-09-21 | The design-principles document the market quotes. The licence file is the **unmodified** 199-line Apache-2.0 text with no added clauses, so an enterprise *may* adopt it internally — a question clients do ask. **Content is 14 months stale.** |
| [humanlayer/fold](https://github.com/humanlayer/fold) | MIT | 187 | 2026-10-23 | Provider-agnostic agent core; small, listed for completeness. |

This is the T46 probe paying off again: a 27,343-star repository reported `NOASSERTION` turned
out to be plain, unaltered Apache-2.0. Three passes of this KB have now found the same class of
error. **GitHub's licence badge is a hint; the file is the answer.**

### Agents managed as a workforce — a 115,408-star MIT repo this KB never mentioned

| Repo | Licence | ★ | Forks | Pushed | Note |
|------|---------|---|-------|--------|------|
| [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | MIT (**`LICENSE` is on `master`, not `main`**) | 115,408 | 19,156 | 2026-11-20 | "The open-source app everyone uses to manage agents at work." More starred than every framework in `agents/top.md` Tier 1 combined. |
| [NousResearch/hermes-paperclip-adapter](https://github.com/NousResearch/hermes-paperclip-adapter) | MIT | 2,065 | 404 | 2026-04-04 | Runs Hermes "as a managed employee in a Paperclip company" — the shape the market is converging on: agents with a manager, a role and a review surface. |

Note the branch trap, which is the exact failure the fourth pass recorded: `paperclip`'s licence
file exists only on `master`. A probe that reads `main/LICENSE` and stops concludes a
115k-star repository is unlicensed.

### Searched and not found this pass

- **No LATAM-origin repository in the interaction layer.** The sweep's results were
  NA-origin (CopilotKit/Seattle, Vercel, Google, tambo) with one EMEA entry (Chainlit, Paris —
  and archived) and one APAC implementation (ByteDance's Lynx renderer for A2UI, Jun 2026).
  **Honest limit: this pass did not run a Spanish/Portuguese-vocabulary sweep**, so this is a
  gap in the measurement, not a measured zero. Next LATAM pass should run it before quoting a
  number.
- **Org location is unverifiable from this environment.** The `users/{org}` endpoint returns
  403 ("sessions are bound to their configured repositories"); only `search/repositories`
  works. Every region-origin attribution in this pass comes from web-search evidence about
  the company, not from GitHub metadata. Do not quote origin ratios to a client.
- **No foundation steward for the agent-to-user layer.** Searched; none exists. MCP, goose,
  AGENTS.md and the control plane are all under the Linux Foundation's AAIF. AG-UI is a
  vendor-held MIT protocol (CopilotKit, $27M Series A, May 2026) and A2UI is a Google-origin
  Apache-2.0 project. See `intel/trends.md` §15.


## 2026-11-20 — fourth pass

**Headline: the agent layer and the control plane are now both covered, and the thing still
missing was consequence. What is this agent allowed to *do* — spend money, read personal data,
believe a table?** Those three questions each turned out to be a layer this KB did not have.

The first three passes today moved through the stack in order: Tier-0 harnesses (pass 1), the
skill supply chain (pass 2), the control plane — gateway, quotas, cost, red-teaming (pass 3).
Each pass found the previous one had been looking one level too high. This pass went one level
*past* the control plane, to the blast radius, and found **sixteen repositories absent from the
KB entirely**, across four layers: agent payments, PII de-identification, catalog/lineage, and
graph RAG. The tables are in `repos/foundations.md`; the trend reading is in `intel/trends.md`
§13 and §14.

**1. There is now a payments layer, and it is not ready — which is itself the finding.**
Three permissively-licensed protocols compete at different layers:
[AP2](https://github.com/google-agentic-commerce/AP2) (Apache-2.0, 3,281 ★),
[ACP](https://github.com/agentic-commerce-protocol/agentic-commerce-protocol) (Apache-2.0,
1,607 ★) and the [A2A x402 extension](https://github.com/google-agentic-commerce/a2a-x402)
(Apache-2.0, 571 ★). **AP2 has 5.7× the stars of the x402 extension and has not been pushed
since 2026-06-17; the extension was pushed 2026-11-11.** The star ranking inverts the activity
ranking inside one protocol family. The client-facing consequence is specific: *the signed-mandate
model is the durable idea, the settlement rail is still contested, and no agent should reach a
payment rail in 2026 without a human approval step.* Anyone who says "AP2 is the standard" is
reading stars, not commits.

**2. Agent identity is the unsolved half of agent payments.** The payment specs answer *how
much* and *on whose mandate*; none answers *is this agent who it claims to be*.
[forter/trusted-agentic-commerce-protocol](https://github.com/forter/trusted-agentic-commerce-protocol)
(MIT, 180 ★) is the only entry addressing it, and it is small. This connects directly to the
workload-identity section already in `repos/foundations.md` (SPIFFE) — the same problem, now
with money attached, which is how it gets budget.

**3. Presidio left Microsoft.** The de facto PII engine is now
[data-privacy-stack/presidio](https://github.com/data-privacy-stack/presidio) (MIT, 11,989 ★),
not `microsoft/presidio`. Evidenced rather than assumed: the old path still serves files, but
`LICENSE` from both paths is **byte-identical (1,083 bytes, md5 `cef898d1…`)**, four other paths
return 200 on both, the copyright line now reads **"Presidio Contributors"**, and the search
index carries only the new org. **A redirect, not a deletion** — so existing installs keep
working, and that is exactly why nobody notices. Fourth repo in two passes to change
organisation; see the rename ledger.

**4. The data catalog category rebranded itself as agent infrastructure.**
[OpenMetadata](https://github.com/open-metadata/OpenMetadata) (Apache-2.0, 15,823 ★, **new to
this KB**) calls itself "The Open **Context Layer** for Data and AI";
[DataHub](https://github.com/datahub-project/datahub) (Apache-2.0, 13,006 ★) calls itself "The
**Context Platform** for your Data and AI Stack". Two independent vendors, pushed the same day,
converging on the same word. For an agent that writes to a system of record, the catalog is what
says which table it may *believe*, and lineage is how you answer "where did this number come
from?" after it has already acted. Commercially this is the best news in the pass: it is usually
**already installed** at the client.

**5. A 36,699-star MIT repo was missing.** [microsoft/graphrag](https://github.com/microsoft/graphrag)
had zero mentions across all eight files. Vector search finds the passage; graph retrieval answers
what connects entities across a whole corpus — an entity's exposure across contracts, suppliers or
incidents, which is the shape of the questions clients actually ask. **Scope the graph-construction
indexing cost explicitly**; it is paid per corpus, re-paid on refresh, and clients do not expect it.

**6. ISO/IEC 42001 is moving from a standard to cite to a gate you pass.** The KB already named it
as a standard to anchor on. The new reading is procurement: buyers are reported to be scoring it in
vendor questionnaires and RFPs, and to be asking for the **scope statement and sample risk
registers**, not just the certificate. Sources disagree on mandatory versus preferred, and
certification is reported to take **6–18 months** — so it is a pipeline question for Globant now,
not a 2027 one. Recorded with its disagreement intact in `intel/trends.md` §14.

**7. LATAM-origin: fifth consecutive zero, now measured in four new layers.** Payments, PII,
catalog and graph RAG were each searched in English, Spanish and Portuguese. Everything returned
was 0–3 stars and **NOASSERTION** — no usable licence. The gap is measured, not unexamined, and it
is the same answer five passes running.

**Evidence standard for this pass:** 16/16 licences read from each repository's own `LICENSE` over
`raw.githubusercontent.com`, none taken from a GitHub badge. Every non-GitHub host still fails to
resolve in this session, so **every market statistic below and in `intel/` remains second-hand** and
is attributed rather than asserted.

## 2026-11-20 — third pass (later still)

**Headline: the agent choice stopped being the interesting decision. The control plane is the
decision, and this KB did not have one.**

The earlier two passes today tracked the agent layer (Tier 0 harnesses) and the skill supply
chain. This pass went looking for the *traffic* layer — where a model or tool call is actually
authorised, routed, rate-limited, attributed and paid for — and found that the KB had no entry
for it at all. Not a thin section: nothing. No gateway, no quota point, no usage attribution,
no cost governance, no red-teaming, no eval-in-CI, no OpenTelemetry instrumentation. Six
sections now exist in `repos/foundations.md`; the twelve most important repositories were
absent from this KB entirely.

That gap is also the market's. **IDC FERS Wave 4 (July 2026): 95% of enterprises run at least
one company-funded agent-enabled workflow in production, and only 45.4% have real-time
dashboards tracking token consumption by workflow** — while **61.8% rate their own cost
governance as "defined" or "optimizing".** Self-assessment is running well ahead of
instrumentation, which is the most sellable gap in this KB.

**1. Envoy AI Gateway became Agent Router, and joined the Agentic AI Foundation.** The single
most consequential discovery of the pass:

| Repo | License | Stars | Pushed | What changed |
|------|---------|-------|--------|--------------|
| [theagentrouter/agent-router](https://github.com/theagentrouter/agent-router) | Apache-2.0 | 2,423 | 2026-11-19 | "The open source control plane for AI and agent traffic, powered by Envoy." **Formerly Envoy AI Gateway.** Now an **Agentic AI Foundation** project under LF Projects, LLC — `README`: *same code, same maintainers, same release cadence and Apache 2.0 license*. |

Why it matters beyond the rename: the AAIF now stewards **MCP, goose, AGENTS.md and the
control plane**. `intel/market.md` flagged that the agent-governance toolchain this KB
recommends is almost entirely NVIDIA's, including a repo whose vendor-neutral org name hides an
NVIDIA copyright. Agent Router is the **structural mitigation** — Apache-2.0, Envoy-based,
foundation-governed. For the first time a client can be told that the layer holding their
model credentials is not owned by a single vendor, and have it be true.

**2. The gateway field, verified and licence-read.** All metadata from the GitHub search API on
2026-11-20; carve-outs read from each `LICENSE`:

| Repo | Real license | Stars | Note |
|------|--------------|-------|------|
| [BerriAI/litellm](https://github.com/BerriAI/litellm) | **MIT core + `litellm/enterprise/` carve-out** | 63,615 | The adoption leader; now a Rust core with a Python SDK. Virtual keys, spend tracking and budgets are in the MIT core — SSO/RBAC reportedly are not. |
| [Kong/kong](https://github.com/Kong/kong) | Apache-2.0 | 44,402 | "The API and AI Gateway." Core permissive; AI features reportedly enterprise-gated — verify per feature. |
| [Portkey-AI/gateway](https://github.com/Portkey-AI/gateway) | **MIT, no carve-out found** | 13,421 | 1,600+ LLMs and **50+ guardrails enforced at the gateway**, not in application code. Cleanest licence in the category. |
| [maximhq/bifrost](https://github.com/maximhq/bifrost) | Apache-2.0 | 9,818 | LLM gateway and MCP gateway in one. Much of the comparative praise is published by its own vendor — discount accordingly. |
| [Helicone/helicone](https://github.com/Helicone/helicone) | Apache-2.0 | 6,291 | Observability-first. **Not** to be confused with `Helicone/ai-gateway` — **GPL-3.0, 647 ★, last pushed 2025-11-21**. |

**3. Cost governance is now a governance control, not a finance report.** New, and it is the
pass's commercial thesis — see `intel/trends.md` trend 12. **Gartner: spend on AI models and
platforms +63.4% YoY to $64B in 2026. FinOps Foundation: 98% of FinOps practitioners now manage
AI spend, up from 31% two years ago. EY: agentic AI converts fixed labour cost into variable
compute consumption**, and predicts 40% of agentic projects cancelled by 2027 (a prediction,
not a measurement). **McKinsey's framing is the one to use in a pitch: the unit of governance
should be the completed business outcome, not the token** — which is precisely how Globant's
**Glob.AI** already bills. The permissive tooling exists:
[openmeterio/openmeter](https://github.com/openmeterio/openmeter) (Apache-2.0, 2,457 ★) for
metering and entitlements, [opencost/opencost](https://github.com/opencost/opencost)
(Apache-2.0, 6,824 ★) for the GPU and pod cost that token counting never sees.

**4. Three large MIT agent repos were simply missing from this KB.** Recorded plainly, because
it is the same method failure the second pass admitted to — tracking frameworks by name misses
new shapes:

| Repo | License | Stars | Why it belongs |
|------|---------|-------|----------------|
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | MIT | 121,597 | AI browser agents. The answer when the client's "integration surface" is a vendor web portal with no API — insurance, logistics, public-sector filing. |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | MIT | 85,545 | "Long-horizon SuperAgent harness." **APAC-origin.** A fourth MIT harness larger than every Tier-1 framework. |
| [letta-ai/letta](https://github.com/letta-ai/letta) | Apache-2.0 | 25,503 | Stateful agents with learning memory (MemGPT lineage). **Pushed 2026-10-18** — verify activity. |

**5. Red teaming exists, is permissive, and has one licence trap.** Static skill scanning is
already being bypassed (see the second pass below); the dynamic control is adversarial testing.
[NVIDIA/garak](https://github.com/NVIDIA/garak) (Apache-2.0, 10,114 ★) and
[microsoft/PyRIT](https://github.com/microsoft/PyRIT) (MIT, 4,980 ★) are both real and active —
**note PyRIT moved**: `Azure/PyRIT` is the stale old home at 128 ★ / 2026-03-25.
[promptfoo/promptfoo](https://github.com/promptfoo/promptfoo) (MIT, 27,494 ★) does eval **and**
red-teaming and is built to run as a CI gate. **The trap:**
[meta-llama/PurpleLlama](https://github.com/meta-llama/PurpleLlama) (4,486 ★) is routinely
proposed as an open guardrail — its `LICENSE` is the **Llama 3.2 Community License Agreement**,
not OSI open source. GitHub shows it as `NOASSERTION`, which is why the mistake is common.

**6. Two more unusable-at-scale repositories, and one mis-scoped one.**
[daytonaio/daytona](https://github.com/daytonaio/daytona) — infrastructure for running
AI-generated code, **71,307 ★** — has **no `LICENSE` file** and was last pushed 2026-07-24.
[getzep/zep](https://github.com/getzep/zep) (Apache-2.0, 5,010 ★) still gets scoped as
self-hosted memory; its `README` now reads *"Zep: Examples and Integrations"* and Zep itself is
a hosted product. For self-hosted memory use
[topoteretes/cognee](https://github.com/topoteretes/cognee) (Apache-2.0, 33,431 ★) or Mem0.

**7. Method note that paid for itself: three of ~35 repos checked had moved, two changed
organisation.** Envoy AI Gateway → Agent Router, `Azure/PyRIT` → `microsoft/PyRIT`,
`explodinggradients/ragas` → `vibrantlabsai/ragas`. An ownership change is a supply-chain event,
not a cosmetic one. Full ledger in `repos/foundations.md`. **This is sellable as a
dependency-provenance review line item.**

**Verification note.** Every repository fact above is first-hand (search API metadata plus
`LICENSE` read from `raw.githubusercontent.com`). Every market figure is from WebSearch result
summaries and **not read at source** — this session's network policy resolves GitHub only;
`curl` and page fetches to Gartner, IDC, Menlo, OECD and Stanford all failed, so the same
caveat as the earlier passes applies, and several of the sources above are vendor or analyst
marketing.


## 2026-11-20 — second pass (later same day)

**Headline: the harness won, and it arrived carrying a skill supply chain nobody has
secured. This is the enterprise opening of the quarter.**

Earlier today this file recorded the foundation-governance story and treated OpenClaw as a
singular breakout. Both stand, but a wider sweep of the GitHub star ceiling shows the
category is now *three* MIT harnesses of comparable scale plus an enormous, largely
ungoverned skills economy on top of them.

**1. Three harnesses, not one.** All verified today, licenses read from each `LICENSE` file:

| Harness | Repo | License | Stars | Pushed |
|---------|------|---------|-------|--------|
| OpenClaw | [openclaw/openclaw](https://github.com/openclaw/openclaw) | MIT | 394,891 | 2026-11-20 |
| DeepSeek Harness | [deepseek-ai/deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | MIT | 284,581 | 2026-11-18 |
| Hermes Agent | [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | MIT | 264,904 | 2026-11-20 |
| Deep Agents | [langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) | MIT | 31,472 | 2026-11-20 |

DeepSeek Harness and Hermes Agent were **entirely absent from this KB** until this pass —
a 284k-star and a 264k-star MIT repository in the exact category the KB exists to cover.
Recorded plainly because it says something about method: the KB was tracking *frameworks*
by name and missed a new *category*.

**2. The skills economy is now the biggest thing on GitHub, and it is a supply chain.**
[openclaw/clawhub](https://github.com/openclaw/clawhub) (MIT, 9,557 ★) is the official
skill + plugin registry; [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills)
(MIT, 53,885 ★) curates **5,400+ skills** filtered from it. Individual skill collections are
larger still — [mattpocock/skills](https://github.com/mattpocock/skills) (MIT, 328,581 ★),
[obra/superpowers](https://github.com/obra/superpowers) (MIT, 322,580 ★),
[affaan-m/ECC](https://github.com/affaan-m/ECC) (MIT, 307,599 ★). Two of the biggest have
**no license at all**: [anthropics/skills](https://github.com/anthropics/skills) (197,931 ★)
and [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
(234,677 ★) — both checked against `LICENSE`, `LICENSE.md`, `LICENSE.txt`, `LICENSE-MIT` and
`COPYING` on `main` and `master`.

**3. NVIDIA quietly shipped the governance toolchain for all of it — Apache-2.0.** This is
the single most useful discovery of the pass, because it is exactly the layer Globant sells
and it is now permissively licensed and off the shelf:

| Repo | License | Stars | Role |
|------|---------|-------|------|
| [NVIDIA/SkillSpector](https://github.com/NVIDIA/SkillSpector) | Apache-2.0 | 27,027 | Security scanner for agent skills — **71 vulnerability patterns across 17 categories** (read from its README; a secondary roundup said 64/16 — the README is authoritative). Covers prompt injection, data exfiltration, privilege escalation, memory poisoning, MCP tool poisoning, MCP least privilege. |
| [NVIDIA/SkillEvaluator](https://github.com/NVIDIA/SkillEvaluator) | Apache-2.0 | 4,224 | Quality gates for skills: security scanning, harness-compatibility checks, semantic overlap detection, synthetic eval datasets, live agent evaluation. **Ships reusable CI templates.** |
| [ai-openshell/OpenShell](https://github.com/ai-openshell/OpenShell) | Apache-2.0 | 21,829 | "The safe, private runtime for autonomous AI agents" (Rust). Note: the neutral org name hides vendor provenance — its `LICENSE` reads **"Copyright (c) 2026 NVIDIA CORPORATION & AFFILIATES"**, and [NVIDIA/OpenShell-Community](https://github.com/NVIDIA/OpenShell-Community) (Apache-2.0, 193 ★) mirrors it. |
| [NVIDIA/NemoClaw](https://github.com/NVIDIA/NemoClaw) | Apache-2.0 | 23,057 | Runs Hermes, Deep Agents and OpenClaw inside OpenShell with managed inference — the bridge from a developer's harness to a governed one. |
| [NVIDIA/NeMo-Relay](https://github.com/NVIDIA/NeMo-Relay) | Apache-2.0 | 254 | Multi-language agent runtime: execution-scope management, lifecycle events and **middleware on tool and LLM calls** — i.e. the interception point where a policy decision can actually be enforced. |
| [NVIDIA/auto-ontology](https://github.com/NVIDIA/auto-ontology) | Apache-2.0 | 14,026 | Semantic, graph-based reasoning layer over data: deterministic query generation, better retrieval, explainable agent workflows. |

**4. The research says the scanners are already being bypassed.** Figures below come from
WebSearch result summaries — **this session's network policy allows GitHub only, so the
underlying papers could not be opened and these are second-hand**. Flagged as such rather
than dropped, because the direction is consistent across four independent samples:
an arXiv study (2601.10338, Jan 2026) analysing **31,132 skills found 26.1% with at least
one vulnerability** across 14 patterns; Snyk's *ToxicSkills* research found **36% of 3,984
ClawHub skills contained prompt-injection techniques**; a third analysis of the same sample
put **critical-severity flaws at 13.4%**; a fourth found **80% of skills had a mismatch
between declared and actual behaviour** (mostly bad documentation, not malice). And on the
defences: Trail of Bits reportedly bypassed the malicious-skill detectors of ClawHub, Cisco
and Vercel's skills.sh, and the Cloud Security Alliance notes **five malicious skills evaded
updated ClawScan *and* VirusTotal between February and May 2026**. Consensus remedy is
layered: scan, pin provenance, check declared capability against observed behaviour, and
sandbox — because skills run with the agent's own OS permissions.

**So what, for an engagement:** every client who adopted a harness this year also adopted an
unaudited dependency tree of natural-language skills that execute with their agent's
privileges. Nobody sold them a control for it. SkillSpector + SkillEvaluator + OpenShell are
Apache-2.0 and exist today. That is a scoped, demonstrable, repeatable engagement — written
up as `compose/patterns.md` **Receta 7**.

*Regional note:* every repo in this section is Global or North-America-origin (NVIDIA,
LangChain, Nous Research) or APAC-origin (DeepSeek). **No EMEA-origin and no LATAM-origin
project appears anywhere in the harness or skill-security layer** — searched
`agentes IA empresa` (one hit, 38 ★, unlicensed) and the `latam-gpt` org (8 repos, 7 of them
unlicensed, most last pushed in 2024–2025). A measured absence, not an unchecked one.

---

## 2026-11-20

**Headline: agent governance moved from vendor to foundation, and it is visible in the repo URLs.**

- **Block's `goose` now lives at [aaif-goose/goose](https://github.com/aaif-goose/goose)**
  (Apache-2.0, 56,815 ★). The org prefix is the story: the project has moved under the
  Linux Foundation's **Agentic AI Foundation (AAIF)**, formed 9 Dec 2025, to which
  Anthropic donated MCP and OpenAI donated AGENTS.md. Any integration pinned to the old
  `block/goose` path needs updating.
- **AGENTS.md became its own governed standard**: [agentsmd/agents.md](https://github.com/agentsmd/agents.md)
  (MIT, 25,620 ★) — a single open format for instructing coding agents, now the de facto
  way to ship repo-level agent context to a client's codebase.
- **MCP is relicensing MIT → Apache-2.0.** The `LICENSE` of
  [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
  (92,133 ★) now opens by declaring the transition explicitly. Consistent with the
  foundation move; Apache-2.0's patent grant is the enterprise-relevant part.
- **AutoGen is effectively over as a starting point.** [microsoft/autogen](https://github.com/microsoft/autogen)
  (61,955 ★) has not been pushed since 2026-11-12 and GitHub reports its license as
  CC-BY-4.0. Successors: [ag2ai/ag2](https://github.com/ag2ai/ag2) (Apache-2.0, 5,076 ★)
  and Microsoft Agent Framework — **but see the MAF 404 gap in `agents/top.md`.**
- **PraisonAI repositioned onto regulated industries**: its description now reads
  "Private AI agents for highly regulated teams" ([MervinPraison/PraisonAI](https://github.com/MervinPraison/PraisonAI),
  MIT, 9,365 ★). A small repo, but the clearest signal that 2026's differentiator is
  compliance posture rather than capability.
- **APAC frameworks are now top-tier, not followers.** [agentscope-ai/agentscope](https://github.com/agentscope-ai/agentscope)
  (Apache-2.0, 36,363 ★) plus a dedicated JVM port
  [agentscope-ai/agentscope-java](https://github.com/agentscope-ai/agentscope-java)
  (Apache-2.0, 6,435 ★) — the Java port matters because APAC enterprise cores are JVM.
- **Observability consolidated into the data layer.** The `LICENSE` of
  [langfuse/langfuse](https://github.com/langfuse/langfuse) (37,671 ★) now carries
  **"Copyright (c) 2023-2026 ClickHouse, Inc."** — confirming ClickHouse's acquisition
  of Langfuse, announced 16 Jan 2026 alongside its $400M Series D. Langfuse core stays
  MIT with `ee/` carve-outs.

*Regional note:* every item above is Global or APAC-origin. **No LATAM-origin agent
project appeared in this week's sweep** — searching `agente IA empresa open source`,
`agentes IA español framework` and `ERP brasil open source nota fiscal` returned one
repo with 0 stars. That is a measured absence, not an unchecked one.

---

## Historical — 2026-07-02 (automated pipeline snapshot)

> Kept for trend history, deliberately fenced as plain text so the compiler does **not**
> ingest it as entities. These rows came from a keyword-matching ingest pipeline and are
> low quality — several are sub-10-star or unrelated to enterprise AI (an Excel-based farm
> ERP, a food-delivery suite). Superseded by the curated sections above.
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
