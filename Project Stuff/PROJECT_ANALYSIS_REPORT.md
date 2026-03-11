# AETHER - AI-Enhanced Threat Enumeration and Reconnaissance Platform

## Complete Project Analysis Report

**Generated:** January 17, 2026  
**Project Name:** Aether Insights  
**Version:** 0.0.0  

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [Architecture Overview](#2-architecture-overview)
3. [Technology Stack](#3-technology-stack)
4. [Backend Services](#4-backend-services)
   - [Backend (Enumeration)](#41-backend-enumeration)
   - [Backend (Intelligence)](#42-backend-intelligence)
   - [Backend (Mobile)](#43-backend-mobile)
   - [Backend (Recon)](#44-backend-recon)
5. [Frontend Application](#5-frontend-application)
   - [Pages](#51-pages)
   - [Components](#52-components)
   - [Services](#53-services)
   - [State Management](#54-state-management)
6. [Database Schema](#6-database-schema)
7. [Novel Research Contributions](#7-novel-research-contributions)
8. [API Endpoints Reference](#8-api-endpoints-reference)
9. [Data Flow Architecture](#9-data-flow-architecture)
10. [Security Features](#10-security-features)

---

## 1. Executive Summary

AETHER (AI-Enhanced Threat Enumeration and Reconnaissance) is a **full-stack, research-grade security analysis platform** designed for comprehensive web and mobile application security testing. The platform combines multiple security domains into a unified interface:

- **Automated Reconnaissance** - Subdomain, DNS, port, and technology discovery
- **Vulnerability Enumeration** - Deep scanning based on OWASP Top 10 2021
- **Mobile Security Analysis** - APK/IPA static analysis via MobSF integration
- **AI-Powered Intelligence** - RAG-based chatbot for security insights
- **Dynamic Graph Sitemap** - Novel infrastructure visualization with security-aware algorithms

The platform is designed as a **research project** with novel contributions in security-aware graph algorithms for infrastructure visualization.

---

## 2. Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           FRONTEND (React + TypeScript)                      │
│                              Port: 8080 (Vite)                               │
├─────────────────────────────────────────────────────────────────────────────┤
│  Dashboard │ Recon │ Enumeration │ Mobile │ Chat │ Sitemap │ Settings       │
└─────────────────────────────────────────────────────────────────────────────┘
                    │           │            │           │
                    ▼           ▼            ▼           ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│   Recon     │ │ Enumeration │ │   Mobile    │ │Intelligence │
│   Backend   │ │   Backend   │ │   Backend   │ │   Backend   │
│  Port:8000  │ │  Port:8001  │ │  Port:3001  │ │  Port:8002  │
│   FastAPI   │ │   FastAPI   │ │   FastAPI   │ │   FastAPI   │
└─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
       │               │              │                │
       │               │              │                │
       ▼               ▼              ▼                ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                         SUPABASE (PostgreSQL)                                │
│   scans │ vulnerabilities │ recon_logs │ recon_findings │ mobile_scans      │
└─────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    EXTERNAL SERVICES & TOOLS                                 │
│     MobSF │ Nmap │ Nikto │ WhatWeb │ Subfinder │ Amass │ Groq LLM          │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Technology Stack

### Frontend

| Technology | Version | Purpose |
|------------|---------|---------|
| **React** | 18.3.1 | UI Framework |
| **TypeScript** | 5.8.3 | Type Safety |
| **Vite** | 5.4.19 | Build Tool & Dev Server |
| **TailwindCSS** | 3.4.17 | Utility-First CSS |
| **shadcn/ui** | Latest | Component Library (Radix-based) |
| **React Router DOM** | 6.30.1 | Client-side Routing |
| **TanStack Query** | 5.83.0 | Server State Management |
| **Framer Motion** | 12.23.26 | Animations |
| **Cytoscape.js** | 3.33.1 | Graph Visualization |
| **Recharts** | 2.15.4 | Dashboard Charts |
| **React Markdown** | 10.1.0 | Markdown Rendering |
| **Supabase JS** | 2.89.0 | Database Client |
| **Zod** | 3.25.76 | Schema Validation |

### Backend (Common)

| Technology | Version | Purpose |
|------------|---------|---------|
| **FastAPI** | 0.109+ | API Framework |
| **Uvicorn** | 0.27+ | ASGI Server |
| **Pydantic** | 2.5+ | Data Validation |
| **Python** | 3.10+ | Runtime |

### Backend (Enumeration) Specific

| Technology | Purpose |
|------------|---------|
| **httpx** | Async HTTP Client |
| **BeautifulSoup4** | HTML Parsing |
| **structlog** | Structured Logging |
| **Redis** | Caching/Queue |
| **SQLAlchemy** | ORM |
| **websockets** | Real-time Communication |

### Backend (Intelligence) Specific

| Technology | Purpose |
|------------|---------|
| **LangChain** | RAG Framework |
| **LangChain-Groq** | LLM Integration |
| **LangChain-HuggingFace** | Embeddings |
| **FAISS** | Vector Store |
| **Sentence-Transformers** | Embedding Models |
| **NetworkX** | Graph Algorithms |
| **Supabase Python** | Database Client |

### Backend (Mobile) Specific

| Technology | Purpose |
|------------|---------|
| **MobSF** | Mobile Security Framework |
| **Docker** | Container Runtime |
| **aiofiles** | Async File Operations |
| **python-magic** | File Type Detection |

### Backend (Recon) Specific

| Technology | Purpose |
|------------|---------|
| **Nmap** | Port Scanning |
| **WhatWeb** | Technology Detection |
| **Nikto** | Web Server Scanning |
| **Subfinder** | Subdomain Discovery |
| **Amass** | Network Mapping |
| **DNSenum** | DNS Enumeration |
| **TheHarvester** | OSINT Gathering |
| **GoBuster** | Directory Bruteforcing |
| **httpx** | HTTP Probing |

### Database

| Technology | Purpose |
|------------|---------|
| **Supabase** | PostgreSQL Backend-as-a-Service |
| **PostgreSQL** | Primary Database |

---

## 4. Backend Services

### 4.1 Backend (Enumeration)

**Location:** `backend(enumeration)/`  
**Port:** 8001  
**Purpose:** Deep vulnerability scanning engine based on OWASP Top 10 2021

#### Directory Structure

```
backend(enumeration)/
├── app/
│   ├── main.py              # FastAPI application entry point
│   ├── config.py            # Settings and environment config
│   ├── models/
│   │   └── scan.py          # Pydantic models for scans/vulnerabilities
│   ├── plugins/             # Vulnerability detection plugins
│   │   ├── base.py          # Abstract base detector class
│   │   ├── sqli.py          # SQL Injection detection
│   │   ├── xss.py           # Cross-Site Scripting detection
│   │   ├── ssrf.py          # Server-Side Request Forgery
│   │   ├── broken_access.py # Broken Access Control
│   │   ├── crypto_failures.py # Cryptographic Failures
│   │   ├── auth_failures.py # Authentication Failures
│   │   ├── security_misconfig.py # Security Misconfiguration
│   │   ├── data_integrity.py # Data Integrity Failures
│   │   ├── logging_failures.py # Logging/Monitoring Failures
│   │   ├── insecure_design.py # Insecure Design
│   │   ├── path_traversal.py # Path Traversal
│   │   ├── sensitive_data.py # Sensitive Data Exposure
│   │   └── vulnerable_components.py # Vulnerable Components
│   ├── routers/
│   │   ├── health.py        # Health check endpoints
│   │   ├── scans.py         # Scan CRUD endpoints
│   │   └── websocket.py     # Real-time WebSocket communication
│   └── services/
│       ├── crawler.py       # Web crawler for endpoint discovery
│       ├── scanner.py       # Scan orchestrator
│       └── http_client.py   # HTTP client with rate limiting
├── requirements.txt
├── Dockerfile
└── docker-compose.yml
```

#### Key Features

1. **Vulnerability Detection Plugins**
   - Modular plugin architecture with `BaseDetector` abstract class
   - Each plugin implements `detect()` method for specific vulnerability type
   - Full OWASP Top 10 2021 coverage:
     - A01: Broken Access Control (IDOR, privilege escalation)
     - A02: Cryptographic Failures (weak crypto, missing HTTPS)
     - A03: Injection (SQL Injection, XSS)
     - A04: Insecure Design (business logic flaws)
     - A05: Security Misconfiguration
     - A06: Vulnerable and Outdated Components
     - A07: Authentication Failures
     - A08: Data Integrity Failures
     - A09: Logging and Monitoring Failures
     - A10: Server-Side Request Forgery (SSRF)

2. **Web Crawler**
   - Async web crawler for endpoint discovery
   - Link extraction from HTML
   - Form extraction with input analysis
   - API endpoint discovery from JavaScript
   - Configurable crawl depth and rate limiting

3. **Scan Orchestrator**
   - Three-phase scanning pipeline:
     - Phase 1: Discovery/Crawling
     - Phase 2: Vulnerability Detection
     - Phase 3: Report Generation
   - WebSocket-based real-time progress streaming
   - Configurable scan options per OWASP category

4. **Detection Techniques (SQLi Example)**
   - Error-based detection with database-specific patterns
   - Time-based blind SQL injection
   - Boolean-based blind SQL injection
   - Union-based SQL injection
   - Supports MySQL, PostgreSQL, MSSQL, Oracle, SQLite

5. **Detection Techniques (XSS Example)**
   - Context-aware payloads (HTML, attribute, JavaScript, URL)
   - Encoding bypass payloads
   - Header analysis for XSS protection
   - Reflection detection with unique markers

#### Data Models

```python
class ScanConfig:
    deep_crawl: bool           # Enable deep crawling
    max_depth: int             # Maximum crawl depth (1-10)
    subdomain_enum: bool       # Enable subdomain enumeration
    api_discovery: bool        # Enable API endpoint discovery
    rate_limit_ms: int         # Delay between requests
    enable_sqli: bool          # SQL Injection detection
    enable_xss: bool           # XSS detection
    enable_ssrf: bool          # SSRF detection
    # ... other OWASP categories

class Vulnerability:
    id: str
    name: str
    severity: SeverityLevel    # critical|high|medium|low|info
    owasp_category: OWASPCategory
    cwe_id: Optional[str]
    endpoint: str
    method: str
    parameter: Optional[str]
    evidence: str
    description: str
    remediation: str
    confidence: float
```

---

### 4.2 Backend (Intelligence)

**Location:** `backend(intelligence)/`  
**Port:** 8002  
**Purpose:** RAG-powered AI security analysis assistant with novel graph algorithms

#### Directory Structure

```
backend(intelligence)/
├── app/
│   ├── main.py              # FastAPI application entry point
│   ├── models/
│   │   └── intelligence.py  # Chat/reference data models
│   ├── routers/
│   │   ├── chat.py          # Chat conversation endpoints
│   │   ├── graph.py         # Dynamic Graph Sitemap API
│   │   ├── ingest.py        # Document/scan ingestion
│   │   └── references.py    # Reference management
│   └── services/
│       ├── rag_service.py   # RAG implementation
│       ├── supabase_service.py # Database operations
│       └── graph/
│           ├── graph_service.py  # Graph management
│           └── algorithms.py     # Novel security algorithms
├── vector_store/
│   ├── index.faiss          # FAISS vector index
│   └── document_metadata.json # Document metadata
├── requirements.txt
└── run.py
```

#### Key Features

1. **RAG (Retrieval Augmented Generation) System**
   - **Embedding Model:** all-MiniLM-L6-v2 (HuggingFace)
   - **LLM:** Groq API with qwen/qwen3-32b model
   - **Vector Store:** FAISS for similarity search
   - **Text Splitting:** RecursiveCharacterTextSplitter (1000 chars, 200 overlap)
   - Automatically ingests scans from Supabase on startup
   - Context-aware responses referencing real scan data

2. **Dynamic Graph Sitemap (Novel Research Contribution)**

   The graph service manages a security infrastructure graph using NetworkX with custom algorithms:

   **a) Security-Aware PageRank (SA-PageRank)**
   ```
   SA-PR(v) = (1-d) + d * Σ(SA-PR(u) * W(u,v) * S(u))
   Where:
   - d = damping factor (0.85)
   - W(u,v) = edge weight based on relationship type
   - S(u) = security factor combining vulnerability scores
   ```
   
   - Node type importance weights (vulnerability = 1.0, authentication_point = 0.85, etc.)
   - Edge type criticality factors (has_vulnerability = 1.0, authenticates_via = 0.95)
   - Power iteration with security awareness

   **b) Vulnerability Propagation Model**
   - Computes risk spread across connected infrastructure
   - Factors: intrinsic risk, propagated risk, exposure factor, criticality factor
   - Models how vulnerabilities in one component affect connected systems

   **c) Functional Zone Clustering**
   - Groups related nodes by security function
   - Zone types: authentication, api, infrastructure, data, external
   - Identifies boundary nodes and internal connectivity

3. **Graph Node/Edge Types**
   
   **Node Types:**
   - `domain` - Primary domain
   - `subdomain` - Subdomains
   - `ip_address` - IP addresses
   - `port_service` - Open ports/services
   - `endpoint` - URL endpoints
   - `parameter` - Input parameters
   - `vulnerability` - Detected vulnerabilities
   - `technology` - Technologies used
   - `certificate` - SSL certificates
   - `api_endpoint` - API endpoints
   - `authentication_point` - Auth endpoints
   - `mobile_endpoint` - Mobile-specific endpoints

   **Edge Types:**
   - `resolves_to` - DNS resolution
   - `has_subdomain` - Domain relationship
   - `hosts_service` - Service hosting
   - `has_vulnerability` - Vulnerability association
   - `uses_technology` - Technology usage
   - `authenticates_via` - Authentication flow
   - `calls_api` - API calls
   - `exposes_data` - Data exposure
   - `inferred` - Inferred relationships

4. **Chat System**
   - Conversation history management
   - Suggested prompts based on available data
   - Source references with relevance scores
   - Context statistics for analysis
   - Manual scan refresh from Supabase

#### API Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/intelligence/chat` | POST | Send chat message |
| `/api/intelligence/suggested-prompts` | GET | Get suggested prompts |
| `/api/intelligence/context-stats` | GET | Get analysis context stats |
| `/api/intelligence/references` | GET | Get reference documents |
| `/api/intelligence/ingest` | POST | Ingest scan/document |
| `/api/intelligence/graph/session` | POST | Create graph session |
| `/api/intelligence/graph/nodes` | POST/GET | Node operations |
| `/api/intelligence/graph/edges` | POST/GET | Edge operations |
| `/api/intelligence/graph/layout` | POST | Compute layout |
| `/api/intelligence/graph/pagerank` | GET | Get PageRank scores |
| `/api/intelligence/graph/risk-scores` | GET | Get risk scores |
| `/api/intelligence/graph/attack-paths` | GET | Get attack paths |
| `/api/intelligence/graph/zones` | GET | Get functional zones |
| `/api/intelligence/graph/export` | GET | Export graph |

---

### 4.3 Backend (Mobile)

**Location:** `backend(mobile)/`  
**Port:** 3001  
**Purpose:** Mobile application security analysis via MobSF integration

#### Directory Structure

```
backend(mobile)/
├── app/
│   ├── main.py              # FastAPI application entry point
│   ├── config.py            # Settings configuration
│   ├── models.py            # Pydantic request/response models
│   ├── routes/
│   │   └── scan.py          # Scan operations endpoints
│   └── services/
│       ├── mobsf_service.py # MobSF API integration
│       └── scraper_service.py # HTML scraping for extra data
├── uploads/                  # Uploaded APK/IPA files
├── reports/                  # Generated reports
├── logs/                     # Application logs
├── requirements.txt
├── Dockerfile
└── docker-compose.yml
```

#### Key Features

1. **MobSF Integration**
   - Automatic API key management (scraped from web interface)
   - Key refresh on Docker container restart
   - Full static analysis pipeline

2. **Supported File Types**
   - Android APK
   - iOS IPA
   - Android App Bundle (AAB)
   - XAPK
   - ZIP archives

3. **Analysis Pipeline**
   ```
   Upload → Static Scan → JSON Report → Scorecard → PDF → Scrape Extra Data
   ```

4. **Analysis Data Retrieved**
   - **JSON Report:** Complete security analysis
   - **Scorecard:** Security grade (A-F), risk scores
   - **Scraped Data:**
     - Malware lookup results
     - APKiD analysis
     - Behavior analysis
     - Domain malware checks
     - Extracted URLs
     - Extracted emails

5. **Scan History**
   - Stores scan history in MobSF
   - View previous scans
   - Delete old scans

#### API Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/api/v1/scan/upload` | POST | Upload APK/IPA file |
| `/api/v1/scan/analyze/{hash}` | POST | Run static analysis |
| `/api/v1/scan/report/{hash}` | GET | Get JSON report |
| `/api/v1/scan/scorecard/{hash}` | GET | Get security scorecard |
| `/api/v1/scan/scraped/{hash}` | GET | Get scraped extra data |
| `/api/v1/scan/full/{hash}` | GET | Get complete analysis |
| `/api/v1/scan/history` | GET | Get scan history |
| `/api/v1/scan/{hash}` | DELETE | Delete scan |
| `/api/v1/refresh-key` | POST | Refresh MobSF API key |
| `/health` | GET | Health check |

---

### 4.4 Backend (Recon)

**Location:** `backend(recon)/`  
**Port:** 8000  
**Purpose:** Automated reconnaissance and security tool orchestration

#### Directory Structure

```
backend(recon)/
├── app/
│   ├── main.py              # FastAPI application entry point
│   ├── core/
│   │   ├── config.py        # Settings configuration
│   │   ├── executor.py      # Safe subprocess execution
│   │   ├── scan_manager.py  # Scan job management
│   │   ├── security.py      # Input validation/sanitization
│   │   └── python_tools.py  # Python-based tool fallbacks
│   ├── models/
│   │   └── responses.py     # Response models
│   ├── routers/
│   │   ├── nmap.py          # Nmap port scanning
│   │   ├── whatweb.py       # Technology detection
│   │   ├── nikto.py         # Web server scanning
│   │   ├── dirsearch.py     # Directory discovery
│   │   ├── gobuster.py      # Directory bruteforcing
│   │   ├── amass.py         # Network mapping
│   │   ├── theharvester.py  # OSINT gathering
│   │   ├── dnsenum.py       # DNS enumeration
│   │   ├── subfinder.py     # Subdomain discovery
│   │   ├── httpx.py         # HTTP probing
│   │   └── scan_control.py  # Scan management
│   └── utils/
│       └── parsers.py       # Tool output parsers
└── requirements.txt
```

#### Key Features

1. **Supported Reconnaissance Tools**

   | Tool | Purpose | Endpoint |
   |------|---------|----------|
   | **Nmap** | Port scanning & service detection | `/api/recon/nmap` |
   | **WhatWeb** | Web technology fingerprinting | `/api/recon/whatweb` |
   | **Nikto** | Web server vulnerability scanner | `/api/recon/nikto` |
   | **Dirsearch** | Web path discovery | `/api/recon/dirsearch` |
   | **GoBuster** | Directory/DNS bruteforcing | `/api/recon/gobuster` |
   | **Amass** | Attack surface mapping | `/api/recon/amass` |
   | **TheHarvester** | OSINT gathering | `/api/recon/theharvester` |
   | **DNSenum** | DNS enumeration | `/api/recon/dnsenum` |
   | **Subfinder** | Subdomain discovery | `/api/recon/subfinder` |
   | **httpx** | HTTP probing & analysis | `/api/recon/httpx` |

2. **Safe Command Execution**
   - No shell execution (`shell=False`)
   - Input sanitization and validation
   - Timeout enforcement (configurable, max enforced)
   - Python-based fallbacks when CLI tools unavailable

3. **Scan Manager**
   - Track running scans by ID
   - Cancel running scans
   - Clean up completed processes
   - Status tracking (pending, running, completed, cancelled, error)

4. **Output Parsers**
   - Nmap: Hosts, open ports, services
   - WhatWeb: Technologies, status codes, titles
   - Nikto: Findings, server info, vulnerability counts
   - DNS tools: Records, subdomains
   - Directory tools: Discovered paths, status codes

5. **Security Validator**
   - Target URL/domain sanitization
   - Port range validation
   - Prevention of command injection

#### Nmap Request Example

```python
class NmapRequest:
    target: str          # Target domain or URL
    scan_type: str       # service|ping|syn|full
    ports: str           # top-100|top-1000|1-65535|80,443
    timeout: int         # 30-300 seconds
```

---

## 5. Frontend Application

### 5.1 Pages

#### Dashboard (`/dashboard`)
**File:** `src/pages/Dashboard.tsx`

The central hub displaying real-time security posture:

- **KPI Cards:**
  - Total Scans (recon + enumeration + mobile)
  - Total Vulnerabilities
  - Critical/High Findings
  - Security Score (weighted calculation)

- **Charts:**
  - Scan trend over time (Area chart)
  - Severity distribution (Pie chart)
  - Scan type distribution

- **Lists:**
  - Recent Activity (last 8 activities)
  - Top Vulnerabilities (by severity)
  - Target Summaries
  - Mobile App Summaries

- **Actions:**
  - Quick navigation to scan pages
  - Refresh all data

#### Reconnaissance (`/recon`)
**File:** `src/pages/Recon.tsx`

Multi-tool reconnaissance dashboard:

- **Scan Presets:**
  - Quick Scan (httpx, whatweb, nmap)
  - Standard Scan (nmap, whatweb, nikto, subfinder, dnsenum)
  - Comprehensive Scan (all tools)
  - Vulnerability Focus (nmap, nikto, gobuster)
  - OSINT Focus (theharvester, dnsenum, subfinder, amass)

- **Tool Grid:**
  - Visual selection of individual tools
  - Tool-specific configuration panels

- **Real-time Features:**
  - Live console log output
  - Progress tracking per tool
  - API availability indicator

- **Results:**
  - Findings table with severity badges
  - Detailed results per tool
  - Export capabilities

- **State Persistence:**
  - Scan state persists across navigation
  - Automatic restoration of last scan

#### Enumeration (`/enumeration`)
**File:** `src/pages/Enumeration.tsx`

OWASP-based vulnerability scanner interface:

- **Configuration:**
  - Target URL input
  - Scan options (deep crawl, subdomain enum, API discovery)
  - Per-category vulnerability detection toggles

- **OWASP Categories Toggle:**
  - A01: Broken Access Control
  - A02: Cryptographic Failures
  - A03: Injection (SQLi, XSS)
  - A04: Insecure Design
  - A05: Security Misconfiguration
  - A06: Vulnerable Components
  - A07: Authentication Failures
  - A08: Data Integrity Failures
  - A09: Logging Failures
  - A10: SSRF
  - Additional: Path Traversal, Sensitive Data

- **Real-time Progress:**
  - WebSocket-based live updates
  - Phase indicators (Discovery, Detection, Report)
  - Progress bar with percentage

- **Results Display:**
  - Filterable vulnerability table
  - Search by name/endpoint
  - Filter by severity
  - Detailed vulnerability cards

- **Export Options:**
  - JSON export
  - CSV export
  - HTML report

- **Supabase Integration:**
  - Auto-save to database
  - Load previous scans

#### Mobile Security (`/mobile`)
**File:** `src/pages/Mobile.tsx`

Mobile application security analysis:

- **File Upload:**
  - Drag-and-drop support
  - Supported: APK, IPA, AAB, XAPK, ZIP

- **Analysis Pipeline:**
  - Progress indicator with steps
  - Visual feedback during analysis

- **Results Tabs:**
  - **Overview:** App info, security grade, risk scores
  - **Permissions:** Android/iOS permissions analysis
  - **Security Issues:** Vulnerabilities found
  - **Components:** Activities, services, receivers, providers
  - **Files:** File tree with sensitive file detection
  - **Trackers:** Detected tracking libraries
  - **Extras:** Malware lookups, APKiD, behavior analysis

- **Scan History:**
  - List of previous scans
  - View/delete old scans

- **MobSF Health:**
  - Connection status indicator
  - API key refresh capability

#### Intelligence Chat (`/chat`)
**File:** `src/pages/Chat.tsx`

RAG-powered security assistant:

- **Chat Interface:**
  - Message history with markdown rendering
  - Code syntax highlighting
  - Collapsible thinking process display

- **Context Awareness:**
  - Automatic scan data loading
  - Source references for answers
  - Relevance scoring

- **Features:**
  - Suggested prompts based on available data
  - File attachments (images, documents)
  - Full-screen mode
  - Copy message content
  - Chat persistence (localStorage)
  - Manual refresh of scan data

- **Context Panel:**
  - Context statistics (scans, documents, chunks)
  - Reference list with filtering
  - Quick access to source documents

#### Dynamic Graph Sitemap (`/sitemap`)
**File:** `src/pages/Sitemap.tsx`

Novel infrastructure visualization:

- **Session Management:**
  - Create new graph session for target
  - Import from existing scans

- **Data Ingestion:**
  - Import recon scans
  - Import enumeration scans
  - Import mobile scans

- **Layout Algorithms:**
  - Force-directed (default)
  - Hierarchical
  - Radial
  - Cluster-based
  - Timeline

- **Security Analysis:**
  - PageRank scores display
  - Risk score calculations
  - Attack path highlighting
  - Functional zone visualization

- **Graph Statistics:**
  - Node/edge counts
  - Type distributions
  - Connected components
  - High-risk node identification

- **Export Options:**
  - PNG image
  - JSON data
  - GEXF (for Gephi)

#### Settings (`/settings`)
**File:** `src/pages/Settings.tsx`

Application configuration interface.

### 5.2 Components

#### Graph Visualization
**File:** `src/components/SitemapGraph.tsx`

Cytoscape.js-based interactive graph:

- **Extensions:**
  - cose-bilkent layout algorithm
  - dagre hierarchical layout

- **Node Styling:**
  - Color by type and risk score
  - Size by importance (PageRank)
  - Shape by category (diamond for vulnerabilities, pentagon for auth)

- **Edge Styling:**
  - Width by weight
  - Color coding for vulnerability edges

- **Interactions:**
  - Pan and zoom
  - Node selection with details panel
  - Attack path highlighting
  - Zone visibility toggle

- **Node Details Panel:**
  - Type, label, risk score
  - Vulnerability count
  - PageRank value
  - Properties display

#### Recon Components
**Location:** `src/components/recon/`

- **ToolGrid** - Tool selection interface
- **ToolOptionsPanel** - Per-tool configuration
- **ScanProgress** - Progress visualization
- **ResultsTable** - Findings display
- **ResultsTabs** - Tab-organized results

#### UI Components
**Location:** `src/components/ui/`

shadcn/ui based component library including:
- Accordion, Alert, Avatar, Badge
- Button, Card, Checkbox
- Dialog, Dropdown, Input
- Progress, ScrollArea, Select
- Tabs, Toast, Tooltip
- And more...

#### Layout Components
**Location:** `src/components/layout/`

- **AppLayout** - Main application shell
- **Sidebar** - Navigation sidebar
- **Header** - Top navigation bar

### 5.3 Services

#### API Service (`src/services/api.ts`)
Base HTTP client configuration with configurable base URL.

#### Scan Service (`src/services/scanService.ts`)
Enumeration scan operations:
- `createScan()` - Create new vulnerability scan
- `getScan()` - Get scan status
- `getScanResults()` - Get completed results
- `cancelScan()` - Cancel running scan

#### Recon Service (`src/services/reconService.ts`)
Reconnaissance tool orchestration:
- Tool definitions with configurations
- Sequential tool execution
- Result aggregation

#### Mobile Service (`src/services/mobileService.ts`)
Mobile analysis operations:
- `uploadFile()` - Upload APK/IPA
- `runScan()` - Execute analysis
- `getReport()` - Fetch results
- `getScorecard()` - Get security grade
- MobSF health checks

#### Intelligence Service (`src/services/intelligenceService.ts`)
AI chatbot operations:
- `sendChatMessage()` - Send message to RAG
- `getSuggestedPrompts()` - Get prompt suggestions
- `getContextStats()` - Get context statistics
- `ingestScanResults()` - Ingest scan to vector store
- `refreshScansFromDatabase()` - Refresh scan data

#### Graph Service (`src/services/graphService.ts`)
Graph sitemap operations:
- Session management
- Node/edge CRUD
- Layout computation
- Security analysis endpoints
- Export functions

#### Supabase Service (`src/services/supabaseService.ts`)
Database operations:
- Scan CRUD operations
- Vulnerability storage
- Recon logs/findings/results
- Mobile scan storage

#### Dashboard Service (`src/services/dashboardService.ts`)
Dashboard data aggregation:
- Statistics calculation
- Trend data
- Distribution charts

#### WebSocket Service (`src/services/websocket.ts`)
Real-time communication for enumeration scans.

#### Export Service (`src/services/exportService.ts`)
Export functionality:
- JSON export
- CSV export
- HTML report generation

### 5.4 State Management

#### ScanContext (`src/contexts/ScanContext.tsx`)

Global state management using React Context + useReducer:

**Three Independent Scan States:**

1. **Recon Scan State:**
   - `scanId`, `status`, `target`
   - `logs`, `results`, `findings`
   - `progress`, `selectedTools`, `toolOptions`
   - `isApiAvailable`, `savedToSupabase`

2. **Enumeration Scan State:**
   - `scanId`, `status`, `target`
   - `logs`, `progress`, `phase`
   - `vulnerabilities`, `savedToSupabase`

3. **Mobile Scan State:**
   - `isAnalyzing`, `analysisProgress`
   - `report`, `scanHistory`
   - `selectedTab`, `error`, `filename`

**Features:**
- State persistence across navigation
- Action dispatch for state updates
- Automatic database sync
- Scan restoration from Supabase

---

## 6. Database Schema

### Tables

#### `scans`
```sql
CREATE TABLE scans (
    id UUID PRIMARY KEY,
    target_url TEXT NOT NULL,
    status scan_status,           -- pending|running|completed|failed|cancelled
    scan_type scan_type,          -- enumeration|recon
    started_at TIMESTAMPTZ,
    completed_at TIMESTAMPTZ,
    created_at TIMESTAMPTZ,
    updated_at TIMESTAMPTZ,
    config JSONB,                  -- Scan configuration
    stats JSONB,                   -- Scan statistics
    parameters JSONB,              -- Additional parameters
    user_id UUID                   -- Optional user association
);
```

#### `vulnerabilities`
```sql
CREATE TABLE vulnerabilities (
    id UUID PRIMARY KEY,
    scan_id UUID REFERENCES scans(id) ON DELETE CASCADE,
    name TEXT NOT NULL,
    severity severity_level,       -- critical|high|medium|low|info
    confidence DECIMAL(3,2),
    owasp_category TEXT NOT NULL,
    cwe_id TEXT,
    endpoint TEXT NOT NULL,
    method TEXT DEFAULT 'GET',
    parameter TEXT,
    evidence TEXT,
    description TEXT NOT NULL,
    remediation TEXT NOT NULL,
    request_sample TEXT,
    response_sample TEXT,
    created_at TIMESTAMPTZ
);
```

#### `recon_logs`
```sql
CREATE TABLE recon_logs (
    id UUID PRIMARY KEY,
    scan_id UUID REFERENCES scans(id) ON DELETE CASCADE,
    log_type recon_log_type,       -- info|success|warning|error
    tool_name TEXT,
    message TEXT NOT NULL,
    created_at TIMESTAMPTZ
);
```

#### `recon_findings`
```sql
CREATE TABLE recon_findings (
    id UUID PRIMARY KEY,
    scan_id UUID REFERENCES scans(id) ON DELETE CASCADE,
    finding_type TEXT NOT NULL,
    tool_name TEXT NOT NULL,
    value TEXT NOT NULL,
    severity TEXT DEFAULT 'info',
    status finding_status,
    details JSONB,
    created_at TIMESTAMPTZ
);
```

#### `recon_results`
```sql
CREATE TABLE recon_results (
    id UUID PRIMARY KEY,
    scan_id UUID REFERENCES scans(id) ON DELETE CASCADE,
    tool TEXT NOT NULL,
    raw_output TEXT,
    parsed_results JSONB,
    execution_time DECIMAL(10,3),
    error TEXT,
    created_at TIMESTAMPTZ
);
```

#### `mobile_scans`
```sql
CREATE TABLE mobile_scans (
    id UUID PRIMARY KEY,
    file_hash TEXT UNIQUE NOT NULL,
    filename TEXT NOT NULL,
    app_name TEXT,
    package_name TEXT,
    version TEXT,
    platform TEXT,                 -- android|ios
    security_score INTEGER,
    grade TEXT,
    json_report JSONB,
    scorecard JSONB,
    scraped_data JSONB,
    created_at TIMESTAMPTZ,
    updated_at TIMESTAMPTZ
);
```

#### `graph_sessions`
```sql
CREATE TABLE graph_sessions (
    id UUID PRIMARY KEY,
    target_domain TEXT NOT NULL,
    created_at TIMESTAMPTZ,
    updated_at TIMESTAMPTZ,
    graph_data JSONB,
    stats JSONB,
    user_id UUID
);
```

### Row Level Security

All tables have RLS enabled with policies allowing:
- Users can view/insert/update/delete their own records
- Anonymous access allowed for records with `user_id IS NULL`

---

## 7. Novel Research Contributions

### Dynamic Graph Sitemap

The Dynamic Graph Sitemap represents the primary novel contribution of this research project. It provides:

#### 1. Security-Aware PageRank (SA-PageRank)

A modification of the standard PageRank algorithm that incorporates security factors:

**Node Type Weights:**
| Node Type | Weight | Rationale |
|-----------|--------|-----------|
| Vulnerability | 1.0 | Direct security concern |
| Authentication Point | 0.85 | Critical security boundary |
| Domain | 0.9 | Root of trust |
| IP Address | 0.8 | Infrastructure exposure |
| Port/Service | 0.75 | Attack surface |
| API Endpoint | 0.7 | Data access point |
| Endpoint | 0.6 | General web surface |
| Technology | 0.4 | Contextual information |

**Edge Type Weights:**
| Edge Type | Weight | Rationale |
|-----------|--------|-----------|
| has_vulnerability | 1.0 | Direct risk association |
| authenticates_via | 0.95 | Authentication flow |
| exposes_data | 0.9 | Data exposure risk |
| hosts_service | 0.9 | Service hosting risk |
| leads_to | 0.85 | Navigation/flow risk |
| resolves_to | 0.8 | DNS relationship |
| calls_api | 0.75 | API interaction |

#### 2. Vulnerability Propagation Model

Computes how risk spreads through connected infrastructure:

**Risk Score Components:**
- **Intrinsic Risk:** Direct vulnerabilities on the node
- **Propagated Risk:** Risk inherited from connected vulnerable nodes
- **Exposure Factor:** Connectivity/centrality of the node
- **Criticality Factor:** Business/security importance

**Formula:**
```
TotalRisk = IntrinsicRisk + α*PropagatedRisk + β*ExposureFactor + γ*CriticalityFactor
```

#### 3. Functional Zone Clustering

Automatically groups nodes into security-relevant zones:

**Zone Types:**
- `authentication` - Login, OAuth, session management
- `api` - REST/GraphQL endpoints
- `infrastructure` - Domains, IPs, ports
- `data` - Databases, storage
- `external` - Third-party services

**Zone Properties:**
- Aggregate risk score
- Boundary nodes (zone edges)
- Internal connectivity metric

#### 4. Attack Path Analysis

Identifies and visualizes potential attack paths:

**Path Properties:**
- Entry point (external-facing node)
- Target (sensitive asset)
- Exploitability score
- Impact score
- CVSS chain (cumulative risk)

---

## 8. API Endpoints Reference

### Enumeration Backend (Port 8001)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API info |
| GET | `/health` | Health check |
| POST | `/api/scans` | Create new scan |
| GET | `/api/scans/{id}` | Get scan status |
| GET | `/api/scans/{id}/results` | Get scan results |
| DELETE | `/api/scans/{id}` | Cancel scan |
| WS | `/ws/scan/{id}` | Real-time updates |

### Intelligence Backend (Port 8002)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API info |
| GET | `/api/intelligence/health` | Health check |
| POST | `/api/intelligence/chat` | Send chat message |
| GET | `/api/intelligence/suggested-prompts` | Get prompts |
| GET | `/api/intelligence/context-stats` | Get stats |
| GET | `/api/intelligence/references` | Get references |
| POST | `/api/intelligence/ingest` | Ingest document |
| POST | `/api/intelligence/graph/session` | Create session |
| GET/POST | `/api/intelligence/graph/nodes` | Node operations |
| GET/POST | `/api/intelligence/graph/edges` | Edge operations |
| POST | `/api/intelligence/graph/layout` | Compute layout |
| POST | `/api/intelligence/graph/ingest` | Ingest scan |
| GET | `/api/intelligence/graph/export/cytoscape` | Export Cytoscape |
| GET | `/api/intelligence/graph/export/json` | Export JSON |
| GET | `/api/intelligence/graph/export/gexf` | Export GEXF |
| GET | `/api/intelligence/graph/pagerank` | Get PageRank |
| GET | `/api/intelligence/graph/risk-scores` | Get risk scores |
| GET | `/api/intelligence/graph/attack-paths` | Get attack paths |
| GET | `/api/intelligence/graph/zones` | Get zones |

### Mobile Backend (Port 3001)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | API info |
| GET | `/health` | Health check |
| POST | `/api/v1/scan/upload` | Upload file |
| POST | `/api/v1/scan/analyze/{hash}` | Run analysis |
| GET | `/api/v1/scan/report/{hash}` | Get JSON report |
| GET | `/api/v1/scan/scorecard/{hash}` | Get scorecard |
| GET | `/api/v1/scan/scraped/{hash}` | Get scraped data |
| GET | `/api/v1/scan/full/{hash}` | Full analysis |
| GET | `/api/v1/scan/history` | Scan history |
| DELETE | `/api/v1/scan/{hash}` | Delete scan |
| POST | `/api/v1/refresh-key` | Refresh MobSF key |

### Recon Backend (Port 8000)

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Health check |
| GET | `/api/tools` | List tools |
| POST | `/api/recon/nmap` | Nmap scan |
| POST | `/api/recon/whatweb` | WhatWeb scan |
| POST | `/api/recon/nikto` | Nikto scan |
| POST | `/api/recon/dirsearch` | Dirsearch scan |
| POST | `/api/recon/gobuster` | Gobuster scan |
| POST | `/api/recon/amass` | Amass scan |
| POST | `/api/recon/theharvester` | TheHarvester scan |
| POST | `/api/recon/dnsenum` | DNSenum scan |
| POST | `/api/recon/subfinder` | Subfinder scan |
| POST | `/api/recon/httpx` | httpx scan |
| GET | `/api/recon/scan/{id}/status` | Scan status |
| POST | `/api/recon/scan/{id}/cancel` | Cancel scan |

---

## 9. Data Flow Architecture

### Enumeration Scan Flow

```
User Input (Target URL)
       │
       ▼
┌─────────────────┐
│  React Frontend │ ──WebSocket──┐
└─────────────────┘              │
       │                         │
       │ POST /api/scans         │ Real-time updates
       ▼                         │
┌─────────────────┐              │
│  Enumeration    │◄─────────────┘
│  Backend        │
└─────────────────┘
       │
       │ 1. Crawling
       │ 2. Plugin Detection
       │ 3. Report Generation
       ▼
┌─────────────────┐
│   Supabase      │
│  (PostgreSQL)   │
└─────────────────┘
       │
       ▼
┌─────────────────┐
│  Intelligence   │
│  Backend (RAG)  │
└─────────────────┘
```

### Recon Scan Flow

```
User Input (Target + Tools)
       │
       ▼
┌─────────────────┐
│  React Frontend │
└─────────────────┘
       │
       │ Sequential tool calls
       ▼
┌─────────────────┐
│  Recon Backend  │
└─────────────────┘
       │
       │ Execute CLI tools / Python fallbacks
       ▼
┌─────────────────┐
│  External Tools │
│  (Nmap, etc.)   │
└─────────────────┘
       │
       │ Parse output
       ▼
┌─────────────────┐
│   Supabase      │
└─────────────────┘
       │
       ▼
┌─────────────────┐
│  Intelligence   │
│  Backend (Graph)│
└─────────────────┘
```

### Graph Sitemap Data Flow

```
Scan Data (Recon/Enum/Mobile)
       │
       ▼
┌─────────────────┐
│  Supabase       │
│  (Stored Scans) │
└─────────────────┘
       │
       │ Load & Transform
       ▼
┌─────────────────┐
│  Intelligence   │
│  Backend        │
│  ┌───────────┐  │
│  │ NetworkX  │  │
│  │   Graph   │  │
│  └───────────┘  │
│        │        │
│        ▼        │
│  ┌───────────┐  │
│  │Algorithms │  │
│  │ PageRank  │  │
│  │ Risk Prop │  │
│  │ Zones     │  │
│  └───────────┘  │
└─────────────────┘
       │
       │ Cytoscape format
       ▼
┌─────────────────┐
│  React Frontend │
│  ┌───────────┐  │
│  │Cytoscape.js│ │
│  │   Graph    │ │
│  └───────────┘  │
└─────────────────┘
```

---

## 10. Security Features

### Input Validation

1. **Frontend:**
   - Zod schema validation
   - URL format validation
   - File type restrictions

2. **Backend:**
   - Pydantic model validation
   - Target sanitization (no command injection)
   - Port range validation

### Command Execution Safety

```python
# Always use shell=False
process = subprocess.Popen(
    command,
    stdout=subprocess.PIPE,
    stderr=subprocess.PIPE,
    shell=False,  # NEVER shell=True
    text=True
)
```

### Database Security

1. **Row Level Security (RLS):**
   - Users can only access their own scans
   - Anonymous access controlled

2. **Prepared Statements:**
   - Supabase client uses parameterized queries

### API Security

1. **CORS Configuration:**
   - Configurable allowed origins
   - Credentials handling

2. **Rate Limiting:**
   - Configurable request delays
   - Max timeout enforcement

### Sensitive Data Handling

1. **API Keys:**
   - Environment variables
   - Not logged or exposed
   - MobSF key auto-refresh

2. **Scan Data:**
   - User-isolated storage
   - Optional anonymization

---

## Appendix: Getting Started

### Prerequisites

- Node.js 18+
- Python 3.10+
- Docker (for MobSF)
- Supabase account
- Groq API key

### Installation

```bash
# Clone repository
git clone <repository-url>
cd AETHER

# Install frontend dependencies
npm install

# Install backend dependencies
cd backend(enumeration) && pip install -r requirements.txt
cd ../backend(intelligence) && pip install -r requirements.txt
cd ../backend(mobile) && pip install -r requirements.txt
cd ../backend(recon) && pip install -r requirements.txt
```

### Running the Application

```bash
# Terminal 1: Frontend
npm run dev

# Terminal 2: Enumeration Backend
cd backend(enumeration)
python -m uvicorn app.main:app --reload --port 8001

# Terminal 3: Intelligence Backend
cd backend(intelligence)
python -m uvicorn app.main:app --reload --port 8002

# Terminal 4: Mobile Backend
cd backend(mobile)
python -m uvicorn app.main:app --reload --port 3001

# Terminal 5: Recon Backend
cd backend(recon)
python -m uvicorn app.main:app --reload --port 8000

# Terminal 6: MobSF (Docker)
docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf
```

### Environment Variables

Create `.env` files in each backend:

**backend(intelligence)/.env:**
```
GROQ_API_KEY=your_groq_api_key
EMBED_MODEL=all-MiniLM-L6-v2
LLM_MODEL=qwen/qwen3-32b
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key
```

**backend(mobile)/.env:**
```
MOBSF_URL=http://localhost:8000
MOBSF_USERNAME=mobsf
MOBSF_PASSWORD=mobsf
```

---

*This document was auto-generated by analyzing the AETHER project codebase.*
