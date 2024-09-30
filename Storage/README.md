### **Storage Estimation for ClearView HR System**

__DB Schema__: https://github.com/bindubc/ClearViewSystem/blob/main/Storage/DB%20Schema.md 

When estimating storage, consider the type of data stored, the expected volume, and how long the data will be retained. For ClearView, storage requirements will include candidate profiles, anonymized data, job postings, system logs, metadata, analytics data, and audit trails. Below is a detailed estimation for each data category:

---

#### **1. Candidate Profile Storage**
   - **Data Type**: Text (Resumes, qualifications, S.M.A.R.T goals, and anonymized data).
   - **Fields**: Name, Email (masked), Experience, Skills, Education, Certifications, Profile Picture (if applicable).
   - **Average Size per Candidate**: 10 KB (text fields) + 50 KB (profile picture) = **60 KB**
   - **Estimated Candidates**: 100,000 (initial phase)
   - **Total Storage Required**: 100,000 candidates × 60 KB = **6 GB**

#### **2. Job Postings Storage**
   - **Data Type**: Text (Job descriptions, requirements, location, compensation details).
   - **Average Size per Posting**: 5 KB
   - **Estimated Postings**: 20,000 per year.
   - **Total Storage Required**: 20,000 × 5 KB = **100 MB**

#### **3. System Logs and Audit Trails**
   - **Data Type**: Logs (security, user activity, transactions).
   - **Fields**: Timestamp, User ID, Action Performed, IP Address, Metadata.
   - **Average Log Entry Size**: 0.5 KB
   - **Log Frequency**: Assume 50 logs/user/day for 100,000 users = 5,000,000 log entries/day.
   - **Retention Period**: 365 days
   - **Total Storage Required**: 5,000,000 entries × 0.5 KB × 365 days = **912.5 GB/year**

#### **4. Anonymized Data and Analytics**
   - **Data Type**: Aggregated analytics and anonymized profiles.
   - **Fields**: Anonymized attributes (age, gender, experience), matching results, success/failure metrics.
   - **Average Size per Candidate**: 2 KB
   - **Data Points**: 100,000 candidates × 20 attributes (anonymized) = 2,000,000 data points.
   - **Total Storage Required**: 2,000,000 × 2 KB = **4 GB**

#### **5. Data Retention and Compliance**
   - **Data Type**: Archived records for compliance (GDPR and EEOC).
   - **Retention Period**: 5 years for compliance purposes.
   - **Estimated Growth**: 20% growth in data/year.
   - **Total Storage Required**: Current Data × Growth Factor over 5 years.
   - **Example Calculation**: For a 6 GB candidate profile database:
     - Year 1: 6 GB
     - Year 2: 6 GB × 1.2 = 7.2 GB
     - Year 3: 7.2 GB × 1.2 = 8.64 GB
     - Year 4: 8.64 GB × 1.2 = 10.37 GB
     - Year 5: 10.37 GB × 1.2 = 12.44 GB
   - **Total Storage for Retention**: **12.44 GB** (candidate profiles) + incremental log growth.

#### **6. Notification and Messaging Data**
   - **Data Type**: Notifications (email and in-app), user messages.
   - **Average Size per Message**: 1 KB (simple text messages).
   - **Messages/User/Day**: 2 (for 100,000 users) = 200,000 messages/day.
   - **Total Storage Required**: 200,000 × 1 KB × 365 days = **73 GB/year**

#### **7. Metadata and Configuration Storage**
   - **Data Type**: Metadata (system configurations, role mappings, component settings).
   - **Average Size**: 50 KB per system component.
   - **Total Components**: 100 components.
   - **Total Storage Required**: 100 × 50 KB = **5 MB**

#### **8. Image and Document Attachments**
   - **Data Type**: Attachments like resumes, certificates, and recommendation letters.
   - **Average Size per Document**: 500 KB
   - **Estimated Documents/User**: 2 per candidate
   - **Total Storage Required**: 100,000 users × 2 × 500 KB = **100 GB**

---

### **Overall Storage Estimation for Year 1**
1. **Candidate Profiles**: 6 GB
2. **Job Postings**: 100 MB
3. **System Logs and Audit Trails**: 912.5 GB
4. **Anonymized Data and Analytics**: 4 GB
5. **Compliance Data Retention**: 12.44 GB (yearly candidate profile growth)
6. **Notification and Messaging Data**: 73 GB
7. **Metadata and Configuration**: 5 MB
8. **Image and Document Attachments**: 100 GB

#### **Total Yearly Storage Requirement**: **~1107.04 GB** (~1.08 TB)

---

### **5-Year Storage Projection**
Taking into account a 20% yearly growth rate in candidate profiles, system logs, and message data:

1. **Year 1**: 1.08 TB
2. **Year 2**: 1.3 TB
3. **Year 3**: 1.56 TB
4. **Year 4**: 1.87 TB
5. **Year 5**: 2.24 TB

#### **Total Projected Storage for 5 Years**: **~8.05 TB**

---

### **Recommendations**
1. **Data Partitioning and Archiving**:
   - Use **AWS S3** or **Azure Blob Storage** for long-term archival.
   - Implement partitioning strategies for logs and compliance data.

2. **Compression and Deduplication**:
   - Use compression algorithms for text-based storage.
   - Deduplicate documents and anonymized data points.

3. **Auto-Scaling Storage**:
   - Leverage auto-scaling storage solutions like **AWS EFS**, **Azure File Storage**, or **Google Cloud Filestore** to handle sudden spikes in data volume.

