# 🧠 Smart Resume Tracker

A full-stack, AI-powered job application tracker designed for job seekers to manage their career journey with structure and intelligence.

> Built using **Spring Boot**, **React**, **MySQL**, and integrated with **OpenAI (LLM)** for personalized resume, cover letter, and interview assistance.

---

## 📌 Problem Statement

Job seekers often struggle with tracking job applications, interviews, recruiter communications, and follow-ups. They also find it difficult to tailor resumes and cover letters for each job manually.

---

## 🚀 Solution Overview

This project provides:

- 📋 End-to-end tracking of job applications
- 🔔 Automated reminders for interviews/follow-ups
- 🧠 LLM-powered tools for:
  - Resume-job match scoring
  - Tailored cover letter generation
  - Interview prep and reflection
- 📂 Document management for resumes and notes

---

## 🏗️ System Design Overview

### 🏛️ **High-Level Architecture**

+-------------+ +----------------+ +------------+ +-------------+
| Frontend | <---> | Spring Boot API| <---> | MySQL | | OpenAI API |
| (React App) | | (RESTful) | | (DB Layer) | | (LLM) |
+-------------+ +----------------+ +------------+ +-------------+


- **Frontend**: React + Axios + TailwindCSS
- **Backend**: Spring Boot + Spring Security (JWT)
- **Database**: MySQL (Normalized schema)
- **AI Integration**: OpenAI GPT for text generation

---

### 🔍 Low-Level Component Design

| Layer         | Module                  | Responsibility                            |
|---------------|--------------------------|--------------------------------------------|
| Frontend      | React Components         | UI for jobs, reminders, AI tools           |
| API Layer     | `JobController`          | CRUD for job apps                          |
|               | `AIController`           | LLM-powered endpoints                      |
|               | `ReminderController`     | Create/view reminders                      |
| Service Layer | `JobService`, `AIService`| Business logic, prompt building            |
| Security      | `AuthController`         | JWT-based login/register                   |
| Scheduler     | `ReminderScheduler`      | Background job to send reminders           |
| Database      | Repositories             | DAO interfaces using Spring Data JPA       |

---

## 🧩 Tech Stack

| Layer           | Tech                         |
|-----------------|------------------------------|
| Frontend        | React, Axios, Tailwind       |
| Backend         | Spring Boot, Spring Security |
| Database        | MySQL                        |
| Authentication  | JWT Token (Stateless)        |
| AI Integration  | OpenAI GPT API               |
| Dev Tools       | Postman, Docker (Optional)   |
| Scheduler       | Spring `@Scheduled` Jobs     |

---

## 📊 Entity-Relationship Diagram (ERD)


# User (id, name, email, password, role)

# JobApplication (id, user_id, title, company, status, applied_date, interview_date, recruiter_email, notes)

# Reminder (id, job_id, type, scheduled_time, is_sent)

# Document (id, job_id, file_name, path, upload_time)

🌐 API Specification (Sample)

| Method | Endpoint              | Description                    |
| ------ | --------------------- | ------------------------------ |
| POST   | `/auth/login`         | JWT login                      |
| POST   | `/jobs`               | Add new job                    |
| GET    | `/jobs`               | Get all jobs for user          |
| POST   | `/ai/cover-letter`    | Generate tailored cover letter |
| POST   | `/ai/interview-notes` | Generate post-interview notes  |

🧠 AI-Integrated Features
| Feature                   | Input                    | Output                      |
| ------------------------- | ------------------------ | --------------------------- |
| Cover Letter Generator    | Resume + Job Description | Tailored cover letter       |
| Resume Match Scorer       | Resume + JD              | % Match Score + Suggestions |
| Interview Notes Generator | Freeform text / Context  | Structured reflection text  |
| Summary Customizer        | Resume + JD              | Optimized summary for role  |

🔐 Security
* JWT-based stateless authentication

* Role-based access control (USER, ADMIN)

* Protected endpoints using Spring Security


