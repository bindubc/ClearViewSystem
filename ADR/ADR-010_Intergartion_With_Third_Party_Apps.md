**ADR-010: Choice of Integration System**
   - **Status**: Decided
   - **Context**: The need for flexibility, ease of integration, and the ability to manage different data formats along with easy routing.
   - **Evaluation Criteria**: 
     - **Ease of Integration**: Handle different data formats, different application stacks and protocols.
     - **Maintainability**: Ease of updating and deploying services independently.
     - **Autonomy**: Third party apps should be able to integrate and exchange data without much changes in codebase.
   - **Options**: 
     - **Webhooks and API endpoints**: Simple REST based architecture which can be easily integrated.
     - **Integration Hubs(Apache Camel)**: More complex but provides flexibility,scalability and ease of integration even with legacy systems.
   - **Decision**: Adopt Integration Hubs architecture using open source Apache Camel to support different data formats, easy routing and easy
                    integration even with legacy systems.
   - **Implications**: Increased complexity in service management and orchestration.
   - **Resolution for Issues**: Develop comprehensive monitoring and alerting systems (e.g., Prometheus, Grafana) to proactively manage service failures.
   - **Consultation**: DevOps team, senior architects.
