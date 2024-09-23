# Architectural-Katas-Fall-2023
<img src="https://cdn.oreillystatic.com/images/live-online-training/og-ak-social.png" alt="drawing" width="1000" height="400"/>

This repository contains team's submission to O'Reilly's [Architectural Katas: Fall 2024](https://www.oreilly.com/live-events/architectural-katas-fall-2024/0642572006974)

## Team

- Bindu B C         &emsp;&emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/bindu-c-a95b1377/)
-  Gopi  Kumar       &emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/bindu-c-a95b1377/)
- Sonali Singh   &emsp;&emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/sonali-singh-219041118/?originalSubdomain=in )
- Mayur Rajwani  &emsp;&emsp;&emsp;<img src="https://cdn3.iconfinder.com/data/icons/free-social-icons/67/linkedin_circle_color-1024.png" alt="drawing" width="20"/> [LinkedIn](https://www.linkedin.com/in/bindu-c-a95b1377/) 

## Structure

- [Architectiure Characteristics]()
- [C4 Models]()
- [ARDs](./ADR/README.md)
  - [000. Use ADR]((./ADR/README.md))
  
## Introduction

Welcome to the architectural story of ClearView - the O'Reilly Fall 2024 Architectural Kata.

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

# ClearView - Transparent Decision Making: HR Platform to Reduce Hiring Bias

### Overview

ClearView is an AI-powered, supplemental HR platform that anonymizes candidate information, emphasizing objective skills and qualifying experiences to reduce bias in the hiring process. It also supports DEI consultants who shadow employer interviews to assess interviewer behavior and report findings, ensuring an equitable hiring environment.

ClearView's HR platform leverages AI to construct personalized, data-driven candidate stories aligned with SMART (Specific, Measurable, Achievable, Relevant, and Time-bound) goals. It anonymizes personal identifiers (e.g., race, lifestyle) until a decision based on qualifications is made. Hiring companies can unlock profiles after objective selection, and aggregated data highlights disparities between those hired and those rejected.


### Key Features and Requirements


* __AI-Powered Resume Reconstruction__: Resumes are converted into SMART goal-based summaries and matched against job descriptions using a similarity score.
* __AI Tips for Resume Improvement__: Automated suggestions to help job seekers optimize their resumes for better alignment with job postings.
* __Anonymization__ : AI eliminates identifiers that may introduce bias, ensuring decisions are based on skills and experience.
* __Data Aggregation and Analysis__: Provides insights into disparities in hiring decisions and generates monthly KPI reports.

### Problem Statements
* __Lack of Impactful Metrics__: Identifying and reducing bias in the candidate hiring and interview process is challenging, as current systems lack actionable data to measure and address bias effectively.
* __Ineffective ATS__: Traditional applicant tracking systems often redundantly fail to match viable candidates to job descriptions, resulting in missed opportunities and inefficient hiring.
