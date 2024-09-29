
![image](https://github.com/user-attachments/assets/0ae9fe17-6a0c-481b-a941-e2b4b838cd26)


### **ClearView Context Diagram**

The **ClearView Context Diagram** represents the high-level interactions between the ClearView HR platform and its external systems, users, and supporting services. It shows how ClearView fits into its environment and the relationships it has with various entities. This diagram provides an overview of the major stakeholders and components that are involved in achieving ClearView’s goal of providing a bias-reducing hiring solution through anonymization and objective skill evaluation.

### **Components of the Context Diagram**

1. **ClearView Platform** (Central System)
   - This is the core HR platform where all internal processes like candidate anonymization, AI-based skill evaluation, resume transformation, and analytics occur.
   - The ClearView platform is responsible for processing candidate data, generating metrics, and providing analytics reports.

2. **External Systems**
   - **DEI (Diversity, Equity, and Inclusion) Consultant Platform**: External systems used by DEI consultants to monitor, evaluate, and report on the hiring process. ClearView provides anonymized data and metrics for review.
     
3. **Users**
   - **Employers**: Hiring managers and HR personnel use the platform to evaluate candidate profiles without exposure to biases and track the overall hiring process.
   - **Job Candidates**: Individuals seeking job opportunities and career growth. They upload resumes and track their application status through the platform.
   - **DEI Consultants**: External consultants who assess interview fairness and provide feedback to improve the hiring experience.
   - **Admin**: admin User in ClearView would have elevated privileges to manage other users, oversee data access, monitor usage, and generate detailed reports.

4. **Supporting Services**
   - **AI/ML Service**: The core AI engine that anonymizes candidate data, evaluates skills, and suggests profile improvements.
   - **Notification Service**: Handles email or in-app messaging to inform users (employers and candidates) about updates in the hiring process.
   - **Authentication Service**: Manages secure access and user authentication for different types of users and external systems.

### **Interconnections and Data Flow**
The context diagram shows how ClearView interfaces with its users and external systems through the following flows:

- **Employers → ClearView Platform**: Employers interact with ClearView to upload job requirements, review anonymized candidate profiles, and manage the interview process.
- **Job Candidates → ClearView Platform**: Candidates register on the platform, submit their resumes, and receive feedback on application status or skills.
- **ClearView Platform → DEI Consultant Platform**: Anonymized data and interview analytics are shared for review and feedback.
- **ClearView Platform → AI/ML Service**: The core AI service is invoked for skill matching, evaluation, and anonymization processes.
- **ClearView Platform → Notification Service**: Sends notifications and alerts to users for status updates, interview scheduling, and new job postings.



![image](https://github.com/user-attachments/assets/4e6f4fa6-4235-4975-830b-83fea0e1c4ce)


