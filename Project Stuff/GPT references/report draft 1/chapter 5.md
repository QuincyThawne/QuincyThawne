Below is **CHAPTER 5 – PROPOSED SYSTEM**, written in a **formal academic/project-report style**, fully consistent with **AETHER** and suitable for **UG/PG dissertations, SIH reports, and evaluations**.

---

# **CHAPTER 5**

## **PROPOSED SYSTEM**

---

## **5.1 Overview of the Proposed System**

The proposed system, **AETHER**, is a modular and legally compliant cybersecurity reconnaissance platform designed to identify, map, and analyze the external attack surface of web-based applications. The system integrates focused web crawling, controlled execution of security reconnaissance tools, graph-based visualization, and AI-assisted reasoning into a unified framework.

Unlike traditional standalone scanners, AETHER emphasizes **structural visibility**, **safe automation**, and **contextual intelligence**. The system separates orchestration from execution by utilizing a serverless API layer for coordination and a sandboxed worker environment for resource-intensive reconnaissance tasks. All collected data is securely stored and later analyzed using graph models and Retrieval-Augmented Generation (RAG) techniques.

---

## **5.2 Block Diagram**

The block diagram of the proposed system consists of the following major components:

1. **User Interface (Frontend)**
2. **API & Orchestration Layer**
3. **Authentication & Database Layer**
4. **Worker / Execution Engine**
5. **Crawler & Sitemap Generator**
6. **Graph Visualization Engine**
7. **AI-Assisted Analysis (RAG Layer)**

**Data Flow Description:**

User → Frontend → API Layer → Job Queue → Worker Engine →
Crawler / Recon Tools → Structured Data Storage →
Graph Visualization + AI Reasoning → User

This flow ensures that user interactions remain lightweight while heavy reconnaissance tasks are executed in isolated environments.

---

## **5.3 System Architecture**

The system architecture of AETHER follows a **distributed, service-oriented design**, consisting of the following layers:

### 1. Presentation Layer

* React-based frontend
* Provides project creation, scan initiation, result visualization, and chatbot interface

### 2. API & Orchestration Layer

* Serverless API (Vercel)
* Handles authentication, job creation, job status queries, and result retrieval
* Does not perform long-running reconnaissance tasks

### 3. Authentication & Storage Layer

* Supabase Authentication for secure user access
* PostgreSQL database for metadata
* Object storage for scan outputs and crawl artifacts

### 4. Worker / Execution Layer

* Self-hosted VM or containerized environment
* Executes Kali Linux reconnaissance tools
* Enforces timeouts, resource limits, and input sanitization

### 5. Intelligence Layer

* Graph engine for asset relationship modeling
* RAG-based AI layer for contextual querying and summarization

This layered architecture ensures scalability, safety, and maintainability.

---

## **5.4 Functional Description**

The functional operation of the proposed system is described below:

1. The user logs in and creates a project using the frontend interface.
2. The user submits a scan request with authorized target details.
3. The API layer validates the request and creates a scan job.
4. The worker engine retrieves the job and performs:

   * Focused crawling
   * Tool-based reconnaissance
5. Results are parsed and stored in structured formats.
6. A sitemap and graph representation are generated.
7. The user views interactive visualizations and queries the data using the AI interface.

Each function is executed within defined scope and safety constraints.

---

## **5.5 Modules / Components Overview**

### 1. User Interface Module

* Project dashboard
* Scan controls
* Graph and sitemap viewers
* Chatbot interface

### 2. Authentication Module

* User login and access control
* Project ownership enforcement

### 3. Crawler Module

* Discovers internal pages and endpoints
* Respects scope, depth, and authorization limits

### 4. Reconnaissance Module

* Executes tools such as Nmap, Nikto, and WhatWeb
* Collects service and configuration information

### 5. Data Normalization Module

* Converts raw outputs into structured JSON
* Ensures consistency across tools

### 6. Graph Engine Module

* Constructs node-edge models
* Supports interactive visualization

### 7. AI Reasoning Module

* Uses RAG to answer project-specific queries
* Grounds responses in stored reconnaissance data

---

## **5.6 Advantages of the Proposed System**

The proposed system offers several advantages over existing approaches:

* **Unified Platform:** Integrates crawling, scanning, visualization, and AI reasoning
* **Legal and Ethical Compliance:** Enforces authorization and scope control
* **Improved Visibility:** Graph-based visualization enhances understanding
* **Scalability:** Separation of orchestration and execution enables efficient scaling
* **Explainability:** AI responses are grounded in real data
* **Modularity:** Supports future extensions and additional tools

---

## **5.7 Chapter Summary**

This chapter presented the proposed system architecture and design of AETHER. It described the overall system flow, block diagram, architectural layers, functional operation, and core modules. The advantages of the proposed system highlight its effectiveness in providing a secure, scalable, and interpretable solution for authorized web reconnaissance. The next chapter will focus on the implementation details of the system.

---

If you want next, I can generate:

* **CHAPTER 6: Implementation**
* **CHAPTER 7: Results and Performance Analysis**
* **CHAPTER 8: Conclusion and Future Enhancements**
* **System architecture diagram (ASCII or PPT-ready)**
