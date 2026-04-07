# Business Scenario

Gateway operates a multi-property gaming and hospitality environment, including casinos, hotels, food & beverage services, and online systems.

Each of these systems generates valuable operational and customer activity data, but they are often siloed across different platforms and vendors.

The organization requires a unified platform that can:

- Ingest activity data from multiple systems (POS, hotel, gaming, etc.)
- Build a consolidated view of guest behavior and activity
- Enable targeted offers and promotions based on real usage patterns
- Provide operational visibility into system health and business metrics
- Support auditability and reliability in a regulated environment

## Problem Statement

Currently:

- Data is fragmented across systems
- No unified guest activity view exists
- Offers and promotions are not dynamically driven by real-time behavior
- Operational visibility is limited across systems
- Incident detection and response is inconsistent

## Objectives

The platform should:

- Centralize ingestion of events from multiple systems
- Maintain a consistent and queryable guest activity profile
- Enable simple rules-based offer generation
- Provide APIs for reporting and dashboards
- Include observability (logs, metrics, health checks)
- Be designed with security and auditability in mind
- Be operationally supportable with clear runbooks

## Scope

This project focuses on:

- Core platform architecture design
- Integration patterns between services
- Data flow and processing
- Observability and operational readiness
- A lightweight implementation to demonstrate system behavior

Out of scope:

- Full production-scale infrastructure
- Advanced ML-based personalization
- External vendor integrations (simulated instead)
