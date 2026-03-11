Below is a **single consolidated Markdown document** that contains **all the Mermaid diagrams we created for the AETHER project**, cleaned up and **guaranteed to render without parse errors**.

You can paste this directly into:

* GitHub Markdown
* VS Code Markdown preview
* Mermaid Live Editor
* Any PPT tool that supports Mermaid → image export

---

# **AETHER – System Diagrams (Mermaid)**

---

## **1. System Architecture Diagram**

```mermaid
graph TD
    User[User Browser]
    FE[Frontend UI]
    API[API Layer]
    AUTH[Authentication Service]
    DB[(Database)]
    STORE[(Object Storage)]
    WORKER[Worker Engine]
    TOOLS[Kali Recon Tools]
    CRAWLER[Web Crawler]
    AI[RAG AI Engine]

    User --> FE
    FE --> API
    API --> AUTH
    API --> DB
    API --> WORKER
    WORKER --> TOOLS
    WORKER --> CRAWLER
    CRAWLER --> STORE
    TOOLS --> STORE
    STORE --> AI
    AI --> FE
```

---

## **2. System Flow Diagram**

```mermaid
flowchart TD
    A[User Login] --> B[Create Project]
    B --> C[Configure Scan Scope]
    C --> D[Submit Scan Request]
    D --> E[Job Created in Database]
    E --> F[Worker Fetches Job]
    F --> G[Run Recon Tools]
    G --> H[Run Web Crawler]
    H --> I[Store Results]
    I --> J[Generate Graph & Sitemap]
    J --> K[AI Analysis via RAG]
    K --> L[Display Results to User]
```

---

## **3. Modular Interaction Diagram**

```mermaid
graph LR
    UI[Frontend Module]
    AUTH[Auth Module]
    API[API Module]
    WORKER[Worker Module]
    CRAWLER[Crawler Module]
    GRAPH[Graph Engine]
    AI[AI Reasoning Module]
    DB[(Database)]

    UI --> AUTH
    UI --> API
    API --> DB
    API --> WORKER
    WORKER --> CRAWLER
    WORKER --> GRAPH
    GRAPH --> DB
    DB --> AI
    AI --> UI
```

---

## **4. RAG (Retrieval-Augmented Generation) Pipeline Diagram**

```mermaid
flowchart LR
    A[Crawled Web Pages]
    B[Scan Tool Outputs]
    C[Text Extraction]
    D[Chunking]
    E[Embedding Generation]
    F[Vector Database]
    G[User Query]
    H[Context Retrieval]
    I[LLM Response]

    A --> C
    B --> C
    C --> D
    D --> E
    E --> F
    G --> H
    F --> H
    H --> I
```

---

## **5. Entity Relationship (ER) Diagram**

```mermaid
erDiagram
    USER ||--o{ PROJECT : owns
    PROJECT ||--o{ SCAN : has
    SCAN ||--o{ ASSET : discovers
    SCAN ||--o{ TOOL_RESULT : generates
    PROJECT ||--o{ AI_QUERY : includes

    USER {
        uuid user_id
        string email
        string role
    }

    PROJECT {
        uuid project_id
        string target
        timestamp created_at
    }

    SCAN {
        uuid scan_id
        string status
        timestamp started_at
    }

    ASSET {
        uuid asset_id
        string asset_type
        string asset_value
    }

    TOOL_RESULT {
        uuid result_id
        string tool_name
        json output
    }

    AI_QUERY {
        uuid query_id
        string question
        timestamp asked_at
    }
```

---

## **6. Deployment Diagram**

```mermaid
graph TD
    Client[User Device]
    Vercel[Vercel Platform]
    Supabase[Supabase Cloud]
    WorkerVM[Worker VM / Container]
    AIService[LLM Service]

    Client --> Vercel
    Vercel --> Supabase
    Vercel --> WorkerVM
    WorkerVM --> Supabase
    Supabase --> AIService
    AIService --> Client
```

---

## **How to Use This**

* **For PPT**:
  Copy each diagram into Mermaid Live → export as PNG → insert into slides.
* **For Project Report**:
  Use screenshots of rendered diagrams under:

  * Chapter 5 (Architecture & Block Diagram)
  * Chapter 6 (System Design)
  * Chapter 8 (Implementation Flow)

If you want next:

* 🎞️ **Slide-wise diagram placement**
* 🧩 **Mermaid diagrams split per chapter**
* 🖼️ **Exact figure captions (IEEE style)**

Just tell me 👍
