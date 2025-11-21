# Demo Request Intake Automation (Make.com)

## 🧩 Overview

This Make.com scenario automates the **demo request intake process** for a SaaS product.

When a prospect submits a demo request form, the workflow:

1. Captures the submission (Typeform / Webhook / Form tool)
2. Creates or updates a **contact in the CRM** (Salesforce / HubSpot)
3. Logs the request in a **tracking sheet** (Google Sheets / Airtable)
4. Sends a **Slack / MS Teams notification** to the sales or SE channel
5. Optionally triggers a **round-robin router** to assign the lead

This is the kind of automation I use to support **pre-sales, SDR, and Solutions Engineering teams**—reducing manual work and ensuring every request is followed up.

---

## ⚙️ Tech Stack

- **Automation Platform:** Make.com  
- **Intake Source:** Typeform (or Webhook module)  
- **CRM:** Salesforce or HubSpot CRM  
- **Collaboration:** Slack or Microsoft Teams  
- **Reporting:** Google Sheets  

---

## 🔄 Scenario Flow

**Trigger → Enrich → Create/Update → Notify → Log**

1. **Trigger:**  
   - Typeform “New Response” module  
   - (Alternative: Webhooks → Custom form)

2. **Parse & Map Fields:**  
   - Name, email, company, role  
   - Use case / interest area  
   - Preferred demo time or urgency  

3. **CRM Action:**  
   - Search for existing contact by email  
   - If found → update record  
   - If not found → create new contact and (optional) a new deal/opportunity

4. **Notification:**  
   - Post formatted message to Slack/MS Teams:  
     - Prospect name + company  
     - Use case summary  
     - Direct link to CRM record  
     - Priority flag (e.g. “Enterprise / High Intent”)

5. **Logging:**  
   - Append a new row in Google Sheets:  
     - Timestamp, source, owner, status, notes  

6. **(Optional) Assignment:**  
   - Use a **Router** or **Data Store** to assign ownership (SDR/AE/SE) round-robin style.  

---

## 🧱 Make.com Modules Used

- **Typeform / Webhooks** – Trigger on new submission  
- **Tools → JSON / Text Parser** – Clean and map payload fields  
- **Salesforce / HubSpot CRM** – Create/Update Contact & Deal  
- **Slack / MS Teams** – Send channel notification  
- **Google Sheets** – Add row to “Demo Requests” sheet  
- **Routers** – Branch logic (new vs existing contact, priority, etc.)  
- **Data Store (optional)** – Track round-robin ownership  

---

## 🗂 Files in This Folder

- `demo-request-intake.json`  
  Exported Make.com scenario (JSON). This is the actual workflow that can be imported into Make.

- `scenario-notes.md`  
  Design notes and field mapping used during planning and pre-sales conversations.

- `screenshots/`  
  Visuals from inside Make:
  - Scenario canvas
  - Module configuration
  - Example Slack message
  - Example Google Sheet log

---

## 🎯 Business Value

- **Speed to Lead:** No manual re-entry of demo requests.  
- **Consistency:** Every request is logged, assigned, and visible.  
- **Collaboration:** Sales, SE, and RevOps can see activity in real time.  
- **Pre-Sales Enablement:** SEs can quickly see context and use case before the call.  

This project is a good example of how I approach **technical discovery → solution design → implementation** as a Solutions Engineer focused on automation and integrations.
