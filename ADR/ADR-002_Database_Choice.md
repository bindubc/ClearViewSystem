**ADR-002: Database Choice**
   - **Status**: Decided
   - **Context**: The need for flexibility in data schema and scalability for candidate data management.
   - **Evaluation Criteria**: 
     - **Scalability**: Ability to efficiently manage growing data volumes.
     - **Flexibility**: Capability to adapt to changing requirements.
     - **Ease of Querying**: Support for complex queries and aggregations.
   - **Options**:
     - **SQL (PostgreSQL)**: Strong consistency and robust querying capabilities.
     - **NoSQL (MongoDB)**: Flexible schema and high scalability.
     - **Blob/Object Storage (AWS S3)**: Useful for storing objects like files(resumes in this case)
   - **Decision**: Use PostgreSQL for structured data, MongoDB for semi and unstructured data and AWS S3 for object storage.
   - **Implications**: Need to ensure data integrity and handle eventual consistency.
   - **Failover Strategy**: Utilize MongoDB's replica sets and sharding for high availability and horizontal scaling.
   - **Resolution for Issues**: Establish data validation and consistency checks to mitigate issues related to eventual consistency.
   - **Consultation**: Database administrators, development team.


