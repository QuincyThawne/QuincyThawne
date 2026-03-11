Below is **CHAPTER 6 – SYSTEM DESIGN**, written in a **formal academic style**, structured exactly as requested, and fully aligned with the **AETHER** platform.
All diagrams are described **textually**, which is standard for reports when images are added later (you can easily convert these into UML diagrams using tools like Draw.io, StarUML, or Lucidchart).

---

# **CHAPTER 6**

## **SYSTEM DESIGN**

---

## **6.1 Introduction to System Design**

System design defines the structural blueprint of the AETHER platform, detailing how system components interact, how data flows across modules, and how functional and non-functional requirements are achieved. This chapter presents the Unified Modeling Language (UML) diagrams, database design, and technical requirements that collectively describe the internal working of the proposed system.

The design of AETHER follows a **modular, scalable, and secure architecture**, ensuring separation of concerns between orchestration, execution, visualization, and intelligence layers.

---

## **6.2 UML Diagrams**

UML diagrams are used to visually represent the functional behavior and structural relationships within the AETHER system.

---

### **6.2.1 Use Case Diagram**

**Actors:**

* User (Security Analyst / Researcher)
* System Administrator
* Worker Node (Execution Engine)

**Use Cases:**

* Register / Login
* Create Project
* Define Scope and Authorization
* Initiate Scan
* View Scan Results
* Visualize Attack Surface Graph
* Query Results using AI
* Manage Users (Admin)
* Monitor Worker Status

**Description:**
The user interacts with the system to create projects, initiate scans, and analyze results. The worker node executes reconnaissance tasks, while the administrator manages system configurations.

---

### **6.2.2 Class Diagram**

**Primary Classes:**

* User
* Project
* Scan
* Asset
* ToolResult
* GraphNode
* GraphEdge
* AIQuery
* Worker

**Key Relationships:**

* A User **creates** multiple Projects
* A Project **contains** multiple Scans
* A Scan **generates** multiple Assets
* Assets **form** GraphNodes and GraphEdges
* ToolResults **belong to** a Scan
* AIQueries **reference** stored scan data

This design ensures data encapsulation and logical separation.

---

### **6.2.3 Sequence Diagram**

**Sequence: Initiate and Execute Scan**

1. User submits scan request via Frontend
2. API validates authorization and scope
3. API creates scan job
4. Worker fetches job from queue
5. Worker executes crawler and tools
6. Results are parsed and stored
7. Graph is generated
8. User retrieves and views results

This sequence ensures asynchronous execution and responsiveness.

---

### **6.2.4 Activity Diagram**

**Activities:**

* Start
* User Login
* Project Selection
* Scan Configuration
* Authorization Validation
* Recon Execution
* Data Processing
* Visualization
* End

Decision nodes ensure scope validation and error handling during execution.

---

### **6.2.5 Component Diagram**

**Components:**

* Frontend (React UI)
* API Gateway
* Auth Service
* Job Queue
* Worker Engine
* Recon Tools
* Database
* Graph Engine
* AI Module

Each component communicates through defined interfaces, supporting loose coupling.

---

### **6.2.6 Deployment Diagram**

**Nodes:**

* Client Machine (Browser)
* Vercel Serverless Platform
* Supabase Cloud
* Worker VM / Container
* AI Service Provider

The frontend runs on the client, orchestration occurs in the serverless layer, and heavy tasks execute in isolated worker nodes.

---

## **6.3 Database Design**

The database design ensures efficient storage, retrieval, and correlation of reconnaissance data.

---

### **6.3.1 ER Diagram**

**Entities:**

* User
* Project
* Scan
* Asset
* ToolResult
* Graph
* AIQuery

**Relationships:**

* User → Project (1:N)
* Project → Scan (1:N)
* Scan → Asset (1:N)
* Scan → ToolResult (1:N)

---

### **6.3.2 Schema Diagram**

**Schema Overview:**

* users(user_id, email, role)
* projects(project_id, user_id, target)
* scans(scan_id, project_id, status)
* assets(asset_id, scan_id, type)
* tool_results(result_id, scan_id, tool_name)
* graph_nodes(node_id, asset_id)
* graph_edges(edge_id, source, target)
* ai_queries(query_id, scan_id)

---

### **6.3.3 Table Definitions**

**Users Table**

* user_id (PK)
* email
* password_hash
* role
* created_at

**Projects Table**

* project_id (PK)
* user_id (FK)
* target_domain
* created_at

**Scans Table**

* scan_id (PK)
* project_id (FK)
* status
* started_at
* completed_at

**Assets Table**

* asset_id (PK)
* scan_id (FK)
* asset_type
* asset_value

**Tool_Results Table**

* result_id (PK)
* scan_id (FK)
* tool_name
* output_json

---

## **6.4 Hardware Requirements**

* Processor: Intel i5 / Ryzen 5 or higher
* RAM: Minimum 8 GB (16 GB recommended)
* Storage: 50 GB free disk space
* Network: Stable internet connection
* Optional: Cloud VM for worker execution

---

## **6.5 Software Requirements**

* Operating System: Linux (Ubuntu/Kali), Windows for frontend
* Frontend: React.js, Tailwind CSS
* Backend: Node.js / Serverless Functions
* Database: PostgreSQL (Supabase)
* Containerization: Docker
* Recon Tools: Nmap, Nikto, WhatWeb
* AI: LLM with RAG integration
* Visualization: D3.js / Cytoscape.js

---

## **6.6 Chapter Summary**

This chapter presented the detailed system design of the AETHER platform, including UML diagrams, database architecture, and technical requirements. The design emphasizes modularity, scalability, and security, ensuring that AETHER can efficiently perform authorized reconnaissance while maintaining data integrity and user safety. The next chapter will discuss the implementation details and execution workflow of the system.

---

If you want next, I can generate:

* **CHAPTER 7: Implementation**
* **CHAPTER 8: Results and Performance Evaluation**
* **CHAPTER 9: Conclusion and Future Scope**
* **All UML diagrams as PPT-ready or image-ready descriptions**

Just tell me what you want next.
