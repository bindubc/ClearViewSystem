### Anonymization Service Architecture and Data Flow

#### Content

1. [Overview of Anonymization Service](#s1)
    -  [Communication with AI Services](#s4)
    - [Data/Operation Flow](#s5)
    - [DataFlow](#s6)
    - [Issues and Resolution](#s7)
3. [Event-Driven Architecture for AI Triggering](#s2)
    - [Example of Events](#s8)
    - [Event Flow](#s9)
5. [Storage](#s3)
    - [Why use of separate db](#s10)
    - [Integration with AI Engine](#s11)

<a name="s1"></a>
#### **1. Overview of Anonymization Service:**
The **Anonymization Service** is responsible for removing or masking personally identifiable information (PII) from resumes, candidate profiles, and other sensitive data to prevent bias and ensure compliance with privacy regulations. It interacts with various components, including the AI processing engine, Candidate Profile Service, and external databases.

#### **2. Database Use:**
- The **Anonymization Service** can use either:
  1. **Shared Databases:** It may access the same Candidate Profile Database to pull the information that requires anonymization.
  2. **Separate Anonymization Database:** A separate database can be created specifically for storing anonymized data if:
    - There is a strict separation required between raw data and processed/anonymized data.
    - Storage of intermediate anonymized versions is necessary for auditing or compliance.
    - Frequent access and storage operations would cause overhead on the main database.

- **Recommendation:**
  - Use a separate **Anonymized Data Store** for logs and records that must be retained for auditing or testing, but leverage shared databases for direct anonymization in real-time to avoid redundancy.

<a name="s4"></a>
#### **3. Communication with AI Services:**
The Anonymization Service communicates directly with the AI processing engine to ensure that the de-identified data maintains context and structure, even when removing identifiers like names, genders, or locations.

<a name="s5"></a>
- **Data/Operation Flow:**
  1. **Input:** 
     - An AI job is triggered when a candidate profile is created or a resume is uploaded.
     - The Candidate Profile Service or Resume Upload Service sends the raw data to the Anonymization Service.
  2. **Anonymization Process:**
     - The service identifies PII markers using pre-defined AI models (e.g., Named Entity Recognition models).
     - The PII data is masked, removed, or replaced with placeholders.
  3. **Communication with AI Processing Engine:**
     - The anonymized data is sent to the AI Engine via secure API calls.
     - The AI engine performs further analysis such as skill extraction, semantic understanding, or matching against job descriptions without using sensitive identifiers.
  4. **Storage:**
     - Once processed, the anonymized data can be stored in the main Candidate Database or a dedicated Anonymization Database, depending on the use case and compliance needs.

- **Data Exchange Protocol:**
  - All communication between the Anonymization Service and AI Engine is typically secured using HTTPS with JWT-based authentication to maintain security and integrity.

<a name="s6"></a>
#### **4. Detailed Data Flow:**
**Step-by-Step Communication Process:**

1. **Raw Data Submission:**
   - When a resume or candidate profile is uploaded, the Candidate Profile Service or Resume Management Service triggers a request to the Anonymization Service.
   
2. **Anonymization Service Actions:**
   - The service identifies PII (such as name, email, phone number, and other demographic information) using machine learning models.
   - Each identified field is either masked or replaced with an anonymous identifier.

3. **AI Engine Request:**
   - The Anonymization Service sends a request to the AI Processing Engine with the anonymized data.
   - **API Call Example:** `POST /anonymized-profile` with payload `{ "profile_id": 12345, "anonymized_data": {...} }`

4. **AI Engine Response:**
   - The AI Engine processes the anonymized data for resume parsing, skill extraction, and job matching, returning a structured response.

5. **Update and Storage:**
   - The processed data is then sent back to the Candidate Profile Service or stored in a separate database depending on whether further anonymized processing is needed.

#### **5. Components Involved:**
1. **Anonymization Service**
   - Responsible for removing PII and interacting with AI.
2. **Candidate Profile Service**
   - Sends and receives profile data with anonymization markers.
3. **AI Processing Engine**
   - Consumes anonymized data and produces processed outputs like skill extraction.
4. **Anonymized Data Store**
   - Optional database for storing anonymized versions of the profiles.
   
#### **6. Sequence Diagram:**

```plaintext
1. [Candidate Profile Service/API Upload] → [Anonymization Service]: "Send raw profile data"
2. [Anonymization Service] → [Anonymized Data Store]: "Store anonymized data (optional)"
3. [Anonymization Service] → [AI Processing Engine]: "Send anonymized data for further processing"
4. [AI Processing Engine] → [Anonymization Service]: "Return processed data"
5. [Anonymization Service] → [Candidate Profile Service]: "Update profile with anonymized data"
```
<a name="s7"></a>
#### **7. Issues and Resolution:**
- **Issue:** Identifiers like gender-specific pronouns or names can be hard to remove while preserving context.
  - **Resolution:** Implement machine learning models that can infer sensitive data based on patterns, not just keywords.

- **Issue:** Performance overhead due to multiple processing layers (anonymization and AI).
  - **Resolution:** Implement a pipeline that optimizes for batch processing and parallel execution.

- **Issue:** Anonymization might lead to loss of meaningful context.
  - **Resolution:** Use pseudonymization (e.g., replace names with generic placeholders) instead of full redaction to maintain sentence flow for NLP models.

#### **8. Considerations for High Availability (HA) and Failover:**
- Use asynchronous messaging queues between the Anonymization Service and AI Engine to decouple operations and improve fault tolerance.
- Implement a retry mechanism and circuit breaker pattern to handle failures in downstream AI services.

<a name="s2"></a>
### **Event-Driven Architecture for AI Triggering:**

The AI job is typically triggered via an event-driven architecture using asynchronous messaging systems like **Kafka**, **RabbitMQ**, or **AWS SNS/SQS** to handle profile updates or resume uploads. 

#### **1. Overview:**
In an event-driven architecture, different services emit events whenever there is a state change or an important action is completed. For example:

- When a **new candidate profile is created**, the Candidate Profile Service can publish a **`CandidateProfileCreated`** event.
- When a **resume is uploaded or updated**, the Resume Service can publish a **`ResumeUploaded`** or **`ResumeUpdated`** event.

The AI Processing Service or Anonymization Service can listen to these events and trigger their own processes asynchronously, avoiding tight coupling between services and improving scalability.

<a name="s8"></a>
#### **2. Example of Events:**

- **`CandidateProfileCreated`:**
  ```json
  {
    "event_id": "123456",
    "event_type": "CandidateProfileCreated",
    "profile_id": "abcd-1234-xyz",
    "timestamp": "2024-09-30T10:00:00Z"
  }
  ```

- **`ResumeUploaded`:**
  ```json
  {
    "event_id": "654321",
    "event_type": "ResumeUploaded",
    "resume_id": "resume-5678",
    "profile_id": "abcd-1234-xyz",
    "file_name": "JohnDoeResume.pdf",
    "timestamp": "2024-09-30T10:05:00Z"
  }
  ```
<a name="s9"></a>
#### **3. Event Flow:**

- **Step 1: Candidate Profile Service / Resume Service Emits Events:**
  - When a new profile is created or a resume is uploaded, the respective service publishes an event to a message broker (e.g., Kafka Topic `CandidateEvents`).

- **Step 2: Anonymization Service / AI Processing Service Subscribes to Events:**
  - The Anonymization Service listens to relevant events (`CandidateProfileCreated`, `ResumeUploaded`) to start processing the profile data.
  - An **Event Processor** component in the AI Service processes these events to initiate further actions, like extracting skills or matching against job descriptions.

- **Step 3: Triggering AI Jobs:**
  - When an event is detected, the AI Service pulls the relevant data (either raw or anonymized) and initiates the AI job.
  - The job may involve multiple steps, such as parsing the resume, extracting key information, or generating recommendations.

- **Step 4: Update and Notify:**
  - Once the AI job completes, the processed data is updated back in the database, and a **`ProfileProcessed`** or **`ResumeProcessed`** event is emitted.
  - This allows downstream services to react, such as notifying the candidate about the status update.

#### **4. Benefits of Event-Driven Architecture:**
1. **Decoupling:** Services operate independently and are loosely coupled.
2. **Scalability:** Components can scale independently based on the number of events.
3. **Resilience:** If a service fails, the events can be reprocessed later.
4. **Flexibility:** Easily add new consumers to react to events without changing the existing flow.

#### **5. Example Event Flow Using Kafka:**

- **Event Producer (Candidate Profile Service):**
  ```python
  # Pseudocode Example for Publishing an Event
  from kafka import KafkaProducer
  import json

  producer = KafkaProducer(bootstrap_servers='localhost:9092',
                           value_serializer=lambda v: json.dumps(v).encode('utf-8'))

  event = {
      "event_id": "123456",
      "event_type": "CandidateProfileCreated",
      "profile_id": "abcd-1234-xyz",
      "timestamp": "2024-09-30T10:00:00Z"
  }

  producer.send('CandidateEvents', value=event)
  producer.flush()
  ```

- **Event Consumer (Anonymization Service):**
  ```python
  from kafka import KafkaConsumer

  consumer = KafkaConsumer('CandidateEvents',
                           bootstrap_servers='localhost:9092',
                           value_deserializer=lambda m: json.loads(m.decode('utf-8')))

  for message in consumer:
      event = message.value
      if event['event_type'] == 'CandidateProfileCreated':
          process_profile(event['profile_id'])  # Initiate anonymization or AI job
  ```

<a name="s3"></a>
### Storage 

The output of the Anonymization Service is typically stored in a **separate database** to maintain data privacy and adhere to the principles of **data segregation**. This ensures that personally identifiable information (PII) is separated from the anonymized data, making it more secure and compliant with data protection regulations such as GDPR.

### **Database Consideration for Anonymized Data:**

1. **Separate Anonymized Data Store:**
   - The Anonymization Service output can be stored in a **dedicated anonymized data store** such as a **NoSQL database** (e.g., MongoDB, Amazon DynamoDB) or a **SQL database** (e.g., PostgreSQL, MySQL), depending on the nature of the anonymized data and the required query patterns.

2. **Characteristics of the Anonymized Data Store:**
   - **Data Segregation**: Ensures that anonymized and raw data are kept separate.
   - **Data Masking**: Stores only the non-sensitive parts of the candidate profiles, such as skills, work experience, and education.
   - **Access Control**: Role-based access control (RBAC) and encryption mechanisms can be applied to this database to prevent unauthorized access.

<a name="s10"></a>
3. **Why Use a Separate Database?**
   - **Compliance**: Helps maintain compliance with regulations (GDPR, CCPA).
   - **Performance**: Reduces the risk of performance issues in the main candidate profile database.
   - **Security**: Isolates sensitive data to prevent accidental exposure.

### **Data Flow between Anonymization Service and AI Service:**
After anonymizing the candidate profile or resume, the anonymized data is stored in the Anonymization Service's database and then shared with the AI Service for further processing, such as skill extraction and job matching.

1. **Primary Anonymized Data Store:**
   - An **anonymized profile database** (e.g., MongoDB or PostgreSQL) stores the anonymized profiles.
   - The structure typically includes:
     ```json
     {
       "anonymized_profile_id": "anon-profile-123",
       "anonymized_name": "Candidate XYZ",
       "skills": ["Python", "Data Analysis", "Machine Learning"],
       "experience": ["Company A", "Company B"],
       "education": ["University of Example"],
       "job_history": ["Data Scientist", "Software Engineer"],
       "timestamp": "2024-09-30T10:05:00Z"
     }
     ```

2. **Reference in Main Profile Database:**
   - The main profile database (e.g., Amazon RDS or PostgreSQL) can have a **reference** to the anonymized profile ID:
     ```json
     {
       "profile_id": "abcd-1234-xyz",
       "candidate_name": "John Doe",
       "resume_id": "resume-5678",
       "anonymized_profile_id": "anon-profile-123",
       "timestamp": "2024-09-30T10:00:00Z"
     }
     ```
<a name="s11"></a>
### **Integration with AI Processing:**
- The **AI Service** can read the anonymized profile data from the anonymized data store when performing its analysis and recommendation tasks.
- The **Data Fetch** step ensures that only non-sensitive fields are accessed:
  - e.g., Retrieve `skills`, `experience`, and `education` for **job matching**.

### **Summary:**
The Anonymization Service’s output should be stored in a **dedicated anonymized data store** that is:
- **Isolated** from the main profile database.
- **Secured** with encryption and access control.
- **Structured** to facilitate downstream processes (e.g., AI, analytics) without exposing sensitive data.

