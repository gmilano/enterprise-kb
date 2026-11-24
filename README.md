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

## Estado de la KB — medido, no estimado (decimoséptimo pase, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Direcciones de repositorio distintas | **514** |
| …en `github.com` | 493 |
| …en `gitlab.com` | 21 |
| Direcciones verificadas este pase | **46** (licencia, estrellas, rama por defecto y último push medidos) |
| …de ellas **nuevas** para la KB | **42** |
| Recetas numeradas en `compose/patterns.md` | **33** |
| Tendencias numeradas en `intel/trends.md` | **36** (con una colisión de numeración heredada) |
| Clases de licencia registradas | **16** (+EUPL-1.2, +0BSD, +WTFPL) |
| Formas registradas de equivocarse | **40** |
| Proyectos archivados-o-desaconsejados pero recomendados | **12** |
| Preguntas registradas como **sin resolver** | **14** |

> **Lea esto antes de prometer una fecha de cumplimiento fiscal.** Dieciséis pases construyeron ocho
> límites —lectura, escritura, procedencia, contención, borrado, accesibilidad, **pesos** e
> **idioma**— más lo que el agente **gasta**. Todos los decide, al final, quien construye el sistema.
> **El noveno no.** Un documento fiscal electrónico no es válido porque el software lo diga: lo es
> porque **una autoridad tributaria lo acepta**, con el formato que ella fija y las reglas que ella
> publica. Medido antes de buscar, en los nueve archivos y en los dos idiomas: `Peppol` 0 · `AS4` 0 ·
> `EN 16931` 0 · `Factur-X` 0 · `ZUGFeRD` 0 · `Schematron` 0 · `CFDI` 0 · `NF-e` 0 · `Verifactu` 0 ·
> `KSeF` 0 · `ViDA` 0 · `SAF-T` 0 · `X12` 0. **No fue un cero limpio, y el residuo es el hallazgo de
> inventario:** `facturacion` **25** y `e-invoic` **5** estaban desde el pase once. **La KB tenía los
> módulos de localización fiscal de LATAM y no tenía ni el formato, ni el validador, ni el
> transporte, ni el modelo de autorización. Tenía el enchufe y le faltaba la red.**
>
> **EL HALLAZGO DEL PASE, PROBADO BYTE A BYTE SOBRE LOS ARTEFACTOS OFICIALES: la norma es una, sus
> conjuntos de reglas son dos, y no coinciden.** EN 16931 tiene un modelo semántico y dos
> vinculaciones de sintaxis (UBL y CII). Leídos los *Schematron* de CEN/TC 434 en la versión
> **1.3.17** (tag `validation-1.3.17`, commit `6e35e0ab…`): **`BR-CO-17`** usa `abs(…) - 1 **<**` en
> UBL y `abs(…) - 1 **<=**` en CII —**una factura desviada exactamente 1,00 unidad monetaria pasa en
> CII y falla en UBL**— y **`BR-S-08`** admite **tolerancia ±1** en UBL frente a **igualdad
> estricta** en CII. **Una conversión UBL↔CII fiel puede invertir la validez sin tocar un número**, y
> convertir entre sintaxis es justo lo que hacen Peppol, XRechnung, Factur-X y toda integración ViDA.
> **Regla de redacción:** «cumple EN 16931» no significa nada sin **vinculación + versión de
> artefactos + conjunto nacional**.
>
> **Clase de licencia nº 14, 15 y 16, y una de ellas recae sobre las reglas de la norma.** Los
> artefactos oficiales son **EUPL-1.2** (`LICENSE.txt`, **13 871 B**; GitHub dice `NOASSERTION`), que
> es **recíproca**: quien los **empaqueta** distribuye copyleft. Sexta aparición de la regla de esta
> KB —**el SPDX de un repo describe su código, no lo que empaqueta**— y la **primera en que lo
> empaquetado es el producto**: un validador sin reglas no valida. El repo que lo documenta bien
> tiene **1 estrella** (`einvoice-validator`, cuyos *crates* publicados declaran
> `MIT AND EUPL-1.2 AND LicenseRef-OASIS-… AND LicenseRef-UN-CEFACT-… AND W3C-19980720`), y ninguno
> de los de 200★+ de la capa publica una expresión compuesta. La alternativa existe y es opuesta:
> `attestwire/en16931` **reimplementa** las reglas (**0** archivos `.sch`/`.xslt` en todo el repo) y
> queda MIT puro **a cambio de ser ahora el autor de la regla**. Las otras dos clases nuevas:
> **0BSD** (`iterasdev/peppol-py`) y **WTFPL** (`techtemplemy/mcp-myinvois`, un servidor MCP con
> `SKILL.md` — permisiva en intención, **sin renuncia de garantía ni concesión de patentes**, no
> certificada por OSI).
>
> **La esquina de transporte es estructuralmente copyleft salvo por un autor.** Oxalis-NG es
> **EUPL-1.1-or-later** —declarada **solo en la cabecera del `pom.xml`**, sexta vía de resolución de
> licencia de esta KB—, Holodeck B2B y OpenAS2 son **GPL-3.0**, Domibus es EUPL-1.2, y la única pila
> AS4/Peppol **permisiva y viva** es la de Philip Helger (`phase4`, `phoss-ap`, `peppol-commons`,
> Apache-2.0, las tres con push en las últimas 24 h). **Esa concentración va en la sección de riesgos
> de la propuesta.** Variante nueva del patrón «recomendado pero no usable»: `OxalisCommunity/oxalis`
> (150★) **no está archivado — su propio README desaconseja usarlo** y **no tiene archivo de
> licencia** (cuatro rutas → 404).
>
> **Dos modelos regulatorios, dos arquitecturas incompatibles.** **Post-auditoría** (EMEA, NA: cuatro
> esquinas, la autoridad mira después) frente a **autorización previa** (LATAM: el documento no vale
> hasta que la autoridad lo autoriza y ella está en el camino crítico). De ahí tres reglas que
> contradicen reflejos habituales de los agentes: **el reintento no es idempotente** —puede crear un
> segundo documento fiscal, así que la clave es **serie + número**, nunca la capa HTTP—; **encolar
> puede caducar el documento** —India, **30 días** al IRP para AATO ≥ ₹10 crore—; y **el agente no
> puede ser el emisor** —MyInvois *guideline* v4.8 exige firma del emisor o de su proveedor
> acreditado—. ⚠️ Las tres obligaciones son **de fuente secundaria**.
>
> **Límite declarado, y es la misma asimetría de siempre.** Los hechos de **código y licencia de este
> pase son byte a byte**; **todos los regulatorios y de mercado son a nivel de snippet de búsqueda** y
> van marcados donde aparecen (no se pudo leer en primario `nfe.fazenda.gov.br`, el SAT, el BOE, la
> documentación de DBNAlliance ni IRAS). **Conflictos registrados sin resolver:** fecha de las
> sanciones de KSeF en Polonia, estado de la orden **HAC/1028/2026** en España, fechas de los
> catálogos CFDI 2026 en México y si cruzar ₹5 crore en FY 2025-26 generó obligación el 2026-04-01 en
> India. **Hueco declarado:** **Japón** — dos búsquedas con el país en la consulta no devolvieron
> nada verificable sobre PINT JP ni el régimen de factura cualificada. El próximo pase debe
> preguntar en japonés (`適格請求書`, `デジタルインボイス`), que es la misma lección de sesgo de idioma
> que el pase dieciséis registró para las auditorías de huecos.
---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
