# ADR-003: Separate Operational and Reporting Concerns

## Status

Accepted

## Context

The platform handles both operational workloads (event ingestion, profile updates, offer generation) and reporting workloads (dashboards, analytics queries).

These workloads have different characteristics:

- Operational workloads are write-heavy and latency-sensitive  
- Reporting workloads are read-heavy and may involve complex queries  

A decision is required on whether to use a single data access pattern or separate concerns.

## Decision

The platform will logically separate operational and reporting concerns.

Operational services will focus on handling real-time updates and state changes, while reporting services will focus on exposing aggregated and query-friendly data for dashboards and analytics.

## Rationale

This approach was selected because it:

- Improves performance for both read and write workloads  
- Prevents reporting queries from impacting operational processing  
- Enables independent scaling of operational and reporting components  
- Allows optimization of data models for different use cases  

## Consequences

### Positive

- Better system performance and scalability  
- Clear separation of responsibilities between services  
- Reduced risk of reporting workloads impacting real-time processing  

### Negative

- Increased architectural complexity  
- Potential need for data duplication or transformation  
- Requires careful data synchronization strategies  

## Notes

In the initial implementation, this separation may be logical rather than physical (same database with different access patterns). In future iterations, this could evolve into separate data stores or data pipelines.