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

## Estado de la KB — medido, no estimado (vigesimotercer pase, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Líneas de contenido | **20.093** |
| Direcciones de repositorio distintas | **701** (+35) |
| …en `github.com` | 680 |
| …en `gitlab.com` | 21 |
| Direcciones verificadas este pase | **32** (SPDX, ★, rama por defecto, `archived` y último push medidos) |
| …de ellas **nuevas** para la KB | **32** (las 32; dedup medido antes de buscar: 0 apariciones previas) |
| Recetas numeradas en `compose/patterns.md` | **48** |
| Tendencias numeradas en `intel/trends.md` | **47** (en dos series heredadas; este pase numeró 40-42, por encima del máximo de ambas) |
| Clases de licencia registradas | **21** (+`MIT-0`, +`PSF-2.0`, +`Sendmail Open Source License`) |
| Formas registradas de equivocarse | **52** (+T89 a T92) |
| Proyectos archivados-o-desaconsejados pero recomendados | **16** |
| Preguntas registradas como **sin resolver** | **19** |

> **Nota de estado, para que no se herede un dato viejo:** este bloque decía «decimoctavo pase» y
> **546 direcciones**. Los pases **diecinueve a veintidós** empujaron contenido (859, 1.018, 916 y
> 648 inserciones) **sin actualizar este bloque**, así que la cifra llevaba cuatro pases obsoleta.
> El valor correcto, **medido** con un regex consciente de la forja: **701**.

