## Container Diagram for ClearView

The Container Diagram for ClearView illustrates the high-level architecture, highlighting the primary software components, their responsibilities, and interactions within the system. It represents the core services and their relationships, providing a structured view of how the system is organized and how different containers communicate with each other and external systems.


<img src="https://github.com/user-attachments/assets/76d1dd09-e638-4d95-972f-97454398f74b" alt="drawing" width="8000" height="800"/>



1. **Users and Roles**
   - **Employers**
     - Interact with the platform to create and manage job postings, view anonymized candidate profiles, and make data-driven hiring decisions.
   - **Job Seekers**
     - Use the platform to create anonymized profiles, view job recommendations, and receive feedback on application status.
   - **DEI Consultants and Admin**
     - Monitor and evaluate hiring processes, review interview data, and provide insights into potential bias.

2. **Containers in the System**

   - **Web Application/Client Application (Frontend)**
     - Technology: **React, Angular**
     - **Purpose**: Provides the main interface for different user types (Employers, Job Seekers, and DEI Consultants). It is responsible for displaying dashboards, managing interactions, and sending API requests to backend services.
     - **Connections**: 
       - Connects to the **API Gateway** to access backend services.
       - Consumes data from the **Analytics & Reporting Service** to present actionable insights.
  
   - **API Gateway**
     - Technology: **Kong, AWS API Gateway**
     - **Purpose**: Serves as the entry point for all incoming client requests. Manages routing, authentication, and traffic between frontend and backend microservices.
     - **Connections**: 
       - Routes requests to internal services like **Job Management**, **Candidate Profile Service**, **AI Matching Engine**, and **Notification Service**.
       - Connects to **Identity & Access Management (IAM)** for authentication and authorization.

   - **Auth (Identity & Access Management) Service**
     - Technology: **OAuth2, Keycloak**
     - **Purpose**: Manages user authentication, roles, and permissions for various components.
     - **Connections**: 
       - Connected to the **API Gateway** for validating user sessions.
       - Manages user roles for different containers like the **Admin Console** and **Job Seeker Portal**.

   - **Candidate Profile Service**
     - Technology: **Python (Flask), MongoDB**
     - **Purpose**: Stores and manages anonymized candidate profiles. This service handles data transformations to eliminate bias indicators.
     - **Connections**: 
       - Interacts with the **Anonymization Engine** for processing and de-identifying profiles.
       - Sends profile data to the **AI Matching Engine** for job fit evaluations.

   - **Job Management Service**
     - Technology: **Java (Spring Boot), PostgreSQL**
     - **Purpose**: Manages job postings, application workflows, and job status tracking. It provides functionalities for creating, updating, and deleting job records.
     - **Connections**: 
       - Linked to the **Candidate Profile Service** to update application statuses.
       - Interacts with external **Job Board Integration Service** for synchronizing job postings.

   - **AI Matching and Recommendation Engine**
     - Technology: **Python, TensorFlow, Scikit-learn**
     - **Purpose**: Evaluates candidate profiles based on their experience and S.M.A.R.T goals, generating a matching score for job recommendations.
     - **Connections**: 
       - Consumes data from the **Candidate Profile Service** and **Job Management Service**.
       - Sends results to the **Web Application** for display.

   - **Anonymization and Bias Reduction Engine**
     - Technology: **Python, Numpy, Pandas**
     - **Purpose**: Removes PII (Personally Identifiable Information) and other bias indicators from candidate profiles before storing them.
     - **Connections**: 
       - Interacts with the **Candidate Profile Service** to transform incoming data.
       - Feeds anonymized profiles to the **AI Matching Engine**.

   - **Interview Management Service**
     - Technology: **Node.js, Redis**
     - **Purpose**: Manages interview scheduling, feedback collection, and status updates. It tracks interactions between candidates and employers.
     - **Connections**: 
       - Integrates with external calendaring services like **Google Calendar** and **Outlook**.
       - Connects to the **Notification Service** for interview reminders.

   - **Notification & Messaging Service**
     - Technology: **Twilio, SendGrid, RabbitMQ**
     - **Purpose**: Sends email and in-app notifications for key events like interview scheduling, application updates, and feedback collection.
     - **Connections**: 
       - Connects to the **Interview Management Service** and **Web Application** to trigger notifications based on user actions.
       - Linked with external services like **Twilio** for SMS notifications.

   - **Data Aggregation and Analytics Service**
     - Technology: **Apache Spark, AWS Athena**
     - **Purpose**: Processes and aggregates data points like hiring decisions and demographic patterns, generating reports and visualizations.
     - **Connections**: 
       - Consumes data from the **Candidate Profile Service** and **Job Management Service**.
       - Feeds insights to the **Reporting Service** for presentation.

   - **Integration Gateway**
     - Technology: **Spring Boot, Apache Camel**
     - **Purpose**: Manages communication with external systems like ATS platforms and job boards. It handles data transformation and error handling.
     - **Connections**: 
       - Linked to **External HR System Adapters** to translate data and synchronize profiles.
       - Feeds data into internal services like the **Job Management Service**.

   - **External HR System Adapters**
     - Technology: **Custom API Adapters (Java, Python)**
     - **Purpose**: Acts as a bridge to external ATS platforms (e.g., Greenhouse, Workday) to ensure seamless data flow and integration.
     - **Connections**: 
       - Sends and receives data through the **Integration Gateway**.
       - Synchronizes job and candidate information between systems.

   - **Databases (Candidate, Job, Audit)**
     - Technology: **MongoDB, PostgreSQL, DynamoDB**
     - **Purpose**: Stores structured and unstructured data related to candidate profiles, job postings, and audit logs.
     - **Connections**: 
       - Accessed by respective services (e.g., **Candidate Profile Service**, **Job Management Service**).
       - Interacts with the **Data Aggregation Service** for report generation.

---

### **Interactions between Components**
- **Web Application ↔ API Gateway**: The UI components send user requests (e.g., create job posting, view profile) to the backend through the API Gateway.
- **API Gateway ↔ IAM Service**: The gateway validates each request against the IAM service to ensure the user is authenticated.
- **API Gateway ↔ Backend Services**: The gateway routes incoming requests to specific services like the Job Management Service or Candidate Profile Service.
- **AI Matching Engine ↔ Candidate Profile Service**: The matching engine fetches profiles, evaluates them against job descriptions, and sends results back.
- **Interview Management Service ↔ Notification Service**: The interview service triggers notifications for scheduling updates, reminders, and feedback collection.

This description outlines the components and their interactions within the ClearView container diagram, providing a clear picture of the high-level architecture.
