# 🏥 Zulekha Hospital RCM — Automated Pre-Claim Scrubbing & Validation Dispatcher (UiPath)

![UiPath](https://img.shields.io/badge/UiPath_Studio-2026.0-FA4616?style=for-the-badge&logo=uipath&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Windows_VB.NET-0078D6?style=for-the-badge&logo=dotnet&logoColor=white)
![Domain](https://img.shields.io/badge/Healthcare_RCM-DHA_eClaimLink_%7C_Riayati-1F4E78?style=for-the-badge)
![Status](https://img.shields.io/badge/Execution_Time-00%3A00%3A01-2E8B57?style=for-the-badge)

## 📌 Project Overview
Developed as an intern sub-module supporting **Zulekha Hospital's** *"Automated Comprehensive and Integrated RCM Solution Using RPA"* initiative, **`Zulekha_RCM_PreClaimScrubber_Dispatcher`** automates front-end Revenue Cycle Management (RCM) pre-claim validation.

In UAE hospital billing operations, outpatient insurance claims submitted to **DHA eClaimLink** and **Riayati** are frequently rejected due to front-desk or coding data entry omissions. This bot ingests daily Hospital Information System (HIS) outpatient Excel dumps, enforces payer-specific validation rules in memory, and segregates clean claims from defective claims in **00:00:01** prior to XML batch generation.

---

## 🎯 Business Problem & RCM Impact
* **Manual Bottleneck:** Billing teams manually audit hundreds of daily outpatient rows for Emirates ID formatting, primary ICD-10 diagnosis codes, and TPA prior authorization numbers.
* **Denial Prevention:** Prevents first-pass claim denials across major UAE Third-Party Administrators (TPAs) and insurers including **Daman, Nextcare, Neuron, Sukoon, and NAS**.
* **Unattended Speed:** Uses background `UiPath.Excel.Activities` Workbook operations (zero Excel desktop UI overhead) to scrub and split patient batches in **1 second (`00:00:01`)**.

---

## 🏗️ Repository & Workflow Architecture

```text
Zulekha-RCM-PreClaim-Scrubber-UiPath/
├── Data/
│   ├── Input/
│   │   └── HIS_Daily_Outpatient_Claims.xlsx        # Daily outpatient dump from HIS (Auto-seeded if missing)
│   └── Output/
│       └── RCM_Scrubbed_Report_DDMMYYYY.xlsx       # Segregated 2-tab output workbook
├── Screenshots/
│   ├── workflow_canvas.png                         # UiPath Studio Main.xaml workflow view
│   └── execution_output.png                        # UiPath Output panel execution log
├── Main.xaml                                       # Primary Dispatcher & Pre-Claim Validation Engine
├── TPA_Approval_TierCheck.xaml                     # Modular Sub-Workflow for AED threshold routing
├── project.json                                    # UiPath Studio dependencies & configuration
├── .gitignore                                      # Excludes local UiPath cache folders
└── README.md                                       # Project documentation & PDD summary
