# Literal AI GraphQL API

Representative GraphQL schema for the [Literal AI](https://www.literalai.com/) LLM
observability, evaluation, and analytics platform from the Chainlit team.

The Literal AI API is **GraphQL**. The Python (`literalai`) and TypeScript
(`@literalai/client`) SDKs are thin clients over a single GraphQL endpoint; there is no
documented public REST surface. A separate OpenTelemetry (OTLP) HTTP ingestion path
exists for pushing traces/spans, but all CRUD, querying, evaluation, and prompt
management happen over GraphQL.

- Documentation: <https://docs.literalai.com>
- Python API reference: <https://docs.literalai.com/python-client/api-reference/api>
- TypeScript API reference: <https://docs.literalai.com/typescript-client/api-reference/api>
- GitHub: <https://github.com/Chainlit/literalai-python>, <https://github.com/Chainlit/literalai-typescript>

---

## Endpoint

| | |
|---|---|
| Cloud GraphQL endpoint | `https://cloud.getliteral.ai/api/graphql` |
| Self-hosted | `{LITERAL_API_URL}/api/graphql` |
| Method | `POST` |
| Content-Type | `application/json` |

The SDK derives the GraphQL endpoint by appending `/api/graphql` to the configured base
URL (`LITERAL_API_URL`). Self-hosted and enterprise deployments substitute their own host.

> The schema in [`literalai-schema.graphql`](./literalai-schema.graphql) is a
> **representative** subset reconstructed from the SDK operations and public docs, not a
> verbatim copy of Literal AI's internal schema. Field and operation names track the
> documented SDK methods (threads, steps, generations, datasets, experiments, prompts,
> scores, users, attachments).

---

## Authentication

All requests are authenticated with an API key passed in the `x-api-key` header. Keys are
created per project in the Literal AI dashboard and supplied via the `LITERAL_API_KEY`
environment variable or the `api_key` client argument.

```
POST https://cloud.getliteral.ai/api/graphql
Content-Type: application/json
x-api-key: <LITERAL_API_KEY>
```

---

## Core entities

| Entity | Purpose |
|--------|---------|
| `Thread` | A conversation or trace grouping a sequence of steps |
| `Step` | A unit of work in a thread: run, tool, retrieval, LLM, embedding, or rerank |
| `Generation` | An LLM call (chat or completion) with prompt, settings, usage, and output |
| `Dataset` / `DatasetItem` | Curated evaluation data, manual or promoted from production steps |
| `Experiment` / `ExperimentItem` | A benchmark run over a dataset with per-item scores |
| `Prompt` | A versioned prompt template with model settings and variables |
| `Score` | Human, AI, or code feedback attached to a step or generation |
| `User` (Participant) | An end-user / participant associated with threads |
| `Attachment` | A file (image, audio, video, document) bound to a step or thread |

---

## Query examples

### Fetch a thread with its steps

```graphql
query GetThread($id: String!) {
  thread(id: $id) {
    id
    name
    createdAt
    participant { id identifier }
    steps {
      id
      name
      type
      input
      output
      startTime
      endTime
    }
  }
}
```

### Paginate generations with a filter

```graphql
query Generations($first: Int, $after: ID, $filters: [generationsInputType!]) {
  generations(first: $first, after: $after, filters: $filters) {
    pageInfo { hasNextPage endCursor }
    edges {
      node {
        id
        type
        model
        promptId
        tokenCount
        messages
        completion
      }
    }
  }
}
```

### List dataset items

```graphql
query Dataset($id: String!) {
  dataset(id: $id) {
    id
    name
    type
    items {
      id
      input
      expectedOutput
      metadata
    }
  }
}
```

---

## Mutation examples

### Ingest a step (send a run/LLM step)

```graphql
mutation IngestStep(
  $id: String!
  $threadId: String
  $type: StepType!
  $name: String
  $input: Json
  $output: Json
) {
  ingestStep(
    id: $id
    threadId: $threadId
    type: $type
    name: $name
    input: $input
    output: $output
  ) {
    id
    type
  }
}
```

### Upsert a thread

```graphql
mutation UpsertThread($id: String!, $name: String, $metadata: Json) {
  upsertThread(id: $id, name: $name, metadata: $metadata) {
    id
    name
  }
}
```

### Create a score

```graphql
mutation CreateScore(
  $name: String!
  $type: ScoreType!
  $value: Float!
  $stepId: String
  $generationId: String
  $comment: String
) {
  createScore(
    name: $name
    type: $type
    value: $value
    stepId: $stepId
    generationId: $generationId
    comment: $comment
  ) {
    id
    name
    value
  }
}
```

### Create a dataset experiment

```graphql
mutation CreateExperiment(
  $datasetId: String!
  $name: String!
  $params: Json
) {
  createExperiment(datasetId: $datasetId, name: $name, params: $params) {
    id
    name
  }
}
```

### Create / version a prompt

```graphql
mutation CreatePrompt(
  $name: String!
  $templateMessages: Json!
  $settings: Json
) {
  createPrompt(name: $name, templateMessages: $templateMessages, settings: $settings) {
    id
    name
    version
  }
}
```

---

## OpenTelemetry ingestion

In addition to GraphQL, Literal AI accepts OpenTelemetry (OTLP/HTTP) traces for
instrumented applications, mapping OTEL spans to Literal AI steps and generations. This is
a one-way ingestion path and is not part of the GraphQL schema; configure an OTLP exporter
pointed at the Literal AI OTEL endpoint with the `x-api-key` header. See the Literal AI
docs for the current OTEL endpoint and span conventions.
