**ADR-005: Data Encryption Strategy**
   - **Status**: Decided
   - **Context**: Compliance requirements for handling PII.
   - **Evaluation Criteria**: Security, performance, compliance.
   - **Options**:
     - AES for data at rest and TLS for data in transit.
     - Only encrypt sensitive fields, leaving others unencrypted.
   - **Decision**: Encrypt all PII using AES; enforce TLS for all communications.
   - **Implications**: Performance overhead but necessary for compliance.
   - **Consultation**: Compliance officer, security team.

