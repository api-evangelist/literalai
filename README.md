# Literal AI (literalai)

Literal AI is the collaborative observability, evaluation, and analytics platform for building production-grade LLM applications, from the Chainlit team. Its API is GraphQL (POST /api/graphql) consumed through Python and TypeScript SDKs, capturing threads, steps, generations, datasets, experiments, prompts, and scores, with an additional OpenTelemetry (OTLP) ingestion path for traces.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/literalai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/literalai/refs/heads/main/apis.yml)

## Tags

- AI
- LLM
- Observability
- Evaluation
- Monitoring

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### Literal AI Threads & Steps API

Create, read, update, upsert, and delete conversation threads and the nested steps (runs, tools, retrievals, LLM calls) that trace an LLM application's execution, queried and mutated over GraphQL.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Threads
- Steps
- Tracing

#### Properties

- [Documentation](https://docs.literalai.com/observability/concepts)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Literal AI Generations API

Log and paginate chat and completion generations - prompts, model, settings, token usage, and outputs - with filtering for analytics and evaluation.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Generations
- LLM
- Logging

#### Properties

- [Documentation](https://docs.literalai.com/observability/concepts)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Literal AI Datasets API

Build and manage datasets and dataset items - curated from production steps or created manually - that serve as ground truth for evaluation and experiments.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Datasets
- Evaluation
- Test Data

#### Properties

- [Documentation](https://docs.literalai.com/evaluation/datasets)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Literal AI Experiments API

Create dataset experiments and record per-item experiment runs with scores to benchmark prompt, model, and pipeline changes over time.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Experiments
- Evaluation
- Benchmarking

#### Properties

- [Documentation](https://docs.literalai.com/evaluation/experiments)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Literal AI Prompts API

Version, store, and retrieve prompt templates with their model settings, enabling collaborative prompt engineering and A/B testing against deployed apps.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Prompts
- Versioning
- Templates

#### Properties

- [Documentation](https://docs.literalai.com/prompt-engineering/prompts)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Literal AI Scores API

Attach human, AI, and code-based scores to steps and generations - numeric, categorical, or boolean - for feedback collection and offline/online evaluation.

- **Human URL:** [https://docs.literalai.com/python-client/api-reference/api](https://docs.literalai.com/python-client/api-reference/api)
- **Base URL:** `https://cloud.getliteral.ai/api/graphql`

#### Tags

- Scores
- Feedback
- Evaluation

#### Properties

- [Documentation](https://docs.literalai.com/evaluation/scores)
- [API Reference](https://docs.literalai.com/python-client/api-reference/api)
- [OpenAPI](openapi/literalai-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/literalai-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/literalai.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/literalai.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/Chainlit)
- [LinkedIn](https://www.linkedin.com/company/chainlit)
- [Website](https://www.literalai.com)
- [Documentation](https://docs.literalai.com)
- [Plans](plans/literalai-plans-pricing.yml)
- [Rate Limits](rate-limits/literalai-rate-limits.yml)
- [Fin Ops](finops/literalai-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
