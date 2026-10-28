🚀 Zenvora Employee Onboarding Application

An enterprise-grade, custom ServiceNow Scoped Application designed to automate the cross-departmental onboarding lifecycle of new hires. From initial HR request submission to dynamic multi-tier manager approvals, role-based access security, and automated IT/Facilities downstream fulfillment provisioning.

📑 Table of Contents

Executive Summary

System Architecture

Key Features & Capabilities

Repository Directory Structure

Technical Implementation & Proof of Work

1. Scoped Application Architecture

2. Data Model & Database Schema

3. Security & Access Control Lists (ACLs)

4. UI & Form Layout Design

5. Process Automation via Flow Designer

6. Request Lifecycle Execution

7. Multi-Department Task Provisioning

8. Notification Engine Log Verification

Installation & Deployment Guide

📌 Executive Summary

Manual employee onboarding processes often lead to delayed IT hardware provisioning, communication gaps, and security compliance risks. The Zenvora Employee Onboarding application standardizes and automates this end-to-end process within ServiceNow.

By leveraging Flow Designer, Catalog Task automation, and Scoped Access Control Lists (ACLs), Zenvora ensures that upon manager approval, necessary fulfillment tasks (Hardware setup, Service Desk access badges) and external candidate communication are generated automatically.

🏗️ System Architecture

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
                                     ┌─────────────┴─────────────┐
                                     │                           │
                                     ▼                           ▼
                             [ State: Approved ]         [ State: Rejected ]
                                     │                           │
                   ┌─────────────────┼─────────────────┐         └─► Terminate Process
                   ▼                 ▼                 ▼
          ┌────────────────┐ ┌───────────────┐ ┌────────────────┐
          │ IT Hardware    │ │ Service Desk  │ │ Outbound Email │
          │ Task Generation│ │ Access Task   │ │ Notification   │
          │ (sc_task)      │ │ (sc_task)     │ │ (sys_email)    │
          └────────────────┘ └───────────────┘ └────────────────┘



✨ Key Features & Capabilities

Scope Isolation: Engineered inside x_2218141_zenvor_0 to prevent global namespace pollution and protect application assets.

Role-Based Security: Custom ACLs enforcing strict access so managers and users only view records relevant to their organizational unit.

Dynamic Flow Orchestration: Automated approval routing sent directly to the designated Reporting Manager.

Parallel Task Generation: Post-approval instantiation of fulfillment tasks (sc_task) assigned to dedicated fulfillment teams (Hardware, Facilities/Service Desk).

Automated SMTP Email Dispatch: HTML-formatted welcome email sent to candidate personal email upon request approval.

📂 Repository Directory Structure

Zenvora-Employee-Onboarding/
├── assets/
│   ├── 01_studio_scope_overview.png
│   ├── 02_table_schema_dictionary.png
│   ├── 03_security_acl_configuration.png
│   ├── 04_form_layout_ui_design.png
│   ├── 05_flow_designer_logic.png
│   ├── 06_approved_record_lifecycle.png
│   ├── 07_downstream_catalog_tasks.png
│   └── 08_outbound_email_log.png
├── update_runs/
│   └── sys_remote_app_x_2218141_zenvor_0.xml
├── .gitignore
├── LICENSE
└── README.md



🔍 Technical Implementation & Proof of Work

1. Scoped Application Architecture

Application assets are grouped and isolated under scope x_2218141_zenvor_0 in Classic Studio, maintaining source control links with Git.

2. Data Model & Database Schema

Custom table x_2218141_zenvor_0_onboarding_request extends task table with customized dictionary entries for new hire metadata, joining dates, department mappings, and equipment requirements.

3. Security & Access Control Lists (ACLs)

Role-based record-level security (read, create, write) restricting access to authorized roles (onboarding_request_user, hiring_manager).

4. UI & Form Layout Design

Clean, responsive user form interface with section grouping, reference lookups, dynamic choice lists, and mandatory data entry rules.

5. Process Automation via Flow Designer

Multi-step workflow featuring date parameter validation, manager approval actions, dynamic record state updates, multi-task spawning, and SMTP email dispatch.

6. Request Lifecycle Execution

Verified record execution showing successful manager approval state updates (Meera Kulkarni sign-off on request ONB0001014).

7. Multi-Department Task Provisioning

Automated creation of child catalog tasks (sc_task) routing hardware configuration to Hardware team and physical access setup to Service Desk.

8. Notification Engine Log Verification

System log proof verifying outbound send-ready SMTP welcome email generation with dynamically populated join date and candidate parameters.

💻 Installation & Deployment Guide

Log into your ServiceNow instance as System Administrator.

Navigate to ServiceNow Classic Studio (/$studio.do).

Click Import From Source Control.

Enter repository URL and credentials.

Select application scope x_2218141_zenvor_0.

Open Flow Designer and activate Onboarding Approval Flow.

Assign target roles (x_2218141_zenvor_0.onboarding_request_user) to test user accounts.

👤 Author & Maintainer

Developer: ServiceNow Application Developer

Instance: PDI dev350797


## 📸 Visual Proof of Work

### 1. Studio Workspace & Application Structure
![Studio Workspace](docs/screenshots/01-studio-workspace.png)

### 2. Data Model & Schema Definition
![Data Model Schema](docs/screenshots/02-data-model-schema.png)

### 3. Role-Based Access Control (ACL)
![ACL Security](docs/screenshots/03-acl-security.png)

### 4. Custom Form Layout & UI Design
![Form UI Design](docs/screenshots/04-form-ui-design.png)

### 5. Automated Workflow Logic (Flow Designer)
![Flow Designer Logic](docs/screenshots/05-flow-designer-logic.png)

### 6. Approved Onboarding Request Record Lifecycle
![Approved Record](docs/screenshots/06-approved-record.png)

### 7. Downstream Fulfillment Tasks
![Fulfillment Tasks](docs/screenshots/07-fulfillment-tasks.png)

### 8. Outbound Email Notification Log
![Email Log](docs/screenshots/08-email-notification.png)
