**ADR-003: API Design Style**
   - **Status**: Decided
   - **Context**: Need for a standardized way of exposing services.
   - **Evaluation Criteria**: Ease of use, flexibility, performance.
   - **Options**:
     - REST: Simplicity and wide adoption.
     - GraphQL: More complex but flexible for clients.
   - **Decision**: Use REST for public APIs.
   - **Implications**: May need to design multiple endpoints for different data needs.
   - **Consultation**: Frontend team, API consumers.

