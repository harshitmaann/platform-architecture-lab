# ADR-001: Use Event-Driven Processing for Internal State Changes

## Status

Accepted

## Context

The platform must ingest activity data from multiple upstream systems and then trigger downstream updates such as guest profile aggregation, offer evaluation, and reporting state changes.

A design choice is required for how internal services should coordinate after an event is accepted by the ingestion layer.

The main options considered were:

1. Direct synchronous service-to-service calls
2. Event-driven internal processing

## Decision

The platform will use event-driven processing for internal state changes after initial ingestion and validation.

This means that once an activity event is accepted, downstream processing steps such as profile updates, offer evaluation, and reporting updates should be modeled as event-driven workflows rather than tightly coupled synchronous chains wherever practical.

## Rationale

Event-driven processing was selected because it:

- Reduces coupling between services
- Improves extensibility for future workflows
- Supports independent scaling of downstream components
- Makes it easier to add new consumers later without changing ingestion contracts
- Better reflects how state-change workflows evolve in distributed systems

## Consequences

### Positive

- New downstream capabilities can be added with less redesign
- Internal workflows are more modular
- Services can evolve more independently
- The architecture is better aligned with scalability goals

### Negative

- Eventual consistency must be accepted
- Debugging becomes more complex than simple request/response flows
- Idempotency and retry behavior must be designed carefully
- Observability becomes more important for tracing workflows

## Notes

Synchronous APIs are still appropriate for query-style operations such as dashboard reads, guest lookup, and health checks. This decision applies primarily to internal state-change processing.