# Demo CRM Contacts API Integration

## 🧩 Overview

This project demonstrates a simple but realistic **CRM Contacts API** integration using Postman.

The goal is to show how a Solutions Engineer or Integration Engineer would:

1. Explore and test REST endpoints  
2. Use an environment for different base URLs and API keys  
3. Create, update, list, and retrieve contact records  
4. Add basic automated tests in Postman  
5. Document the integration flow for use in PoCs or customer calls  

This API integration can be referenced in pre-sales conversations to explain how a SaaS platform communicates with a CRM or internal customer database.

---

## 🔗 High-Level Flow

```mermaid
flowchart LR
  A[Client App / Workflow] -->|REST API Call| B[Contacts API Gateway]
  B -->|GET /contacts| C[(CRM Database)]
  B -->|POST /contacts| C
  B -->|PUT /contacts/:id| C
  B -->|GET /contacts/:id| C
