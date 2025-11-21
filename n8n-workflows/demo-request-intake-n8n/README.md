# Demo Request Intake Automation (n8n)

## 🧩 Overview

This n8n workflow is the **node-based version** of my Make.com “Demo Request Intake” automation.

When a prospect submits a demo request form, the workflow:

1. Receives the form payload via **Webhook** (or Form tool integration)
2. Creates or updates a **Contact** in the CRM (Salesforce / HubSpot)
3. Logs the request in a **tracking sheet** (Google Sheets / Airtable)
4. Sends a **Slack / MS Teams notification** to the sales / SE channel
5. Optionally assigns the request to an owner using a **round-robin strategy**

This scenario shows how I can implement the *same business workflow* in multiple tools, which is a key skill for **Solutions Engineering and Integration roles**.

---

## ⚙️ Tech Stack

- **Automation Platform:** n8n
- **Trigger:** Webhook (public URL) or Form integration node
- **CRM:** Salesforce or HubSpot CRM
- **Collaboration:** Slack or Microsoft Teams
- **Reporting:** Google Sheets / Airtable

---

## 🔄 Workflow Logic

**Webhook → Transform → CRM → Notify → Log → (Optional) Assign**

1. **Webhook Trigger**
   - `Webhook` node receives form data (`POST`)
   - Validates required fields (name, email, company, use_case)

2. **Transform Payload**
   - `Set` / `Function` node normalizes fields
   - Maps raw form keys to CRM-friendly property names

3. **Check Existing Contact**
   - `HTTP Request` → CRM API OR native `Salesforce / HubSpot` node
   - Searches for contact by email

4. **Branch Logic (IF Node)**
   - If contact exists → Update record
   - Else → Create new contact (and optionally a Deal / Opportunity)

5. **Notification**
   - `Slack` node or `Microsoft Teams` node posts a formatted message with:
     - Name, company, role
     - Use case summary
     - Priority level
     - Link to CRM record

6. **Log to Sheet**
   - `Google Sheets` / `Airtable` node appends a row:
     - Timestamp, source, owner, status, notes

7. **(Optional) Assignment**
   - `Function` node + `Google Sheets` / `Airtable` / `Data` node
   - Implements round-robin owner assignment based on last assigned user

---

## 🧱 n8n Nodes Used

- `Webhook`
- `Set` / `Function`
- `IF`
- `HTTP Request` (or `Salesforce` / `HubSpot` nodes)
- `Slack` / `Microsoft Teams`
- `Google Sheets` or `Airtable`
- (Optional) `Code` / additional `HTTP Request` nodes for advanced routing

---

## 🗂 Files in This Folder

- `demo-request-intake-n8n.json`  
  Exported n8n workflow that can be imported into any n8n instance.

- `scenario-notes.md`  
  Detailed design notes, field mappings, and routing rules.

- `screenshots/`  
  - n8n editor canvas
  - Node configurations
  - Example Slack/Teams message
  - Example Google Sheet log

---

## 🎯 Business Value

- **Faster follow-up:** Every demo request is captured, logged, and notified automatically.
- **Better data quality:** Contacts and deals are created/updated consistently.
- **Better collaboration:** Sales, SEs, and RevOps always know what’s in the queue.
- **Tool flexibility:** Same workflow can run in Make **or** n8n, depending on stack and customer preference.

This project demonstrates my ability to deliver **tool-agnostic automation**—a core capability for any modern Solutions Engineer.
