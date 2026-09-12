Senior Platform Engineer building resilient data ingestion systems.

## Johnny Schuster

I design and operate ingestion pipelines that move tens of millions of events per day from edge services into analytics stores. I own the end-to-end path: schema evolution, queue backpressure, worker autoscaling, and the dashboards that tell us when a partition lag is a real problem. I accept eventual consistency at the edges, and I trade strict ordering for throughput where the domain allows it.

### 🛠 Tech & Infrastructure

**Core** `TypeScript` `Node.js` `PostgreSQL` `Redis`
**Data** `Kafka` `Debezium` `Parquet` `ClickHouse`
**Infra** `Kubernetes` `Terraform` `Helm`
**Tooling** `GitHub Actions` `Prometheus` `Grafana` `OpenTelemetry`

### ⚙️ Engineering Areas

- Designing idempotent consumers with at-least-once delivery and deduplication keys.
- Evolving Avro schemas across producers and consumers without breaking old readers.
- Building retry queues with exponential backoff and dead-letter handling for poisoned messages.
- Automating blue/green deployments for stateful workers that drain before shutdown.

### 🔭 Current Focus

- Reducing Kafka rebalance time for a consumer group with 200+ partitions and heterogeneous processing speeds.
- Moving from a monolith to bounded contexts without creating distributed monolith anti-patterns.
- Tuning ClickHouse merges to keep query latency under 200ms while ingesting 50k rows/second.
- Standardizing trace sampling so we get representative traces without paying for full fidelity.

### 📌 Engineering Notes

- Tests that depend on real external systems are integration tests; they run in a separate pipeline and are not allowed to block local development.
- Migrations are additive and reversible; destructive changes are staged behind feature flags and removed after a full deploy cycle.
- Retries are for transient failures only; if a message is malformed, dead-letter it and alert, don't hammer the broker.
- Every service exposes health and readiness endpoints, and on-call runbooks are generated from the same OpenTelemetry traces that drive alerts.

### 🧭 How I Work

- Prefer boring, well-understood technology over novelty; the cost of debugging exotic infrastructure is rarely worth the demo.
- Write code for the next person who has to debug it at 3am; that means explicit error paths and no clever one-liners.
- Optimize for operability first: if it can't be observed, it doesn't ship.

*The best production system is the one that fails predictably and recovers without a page.*