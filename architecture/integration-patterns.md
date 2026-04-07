

# Integration Patterns

## Overview

This document outlines the integration approaches used in the platform architecture and explains when synchronous versus asynchronous communication should be used.

## Integration Goals

- Reliable ingestion from external systems  
- Loose coupling between services  
- Scalability and extensibility  
- Observability across interactions  
- Graceful failure handling  

---

## API-Based Integration (Synchronous)

### Description
External systems interact with the platform using HTTP APIs.

### Use Cases
- POS events
- Hotel updates
- Gaming activity

### Pros
- Simple and direct
- Immediate validation
- Easy to debug

### Cons
- Tight coupling
- Requires system availability
- Retry logic needed

---

## Event-Driven Integration (Asynchronous)

### Description
Internal services communicate via events instead of direct calls.

### Use Cases
- Guest profile updates
- Offer generation
- Reporting updates

### Pros
- Loose coupling
- Scalable
- Easy to extend

### Cons
- Eventual consistency
- Requires idempotency
- More complex debugging

---

## Synchronous Service Calls

Used for:
- Fetching guest data
- Dashboard APIs

---

## Observability Integration

All services expose:
- `/health`
- `/metrics`
- Structured logs

---

## Design Principles

- Use sync for reads  
- Use async for state changes  
- Design for failure  
- Ensure traceability  

---

## Example Flow

1. POS → Ingestion API  
2. Validation → Processing  
3. Profile updated  
4. Offer generated  
5. Data exposed via API  
6. Logs + metrics recorded  