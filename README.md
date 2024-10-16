# Architectural-Katas-Fall-2024
<img src="https://cdn.oreillystatic.com/images/live-online-training/og-ak-social.png" alt="drawing" width="1000" height="400"/>

Welcome to the architectural story of ClearView - the O'Reilly Fall 2024 Architectural Kata.

This repository contains team's submission to O'Reilly's [Architectural Katas: Fall 2024](https://www.oreilly.com/live-events/architectural-katas-fall-2024/0642572006974)

## Team

- Bindu B C         &emsp;&emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/bindu-c-a95b1377/)
-  Gopi  Kumar       &emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/kumar91gopi/)
- Sonali Singh   &emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/sonali-singh-219041118/?originalSubdomain=in )
- Mayur Rajwani  &emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/bindu-c-a95b1377/) 

## Index

Here's a categorized index based on the content you've provided:

__Video__: [System Design Explanation](https://drive.google.com/file/d/1DVPQZntFyxFbdJqTcmRJ4l4_xdmvLp7U/view)

###   **Introduction and Overview**
   - [Introduction](#Introduction)
   - [Problem Overview](#ClearView) 
   - [ClearView Functional Requirement](#Requirements)
   - [Architectiure NonFunctional Requirement](#characteristics)

###  **Use Cases and User Journey**
   - [Usecase](https://github.com/bindubc/ClearViewSystem/tree/main/UseCase)
   - [UserJourney](https://github.com/bindubc/ClearViewSystem/blob/main/UserJourney.md)
   

###  **System Design and Architecture**
   - [Scrutinizing Component](#ComponentAnalysis)
   - [Deployment](https://github.com/bindubc/ClearViewSystem/blob/main/deployment.md)
   - [System Design and Component Analysis](https://github.com/bindubc/ClearViewSystem/tree/main/Component%20Analysis)
   - [API](https://github.com/bindubc/ClearViewSystem/tree/main/API)
   - [C4 Models](https://github.com/bindubc/ClearViewSystem/tree/main/C4)
   - [ADR](https://github.com/bindubc/ClearViewSystem/tree/main/ADR)
   - [Architecture Challenges](https://github.com/bindubc/ClearViewSystem/blob/main/ArchitectureCharacteristics/Challenges.md)
   - [Architectiure Characteritics and Functional Requirement Anaalysis](https://github.com/bindubc/ClearViewSystem/tree/main/ArchitectureCharacteristics)
  

### **Technical Considerations**
   - [Fitness Function](https://github.com/bindubc/ClearViewSystem/tree/main/Fitness%20Function)
   - [Storage Estimation](https://github.com/bindubc/ClearViewSystem/tree/main/Storage)
   - [Coding Strategy](https://github.com/bindubc/ClearViewSystem/tree/main/Coding%20Strategy)
   - [Algorithm](https://github.com/bindubc/ClearViewSystem/blob/main/Component%20Analysis/algorthim.md)
   - [DB Schema](https://github.com/bindubc/ClearViewSystem/blob/main/Storage/DB%20Schema.md)

### **Architecture Views**
   * [__Context View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/ContextDiagram.md)
   * [__Container View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/Container.md)
   * [__component View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/Component%20Diagram.md)


### **Deployment and System Configuration**
   - [Deployment](https://github.com/bindubc/ClearViewSystem/blob/main/deployment.md)
   - [System Design Explanation](https://drive.google.com/file/d/1DVPQZntFyxFbdJqTcmRJ4l4_xdmvLp7U/view)
   - [System Design](https://github.com/bindubc/ClearViewSystem/blob/main/images/SystemDesign.mp4)
     
  

<div id="Introduction"></div>

## Introduction


The need for a more inclusive and equitable hiring process has become increasingly urgent, particularly in the tech industry, where underrepresented groups, such as women, people of color, and individuals from marginalized communities, continue to face significant barriers to entry. Despite growing awareness and efforts around diversity and inclusion, systemic issues persist. Traditional hiring practices, often driven by implicit bias, contribute to these challenges by focusing on surface-level attributes like names or backgrounds, which can lead to biased decisions. Without proper tools or metrics to assess the fairness of these processes, companies struggle to create a truly inclusive workforce.

In this context, there is a clear need for platforms like **ClearView**, which leverages AI to remove identifiers that could introduce bias and emphasize candidates' skills and qualifications. By anonymizing candidates and aligning resumes with job requirements based on SMART (Specific, Measurable, Achievable, Relevant, Time-bound) goals, ClearView ensures that hiring decisions are based on merit, reducing the likelihood of unconscious bias. Additionally, organizations like the **Diversity Cyber Council** address the broader need by providing access to education, training, and job placement for underrepresented demographics. Together, these initiatives support a more diverse and inclusive talent pipeline, crucial for addressing the diversity gap in the tech industry.

### Company Overiew

The Diversity Cyber Council is a non-profit organization dedicated to increasing diversity and inclusion within the tech industry. Its primary focus is on underrepresented demographics, aiming to provide them with access to education, training, and job placement opportunities. Here’s a breakdown of its key components:

- __Purpose__ : The council serves groups that are often underrepresented in tech, helping them gain the skills and opportunities necessary to thrive in the workforce.

- __Vision__: Their broader aim is to foster greater inclusion and representation in the tech industry. They do this through initiatives such as:

    * Training programs
    * Mentoring support
    * Networking opportunities
    * Visibility campaigns
- __Goal__: Their main objective is to create a lasting, diverse talent pipeline. This is done by offering effective training programs that lead to direct employment, providing individuals from marginalized communities with equitable access to tech careers.

By focusing on these areas, the Diversity Cyber Council seeks to ensure more inclusive participation in the tech sector, helping to close the diversity gap in the industry.

<div id="ClearView"></div>

# ClearView - Transparent Decision Making: HR Platform to Reduce Hiring Bias

### Overview

ClearView is an AI-powered, supplemental HR platform that anonymizes candidate information, emphasizing objective skills and qualifying experiences to reduce bias in the hiring process. It also supports DEI consultants who shadow employer interviews to assess interviewer behavior and report findings, ensuring an equitable hiring environment.

ClearView's HR platform leverages AI to construct personalized, data-driven candidate stories aligned with SMART (Specific, Measurable, Achievable, Relevant, and Time-bound) goals. It anonymizes personal identifiers (e.g., race, lifestyle) until a decision based on qualifications is made. Hiring companies can unlock profiles after objective selection, and aggregated data highlights disparities between those hired and those rejected.


<div id="Requirements"></div>

### Problem Statements

The problem presented revolves around creating a more inclusive and unbiased hiring process, addressing issues of diversity and representation in the tech industry, particularly for marginalized communities.

* __Lack of Impactful Metrics__: Identifying and reducing bias in the candidate hiring and interview process is challenging, as current systems lack actionable data to measure and address bias effectively.
* __Ineffective ATS__: Traditional applicant tracking systems often redundantly fail to match viable candidates to job descriptions, resulting in missed opportunities and inefficient hiring.

<div id="business"></div>

### Business UseCase
Here are a few **business use cases** for a system like ClearView:

### 1. **Bias-Free Hiring Process**
   - **Problem**: Traditional hiring practices can introduce bias based on factors like gender, age, or ethnicity.
   - **Solution**: ClearView anonymizes candidate profiles and resumes to eliminate identifiable information, allowing recruiters to focus on skills and experience.
   - **Impact**: Reduced bias in hiring decisions and a fairer recruitment process.

### 2. **Automated Resume Matching**
   - **Problem**: Manually sifting through thousands of resumes is time-consuming and inefficient, leading to missed opportunities for both candidates and employers.
   - **Solution**: ClearView uses AI to automatically parse resumes and match candidates with job listings based on skills, experience, and goals.
   - **Impact**: Improved efficiency in finding the right candidate, reducing hiring time and improving match quality.

### 3. **Enhanced Resume Optimization**
   - **Problem**: Candidates often struggle to tailor their resumes to specific job postings, missing out on relevant opportunities.
   - **Solution**: ClearView provides AI-driven tips to help candidates improve their resumes, aligning them better with job requirements.
   - **Impact**: Increased chances of securing an interview by optimizing resumes for applicant tracking systems (ATS).

### 4. **KPI Analytics and Insights for Employers**
   - **Problem**: Companies lack visibility into hiring patterns, including potential biases or bottlenecks in the process.
   - **Solution**: ClearView generates monthly reports with key performance indicators (KPIs), offering insights into hiring trends and bias detection.
   - **Impact**: Data-driven decision-making for continuous improvement in recruitment strategies.

### 5. **Real-Time Application Status Updates**
   - **Problem**: Candidates are often left in the dark regarding their application status, leading to frustration.
   - **Solution**: ClearView sends real-time notifications to candidates about their application status, job matches, and feedback.
   - **Impact**: Improved candidate experience and engagement throughout the hiring process.

### 6. **Scalable Recruitment Platform**
   - **Problem**: Large companies face challenges managing high volumes of applications during peak recruitment periods.
   - **Solution**: ClearView's cloud-based infrastructure ensures scalability, allowing it to handle thousands of concurrent applications seamlessly.
   - **Impact**: Reliable and efficient hiring processes even during periods of high demand.

These business use cases demonstrate how ClearView improves the recruitment process for both employers and job seekers, making it faster, fairer, and more data-driven.

### Key Features and Requirements


* __AI-Powered Resume Reconstruction__: Resumes are converted into SMART goal-based summaries and matched against job descriptions using a similarity score.
* __AI Tips for Resume Improvement__: Automated suggestions to help job seekers optimize their resumes for better alignment with job postings.
* __Anonymization__ : AI eliminates identifiers that may introduce bias, ensuring decisions are based on skills and experience.
* __Data Aggregation and Analysis__: Provides insights into disparities in hiring decisions and generates monthly KPI reports.


### Problem Statements

The problem presented revolves around creating a more inclusive and unbiased hiring process, addressing issues of diversity and representation in the tech industry, particularly for marginalized communities.

* __Lack of Impactful Metrics__: Identifying and reducing bias in the candidate hiring and interview process is challenging, as current systems lack actionable data to measure and address bias effectively.
* __Ineffective ATS__: Traditional applicant tracking systems often redundantly fail to match viable candidates to job descriptions, resulting in missed opportunities and inefficient hiring.

<a name="ComponentAnalysis"></a>
### Component Analysis:

These components form a cohesive architecture for the ClearView platform, enabling it to support user registration, resume processing, job matching, interview management, analytics, and compliance requirements. Each component is designed to be modular, ensuring easy maintenance and scalability.

### Target Users:
* __Employers__: Companies looking for equitable hiring practices.
* __Job Candidates__: Professionals seeking a less biased hiring process, where their skills and experience are prioritized.
* __Administrators__: Platform managers responsible for user registrations, maintaining data analytics, and assisting in bias-reduction strategies for executives.



![image](https://github.com/user-attachments/assets/0ce882b6-9442-4df1-93ec-24347e0cea26)


#####  User Management Components
1. Authentication Service :  Handles user authentication and authorization.
2. User Profile Service:  Manages user profiles and account settings.
3. Role Management Service : Defines permissions for each type of user (Employer, Candidate, Admin, DEI Consultant).

##### Resume Processing Components
1. Resume Upload Service:  Manages the resume upload process.
2. Resume Anonymization Service : Anonymizes candidate resumes to remove personal identifiable information (PII).
3. Resume Analysis Service : Analyzes resumes and generates structured data.

#####  Job Management Components
1. Job Listing Service: Manages job listings posted by employers.
2. Job Matching Service : Matches candidate profiles to job listings using AI.
3. Candidate Management Service : Manages candidate applications for job postings.

#####  Interview Management Components
1. Interview Scheduling Service: Manages scheduling of interviews between employers and candidates.
2. Interview Feedback Service: Collects and manages feedback from interviewers and candidates.

#####  Analytics and Reporting Components
1. Data Aggregation Servic: Aggregates data from various sources for reporting.
2. Report Generation Service:Generates reports for different stakeholders.
3. Dashboard Service: Provides an interactive dashboard for real-time insights.

#####  Notification and Communication Components
1. Notification Service: Manages notifications and alerts.
2. Messaging Service: Enables communication between candidates and employers.

#####  Admin and Compliance Components
1. User Activity Monitoring Service: Monitors user activity and generates logs.
2. Compliance and Security Service: Manages compliance with data protection regulations.
3. Role-Based Access Control (RBAC) Service: Manages permissions based on user roles.


##### Platform Services
1. API Gateway: Manages communication between microservices.
2. Service Registry: Manages discovery of microservices.
3. Logging and Monitoring Service: Centralizes logging and monitoring for all components.


<a name="characteristics"></a>
## Identifying architecture characteristics

   **Reference** : https://github.com/bindubc/ClearViewSystem/blob/main/ArchitectureCharacteristics/README.md 
Choosing the right architectural characteristics is a critical process that lays the foundation for designing an effective architecture and defining efficient data flow within a system. By carefully considering these characteristics, one can determine the most suitable software and hardware components to effectively fulfill the system requirements. This ensures not only the proper functioning of the system but also its scalability, maintainability, and overall performance. Based on the requirements and our expertise, the following top three characteristics have been identified:

![image](https://github.com/user-attachments/assets/bb7da18d-a07e-40cb-9abd-84f148c0c160)

![image](https://github.com/user-attachments/assets/09909c04-669f-40fa-b46e-10ed99c8758a)



1. **Microservices Architecture**
   - **Use Case**: The platform can independently update the **Job Management Service** without affecting the **User Management Service**. If a new feature is added to job postings, it can be deployed without downtime for other services.

2. **High Availability**
   - **Use Case**: During peak hiring seasons, the platform must remain operational for both candidates and employers. Load balancers ensure that traffic is distributed across multiple instances of services, preventing downtime.

3. **Scalability**
   - **Use Case**: If the platform experiences a sudden increase in job postings or candidate registrations, additional instances of the **Notification Service** can be spun up to handle the increased load without affecting performance.

4. **Modularity**
   - **Use Case**: The **Resume Processing Service** can be modified to use a different AI algorithm for parsing resumes without impacting the **Interview Management Service** or other components.

5. **Interoperability**
   - **Use Case**: ClearView integrates with third-party authentication services (like **Auth0**) and external AI tools to enhance resume matching capabilities, allowing smooth communication and data exchange.

6. **Data Consistency**
   - **Use Case**: When a candidate is hired, the **User Management Service** and **Interview Management Service** must reflect this change consistently to avoid discrepancies in user status.

7. **Robust Security**
   - **Use Case**: Sensitive candidate data is protected through encryption during transmission and storage, ensuring that information remains confidential and compliant with regulations like GDPR.

8. **Event-Driven Communication**
   - **Use Case**: When a candidate applies for a job, an event is published to the message queue, triggering notifications to the hiring manager and updating the dashboard in real-time.

9. **Resilience and Fault Tolerance**
   - **Use Case**: If the **Notification Service** encounters an error, the system can automatically retry sending notifications without affecting the overall application’s functionality.

10. **Observability**
    - **Use Case**: The **Monitoring Service** tracks system performance and alerts administrators of unusual activity (e.g., high latency), enabling quick identification and resolution of issues.

11. **Performance Optimization**
    - **Use Case**: Caching frequently accessed job postings can significantly reduce response times for users viewing job listings, enhancing the user experience.

12. **Compliance and Regulatory Considerations**
    - **Use Case**: The platform ensures that all data handling processes are compliant with employment laws and data privacy regulations, providing necessary audit trails and user consent management.

These architectural characteristics are essential for ensuring that the ClearView platform is robust, efficient, and user-friendly. By aligning these characteristics with specific use cases, the platform can better meet the needs of its users while adapting to changes in the job market and technology landscape. If you need more details or specific examples, feel free to ask!

## Designing the Architecture

* [__Context View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/ContextDiagram.md)
* [__Container View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/Container.md)
* [__component View__](https://github.com/bindubc/ClearViewSystem/blob/main/C4/Component%20Diagram.md)

  ## Architecture

  * [__UserJourney__](https://github.com/bindubc/ClearViewSystem/blob/main/UserJourney.md)
  * [__Usecase with API Flow and its Operations__](https://github.com/bindubc/ClearViewSystem/tree/main/UseCase)
  * [__Component Analysis__](https://github.com/bindubc/ClearViewSystem/tree/main/Component%20Analysis)
  * [__Fitness Function__](https://github.com/bindubc/ClearViewSystem/tree/main/Fitness%20Function)
  * [__DB Schema__](https://github.com/bindubc/ClearViewSystem/blob/main/Storage/DB%20Schema.md)
  * [__Storage Estimation__](https://github.com/bindubc/ClearViewSystem/blob/main/Storage/README.md)
  * [__Deployment__](https://github.com/bindubc/ClearViewSystem/blob/main/deployment.md)

   ## System Design

   Link: https://github.com/bindubc/ClearViewSystem/blob/main/images/SystemDesign.mp4

  <video src="https://github.com/bindubc/ClearViewSystem/blob/main/images/SystemDesign.mp4" controls="controls" style="max-width: 730px;"></video>


  ![image](https://github.com/user-attachments/assets/8f4dc98e-fcd0-478b-aa32-f2463c7c472e)


 

  

  

