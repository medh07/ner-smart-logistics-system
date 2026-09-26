🏔️ NER Smart Logistics & Nexus Command
AI-Powered Accessibility Intelligence & Predictive Disaster Logistics for North East India
🌐 Central Command Hub Repo • 📱 Driver & Field PWA Repo • 📄 Research & Problem Statement

[!IMPORTANT]
Project Scope: Designed specifically for high-stakes regional disaster response and supply chain resilience across the 8 North Eastern States of India (Assam, Meghalaya, Manipur, Mizoram, Tripura, Nagaland, Arunachal Pradesh, Sikkim).

📑 Table of Contents
✨ System Architecture & Ecosystem

🏛️ Ecosystem Repositories

💡 Core Features & Dual-Portal Capabilities

1. Mother Command Center Dashboard

2. Driver & Field Officer PWA

🧬 Technical Architecture & Flowcharts

📚 Research Foundation & Impact

🛡️ Real-World Challenges & Engineering Solutions

💻 Tech Stack Overview

⚡ Quick Start & Installation

👥 Team Data Drizzlers


✨ System Architecture & Ecosystem
In the North Eastern Region (NER) of India, severe monsoons, cloudbursts, and landslides regularly paralyze critical logistics highways (e.g., NH-37, NH-27), stranding medical supplies and agricultural produce.
NER Smart Logistics solves this through an API-First, Dual-Ecosystem Architecture that connects live ground-truth verification with high-level strategic disaster management:


┌─────────────────────────────────────────────────────────────┐
│          📱 FIELD OFFICERS & DRIVER PWA                    │
│     Offline-First • EXIF Geo-Tagged Uploads                │
└──────────────────────────────┬──────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│              ⚡ SUPABASE REALTIME BaaS LAYER               │
│  REST APIs • WebSockets • PostgreSQL/PostGIS • RLS         │
└──────────────────────────────┬──────────────────────────────┘
                               │
                    ┌──────────┴──────────┐
                    │                     │
                    ▼                     ▼
┌──────────────────────────────┐  ┌───────────────────────────┐
│ 🤖 AI RISK PREDICTION ENGINE │  │ 📍 OSRM DYNAMIC ROUTING   │
│                              │  │                           │
│ • 6-Hr Pre-Emptive Forecasts│  │ • Axle Weight Limits     │
│ • Multi-Factor Risk Scoring  │  │ • Vehicle Restrictions   │
└───────────────┬──────────────┘  └─────────────┬─────────────┘
                │                               │
                └───────────────┬───────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────┐
│       🏛️ CENTRAL COMMAND HUB — MOTHER DASHBOARD            │
│                                                            │
│        MDoNER • DDMA • Police • BRO Portal                 │
│                                                            │
│   Real-Time Monitoring • Risk Alerts • Route Intelligence  │
└─────────────────────────────────────────────────────────────┘



🧬 Technical Architecture & Flowcharts
Real-Time Ground-to-Command Data Pipeline : 
sequenceDiagram
    autonumber
    actor Field as 👮 Field Officer / Driver
    participant PWA as 📱 Field App (PWA)
    participant DB as ⚡ Supabase BaaS
    participant Engine as 🤖 AI & OSRM Engine
    participant Dash as 🏛️ Command Dashboard

    Field->>PWA: Captures Hazard Photo + Note
    PWA->>PWA: Extracts EXIF Metadata (GPS, Timestamp)
    alt Cellular Signal Available
        PWA->>DB: POST /incidents (HTTPS REST)
    else Network Dead Zone
        PWA->>PWA: Queue in Local IndexedDB
        PWA-->>DB: Auto-Sync on Signal Recovery
    end
    DB->>Engine: Trigger Risk Recalculation
    Engine->>DB: Update Route Risk Scores (0-100)
    DB-->>Dash: Push Alert via Realtime WebSockets
    DB-->>PWA: Broadcast Voice Detour Notification to Active Drivers


    📚 Research Foundation & Impact
Our platform design is validated against official geological, agricultural, and logistics research data:


| **Category**               | **Key Statistic / Impact**                                            | **Source / Reference**                      |
| -------------------------- | --------------------------------------------------------------------- | ------------------------------------------- |
| 📍 **GEOLOGICAL RISKS**    | **0.18 Million Sq. Km** of NE India lies in high-risk landslide zones | Geological Survey of India (GSI)            |
| 🚜 **ECONOMIC LOSSES**     | **₹1.53 Lakh Crore** lost annually in India due to transit delays     | NABCONS / ICAR National Study               |
| 🌾 **REGIONAL DISPARITY**  | **6.07% Paddy Loss** in Assam due to monsoon flood blockages          | NABCONS Report *(vs. 2.87% Flat State Avg)* |
| ⚡ **AI REROUTING BENEFIT** | **20%–35% Travel Time Saved** via dynamic real-time GIS rerouting     | IEEE / Transportation Research Studies      |




🛡️ Real-World Challenges & Engineering Solutions

| Challenge in NER Logistics              | Technical Limitation                                        | Our Integrated Solution                                                      |
| --------------------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Network Dead Zones**                  | Cellular dropouts in deep mountain valleys (NH-37).         | **Offline-First PWA** caching with background synchronization.               |
| **Heavy Freight Detour Bottlenecks**    | Secondary rural roads cannot support 10+ ton trucks.        | **Vehicle-Constrained OSRM Filtering** (axle weight & bridge caps).          |
| **Micro-Climate Landslide Variability** | Macro weather radar misses hyper-local slope collapse.      | **Dual-Verification Pipeline** fusing weather APIs + live EXIF photos.       |
| **Spam / Fake Incident Reports**        | Malicious or outdated image submissions.                    | **Automated EXIF Extraction** validating device GPS & live camera timestamp. |
| **High Proprietary Mapping Costs**      | Google Maps API charges scale prohibitively for public use. | **100% Open-Source Stack** (Leaflet, OSRM, OpenStreetMap, PostgreSQL).       |


💻 Tech Stack Overview
| **Layer**              | **Technologies & Tools Used**                                      |
| ---------------------- | ------------------------------------------------------------------ |
| **Frontend UI/UX**     | HTML5, CSS3, JavaScript, React.js, Tailwind CSS                    |
| **Mapping & GIS**      | Leaflet.js, OpenStreetMap, GIS Data, Satellite Data                |
| **Routing Engine**     | OSRM (Open Source Routing Machine), Vehicle-Constrained Routing    |
| **Backend & Database** | Node.js, Express.js, PostgreSQL, PostGIS                           |
| **Protocols & PWA**    | WebSockets, RESTful APIs, Service Workers, IndexedDB, EXIF Parsers |



🔌 API-First Architecture Justification
Our system is engineered as an API-First Infrastructure, offering critical architectural advantages:

1) Decoupled Micro-Frontends: The Command Dashboard and Driver PWA consume standardized, stateless Supabase REST and WebSocket APIs.

2) Modular GIS & AI Integration: Routing calculations are offloaded to the OSRM REST API, weather data is ingested via IMD/OpenWeather APIs, and maps are served via Tile APIs.

3) Sovereign Interoperability: External government portals (BRO, PWD, NHAI) can directly query or push corridor risk data via secure RESTful Webhooks without forcing staff to switch software.




