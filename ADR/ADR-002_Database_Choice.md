 **ADR-002: Database Choice**
   - **Status**: Decided
   - **Context**: Need for flexible schema and scalability for candidate data.
   - **Evaluation Criteria**: Scalability, flexibility, ease of querying.
   - **Options**:
     - SQL (PostgreSQL): Strong consistency, complex queries.
     - NoSQL (MongoDB): Flexible schema, high scalability.
   - **Decision**: Use MongoDB for candidate data.
   - **Implications**: Must ensure data integrity and handle eventual consistency.
   - **Consultation**: Database administrators, development team.

