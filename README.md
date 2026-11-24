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

## Estado de la KB — medido, no estimado (vigesimocuarto pase, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Líneas de contenido | **21.022** (+881) |
| Direcciones de repositorio distintas | **741** (+44) |
| …en `github.com` | 720 |
| …en `gitlab.com` | 21 |
| Direcciones **probadas** este pase | **45** — de las que **44 existen** y **1 era una conjetura propia** (404) |
| …de ellas **nuevas** para la KB | **44** (dedup medido antes de buscar: sólo `documenso/documenso` tenía apariciones previas) |
| Recetas numeradas en `compose/patterns.md` | **52** (+49 a 52) |
| Tendencias numeradas en `intel/trends.md` | **46** (+43 a 46) |
| Clases de licencia registradas | **21** (**ninguna nueva**, y se dice en lugar de inflar la cifra) |
| Formas registradas de equivocarse | **57** (+T93 a T97) |
| Proyectos parados-o-archivados pero recomendados | **18** (+Sphereon, +la organización `OpenICP-BR` entera) |
| Preguntas registradas como **sin resolver** | **22** |

> **Nota de instrumentación, porque esta vez el instrumento cambió de carril.** En esta sesión
> `api.github.com` **y** `github.com` devuelven **403** —el acceso a la API está limitado a los
> repositorios adjuntos—, así que **este pase no tiene ni una estrella ni una bandera `archived`,
> y no finge tenerlas.** Lo que funciona es el carril de lectura anónima de git:
> `git clone --bare --depth 1 --filter=blob:none` + `git log -1 --format=%cI` da la **fecha real
> del último commit en ~0,5 s y 196 KB por repositorio**, y `raw.githubusercontent.com` da el
> **fichero de licencia byte a byte**. **La fecha del último commit es mejor evidencia que
> `pushed_at`**, que se mueve con cualquier rama mientras el commit no. **Contrapartida honesta:
> sin `archived` este pase no puede distinguir «archivado» de «parado», y por eso dice siempre
> «sin commit desde X».** Los dos contadores de direcciones de esta KB discrepaban en uno al
> cerrar el pase; la causa se encontró (una dirección escrita en prosa y no como enlace) y se
> corrigió, y ahora ambos dan **+44**.

