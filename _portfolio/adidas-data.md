---
title: "Adidas (Internship): Supply Chain Automation & Systems Architecture"
excerpt: "Architecting a real-time data pipeline for Adidas's global supply chain, transforming manual logistics into automated insights as a Logistics Automation Specialist."
collection: portfolio
order: 5
---

**Objective:** During my tenure as a **Logistics Automation Specialist (Intern)**, I designed and implemented a centralized data pipeline to automate the integration of global supplier manufacturing data, replacing manual Excel-based workflows with a real-time monitoring solution.

### The Problem: Manual Latency & Human Error
Prior to implementation, suppliers submitted data via weekly emails, requiring 30–60 minutes of manual cleaning per cycle. This fragmented process led to performance monitoring gaps and logistics delays.

### The "Linker" Achievement: System Design & Integration
Acted as the **"Master Brain"** by fetching and harmonizing data from disparate departments. This project served as a training ground for building complex systems from scratch, bridging the gap between factory-level operations and executive-level decision-making.

### Technical Implementation & Data Modeling
Built a robust data architecture using the Power Platform to ensure standardized, real-time visibility:

*   **Data Pipeline (Power Automate):** Engineered an automated trigger to capture emailed supplier files and push them directly to a structured cloud directory, enabling instant refreshes.
*   **Relational Data Modeling (Power BI):**
    *   **P.O Data Management:** Tracks daily production and order status updates.
    *   **P.O Rolling Table:** Master file containing all global order information.
    *   **PODD Stability Tracker:** A historical audit table that flags consistency issues if delivery dates change more than once.
    *   **Dimension Tables:** Created a centralized **Date Table** and **P.O Primary Key Table** to bridge daily order data with the master rolling file.

### Impact & Visualization
*   **Operational Efficiency:** Reduced manual processing time by 100% through automation.
*   **Risk Mitigation:** Developed a "Lateness Category" bar chart and "MDP/SDP" metrics (On-time Quantity vs. Total) to proactively identify delivery risks.
*   **Comprehensive Visibility:** Stacked column charts and area graphs providing a "Future vs. Completed" order overview for real-time health checks of the supply chain.

### Tech Stack
*   **Tools:** Power BI, Power Automate, Advanced Excel.
*   **Focus:** Data Modeling, ETL Automation, System Architecture, Risk Quantification.
