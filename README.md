# AI-Talent-Intelligence-Pipeline

### Automated Resume Screening & Candidate Scoring System

---

## Summary

This project builds an **AI-powered Talent Intelligence Pipeline** that automatically ingests resumes, extracts structured candidate data, evaluates skills using deterministic scoring logic, and delivers ranked candidates directly into recruiter dashboards and Slack workflows.

The system reduces manual screening effort while improving consistency, speed, and hiring signal quality.

---
##  Overview

This system implements an **event-driven AI recruitment pipeline** using Make.com to automate end-to-end resume processing.

### Core Capabilities:

* Automated resume ingestion from Google Drive
* AI-powered structured data extraction
* Standardized candidate scoring system
* Duplicate detection via Airtable
* Centralized candidate database
* Recruiter-ready analytics dashboard (Google Sheets)
* Real-time Slack notifications for hiring teams

---

## 🏗 System Architecture

```
Google Drive (Resume Upload)
        ↓
File Type Router (PDF / DOCX)
        ↓
Text Extraction Layer
(PDF.co / AI Content Extractor)
        ↓
AI Evaluation Engine
(Structured Extraction + Scoring)
        ↓
Duplicate Detection Layer
(Airtable Search)
        ↓
Conditional Router
    ├── Duplicate → Stop
    └── New Candidate → Continue
        ↓
Candidate Database (Airtable)
        ↓
Analytics Pipeline (Google Sheets)
        ↓
Notification Engine (Slack)
        ├── General Candidate Alert
        └── High-Score Candidate Alert
```

---

## 🧰 Tech Stack

### 🔄 Automation Layer

* Make.com (Scenario Orchestration)

### 🤖 AI Layer

* Make AI Agent (Resume parsing & evaluation logic)

### 📄 Document Processing

* Google Drive (File ingestion)
* PDF.co (PDF extraction)
* Make AI Content Extractor (DOCX parsing)

### 🗄 Data Storage

* Airtable (Candidate database)

### 📊 Analytics

* Google Sheets (Recruiter dashboard)

### 🔔 Communication

* Slack (Real-time alerts)

---

## ⚙️ Workflow Breakdown

### 1. Resume Intake

* Watches Google Drive folder: `Candidate Resumes`
* Triggers on new file creation

---

### 2. File Type Routing

* PDF resumes → PDF.co extraction
* DOCX resumes → AI content extractor

---

### 3. AI Evaluation Engine

The AI agent performs:

* Structured candidate data extraction
* Skill scoring across:

  * SQL
  * Excel
  * BI Tools (Power BI / Tableau / Looker)
  * Analytics Projects

### Scoring Logic:

* Each category scored 0–2
* Total score = 0–8

### Classification:

* 7–8 → Excellent
* 5–6 → Good
* 3–4 → Review
* 0–2 → Reject

---

### 4. Duplicate Detection

* Searches Airtable by email
* Stops workflow if candidate exists

---

### 5. Candidate Storage

Stores structured profile:

* Personal details
* Skills
* Scores
* AI-generated summary
* Resume metadata

---

### 6. Analytics Dashboard

* Pushes candidate data to Google Sheets
* Enables recruiter filtering, sorting, and tracking

---

### 7. Notification System

Slack alerts:

* All candidates → evaluation summary
* Excellent candidates → priority alert

---

## ✨ Key Features

* AI-powered structured resume parsing
* Standardized skill scoring framework
* Multi-format document support (PDF/DOCX)
* Duplicate candidate prevention
* Real-time recruiter notifications
* Centralized hiring analytics dashboard
* Fully automated end-to-end pipeline

---
## 🧠 Edge Cases & Error Handling

* Missing resume fields handled via `null` assignment
* Invalid file types filtered via MIME routing
* Duplicate detection prevents redundant entries
* AI constrained to structured JSON output only
* Fail-safe routing stops incomplete evaluations

---

## 🛠 Setup Instructions

1. Create Google Drive folder: `Candidate Resumes`
2. Set up Make.com scenario with modules listed in architecture
3. Connect:

   * Google Drive
   * Airtable
   * Slack
   * Google Sheets
   * PDF.co
4. Configure AI Agent prompt for structured JSON output
5. Define Airtable schema matching candidate model
6. Enable scenario scheduling or instant triggers

---

## 🔗 Live Automation Workflow

👉 [View Automation Blueprint](https://eu2.make.com/public/shared-scenario/DDibFUaLzjK/resume-processing)



