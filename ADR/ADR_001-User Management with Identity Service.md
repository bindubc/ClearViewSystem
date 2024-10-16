# **User Management, Identity Service with OIDC**

## **Context**
The ClearView platform requires a secure and confidential method for users, including both employers and job seekers, to register and authenticate within the system. This user information is highly sensitive, containing personally identifiable information (PII), such as resumes, job histories, and contact information, which must be encrypted and accessible only to authorized ClearView services.

ClearView’s primary objectives are:
- Ensuring data confidentiality and protection from external threats.
- Complying with GDPR and other relevant data protection regulations.
- Minimizing reliance on third-party authentication providers to reduce potential points of failure and risk of exposure.
- Providing seamless and scalable authentication for a large user base across multiple geographies.

Data anonymization and encryption are crucial to ensuring that no external entity can access user data without proper authorization. The chosen identity management solution must be compatible with ClearView’s anonymization service, which removes identifiers to prevent bias in the hiring process.

## **Status**
Proposed

## **Evaluation Criteria**
In making this decision, we considered the following key factors:
- **Security**: The ability to protect user data, enforce encryption, and prevent unauthorized access.
- **Privacy**: Ensuring compliance with GDPR and avoiding sharing personal data with third-party providers unnecessarily.
- **User Experience**: Balancing security with ease of use, offering features such as multi-factor authentication and secure password recovery.
- **Scalability**: Handling increasing user volumes and supporting global operations with minimal latency.
- **Control Over Data**: Maintaining ClearView's control over sensitive user data without relying too heavily on third-party authentication systems.
- **Integration**: Seamless integration with ClearView's existing services, such as Resume Parsing, Matching Service, and the Anonymization Service.

## **Options**

### **Option 1: Auth Service with OIDC (OpenID Connect)**
**Description**: Implement an in-house authentication service that uses the OIDC protocol to manage user identities and provide secure access to the platform.

**Pros**:
- Full control over user data and authentication processes.
- Supports industry-standard security features like token-based authentication, multi-factor authentication (MFA), and encryption.
- Easier to ensure compliance with regulations (GDPR, EEOC).
- Seamless integration with ClearView’s Anonymization Service and internal data processing.

**Cons**:
- Higher implementation complexity, requiring expertise in security, token management, and encryption.
- Increased operational overhead for maintaining and updating the OIDC service.
- Potential latency in user authentication if not optimized for scalability.

### **Option 2: Integration with External Authentication Providers (Google, Facebook, etc.)**
**Description**: Integrate with existing external authentication providers to allow users to sign up or log in using social accounts.

**Pros**:
- Simplifies user registration and login process (users can log in with existing accounts).
- Offloads authentication complexity to external providers.
- Reduces internal resource allocation for managing identity services.

**Cons**:
- Reliance on third-party providers for user data security.
- Sharing user data with external providers introduces potential privacy risks.
- Difficult to enforce GDPR compliance, as data could be exposed to third-party systems.
- Incompatible with ClearView’s anonymization service, which relies on full control over user identity data.

### **Option 3: Combination of Auth Service with External Auth Providers**
**Description**: Combine an in-house authentication system with external authentication providers. Users can log in with social accounts, but core identity management is handled by ClearView.

**Pros**:
- Flexibility for users to choose between external providers or ClearView’s internal authentication.
- ClearView retains control over core identity data, while allowing external sign-in options for convenience.
- Reduces implementation complexity compared to building the entire system in-house.

**Cons**:
- Added complexity in managing hybrid systems (mapping external identities to ClearView’s internal identity management).
- Increased risk of misalignment in security policies between internal and external systems.
- Could still expose some user data to third-party providers, potentially complicating compliance efforts.

## **Decision**
The selected option is **Auth Service with OIDC**. This option provides the necessary control over user data, ensuring that sensitive information is securely managed within ClearView's infrastructure. External providers are avoided to minimize risks related to data breaches, third-party dependencies, and privacy compliance issues.

ClearView’s user base includes large enterprises, as well as individual job seekers. It’s critical to ensure that data belonging to both employers and candidates is encrypted and protected from unauthorized access, which makes an in-house OIDC solution the best fit. Additionally, OIDC integrates seamlessly with other internal services, such as the Anonymization Service and Resume Parsing.

## **Implications**

### **Positive Consequences**:
- Full control over user identity and data security, ensuring compliance with GDPR, EEOC, and other privacy regulations.
- Improved privacy and confidentiality of sensitive data.
- Seamless integration with ClearView’s existing internal services and future scalability.
- Enables additional security features such as MFA, token revocation, and access logs.

### **Negative Consequences**:
- Increased operational and development complexity in building and maintaining the OIDC service.
- Requires expertise in security and authentication management.
- Higher upfront costs due to infrastructure and development needs.

## **Consultation**
Input was gathered from:
- **Security Team**: Provided insights on encryption, token management, and regulatory compliance.
- **Data Protection Officer**: Reviewed GDPR and EEOC compliance implications.
- **Engineering Team**: Provided technical feasibility analysis and integration points with other services like Resume Parsing, Job Matching, and Anonymization.
  
---

### **Additional Considerations**:
- **Failure Scenarios**: OIDC should support token invalidation and recovery mechanisms to handle service outages. Failover strategies should be in place to route authentication requests to backup systems in case of downtime.
- **Scalability Strategy**: OIDC should be optimized to handle thousands of authentication requests per minute with minimal latency, leveraging cloud scaling techniques (e.g., AWS Auto Scaling) to ensure availability.
- **Future Extensions**: The system should be designed to easily integrate with future services, such as user role management and access policies, without requiring a complete overhaul.

---

