# National Election Results & Risk Intelligence Dashboard

An interactive Excel/VBA dashboard that combines real-time election results tracking with a predictive **Risk Score model** to flag high-risk polling zones — built as a simulated case study for an electoral commission (INEC-style) use case.

> **Disclaimer:** This project uses a synthetic/simulated dataset built for demonstration purposes. It is not affiliated with, endorsed by, or built using real data from the Independent National Electoral Commission (INEC) or any government body.

---

## 📌 Overview

Election oversight bodies typically rely on retrospective, after-the-fact reporting — by the time patterns of violence, voter suppression, or data anomalies are identified, the election has already happened. This project reframes that problem: it turns raw polling-unit-level data into a **forward-looking, prioritized risk view**, so stakeholders can allocate limited security and observer resources before voting day, not after.

The deliverable is a single, self-contained interactive Excel workbook — no external BI tool required — with a full navigable experience:

**Home Landing Page → VBA Loading Screen → Main Dashboard → Executive Overview → Insights → Database View**

---

## 🎯 The Problem

- No unified view existed for translating thousands of granular polling-unit returns into a prioritized, LGA-level risk picture.
- Security and observer deployment was effectively uniform across regions, rather than data-driven.
- Data anomalies (missing/inconsistent returns) were tracked separately from incident reports, hiding potential under-reporting or suppression patterns.

---

## 🛠️ Approach

### 1. Data Modeling
Aggregated raw polling unit data (votes cast, party vote splits, turnout %, registered voters) up to **Ward → LGA → State** level, with automated vote-share and turnout-rate calculations built directly into the dataset using Excel formulas.

### 2. Risk Score Engine
Designed a weighted composite Risk Score (0–100 scale) per LGA:

```
Risk Score = (ScaledAnomaly × 0.20 + ScaledIncidents × 0.35 + ScaledSeverity × 0.45) × 100
```

| Component            | Weight | Rationale                                                                 |
|-----------------------|--------|----------------------------------------------------------------------------|
| Average Severity      | 45%    | Prioritizes human cost — physical intimidation/violence is the most severe disruption to democratic integrity |
| Incident Frequency    | 35%    | Captures how widespread the disruption is across an LGA                   |
| Data Anomaly Rate     | 20%    | Captures hidden administrative vulnerabilities (paper-trail inconsistencies) |

### 3. UX & Navigation Design
Built a complete click-through information architecture with consistent INEC-style branding:

- **Home** — landing page with project framing and a "View Interactive Dashboard" entry point
- **Loading Screen** — custom animated transition scripted in VBA
- **Main Dashboard** — KPI cards (LGAs, States, Wards, Registered Voters, Votes Cast, Party Votes), State/LGA slicers, Top LGAs & Top Wards leaderboards
- **Executive Overview** — narrative "so-what" insights paired with each chart (geographic vote distribution, national party market share)
- **Insights** — written breakdown of key findings and policy recommendations
- **Database View** — full raw, filterable polling-unit-level dataset

### 4. VBA Automation
Used VBA to script the loading screen transition between the landing page and dashboard, giving the workbook a more product-like feel than a static spreadsheet, along with navigation buttons linking every page together.

### 5. Narrative Layer
Every chart is paired with a written interpretation rather than left to speak for itself — e.g., framing high-turnout states as "macro-battlegrounds," and flagging LGAs with high anomaly rates but zero incident reports as likely **under-reporting blind spots**.

---

## 📊 Key Findings

Analysis synthesized **2,000+ granular data points** across the 2019 and 2023 election cycles, spanning **4 states, 8 LGAs, and 802 wards**, covering **761.5K registered voters**.

**Top 3 highest-risk LGAs (immediate security priority):**

| Rank | LGA           | Risk Score | Primary Driver                                              |
|------|---------------|------------|---------------------------------------------------------------|
| 1    | Surulere      | 82.27%     | Extreme convergence of weapon-related incidents + peak severity |
| 2    | Nassarawa     | 75.97%     | Severe voter harassment + high turnout discrepancy vs. state average |
| 3    | Port Harcourt | 68.14%     | Persistent civil unrest + systemic data anomalies across both cycles |

**Other findings:**
- No measurable improvement in risk levels was observed between the 2019 and 2023 election cycles.
- A distinct class of LGAs showed **high data anomalies with zero recorded incidents** — flagged as potential under-reporting blind spots where suppression or communication blackouts may have masked real intimidation.

---

## 💡 Policy Recommendation

A **Data-Driven Tiered Security Deployment Strategy**:

- Dynamically allocate security personnel and independent international observers to LGAs scoring **≥70 (Risk Score "red zone")**, at least **72 hours before voting day** — instead of uniform distribution across states.
- Pre-deploy independent audit teams to identified under-reporting blind spots to provide uncompromised oversight of paper-to-digital data transmission.

---

## ⚠️ Limitations

The model relies heavily on historical field/observer reports. In regions with severe communication blackouts or structural voter suppression, incident tracking data is naturally truncated or absent — meaning risk scores for low-observer-presence areas may **underrepresent** true operational threats on the ground.

---

## 🧰 Tech Stack

| Tool               | Purpose                                              |
|---------------------|-------------------------------------------------------|
| Microsoft Excel     | Data modeling, dashboard visuals, KPI cards, slicers |
| Excel Formulas      | Vote-share %, turnout rate, weighted risk score calc |
| VBA                 | Custom loading screen, page navigation automation    |

---

## 📁 Repository Structure

```
├── README.md
├── screenshots/
│   ├── home-landing-page.png
│   ├── main-dashboard.png
│   ├── executive-overview.png
│   └── database-view.png
├── Election_Risk_Dashboard.xlsm
└── Executive_Summary.docx
```

---

## 🚀 How to Use

1. Download `Election_Risk_Dashboard.xlsm`.
2. Open in Excel and **enable macros** (required for the VBA-driven loading screen and navigation).
3. Start from the Home page and click **View Interactive Dashboard**.
4. Use the State/LGA slicers on the Main Dashboard to filter results.
5. Navigate to **Executive Overview** or **Insights** for the narrative analysis, or **Database View** for the raw polling-unit-level data.

---

## 📸 Screenshots

<img width="1677" height="857" alt="Screenshot 2026-06-12 205639" src="https://github.com/user-attachments/assets/580ae399-2eb4-4d85-a33d-6161c43b4bb1" />

---

## 👤 Author

**Peter Obikpe (Pheonix)**
Data Analyst | IT Instructor
[Portfolio](https://peter-portfolio11.vercel.app) · [LinkedIn](#) · [Email](#)
