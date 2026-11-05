Markdown
# 🚀 Zenvora Employee Onboarding Application

An enterprise-grade, custom ServiceNow Scoped Application designed to automate the cross-departmental onboarding lifecycle of new hires. From initial HR request submission to dynamic multi-tier manager approvals, role-based access security, and automated IT/Facilities downstream fulfillment provisioning.

---

## 📑 Table of Contents

- [Executive Summary](#-executive-summary)
- [System Architecture](#️-system-architecture)
- [Key Features & Capabilities](#-key-features--capabilities)
- [Repository Directory Structure](#-repository-directory-structure)
- [Visual Proof of Work](#-visual-proof-of-work)
- [Installation & Deployment Guide](#-installation--deployment-guide)
- [Author & Maintainer](#-author--maintainer)

---

## 📌 Executive Summary

Manual employee onboarding processes often lead to delayed IT hardware provisioning, communication gaps, and security compliance risks. The Zenvora Employee Onboarding application standardizes and automates this end-to-end process within ServiceNow.

By leveraging Flow Designer, Catalog Task automation, and Scoped Access Control Lists (ACLs), Zenvora ensures that upon manager approval, necessary fulfillment tasks (Hardware setup, Service Desk access badges) and external candidate communication are generated automatically.

---

## 🏗️ System Architecture

```text
                        ┌────────────────────────────────────────┐
                        │   HR / Hiring Manager Submission       │
                        └──────────────────┬─────────────────────┘
                                           │
                                           ▼
                        ┌────────────────────────────────────────┐
                        │   Custom Table: onboarding_request     │
                        └──────────────────┬─────────────────────┘
                                           │
                                           ▼
                        ┌────────────────────────────────────────┐
                        │      Flow Designer Approval Engine     │
                        └──────────────────┬─────────────────────┘
                                           │
                               ┌───────────┴─────────────┐
                               │                         │
                               ▼                         ▼
                      [ State: Approved ]       [ State: Rejected ]
                               │                         │
                 ┌─────────────┼─────────────┐           └─► Terminate Process
                 ▼             ▼             ▼
          ┌─────────────┐ ┌───────────────┐ ┌────────────────┐
          │ IT Hardware │ │ Service Desk  │ │ Outbound Email │
          │ Task Gen    │ │ Access Task   │ │ Notification   │
          │ (sc_task)   │ │ (sc_task)     │ │ (sys_email)    │
          └─────────────> └───────────────┘ └────────────────┘
✨ Key Features & Capabilities
Scope Isolation: Engineered inside x_2218141_zenvor_0 to prevent global namespace pollution and protect application assets.

Role-Based Security: Custom ACLs enforcing strict access so managers and users only view records relevant to their organizational unit.

Dynamic Flow Orchestration: Automated approval routing sent directly to the designated Reporting Manager.

Parallel Task Generation: Post-approval instantiation of fulfillment tasks (sc_task) assigned to dedicated fulfillment teams (Hardware, Facilities/Service Desk).

Automated SMTP Email Dispatch: HTML-formatted welcome email sent to candidate personal email upon request approval.

📂 Repository Directory Structure
Plaintext
Zenvora-Employee-Onboarding/
├── assets/
│   ├── 01-studio-workspace.png
│   ├── 02-data-model-schema.png
│   ├── 03-acl-security.png
│   ├── 04-form-ui-design.png
│   ├── 05-flow-designer-logic.png
│   ├── 06-approved-record.png
│   ├── 07-fulfillment-tasks.png
│   ├── 08-email-notification.png
│   └── 09-service-catalog-intake.png
├── update_runs/
│   └── sys_remote_app_x_2218141_zenvor_0.xml
├── .gitignore
├── LICENSE
└── README.md
📸 Visual Proof of Work
1. Studio Workspace & Application Structure
Classic Studio workspace view displaying the scoped application file tree, custom table definitions, and application components.

2. Data Model & Schema Definition
Schema configuration for the custom x_2218141_zenvor_0_onboarding_request table detailing fields, data types, and mandatory constraints.

3. Role-Based Access Control (ACL)
Role-based access control rule configuration restricting read and write privileges on the onboarding request table to authorized roles.

4. Custom Form Layout & UI Design
Backend user interface form layout featuring structured sections for new hire details, joining date selection, and manager assignment.

5. Automated Workflow Logic (Flow Designer)
End-to-end Flow Designer workflow canvas illustrating trigger conditions, validation logic, dynamic manager approval routing, and task creation.

6. Approved Onboarding Request Record Lifecycle
Live execution record demonstrating full lifecycle progression, showing active approval state set to Approved by hiring manager.

7. Downstream Fulfillment Tasks
Generated child catalog tasks (sc_task) automatically spawned for hardware and service desk provisioning upon request approval.

8. Outbound Email Notification Log
Rendered system log proof verifying outbound send-ready SMTP welcome email generation with dynamically populated variables.

9. Service Catalog Intake Portal
User-facing Service Catalog interface featuring structured container variable sets, mandatory field rules, and joining date validation.

💻 Installation & Deployment Guide
Log into your ServiceNow instance as System Administrator.

Navigate to ServiceNow Classic Studio (/$studio.do).

Click Import From Source Control.

Enter repository URL and credentials.

Select application scope x_2218141_zenvor_0.

Open Flow Designer and activate Onboarding Approval Flow.

Assign target roles (x_2218141_zenvor_0.onboarding_request_user) to test user accounts.

👤 Author & Maintainer
Developer: ServiceNow Application Developer (Rohit Kumar Patel)

Instance: PDI dev350797


### 1. Studio Workspace & Application Structure
![Studio Workspace](01-studio-workspace.png)

### 2. Data Model & Schema Definition
![Data Model Schema](02-data-model-schema.png)

### 3. Role-Based Access Control (ACL)
![ACL Security](03-acl-security.png)

### 4. Custom Form Layout & UI Design
![Form UI Design](04-form-ui-design.png)

### 5. Automated Workflow Logic (Flow Designer)
![Flow Designer Logic](05-flow-designer-logic.png)

### 6. Approved Onboarding Request Record Lifecycle
![Approved Record](06-approved-record.png)

### 7. Downstream Fulfillment Tasks
![Fulfillment Tasks](07-fulfillment-tasks.png)

### 8. Outbound Email Notification Log
![Email Log](08-email-notification.png)

### 9. Service Catalog Intake Portal
![Service Catalog Intake](09-service-catalog-intake.png)

