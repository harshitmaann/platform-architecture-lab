# Assumptions and Constraints

## Assumptions

- External systems (POS, hotel, gaming) can provide event data via APIs or batch feeds
- Event data follows a consistent structure after validation
- Initial system load is moderate and can scale over time
- Internal users (business teams, dashboards) will consume APIs
- Authentication mechanisms will be integrated at the API layer
- Observability tools (logging, metrics) are available in the environment
- The platform will evolve incrementally, starting with core features

## Constraints

- External vendor systems may have inconsistent interfaces or data formats
- Some systems may be on-premise while others are cloud-based (hybrid environment)
- Strict audit and compliance requirements in a regulated gaming environment
- Limited control over upstream data quality
- Initial implementation prioritizes simplicity over full production complexity
- Budget and infrastructure constraints may limit early scalability decisions
