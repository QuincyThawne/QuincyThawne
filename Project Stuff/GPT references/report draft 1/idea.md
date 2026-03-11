
---

## 🔷 Project Name

**AETHER**

---

## 🧩 Primary Context

AETHER is being developed **for Smart India Hackathon (SIH) 2025**, aligned with a **national-scale public-interest problem** involving **edible oil consumption, quality monitoring, and digital awareness**, with strong emphasis on:

* **AI-driven decision making**
* **Cybersecurity & data integrity**
* **Public health & regulatory compliance**
* **Scalable digital platforms**

---

## 🧠 Problem Statement Alignment

**SIH 2025 – Problem Statement ID: 25269**
**Title:** National Campaign and Digital Platform for Reducing Edible Oil Consumption

### Key Issues Addressed:

* India’s per-capita edible oil consumption (~19.3 kg/year) exceeds ICMR recommendation (12 kg/year)
* Health risks due to **overuse and reuse of cooking oil**
* Economic burden via **high edible oil imports**
* Lack of **real-time oil quality awareness** for households, street vendors, and small food businesses

---

## 🏗️ Core Components of AETHER

### 1️⃣ Oil Quality Detection System (Tech Core)

* Initially included **IR sensor-based readings**
* Later refined to **remove IR-specific hardware dependency**
* Uses **configurable parameters** (via sliders / inputs) such as:

  * Oil physical & chemical properties
  * Noise-aware readings
* A **custom formula** (implemented by you) determines oil condition

#### Output Classification (via API):

* `"fresh-oil"`
* `"reusable"`
* `"unfit-for-consumption"`

Returned directly from:

```http
GET /reading
```

---

### 2️⃣ Backend Architecture

* **FastAPI-based backend**
* Single-file, runnable API
* JSON response includes:

  * Raw readings
  * Computed quality score
  * Human-readable oil status label
* Designed for:

  * Sensor simulation
  * Future real hardware integration
  * Dashboard & app consumption

---

### 3️⃣ AI & Data Layer

* **Synthetic dataset generation** for edible oils
* Parameters include:

  * Oleic acid %
  * Linoleic acid %
  * Density
  * Viscosity
  * Refractive index
* Dataset structured for:

  * Oil classification
  * ML model training
  * Predictive quality analysis

---

### 4️⃣ Digital Platform Vision

AETHER is positioned as a **national digital platform**, not just a sensor project.

Includes:

* Oil quality awareness
* Behavioral nudging to reduce oil consumption
* Educational content (children & general public)
* Economic insights:

  * Imports & exports
  * Farmer welfare
  * Domestic oilseed promotion

---

## 🔐 Cybersecurity & Legal-Tech Angle

(Important for evaluations & judging)

* Secure API design
* Integrity of sensor/data inputs
* AI ethics in health-impact decisions
* Compliance alignment with:

  * FSSAI guidelines
  * Public health advisories
* Tamper-resilient decision logic (important for enforcement use cases)

---

## 📊 SIH Evaluation & Presentation Context

You explicitly worked on:

* **Final evaluation strategy (3rd round)**
* PPT structure:

  * Slide limits
  * Content optimization
  * Checklist for judges
* Direct PPT generation for demo day
* Emphasis on:

  * Innovation
  * Practical deployability
  * National scalability
  * Ethical AI use

---

## 🏆 Related Achievements Context

While not strictly part of AETHER, relevant credibility:

* **Winner – Smart India Hackathon 2025 (1st Place)** 🏆
* Departments involved:

  * CSE (Cyber Security)
  * ECE
* Strong interdisciplinary approach (mirrored in AETHER)

---

## 🧪 Research & Policy References Used

* FSSAI **Edible Oil Survey Report (2022)**

  * Analysis of survey type
  * Oil categories studied
  * Purpose and policy implications
* Used to justify:

  * Problem relevance
  * Government alignment
  * Need for intervention

---

## 🧠 What AETHER Is (One-Line Summary)

> **AETHER is an AI-powered, secure digital ecosystem for monitoring edible oil quality and reducing oil overconsumption in India through real-time classification, public awareness, and policy-aligned insights.**

---

