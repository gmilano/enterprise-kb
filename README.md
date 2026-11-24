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

## Estado de la KB — medido, no estimado (thirteenth pass, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Direcciones de repositorio distintas | **388** |
| …en `github.com` | 367 |
| …en `gitlab.com` | 21 |
| Nuevas direcciones este pase | **32**, todas con licencia, estrellas y fecha de push medidas |
| Recetas en `compose/patterns.md` | **26** |
| Tendencias numeradas en `intel/trends.md` | **30** |
| Clases de licencia registradas | **12** |
| Formas registradas de equivocarse (`intel/trends.md`) | **25** |
| Proyectos archivados-pero-recomendados detectados | **10** |
| Preguntas registradas como **sin resolver** | 6 |

> **Lea esto antes de prometer un borrado.** Doce pases construyeron cuatro límites — lectura,
> escritura, procedencia y contención — más la licencia de los **pesos**. Todos gobiernan lo que el
> agente **puede hacer**. El pase trece añade el quinto: **qué tiene que volver a salir**, y es el
> primero que no se puede comprar.
>
> **Un borrado no es una operación, es una cascada con siete lugares de reposo** (sistema de
> registro, stream CDC, snapshot del lakehouse, índice vectorial, fixtures de evaluación, pesos
> afinados, logs). **Dos no tienen borrado**: el *unlearning* no es tecnología de producción
> (código de investigación de dos cifras de estrellas; el benchmark de referencia **inactivo 21
> meses**), y los **logs no deben borrarse** — el AI Act Art. 19 exige conservarlos **≥ 6 meses** y
> la Regla 8 del DPDP indio **≥ 1 año**. De ahí una única regla de diseño con base legal:
>
> **los datos personales van en recuperación sobre almacenes borrables, nunca en un fine-tune; y el
> log lleva un seudónimo, nunca el identificador.**
>
> **El producto de referencia de esta capa está archivado.** `ethyca/fides` (Apache-2.0, 483★,
> último push 2026-08-06) —el motor DSAR open source que todos los listados de 2026 siguen
> recomendando— **está archivado**, junto con `fidesops`, `fidesdemo`, `fideslib` y dos más. Los
> únicos repos activos de esa organización son tres SDK móviles que **no declaran licencia**:
> primera vez que esta KB registra un archivado **y una regresión de licencia** en el mismo
> namespace. No se encontró reemplazo permisivo mantenido, y eso se declara como hallazgo en lugar
> de rellenarse con una fila verosímil.
>
> **Clase de licencia nº 12 — SOM-1.0.** `vec2text/vec2text` reporta `NOASSERTION`; su `LICENSE` es
> la *Software for Open Models License 1.0*, cuyo §3(A) obliga a quien use la herramienta *"para
> crear inferencias con un Modelo, lo publique o no"* a **publicar los pesos de ese modelo**. El
> pase doce encontró la cláusula decisiva **fuera** de la licencia (en un AUP); este la encontró
> **dentro de la licencia de una herramienta, alcanzando un activo que la herramienta no
> contiene**. Use `jina-ai/embedding-inversion-demo` (Apache-2.0) para la misma demostración.
>
> **El borrado de la plataforma no borra — leído del código, no de un blog.** En
> `SuiteCRM/SuiteCRM`, `data/SugarBean.php:5313`, `mark_deleted()` ejecuta
> `UPDATE … set deleted=1` y el método `mark_undeleted()` viaja al lado. La misma comprobación
> **no** se hizo sobre Odoo, ERPNext, Dolibarr ni Axelor: se declara como hueco, no como hallazgo.
>
> **Instrumento recuperado:** el pase doce no pudo medir estrellas ni fechas de push. Este sí:
> `gh api search/repositories` con varios `repo:` en un mismo `q` devuelve licencia, estrellas,
> push, estado de archivado **y `default_branch`** en una sola petición. **Cómo miente:** un
> `repo:` inválido se descarta **en silencio** si quedan válidos, pero si todos son inválidos
> devuelve **422** — que es evidencia positiva de que una ruta desapareció.
>
> **Límite declarado y asimétrico.** Doce hosts legales y de marketplaces (EUR-Lex, el service desk
> del AI Act, GDPR-info, CPPA/oag.ca.gov, MeitY, PDPC, Planalto, gov.br, apps.odoo.com y tres más)
> **no resuelven desde esta sesión**. Por eso **los hechos de código de este pase son más fuertes
> que sus hechos jurídicos**, y cada archivo lo dice en el punto donde aparece: licencias y repos
> verificados byte a byte, regulación **a nivel de snippet de búsqueda**. Fechas regionales con
> plazo: **DROP de California** (sondeo cada 45 días desde 1-ago-2026), **consent managers del DPDP
> indio** (13-nov-2026), **Ley 21.719 de Chile** (1-dic-2026, con un proyecto de postergación que
> **no es ley**) y **Resolución CD/ANPD nº 30/2025** de Brasil (derechos del titular + IA como
> prioridades 2026-2027).

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
