# Observability: Metrics, Rate Limits, Health

## Metrics to track

- Total calls, calls per tool
- Error rate and errors by type
- Latency (avg and p50/p95/p99)
- Token usage (if your runtime exposes it)

## Rate limiting

- Enforce per-user or per-integration quotas.
- When tripped, return an error that includes:
  - the limit, remaining quota, and when to retry (roughly)

## Health checks

Expose a lightweight health surface (implementation-dependent) that reports:

- server version
- uptime
- transport status (if applicable)
- minimal summary metrics (no secrets)
