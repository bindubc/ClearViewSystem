3. **ADR-003: API Design Style**
   - **Status**: Decided
   - **Context**: Need for a standardized and developer-friendly way to expose services.
   - **Evaluation Criteria**: 
     - **Ease of Use**: Simplicity for developers consuming the API.
     - **Flexibility**: Ability to cater to diverse client needs.
     - **Performance**: Efficient response times and resource usage.
   - **Options**:
     - **REST**: Widely adopted, simple to implement.
     - **GraphQL**: More complex but provides flexibility for clients to request specific data.
   - **Decision**: Use REST for public APIs.
   - **Implications**: May require designing multiple endpoints to meet various data needs.
   - **Failover Strategy**: Implement API gateways (e.g., AWS API Gateway) with built-in load balancing and rate limiting to ensure high availability.
   - **Resolution for Issues**: Develop clear API documentation and versioning strategies to manage breaking changes.
   - **Consultation**: Frontend team, API consumers.

