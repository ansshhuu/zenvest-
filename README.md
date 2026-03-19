# 🛡️ Zenvest — AI-Powered Parametric Insurance for Gig Workers
 
> Instant, affordable, AI-driven income protection for India's 80M+ gig economy workers — delivered mobile-first with vernacular support.
 
---
 
## 📋 Table of Contents
 
1. [Project Overview](#project-overview)
2. [Persona-Based Scenarios & Workflow](#persona-based-scenarios--workflow)
3. [Weekly Premium Model](#weekly-premium-model)
4. [Parametric Triggers](#parametric-triggers)
5. [Platform Justification: Mobile-First](#platform-justification-mobile-first)
6. [AI/ML Integration](#aiml-integration)
7. [Tech Stack & Development Plan](#tech-stack--development-plan)
8. [Functional Requirements](#functional-requirements)
9. [System Architecture](#system-architecture)
 
---
 
## Project Overview
 
Zenvest is a parametric micro-insurance platform designed for India's gig workforce — delivery riders, auto-rickshaw drivers, platform workers — who lack access to traditional insurance. The platform provides:
 
- **Fixed weekly plans** (₹99 / ₹149 / ₹249/week) across three clearly defined tiers — Starter Shield, Smart Shield, Pro Shield
- **Zero-claim-filing** — payouts triggered automatically by verified parametric events (rain, AQI, curfew, platform downtime)
- **Instant UPI payouts** in under 30 seconds via Razorpay
- **Bilingual UI** (English + Hindi) with voice-assisted chatbot support
- **AI/ML at every layer** — from onboarding fraud detection to dynamic pricing and churn prevention
 
---
 
## Persona-Based Scenarios & Workflow
 
### Persona 1 — Ravi, Delivery Rider (Swiggy), Mumbai
 
**Situation:** Ravi earns ₹600/day but loses income every monsoon week. He has no savings buffer and no insurance.
 
**Journey:**
 
1. Opens Zenvest app → verified via Aadhaar OCR + liveness check (deepfake detection)
2. AI risk profiler scores him: Zone = High rainfall corridor, Tenure = 14 months → **Medium risk tier**
3. LLM plan explainer (Hindi) recommends the **Smart Shield** plan (₹149/week)
4. Ravi reviews coverage details and confirms selection
5. Ravi pays ₹149 via UPI. **Policy is active.**
6. Thursday: Heavy rain triggers AQI + rainfall parametric threshold
7. LSTM disruption model had predicted this 6 hours ahead → claim pre-authorized
8. Fraud detection checks GPS (Ravi was on-road), no anomaly found
9. **₹350 payout lands in Ravi's wallet in 28 seconds. Zero action needed from Ravi.**
10. Sunday night: Renewal nudge sent via push notification in Hindi
 
---
 
### Persona 2 — Sunita, Auto Driver, Delhi
 
**Situation:** Sunita works odd hours; the app must support low-digital-literacy users.
 
**Journey:**
 
1. Opens app → selects Hindi language on first screen
2. Voice-guided chatbot (LLM) walks her through onboarding in Hindi
3. Platform ID (Ola) + Aadhaar linked → identity verified
4. Risk profile: AQI zone risk (Delhi winters), High tier → AI recommends **Pro Shield** (₹249/week)
5. Selects plan; coverage breakdown shown clearly in Hindi
6. Pays ₹249 via UPI. **Policy active.**
7. AQI crosses 400 (parametric trigger) → auto claim approved
8. Payout sent; NLP feedback loop captures her voice rating → sentiment retrains model
9. Her **Worker Trust Score** improves after 6 clean weeks → AI recommends downgrade to Smart Shield (₹149/week)
 
---
 
### Persona 3 — Arjun, Platform Manager / Insurer (B2B Admin)
 
**Situation:** Arjun manages 12,000 gig workers and needs aggregate risk visibility.
 
**Journey:**
 
1. Admin dashboard shows: live loss ratio, zone heatmap, fraud log
2. Insurer analytics: predictive next-week claim volume forecast (Bayesian + LSTM)
3. Weekly model retrain ingests all claims → zone risk weights auto-adjusted
4. Flagged fraud cases (GPS spoofing, duplicate claims) routed to human-in-loop review
5. Arjun exports zone report → informs premium pool allocation
 
---
 
### Core Enrollment → Claim Workflow (All Personas)

 <img width="2816" height="1536" alt="Gemini_Generated_Image_u2lw15u2lw15u2lw" src="https://github.com/user-attachments/assets/5c8b8136-ba5e-4831-be26-b0196137c1bd" />

 
```
Parametric Event Occurs
       ↓
LSTM Predicts Disruption (6h ahead)
       ↓
Fraud Detection Engine (GPS, activity, duplicate check)
       ↓
   Fraud?  ──Yes──→  Flag for Review (Human-in-loop)
       │
      No
       ↓
Auto Claim Approved (Zero worker action)
       ↓
Instant Payout — UPI/Wallet (under 30s)
       ↓
Worker Feedback → NLP Sentiment Model → Retrains System
```
 
---
 
## Weekly Premium Model
 
### Fixed Plan Tiers
 
Zenvest offers three clearly defined weekly plans. Unlike dynamic pricing models, our fixed-tier approach ensures **transparency and trust** — workers always know what they're paying and what they get.
 
| Plan | Weekly Premium | Coverage Level | Best For |
|---|---|---|---|
| 🟢 **Starter Shield** | ₹99/week | Basic coverage for low-risk days | New workers, low-risk zones, fair weather seasons |
| 🔵 **Smart Shield** | ₹149/week | Balanced coverage at medium pricing | Urban riders, moderate-risk zones, mixed weather |
| 🟣 **Pro Shield** | ₹249/week | Highest coverage with best benefits | High-risk zones, monsoon season, full-time gig workers |
 
### How the AI Recommends a Plan
 
Although premiums are fixed, the AI risk profiler still runs at onboarding and weekly to **recommend the right plan tier** to the worker based on:
 
| Signal | Source | Role |
|---|---|---|
| Geographic zone risk | GPS + historical claim density | Plan tier recommendation |
| 7-day weather forecast | LSTM weather model | Risk alert + plan upgrade nudge |
| Worker's personal claim history | Internal DB | Trust score adjustment |
| Platform activity hours | Swiggy/Ola/Zomato APIs | Coverage adequacy assessment |
| AQI forecast | CPCB API | Trigger probability estimate |
| Worker Trust Score | Behavioral model | Loyalty reward signals |
 
Workers receive a **Sunday night recommendation** each week — they can accept the suggested plan or choose a different tier freely. The AI also flags when a worker may be under-insured for the coming week (e.g., high rain forecast but on Starter Shield).
 
### Weekly Renewal Loop
 
Every Sunday night, Zenvest:
 
1. Evaluates each worker's risk profile for the upcoming week
2. Pushes a personalized plan recommendation via push notification
3. Worker confirms or changes plan; UPI auto-debit processes if pre-authorized
4. Claims from the prior week feed back into the ML retrain pipeline
5. Zone risk weights and loss ratios updated for the new week
 
Workers with improving Trust Scores receive loyalty nudges to stay on their current plan or upgrade with confidence.
 
---
 
## Parametric Triggers
 
Parametric insurance pays automatically when a measurable external event crosses a predefined threshold — no claim filing, no paperwork.
 
### Defined Trigger Events
 
| Trigger Type | Parameter | Threshold | Payout |
|---|---|---|---|
| Rainfall | mm/hr (IMD API) | > 25mm in 3hr window | ₹250–500 |
| AQI | Air Quality Index (CPCB) | > 400 for 4+ hours | ₹250–350 |
| Curfew / Shutdown | Government API / news NLP | Verified order issued | ₹350–500 |
| Platform Downtime | Swiggy / Ola / Zomato API | > 2hr outage in worker's zone | ₹200–350 |
| Extreme Heat | IMD temperature index | > 45°C for 6hr | ₹200–300 |
 
### Why Parametric Over Traditional?
 
- **Zero friction** — workers don't file claims; events trigger automatically
- **Speed** — payouts under 30 seconds vs. 7–30 days for traditional claims
- **Trust** — transparent rules workers can understand
- **Loss ratio control** — measurable triggers = actuarially predictable
- **Scalability** — no adjuster workforce needed
 
### Predictive Trigger (LSTM Forecasting)
 
The LSTM model monitors weather and AQI APIs and **forecasts disruption 6 hours ahead**. This allows the system to:
- Pre-authorize claims before an event peaks
- Alert workers to stay safe
- Prepare payment processing in advance
 
---
 
## Platform Justification: Mobile-First
 
**We chose a Mobile-First Progressive Web App (PWA) with a React Native core, not a desktop web app.**
 
### Rationale
 
| Factor | Evidence |
|---|---|
| Target users are mobile-only | 94% of India's gig workers access internet solely via smartphone (IAMAI 2023) |
| UPI payments | UPI is natively mobile; no desktop equivalent for gig workers |
| Vernacular input | Voice notes, Hindi keyboard — better on mobile |
| Push notifications | Renewal nudges and payout alerts require native push (no desktop equivalent) |
| GPS data for fraud detection | Mobile GPS essential for Isolation Forest fraud model |
| Offline resilience | PWA service workers cache critical flows for low-connectivity zones |
 
### Platform Architecture
 
- **React Native** — cross-platform iOS + Android from single codebase
- **PWA fallback** — works on basic Android browsers for older devices
- **Low-bandwidth mode** — UI degrades gracefully on 2G/3G connections
- **Admin dashboard** — web-only (React.js) for insurer/manager persona
 
---
 
## AI/ML Integration
 
### 1. Identity Verification (Onboarding)
 
| Model | Task |
|---|---|
| OCR model (Tesseract + fine-tuned) | Extract Aadhaar details |
| Liveness detection CNN | Prevent photo spoofing |
| Deepfake classifier | Detect AI-generated face videos |
 
### 2. Risk Profiling (XGBoost Scorer)
 
Trained on historical gig worker claim data, platform earnings, and zone-level risk data. Outputs Low / Medium / High tier at onboarding and updates weekly via Bayesian inference as claim history accumulates.
 
**Features:** zone, average weekly hours, platform type, tenure, prior claims, city, season
 
### 3. Dynamic Pricing (Weekly Premium ML)
 
Ensemble model combining:
- XGBoost base risk score
- LSTM 7-day weather risk score
- Zone loss ratio from prior week
- Worker Trust Score modifier
 
Output: ₹ premium for the upcoming week.
 
### 4. Predictive Disruption (LSTM)
 
Sequence model trained on IMD rainfall, CPCB AQI, and historical platform downtime logs. Forecasts disruption probability at zone level for next 6 hours, enabling pre-authorization of likely claims.
 
### 5. Fraud Detection (Isolation Forest)
 
Unsupervised anomaly detection on:
- GPS coordinates at claim time vs. declared work zone
- Activity patterns (sudden inactivity before threshold breach)
- Duplicate identity signals across accounts
- Claim frequency vs. zone-level event data
 
Flagged claims route to human-in-loop review. Clean claims auto-approve.
 
### 6. Plan Explainer (LLM — Vernacular)
 
Fine-tuned LLM (IndicBERT base + GPT-4o API) provides:
- Plan recommendation in Hindi/English
- Q&A chatbot for onboarding doubts
- Voice note input → text → response
 
### 7. Churn Predictor
 
Gradient Boosted model trained on: last payment date, app opens, notification response rate, claim history. Outputs churn probability; if high, triggers a discount offer via push notification.
 
### 8. NLP Sentiment (Post-Payout Feedback)
 
Worker submits 1-tap rating + optional voice note post-payout. NLP model derives tone and trust score. Feeds back into worker's risk profile and overall model retraining pipeline.
 
### 9. Insurer Analytics (Predictive Volume Forecast)
 
Bayesian model predicts next week's claim volume by zone for insurer capacity planning. Updates each Monday post-retrain.
 
---
 
## Tech Stack & Development Plan
 
### Tech Stack
 
| Layer | Technology |
|---|---|
| **Mobile App** | React Native (iOS + Android) |
| **Admin Dashboard** | React.js + TailwindCSS |
| **Backend API** | FastAPI (Python) |
| **Database** | PostgreSQL (core) + Redis (session/cache) |
| **ML Pipeline** | Python — scikit-learn, XGBoost, TensorFlow/Keras (LSTM) |
| **LLM / NLP** | GPT-4o API + IndicBERT (vernacular) |
| **Payments** | Razorpay UPI API |
| **Weather / AQI** | IMD API + CPCB API + OpenWeatherMap |
| **Identity Verification** | Aadhaar eKYC API + custom liveness model |
| **Push Notifications** | Firebase Cloud Messaging (FCM) |
| **Infrastructure** | AWS (ECS + RDS + S3 + Lambda) |
| **CI/CD** | GitHub Actions + Docker |
| **Monitoring** | Datadog + Sentry |
 
### Development Plan
 
**Phase 0 — Foundation (Weeks 1–3)**
- Project scaffolding: React Native app + FastAPI backend
- Aadhaar eKYC integration + liveness model (MVP version)
- PostgreSQL schema: workers, policies, claims, zones
- Razorpay UPI sandbox integration
- Bilingual UI (English + Hindi string files)
 
**Phase 1 — Core Enrollment Flow (Weeks 4–6)**
- Steps 1–5 of enrollment workflow (Identity → Payment)
- XGBoost risk scorer trained on synthetic data
- Static premium tiers (pre-dynamic pricing)
- LLM chatbot (plan explainer, Hindi + English)
- Push notification setup via FCM
 
**Phase 2 — Parametric Engine (Weeks 7–9)**
- Weather and AQI API integrations
- Parametric trigger monitor with threshold logic
- LSTM disruption prediction model (initial version)
- Auto claim approval pipeline
- Razorpay instant payout flow (< 30s target)
 
**Phase 3 — AI/ML Hardening (Weeks 10–12)**
- Isolation Forest fraud detection + GPS validation
- Dynamic pricing ML (weekly premium recalculation)
- Churn predictor + nudge engine
- NLP post-payout sentiment model
- Bayesian risk profile update on weekly retrain
 
**Phase 4 — Admin & Analytics (Weeks 13–14)**
- Insurer admin dashboard (loss ratio, zone heatmap, fraud log)
- Predictive claim volume forecast for insurers
- Worker Trust Score system
- Human-in-loop fraud review interface
 
**Phase 5 — Hardening & Launch (Weeks 15–16)**
- Security audit + penetration testing
- Load testing (10,000 concurrent users)
- Regulatory compliance review (IRDAI sandbox)
- Beta with 500 gig workers in Mumbai + Delhi
- Production launch
 
---
 
## Functional Requirements
 
### Weather Prediction System
 
The platform integrates real-time and forecast weather data (IMD API + OpenWeatherMap) to:
- Display a 7-day weather forecast to the worker before they purchase the week's plan
- Feed zone + weather data into the LSTM disruption model
- Contribute to the dynamic weekly premium calculation
- Trigger parametric payouts when rainfall/AQI/heat thresholds are crossed
 
Workers see a simple "Risk Forecast" card on their home screen each Sunday night alongside their new weekly premium quote.
 
### Payment Plan Options
 
Zenvest offers three fixed weekly plans — no hidden fees, no dynamic price changes mid-week:
 
| Plan | Weekly Premium | Coverage Level | Description |
|---|---|---|---|
| 🟢 Starter Shield | ₹99/week | Basic | Basic coverage for low-risk days |
| 🔵 Smart Shield | ₹149/week | Balanced | Balanced coverage at medium pricing |
| 🟣 Pro Shield | ₹249/week | Premium | Highest coverage with best benefits |
 
The AI recommends the most appropriate plan based on the worker's risk profile, zone, and upcoming weather forecast. Workers can freely upgrade or downgrade at any Sunday renewal — there is no lock-in.
 
### Bilingual Language Support
 
- English and Hindi supported across all screens
- Language chosen at first launch; can be changed in settings at any time
- LLM chatbot responds in the selected language
- Voice note input (Hindi speech-to-text) supported for low-literacy users
- Push notifications delivered in the selected language
- All UI strings maintained in a centralized i18n JSON file (`en.json`, `hi.json`)
 
### Help Chatbot Support
 
An in-app LLM chatbot powered by GPT-4o (with IndicBERT fallback for offline/low-bandwidth):
- Answers plan-related questions ("What does my plan cover?")
- Guides users through onboarding steps
- Explains payout status ("Why haven't I received payment?")
- Accepts voice input in Hindi
- Escalates unresolved issues to human support via WhatsApp handoff
 
---
 
## Additional Considerations
 
### Regulatory Compliance
 
Zenvest will operate under the **IRDAI Sandbox Framework** for innovative insurance products. Key requirements:
- Partnering with a licensed insurer as underwriter (not self-insured)
- Parametric trigger definitions pre-approved by IRDAI
- Aadhaar eKYC compliant with UIDAI regulations
- UPI integration compliant with RBI guidelines
- Data localization: all personal data stored on Indian AWS region (ap-south-1)
 
### Privacy & Data Security
 
- Aadhaar data never stored raw — tokenized post-verification
- GPS data used only for fraud detection, not sold or shared
- Workers can request data deletion (DPDP Act 2023 compliant)
- All API communications over TLS 1.3
- ML model inputs anonymized before training
 
### Financial Model
 
- **Revenue:** 20–30% margin on premiums collected
- **Claims reserve:** 60–65% of premium pool held as claims reserve
- **Re-insurance:** Catastrophic risk (city-wide flood) reinsured via partner
- **Loss ratio target:** < 65% at steady state (typical parametric product benchmark)
 
### Why This Wins for Gig Workers
 
Traditional insurance fails gig workers because it requires: stable income proof, annual commitments, complex claim filing, and long payout waits. Zenvest removes every one of these barriers — fixed transparent weekly plans, zero-action payouts, instant UPI transfers, and a vernacular AI assistant that works even for first-time smartphone users.
 
---
 
*Built for Bharat's gig economy. Powered by AI. Settled in seconds.*
