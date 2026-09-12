Staff engineer building resilient ingestion pipelines for financial data. I own the systems that move millions of events per day from edge sources into analytical storage, and I keep them honest under partial failures and schema drift.

## Rick Torp

I design and operate event-driven ingestion systems that process high-volume financial transactions. I've owned the full lifecycle of data pipelines: from API contracts and queue consumers to storage schemas and backfill jobs. My operational priority is predictable latency under load, which means I accept the cost of idempotent writes and duplicate detection rather than risking silent data loss. I trade strict consistency for availability in hot paths, and I enforce schema versioning to keep downstream consumers safe during migrations.

### 🛠 Tech & Infrastructure
- **Core**: `TypeScript`, `Node.js`, `PostgreSQL`, `Redis`
- **Data**: `Kafka`, `Debezium`, `Parquet`, `Iceberg`
- **Infra**: `Kubernetes`, `Terraform`, `Grafana`, `Prometheus`
- **Tooling**: `GitHub Actions`, `pino`, `Zod`

### ⚙️ Engineering Areas
- Designing idempotent ingestion APIs with at-least-once delivery and deduplication keys.
- Building schema evolution workflows that validate producers and isolate consumers from breaking changes.
- Implementing backpressure controls in queue consumers to protect downstream databases from bursts.
- Tuning partition keys and index layouts to keep query latency under 100ms for time-series access patterns.

### 🔭 Current Focus
- Reducing replay cost for out-of-order events by refining watermark tracking in the consumer layer.
- Migrating a monolith batch job to streaming workers without losing exactly-once semantics for financial settlements.
- Cutting tail latency in the ingestion path by moving hot data to columnar storage and pruning partitions aggressively.
- Automating schema drift detection across Kafka topics and Postgres tables to catch contract breaks before deployment.

### 📌 Engineering Notes
- Tests that don't inject real network failures miss the bugs that matter; I always include chaos cases for timeouts and partial writes.
- Migrations should be additive and reversible; I never ship a destructive schema change without a dual-write period.
- Retries need exponential backoff with jitter, but they also need a dead-letter queue and an alert when the retry budget is exhausted.
- Every service exposes latency percentiles and error rates as traces; if it's not in Grafana, it didn't happen.

### 🧭 How I Work
- I optimize for debuggability: explicit contracts, structured logs, and trace IDs on every request.
- I prefer boring, well-understood technology over clever abstractions, unless the abstraction pays for itself in reduced operational load.
- I review code as a design conversation, not a checklist; the goal is to reduce the cost of future changes.

*Reliability is not a feature; it's the absence of surprises.*