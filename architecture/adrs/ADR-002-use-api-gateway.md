# ADR-002: Use an API Gateway as the Primary Platform Entry Point

## Status

Accepted

## Context

The platform receives requests from multiple external and internal consumers, including upstream operational systems and downstream dashboard or reporting clients.

A decision is needed on how requests should enter the platform and how cross-cutting concerns such as authentication, routing, and request handling should be managed.

The main options considered were:

1. Allow consumers to call each service directly
2. Introduce a single API gateway / entry layer

## Decision

The platform will use a single API gateway as the primary entry point for external and internal client requests.

The gateway will be responsible for routing requests to the appropriate backend services and will serve as the control point for shared concerns such as authentication, request validation, and traffic management.

## Rationale

An API gateway was selected because it:

- Provides a single, consistent entry point for clients
- Reduces direct exposure of internal services
- Centralizes routing and access-control concerns
- Simplifies client integration as the platform grows
- Supports future operational controls such as rate limiting, logging, and request tracing

## Consequences

### Positive

- Internal services remain less exposed
- Clients integrate with a simpler interface
- Shared concerns can be managed more consistently
- Platform evolution becomes easier as backend services change

### Negative

- Introduces an additional component to operate and monitor
- Can become a bottleneck if poorly configured
- Adds some deployment and troubleshooting complexity

## Notes

This decision does not eliminate direct internal service communication where appropriate. It primarily applies to how clients and upstream systems enter the platform boundary.