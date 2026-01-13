# Demo Request Intake – Scenario Notes

## Goal

Automate the flow from **demo request form submission → CRM record → team notification → reporting**, to reduce manual work for SDRs/SEs and ensure fast, consistent follow-up.

---

## Inputs

- Form fields:
  - `full_name`
  - `email`
  - `company`
  - `role`
  - `use_case`
  - `preferred_time`
  - `company_size`
  - `notes`

---

## Field Mapping

| Source Field     | CRM Field             | Sheet Column         |
|------------------|-----------------------|----------------------|
| full_name        | Contact Name          | Name                 |
| email            | Email                 | Email                |
| company          | Account / Company     | Company              |
| role             | Title                 | Role                 |
| use_case         | Description / Notes   | Use Case             |
| preferred_time   | Custom Field          | Preferred Time       |
| company_size     | Company Size          | Company Size         |
| notes            | Notes                 | Internal Notes       |

---

## Logic & Routing

1. **Check for existing contact (Search by Email)**  
   - If exists → update contact, log activity  
   - If not → create new contact + (optional) new opportunity

2. **Priority Rules (optional)**  
   - If `company_size` ≥ 500 or use case contains “enterprise” → mark as High Priority  
   - Route notification to a dedicated Enterprise channel

3. **Assignment Logic**  
   - Use a Make Data Store to track last assigned owner  
   - Rotate between SDR/AE/SE user IDs

---

## Error Handling

- Log errors to a separate Google Sheet tab (`errors`) with:
  - Timestamp
  - Payload snippet
  - Error message
- Optionally send a Slack alert to a `#automation-alerts` channel

---

## Notes for Reviewers

This scenario is representative of the type of **pre-sales automation** I design:
- It connects multiple SaaS tools
- Uses conditional logic and search/update patterns
- Improves visibility and accountability in the sales cycle
