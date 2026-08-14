# TEAM2 - MoNew [![codecov](https://codecov.io/gh/sb04-team02/sb04-MoNew-team02/graph/badge.svg)](https://codecov.io/gh/sb04-team02/sb04-MoNew-team02)

## Table of Contents
1. [Links](#links)
2. [Project Introduction](#project-introduction)
3. [Tech Stack](#tech-stack)
4. [Project Execution Guide](#project-execution-guide)
   - [1. Prerequisites](#1-prerequisites)
   - [2. Environment Variables](#2-environment-variables)
   - [3. Database Setup](#3-database-setup)
   - [4. External APIs](#4-external-apis)
   - [5. AWS](#5-aws)
   - [6. Running the Project](#6-running-the-project)
   - [7. Batch / Backup Criteria](#7-batch--backup-criteria)
5. [Directory Structure](#directory-structure)
6. [Team Members](#team-members)

---  

## Links
<a href="https://www.notion.so/2-2472c93d1bbc801e992fc5a874008bf1">
  <img src="https://github.com/user-attachments/assets/b8d5ff15-4c53-49ea-83d4-97b08af86455" width="30" height="30" valign="middle" />
  MoNew Team Notion
</a><br><br>
<a href="http://43.200.245.129/#/login">
  <img src="https://github.com/user-attachments/assets/3700f539-d6fe-40b7-869b-e5a4c0a01463" width="30" height="30" valign="middle" />
  Deployment Link ( ~25.09.30 / 25.12.18 ~ 26.06.30 )
</a><br><br>
<a href="http://sprint-project-1196140422.ap-northeast-2.elb.amazonaws.com/sb/monew/api/swagger-ui/index.html">
  <img src="https://github.com/user-attachments/assets/3a34ba65-4ba4-4d1b-a170-16b615bf05cb" width="30" height="30" valign="middle" />
  Swagger API
</a><br><br>
<a href="https://github.com/user-attachments/files/24227954/2._Monew_.pdf">
  <img src="https://github.com/user-attachments/assets/77090a76-0e05-45f6-b563-b885592b8321" width="30" height="30" valign="middle" />
  Portfolio (PDF)
</a><br>

---

## **Project Introduction**

- Project Period: 2025.09.01 ~ 2025.09.23
- MongoDB & PostgreSQL Backup and Recovery System
- Gather scattered news in one place, collecting only the topics you care about!  
  MoNew is an integrated news management platform that consolidates various news sources and allows users to save articles based on their interests.  
  Users receive real-time notifications when articles on their topics of interest are registered, and social features like comments and likes allow them to share opinions with others.
- Stable Batch Management using Spring Batch
  - Custom metrics definition
  - Batch job monitoring via Actuator
  - Target Domains:
    - News Articles: Scraping, Backup
    - Notifications: Deletion
    - Users: Physical Deletion
- Read Optimization with MongoDB
  - Resolved excessive JOIN issues in user activity logs
  - Optimized read performance through denormalization
  - Target Domain: User Activity Logs
- S3 Log Management
  - Daily log file storage in AWS S3

---

## **Tech Stack**

<!--
 - Basic Dev Environment: IntelliJ, Spring Boot(v3.5.5), Java(v17)
- Database: PostgreSQL(v17.5), MongoDB(Atlas), AWS-RDS
- Storage: AWS-S3
- Deployment: Docker, GitHub Actions(CI/CD), AWS(AWS-ECR, AWS-ECS, AWS-EC2)
- Additional Stack: Spring Data JPA, Spring Actuator, Spring WebFlux(Naver API), Jsoup(RSS), Spring Batch, Mockito, micrometer(custom metrics)  
- Collaboration Tools: Git & Github, Discord, Notion
 -->

| Category | Stacks |
| :--- | :--- |
| **Backend** | <img src="https://img.shields.io/badge/Java-17-007396?logo=java&logoColor=white"> <img src="https://img.shields.io/badge/SpringBoot-3.3.5-6DB33F?logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/Spring Data JPA-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Spring Batch-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Spring WebFlux-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Spring Actuator-6DB33F?logo=spring&logoColor=white"> <img src="https://img.shields.io/badge/Jsoup-FB8C00?logo=java&logoColor=white"> |
| **Database** | <img src="https://img.shields.io/badge/PostgreSQL-17.5-4169E1?logo=postgresql&logoColor=white"> <img src="https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb&logoColor=white"> <img src="https://img.shields.io/badge/Amazon RDS-527FFF?logo=amazonrds&logoColor=white"> |
| **Deployment & CI/CD** | <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/GitHub Actions-2088FF?logo=githubactions&logoColor=white"> <img src="https://img.shields.io/badge/Amazon EC2-FF9900?logo=amazonec2&logoColor=white"> <img src="https://img.shields.io/badge/Amazon ECS-FF9900?logo=amazon-ecs&logoColor=white"> <img src="https://img.shields.io/badge/Amazon ECR-FF9900?logo=amazon-ecr&logoColor=white"> |
| **Storage** | <img src="https://img.shields.io/badge/Amazon S3-569A31?logo=amazons3&logoColor=white"> |
| **Monitoring** | <img src="https://img.shields.io/badge/Micrometer-1081C2?logo=micrometer&logoColor=white"> |
| **Testing** | <img src="https://img.shields.io/badge/Mockito-8A2BE2?logo=mockito&logoColor=white"> |
| **Collaboration** | <img src="https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white"> <img src="https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white"> <img src="https://img.shields.io/badge/Discord-5865F2?logo=discord&logoColor=white"> <img src="https://img.shields.io/badge/Notion-000000?logo=notion&logoColor=white"> |
| **IDE** | <img src="https://img.shields.io/badge/IntelliJ IDEA-000000?logo=intellijidea&logoColor=white"> |

---  

## Project Execution Guide
### 1. Prerequisites
- Docker & Docker Compose
- PostgreSQL (v17.5)
- Java 17, Gradle
- Other: Internet connection (for external API usage)

### 2. Environment Variables
1. Create a `.env` file in the project root directory.
2. Refer to the following template to fill out the `.env` file:
