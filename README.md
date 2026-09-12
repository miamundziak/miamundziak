Staff engineer building ingestion infrastructure for real-time analytics platforms.

## Fannie Marquardt

I design and operate high-throughput data pipelines that move billions of events per day from edge collectors into queryable storage. I own the end-to-end lifecycle of ingestion services: schema evolution, partition strategies, replay semantics, and the operational runbooks that keep them healthy. My priorities are durable delivery, bounded latency, and making the system observable enough that an on-call engineer can diagnose a problem in under ten minutes. I accept the trade-off of higher infrastructure cost for simpler recovery paths and idempotent reprocessing.

### 🛠 Tech & Infrastructure
- **Core**: `TypeScript`, `Node.js`, `PostgreSQL`, `Redis`
- **Data**: `Apache Kafka`, `ClickHouse`, `Parquet`, `Flink`
- **Infra**: `Docker`, `Kubernetes`, `Terraform`, `GitHub Actions`
- **Observability**: `Prometheus`, `Grafana`, `OpenTelemetry`

### ⚙️ Engineering Areas
- Schema evolution for event payloads across hundreds of producer teams, using explicit versioning and migration checks in CI.
- Partitioning and retention strategies for time-series data that balance query performance against storage costs.
- Backpressure and dead-letter handling for Kafka consumers, including replayable DLQs with idempotent sinks.
- Capacity planning and load testing for ingestion clusters under 10x traffic spikes.

### 🔭 Current Focus
- Reducing end-to-end latency from event production to queryable state, currently constrained by cross-region replication.
- Implementing a zero-downtime migration path for the core event schema, without breaking existing consumers.
- Improving backpressure semantics for bursty traffic while keeping consumer lag within SLOs.
- Evaluating columnar compression trade-offs for high-cardinality dimensions in ClickHouse.

### 📌 Engineering Notes
- Tests should verify behavior, not implementation details; unit tests for pure logic, integration tests for boundaries, and property tests for serialization.
- Prefer explicit contracts and versioned APIs over implicit coupling; migrations should be additive and reversible.
- Error handling must distinguish retryable from fatal; use exponential backoff with jitter, and never swallow exceptions silently.
- Observability is a first-class requirement: every service exposes metrics, traces, and structured logs, and deployments must be reversible with automated rollbacks.

### 🧭 How I Work
- Design for operability first: if a system cannot be debugged in production, it is not done.
- Make incremental changes with clear rollback paths; big-bang rewrites are a last resort.
- Document decisions and trade-offs in code comments and ADRs, so future engineers understand the “why”.

*Reliability is a feature, not an afterthought.*