> **Lea esto antes de prometer que un agente puede escribir a un cliente.** Veintidós pases
> construyeron once límites —lectura, escritura, procedencia, contención, borrado, accesibilidad,
> pesos, idioma, el documento fiscal, el calendario, el sistema heredado, el ciclo de vida, la voz y
> la tenencia— y **ninguno preguntó con qué dominio firma el agente**. Medido antes de buscar, sobre
> **19.436 líneas** y los nueve ficheros: `DMARC` **0** · `DKIM` **0** · `SPF` **0** · `ARC` **0** ·
> `BIMI` **0** · `MTA-STS` **0** · `SMTP` **0** · `IMAP` **0** · `phishing` **0** ·
> `suplantación` **0** · `rebote`/`bounce` **0** · `unsubscribe` **0** · `buzón` **0** ·
> `correo electrónico` **0** · `remitente` **1** —y esa única aparición era de **voz**, la
> pre-declaración de CLI de TRAI del pase veintiuno. **El pase veintiuno dio a esta KB el canal
> hablado; el canal escrito, que es por el que una empresa alcanza de verdad a un cliente o a un
> proveedor, no se había hecho nunca.**
>
> **EL HALLAZGO DEL PASE: EL ESTÁNDAR DEL CANAL SE REESCRIBIÓ EN MAYO DE 2026 Y SU IMPLEMENTACIÓN
> DE REFERENCIA ES ANTERIOR A LA REESCRITURA.** DMARCbis se publicó el **2026-05-19** como
> **RFC 9989**, que deja obsoletos el **RFC 7489** y el **RFC 9091**, con **RFC 9990** (informes
> agregados) y **RFC 9991** (informes de fallo). **`pct` se eliminó, no se marcó obsoleto**: la rampa
> `p=none → quarantine → reject` ya no se expresa con un porcentaje sino con un indicador binario
> **`t=y`/`t=n`**; `rf` y `ri` desaparecen; y el dominio organizativo se resuelve con un **DNS Tree
> Walk** en lugar de la lista de sufijos públicos. **Enfrente, el código:**
> `trusteddomainproject/OpenARC` —la implementación de referencia de **ARC**, que es lo que hace que
> el correo **reenviado y las listas de distribución sobrevivan a DMARC**— **no recibe un commit
> desde el 2024-04-19**, tiene **150 ★** (el más estrellado de los tres hermanos) y **no está
> archivada**, así que la forja la muestra viva; `OpenDKIM` sigue en **`2.11.0~beta2`** y
> `OpenDMARC` en **1.4.2 desde 2021**. **Para un cliente esto no es trivia: la progresión de política
> que su proveedor le documentó con `pct` ya no es la que describe el estándar vigente.** El
> sustituto permisivo y vivo existe y ningún tutorial lo nombra: **`emersion/go-msgauth` (MIT,
> 231 ★, push 2026-11-06)**, que implementa DKIM **y ARC** (Receta 47).
>
> **La capa no tiene agentes, igual que la tenencia del pase veintidós.** Agentes de correo con IA
> reales: **dos** —`Mail-0/Zero` (**MIT**, 10.900 ★) y `elie222/inbox-zero`
> (`NOASSERTION` → **AGPL-3.0** leída byte a byte en **36.236 B**, 13.112 ★, **no proponible** porque
> la AGPL alcanza al servicio en red, que es la forma de entrega)—. Y **las manos del agente sobre el
> buzón están muertas o paradas**: `GongRzhe/Gmail-MCP-Server` (**MIT**, 1.173 ★), el servidor MCP de
> Gmail **más recomendado de los listados**, está **ARCHIVADO** desde el 2025-08-06
> —**decimosexto archivado-pero-recomendado**, y el delator es el de siempre: lo recomienda la
> documentación adyacente al propio ecosistema— y su alternativa `MarkusPfundstein/mcp-gsuite`
> (**MIT**, 492 ★) lleva **19 meses sin un commit** sin estar archivada. **El remitente no se compra:
> se construye** (Receta 46).
>
> **Tres clases de licencia nuevas, y las tres salen de que la forja no sabe leer esta capa.** De
> 32 direcciones, **8 devolvieron `NOASSERTION` y 1 devolvió `null`**, y al resolverlas aparecieron
> **seis veredictos distintos**. (1) **`nodemailer` (17.717 ★)**, la biblioteca de envío de medio
> ecosistema Node, trae un `LICENSE` de 935 B que es un **MIT truncado**: dice *«subject to the
> following conditions:»* y **no enumera ninguna condición**, salta al descargo de garantía. La
> autoridad es el registro: `registry.npmjs.org/nodemailer/latest` → **v10.6.1, `license: "MIT-0"`**
> — **clase nº 19**, y **la diferencia práctica entre fichero y registro es si hay que atribuir o
> no**. (2) **`OpenDKIM` y `OpenDMARC`** comparten un `LICENSE` **byte a byte idéntico** (**2.238 B**,
> `diff` vacío) con **doble régimen por FICHERO** — Trusted Domain Project (estilo BSD-3) **+
> Sendmail Open Source License**, y textualmente *«Files bearing both banners are covered under both
> sets of license terms»*: **la licencia depende de qué ficheros copiaste**, tercera aparición del
> patrón tras `eggert/tz`, **clase nº 21**. Y su hermano **`OpenARC` es BSD-2-Clause limpia**: *tres
> repos de una organización, dos regímenes* — el espejo exacto de T87, **la licencia es por
> repo-entregable, no por organización**. (3) **`sdgathman/pyspf`** → **PYTHON SOFTWARE FOUNDATION
> LICENSE v2**, **clase nº 20**: permisiva, pero ninguna de las 18 que había.
>
> **Y el caso que obliga a distinguir `NOASSERTION` de `null`: `stalwartlabs/stalwart`, 16.280 ★,
> NO TIENE FICHERO DE LICENCIA.** Ocho rutas canónicas probadas en `main`, **ocho 404**, y el
> `Cargo.toml` de la raíz **sin campo `license`**. Su AGPL-3.0 vive en **una insignia del README** y
> en la frase *«Stalwart remains licensed under the AGPL-3.0»*. El mismo README reparte el producto:
> *«About 85% of Stalwart's features are free and open source under the AGPL-3.0»*, y el resto es
> Enterprise — ***multi-tenancy, SCIM provisioning, sharded storage and live telemetry***.
> **Eso es el límite de la tenencia del pase veintidós, con precio**, y es la **tercera** vez que
> esta KB mide el mismo reparto (Onyx: *permission sync* sólo en `ee/`; Weaviate: licencia partida;
> Stalwart: multi-tenencia y SCIM en Enterprise): **lo que se licencia no es la función, es el
> aislamiento y el aprovisionamiento entre clientes.**
>
> **Tercera confirmación independiente en tres pases consecutivos del reparto permisivo/recíproco.**
> Las bibliotecas y los servidores son MIT/Apache-2.0/BSD (`go-msgauth`, `mailauth`, `mox`, `james`,
> `haraka`, `postal`, `chasquid`, `rspamd`); **las aplicaciones con las que un humano manda campañas
> son copyleft sin excepción**: Mautic (GPL-3.0), listmonk (AGPL-3.0, **24.446 ★**, la más estrellada
> de la capa), Keila (AGPL-3.0) e `inbox-zero` (AGPL-3.0) — **cuatro de cuatro**. El pase diecisiete
> lo midió en el transporte AS4/Peppol y el dieciocho en las aplicaciones de calendario. **Tres capas
> sin relación y el mismo reparto**: lo empaquetable es la tubería; la excepción permisiva de esta
> capa es **Apache James** (Apache-2.0, push **2026-11-24T21:27Z**, doce minutos antes de verificarlo).
>
> **El canal lo regulan tres proveedores de buzón, no un parlamento, y esa es la lectura comercial.**
> **No hay mandato DMARC vinculante en toda la UE** —NIS2 Art. 21 es **basada en riesgo y neutral
> tecnológicamente**, así que la autenticación *evidencia* el cumplimiento, no es un control
> exigido—, y sin embargo ningún correo masivo entra en Gmail sin autenticar: **Google y Yahoo desde
> febrero de 2024** (~**5.000 mensajes/día** a cuentas personales de Gmail), **Microsoft desde mayo
> de 2025** para Outlook.com, **baja en un clic (RFC 8058)** en marketing y **queja < 0,3 %**.
> **La regla privada llega antes y se aplica más rápido que la norma pública**, así que el criterio
> de aceptación de un agente que manda correo **se escribe contra la política de un proveedor de
> buzón** —verificable hoy, sin período de transposición— y se entrega como **dossier del remitente**
> (Receta 48). Adopción de las capas superiores, aún marginal: **MTA-STS 1,1 % · BIMI 2,4 % ·
> DANE 4,3 %** frente a **DMARC 64 %** (top-1M apto para correo, jun-2026), con **56 %** de los que
> publican MTA-STS en `enforce`. *Una segunda medición (Tranco top-10.000) da MTA-STS 2,6 %,
> TLS-RPT 3 % y BIMI 9,5 %, con sólo ~0,7 % con todas las capas: la discrepancia es de **muestra**,
> y se registran las dos.*
>
> **Cuatro reglas de método nuevas, reutilizables por toda la flota.** **T89** — un fichero llamado
> **`LICENSE.md`** correlacionó con `NOASSERTION` en **2 de 2** casos (`rspamd` → Apache-2.0,
> `Mailu` → MIT, ambos verbatim): **se registra la correlación y NO se afirma el mecanismo** (puede
> ser la extensión o la línea de copyright modificada). **T90** — el **registro de paquetes gana
> cuando el fichero está ROTO, no sólo cuando falta**: extiende la regla de `date-fns` del pase
> dieciocho al caso peor, el fichero presente y malformado, que invita a confiar. **T91** — una
> **licencia compuesta** se localiza **por número de línea**: `mautic` responde `NOASSERTION` porque
> su `LICENSE.txt` de 38.326 B abre con avisos de terceros (Apache-2.0 de *Mousetrap*, línea 54) y no
> llega a la **GPL-3.0** hasta la **línea 91**. **T92** — **una insignia del README no es un fichero
> de licencia**: probar ocho rutas canónicas y el manifiesto antes de registrar nada.
>
> **Límite declarado, y la asimetría de siempre, peor que de costumbre en lo normativo.** Todo lo de
> **licencias, estrellas, ramas, `archived` y fechas de push es byte a byte o medido en API**. Todo lo
> **normativo y de mercado es a nivel de resumen de búsqueda** y va marcado donde aparece. **Las
> cuatro fuentes primarias del hallazgo principal son inalcanzables desde esta sesión**:
> `www.rfc-editor.org`, `datatracker.ietf.org`, `www.ietf.org` y `data.iana.org` devuelven **000** (no
> resuelven) con GET por rango. **RFC 9989, 9990 y 9991 NO se leyeron en primario**, ni tampoco la
> documentación oficial de Google, Yahoo, Microsoft ni Apple. **Conflictos declarados en lugar de
> promediados:** si Microsoft *exige* RFC 8058 o sólo recomienda una baja funcional; si Apple lo
> aplica en 2026-2027 o lo recomienda; el orden de los *milter* OpenDMARC/OpenARC (el propio tracker
> dice una cosa y una guía de 2026 la contraria); el régimen de Singapur (**tres fuentes, tres
> respuestas**: opt-out, opt-in y exención B2B); el plazo de baja en Brasil (**1 día / 15 días / «con
> prontitud»**); y la afirmación de que el regulador brasileño cambió de nombre por la **MP
> 1.317/2025** y la **Lei 15.352/2026**, **que no se pudo corroborar en ninguna otra fuente** y por
> eso **no debe citarse a un cliente**. **Hueco LATAM medido en español** —`correo electrónico`,
> `remitente`, `buzón`, `suplantación`— : **ninguna de las 32 direcciones es de origen
> latinoamericano**, todas norteamericanas o europeas; es un **cero medido, no un silencio**.
> **Item abierto sobre el sesgo de forja:** no se repitió la auditoría T83 porque esta capa tiene su
> propio sesgo ya documentado —`chasquid` y `spamassassin` **se declaran espejos** de primarios fuera
> de GitHub, y **Postfix y Exim, los dos MTA más desplegados del mundo, no tienen repositorio
> canónico en GitHub en absoluto**—, así que el catálogo de esta capa **infrarrepresenta
> estructuralmente** a los dos emisores que más correo mueven. **Corrección de método que se apunta
> contra uno mismo:** este pase sospechó que `microsoft/presidio` se había movido y que las 83 citas
> de la KB apuntaban a una dirección vieja; al comprobarlo, **la KB ya escribía
> `data-privacy-stack/presidio`** en sus 12 direcciones. **Segundo pase consecutivo en que la KB va
> por delante de la sonda del propio pase**, que es exactamente lo que T88 predice: *un hueco falso
> se publica como noticia y degrada el dato correcto*.

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