> **Lea esto antes de prometer que un agente puede firmar algo.** Veintitrés pases construyeron
> catorce límites —lectura, escritura, procedencia, contención, borrado, accesibilidad, pesos,
> idioma, el documento fiscal, el calendario, el sistema heredado, el ciclo de vida, la voz, la
> tenencia y el remitente— y **ninguno preguntó qué hace que lo que el agente produce se
> sostenga**. Medido antes de buscar, sobre **20.141 líneas** y los nueve ficheros: `eIDAS` **0** ·
> `PAdES` **0** · `CAdES` **0** · `e-signature` **0** · `firma electrónica` **0** ·
> `qualified signature` **0** · `RFC 3161` **0** · `sello de tiempo` **0** · `no repudio` **0** ·
> `non-repudiation` **0** · `trust list` **0** · `TSP` **0** · `certificate authority` **0** ·
> `C2PA` **0** · `RFC 9421` **0** · `Web Bot Auth` **0** · `verifiable credential` **0** ·
> `SD-JWT` **0** · `EUDI` **0** · `mDL` **0** · `pyHanko` **0** · `EJBCA` **0** — y `XAdES` **2**,
> `DocuSign` **4**. **El pase noveno dio a esta KB la firma de un *build* (`sigstore` 46,
> `SLSA` 54, `in-toto` 44 apariciones). Firmar un build no es sellar un documento.** El pase 17
> dio el documento fiscal y el 23 el canal para enviarlo; **lo que lo firma no se había hecho
> nunca.**
>
> **EL HALLAZGO DEL PASE: UN AGENTE NO PUEDE *FIRMAR*; SÓLO PUEDE *SELLAR*.** El Reglamento (UE)
> 910/2014 separa dos actos que el castellano comercial mezcla y que ningún listado de
> herramientas distingue. La **firma** electrónica cualificada es de una **persona física**,
> acredita **origen, integridad y voluntad**, y **no es automatizable** porque exige control
> exclusivo del firmante (Art. 25 y ss.). El **sello** electrónico cualificado es de una **persona
> jurídica**, acredita **origen e integridad pero no voluntad**, y **es automatizable: ése es su
> caso de uso** (Arts. 35–40). **Consecuencia de arquitectura, y es la que se factura: el agente
> prepara, rellena, envía y *sella*; la *firma* la pone una persona.** Meter el certificado de
> firma de un humano en una tubería automática **no es un atajo técnico: es una atribución falsa
> de voluntad**, y es el primer defecto que busca un abogado contrario (Receta 49).
>
> **La capa SÍ tiene agentes —al contrario que la tenencia y el remitente— y el único bien
> diseñado pone la puerta en el servidor.** Cuatro verificados: `varops/signed-md` (**AGPL-3.0**,
> commit **2026-11-24**), `imagine-ai-inc/sign` (**MIT**), `hanzoai/sign` (**AGPL-3.0**) y
> `signbee/skill` (**MIT**, que no es un servidor sino una *skill*, y por eso traslada el límite al
> proveedor en vez de resolverlo). El README de `signed-md`, **leído en primario (12.754 B)**, dice
> *«Your agents handle the paperwork. **People approve and sign**»*, *«Only a person approves a
> template, and an agent can only send the exact revision a person saw»* y la frase que importa:
> *«**Guardrails the agent can't talk its way around. These live in the server, not in a
> prompt**»*. **Eso es el reparto firma/sello del Reglamento sin citarlo** — primera vez en 24
> pases que esta KB encuentra una herramienta cuyo diseño coincide con una obligación jurídica que
> la herramienta no menciona. **Y el reparto cruel de la capa: lo que se puede entregar no tiene la
> puerta, y lo que tiene la puerta no se puede entregar.**
>
> **La decisión de presupuesto, medida byte a byte: la biblioteca completa es copyleft y la
> permisiva se declara beta.** `esig/dss` —de la **propia Comisión Europea**, la **única** con
> PAdES + CAdES + XAdES + JAdES **y validación contra listas de confianza**— es **LGPL-2.1**
> (`LICENSE`, **26.530 B**, último commit 2026-10-14). `MatthiasValvekens/pyHanko` —única ruta
> permisiva completa a PAdES— es **MIT** (**1.080 B**) y arrastra un aviso de *beta / not
> production-ready* **mientras recibía un commit el 2026-11-23**: el aviso es más viejo que el
> repositorio, y **se registra la contradicción en lugar de resolverla en su favor**. La LGPL-2.1
> **se enlaza dinámicamente sin contaminar el producto**: lo que decide es el **empaquetado**, no
> el permiso. **Y la pieza del sello automatizado existe y no aparece en ninguna lista de
> «alternativas a DocuSign»**: `Keyfactor/signserver-ce` (**LGPL-2.1**) — porque las listas
> comparan productos para personas y el sello no es un producto para personas.
>
> **Dos fechas de diciembre de 2026 y el agente está justo en medio.** El **Art. 50(2) del AI
> Act** (marcado **legible por máquina** de la salida sintética) es aplicable desde el
> **2026-08-02**, con transición hasta el **2026-12-02** para sistemas ya en el mercado
> (*AI Omnibus*); y el **2026-12-24** cada Estado miembro debe **ofrecer** una **cartera EUDI** y
> el sector público **aceptarla**, con las **partes privadas** obligadas a aceptarla el
> **2027-12-24** (micro y pequeñas exceptuadas). *Conflicto declarado: una fuente da 2026-12-31
> para la cartera; la que sostiene el plazo de 24 meses es el **24**.* **No son dos proyectos, es
> uno: un agente empresarial en la UE tiene que poder marcar lo que genera y aceptar una identidad
> que no emitió él.** Y la respuesta de manual —«usamos C2PA»— **no cubre texto**, porque el
> manifiesto C2PA vive **en el fichero**: para texto hace falta marca de agua en el muestreo
> (`google-deepmind/synthid-text`, **Apache-2.0**). El entregable es una **matriz de divulgación
> por tipo de salida**, no una herramienta (Receta 51).
>
> **El reparto dentro de una misma organización, y es el dato comercial (T95).**
> `eu-digital-identity-wallet` publica **las apps de cartera en AGPL-3.0** (**13.961 B**) y **las
> bibliotecas y el verificador en Apache-2.0** (**9.425 B**). **El lado en el que está una empresa
> cliente —el que verifica— es justo el permisivo:** se puede entregar un verificador de cartera
> dentro de un producto cerrado; **no** se puede forkear la cartera del Estado dentro de uno.
> Cuarta confirmación de que **la licencia es por repo-entregable y no por organización**, y la
> primera que corta justo entre **producto** y **biblioteca**. Y **las especificaciones no son
> código**: el ARF trae `LICENCE` —ortografía británica, **249 B**— con **CC-BY-4.0**, y el perfil
> italiano va en **CC0-1.0**.
>
> **Quinta confirmación consecutiva del reparto permisivo/recíproco.** Las bibliotecas y los
> servidores son MIT/Apache-2.0/BSD/LGPL (`pyHanko`, `bc-java`, `pdfbox`, `c2pa-rs`, `c2patool`,
> `synthid-text`, `credo-ts`, `multipaz`, `sd-jwt-python`, `web-bot-auth`, `cfssl`,
> `smallstep/certificates`, `uts-server`, `dss`, `OpenSC`, `EJBCA-CE`, `SignServer-CE`); **las
> aplicaciones con las que un humano hace el acto jurídico son copyleft sin excepción**:
> `documenso`, `docuseal`, `OpenSign`, `hanzoai/sign` y `signed-md` — **cinco de cinco AGPL-3.0**.
> Los pases 17 (AS4/Peppol), 18 (calendario), 22 (tenencia) y 23 (correo) midieron el mismo
> reparto. **Cinco capas sin relación técnica y la misma ley**, y aquí con una vuelta de tuerca:
> **el acto jurídico es justo el que no se puede automatizar, así que la pieza AGPL es la pieza
> donde está la persona. No es coincidencia: el humano y el copyleft viven en el mismo sitio.**
>
> **La región se invierte, y eso cambia qué se factura.** **EE. UU. no tiene nivel cualificado ni
> lista de confianza**: ESIGN y UETA son **de un solo nivel** y neutrales tecnológicamente (49
> estados con UETA, Nueva York con su **ESRA**), y lo que la ley pide son **intención,
> consentimiento, asociación y retención**. **En la UE se vende el certificado y la lista de
> confianza; en EE. UU. se vende el rastro de auditoría** — el mismo agente, dos dossieres
> (Receta 50). En **APAC** el obstáculo no es la fuerza de la firma sino **el tipo de documento**:
> la **IT Act** india sólo admite técnicas de su **Segunda Lista** (Aadhaar eSign sí, una firma
> tecleada no) y **excluye por completo** inmuebles, títulos negociables, **poderes** y
> fideicomisos, así que **un agente que redacte un poder en India produce algo que ninguna firma
> electrónica puede cerrar**: el clasificador de tipo documental va **antes** del flujo de firma.
> China añade medidas de uso de criptografía en servicios de certificación **en vigor el
> 2026-07-01**. **Cero repositorios de origen APAC en esta capa: es un cero medido**, con una
> hipótesis registrada como hipótesis —donde la validez depende de un proveedor licenciado o de una
> lista cerrada de técnicas, el valor está en el servicio acreditado y no en la biblioteca—.
>
> **EL CERO DE LATAM ERA DEL IDIOMA, Y ESO CORRIGE HACIA ATRÁS VARIOS PASES (T97).** Pases
> anteriores midieron **cero repos de origen latinoamericano** con «el instrumento corto en
> español». **La misma pregunta en portugués devolvió seis**: `demoiselle/signer` (**LGPL-3.0**,
> del **SERPRO**, CAdES+XAdES+PAdES según políticas del **ITI**, **2026-09-04**),
> `junior9283/assinador-icp-brasil` (**MIT**, **2026-10-10**, **el único permisivo y vivo**, un
> solo mantenedor), `evandrojr/signer` (fork, 2026-05-20) y las tres de **`OpenICP-BR`**:
> `libICP` (**2018-09-24**), `wxApp` (**2018-07-11**) y `ktLib` (**sin fichero de licencia**,
> **2018-11-05**). **Cuando una capa depende de una infraestructura estatal obligatoria, el corpus
> libre está en el idioma del Estado que la impuso**, y Brasil es el único país de LATAM con una
> PKI nacional obligatoria (**MP 2.200-2/2001**, raíz en el **ITI**, tres niveles por la **Lei
> 14.063/2020** y presunción del art. 10 §1 sólo para la cualificada). **Pero el no-cero no es una
> buena noticia sin matices: 3 de 6 llevan 8 años sin un commit y son los primeros resultados de
> búsqueda. El hueco de LATAM aquí no es de ausencia: es de mantenimiento**, y eso es una venta
> mejor que un vacío (Receta 52). **Para el resto de LATAM el cero sigue en pie, ahora con el
> instrumento corregido.**
>
> **Cinco reglas de método nuevas, y dos son fallos del propio instrumento.** **T93** — **el texto
> de la GPL-2.0 contiene la cadena «GNU Lesser General Public License»** en su apéndice (línea 18
> del `LICENSE` de `dogtagpki/pki`) mientras su línea 1 dice `GNU GENERAL PUBLIC LICENSE /
> Version 2`: **clasificar por la primera línea de encabezado, nunca por subcadena**; veredicto
> corregido a **GPL-2.0**. **T94** — si la sonda dice «sin licencia», **leer el README para obtener
> el NOMBRE DEL FICHERO**: `open-eid/digidoc4j` y `libdigidocpp` dieron **13 rutas, 13 fallos**, y
> la licencia está en **`LICENSE.LGPL`** (**LGPL-2.1, 26.436 B**); es el **inverso de T92** —una
> insignia no sustituye al fichero, pero el README puede ser su **índice**—, y de propina el README
> **misnombra su propia licencia** («GNU *Library* GPL», que es la 2.0, siendo la 2.1). **T95** —
> dentro de una organización, el corte de licencia separa **producto** de **biblioteca**. **T96** —
> **la afirmación NEGATIVA de un resumen de búsqueda no es un cero medido**: el resumen dijo que
> ningún proyecto documenta puerta humana y el byte a byte dijo lo contrario, y creerlo habría
> descartado **el único** proyecto bien diseñado de la capa. **T97** — **medir LATAM en portugués
> además de en español**.
>
> **Límite declarado, y la asimetría de siempre.** Todo lo de **licencias, ramas por defecto y
> fechas de último commit es byte a byte o medido en el carril de git**. **Todo lo normativo y de
> mercado es a nivel de resumen de búsqueda** y va marcado donde aparece. **Ninguna fuente primaria
> del hallazgo principal es alcanzable desde esta sesión**: `eur-lex.europa.eu`,
> `datatracker.ietf.org` y las páginas de la Comisión no responden. **No se leyeron en primario**
> el Reglamento (UE) 910/2014, el Reglamento (UE) 2024/1183, el Art. 50 del AI Act, el RFC 9421,
> ESIGN, UETA, la MP 2.200-2/2001 ni la Lei 14.063/2020; la distinción firma/sello se sostiene en
> **blogs de proveedores con interés comercial**, y **una de esas fuentes sitúa mal el articulado
> del sello** (lo etiqueta «Art. 25» en vez de 35–40), lo que confirma que la capa se documenta mal
> incluso donde acierta. **Conflictos declarados en lugar de promediados:** la fecha de la cartera
> (24 frente a 31 de diciembre); el estado del borrador de **Web Bot Auth** (grupo IETF constituido
> en 2026 **sin documentos adoptados** a agosto frente a «borrador activo»); si **Googlebot** firma
> sus peticiones o sólo `Google-Agent`; el año de la ley china (2004/2005/revisión 2019) y de la
> japonesa (2000/2001); y la **Resolución 11/2025** argentina, cuyo contenido **no se pudo
> corroborar** y por eso **no debe citarse a un cliente**. **Y un 404 que se registra en lugar de
> borrarse:** `eu-digital-identity-wallet/eudi-srv-web-issuing-qeaa-py` **no existe** — el nombre
> lo dedujo este pase por analogía con sus repos hermanos y no lo verificó antes de escribirlo.
> **De 45 direcciones, 44 reales y 1 conjetura propia.**

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
