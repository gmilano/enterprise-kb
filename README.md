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

## Estado de la KB — medido, no estimado (twelfth pass, 2026-11-24)

| Medida | Valor |
|---|---|
| Archivos de contenido | 9 (8 + README) |
| Direcciones de repositorio distintas | **355** |
| …en `github.com` | 334 |
| …en `gitlab.com` | 21 |
| Forjas alcanzables desde la sesión | **1 de 9** probadas (`gitlab.com`); las otras 8 responden `CONNECT tunnel failed, 403` |
| Recetas en `compose/patterns.md` | **24** |
| Tendencias numeradas en `intel/trends.md` | **28** |
| Clases de licencia registradas | **11** |
| Licencias de **pesos** verificadas byte a byte | **8 familias de modelos** |
| Preguntas registradas como **sin resolver** | 2 (Gemma; alcance del AUP de Apertus) |

> **Lea esto antes de citar la licencia de un modelo.** Durante once pases esta KB construyó una
> taxonomía de licencias leyendo archivos `LICENSE` de repositorios de **código**. El doceavo pase
> apuntó ese instrumento a los **pesos del modelo** y encontró que `LICENSE` es **el archivo
> equivocado**: de cuatro familias medidas, dos divergen — y en direcciones **opuestas**.
> `google-deepmind/gemma` tiene un `LICENSE` Apache-2.0 que cubre el **código**; `QwenLM/Qwen3` no
> tiene `LICENSE` alguno y sus pesos **sí** son Apache-2.0.
>
> Peor: **la cláusula que decide un engagement en EMEA no está en la licencia.**
> `meta-llama/llama-models` → `models/llama4/USE_POLICY.md:71` retira los derechos de la Sección 1(a)
> de los modelos multimodales de Llama 4 a *"una empresa con su establecimiento principal en la Unión
> Europea"*. `grep -c 'European Union'` sobre los cuatro archivos `LICENSE` de Llama devuelve **0**.
> Ningún escáner de licencias lee el AUP.
>
> Y el modelo soberano **hereda**: Latam-GPT (CENIA, Chile) es un derivado de Llama 3.1 70B bajo la
> **Llama 3.1 Community License**. La soberanía está en los datos y el idioma, **no en la licencia**.
>
> Clase de licencia nº 11: **OpenMDW-1.1** (Linux Foundation) — un solo permiso sobre modelo + datos +
> documentación + código, con derechos de **base de datos** y secreto comercial, salidas sin
> restricción, **sin aprobación OSI y sin identificador SPDX**. Detalle en `intel/trends.md`
> (tendencias 27 y 28), tablas en `repos/foundations.md`, compuerta en `compose/patterns.md`
> (Recetas 23 y 24).
>
> **Límite de instrumento declarado:** `huggingface.co` y `ai.google.dev` no resuelven desde esta
> sesión y `api.github.com` responde 403 fuera del alcance, por lo que **este pase no pudo medir
> estrellas ni fechas de push**. Las filas nuevas traen licencia y evidencia en bytes, y **omiten la
> estrella en lugar de copiarla de un blog**.

---
*Red de KBs Globant AI Studios → [globant-kb](../globant-kb/)*
