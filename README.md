## 📌 Project Overview
This lab demonstrates the deployment and configuration of an enterprise ticketing system using **osTicket** hosted on **Ubuntu Server**. The project simulates real-world **ITSM (IT Service Management)** practices by managing user requests, enforcing **SLA** compliance, and executing multi-tier **Ticket Escalations** between departments.

---

## 🛠️ Phase 1: Infrastructure & Administration Setup

### 1. System Environment
To build a realistic corporate environment, the platform was deployed on a dedicated Linux environment. The osTicket application runs on an Ubuntu Server virtual machine with a fully configured Apache web server to host the ticketing services.
* **Screenshot Reference:** `01-ubuntu-apache-environment.png` *(Shows the active Ubuntu Linux terminal interface alongside the successful Apache2 default web server landing page).*

### 2. Team & Department Structures
To simulate a real company, I created a cross-departmental structure with dedicated technical roles to ensure tasks are routed to the right specialists:
* **Departments Created:** IT (Default), NOC (Network Operations Center), and SOC (Security Operations Center).
* **Agents (Staff) Assigned:** 
  * **Fahad:** General IT Support Manager.
  * **Rayan:** NOC Department Manager.
  * **Nasser:** SOC Department Manager.
* **Screenshot Reference:** `02-agents-departments-setup.png` *(Shows the organized list of departments, active agents, and their respective management roles).*

### 3. SLA (Service Level Agreement) Policies
To ensure IT support tickets are resolved on time, I configured 4 distinct Service Level Agreements (SLA) based on urgency:
* **P1 (Critical):** 2-hour grace period (24/7 schedule).
* **P2 (High):** 4-hour grace period (24/7 schedule).
* **P3 (Medium):** 24-hour grace period.
* **P4 (Low):** 48-hour grace period.
* **Screenshot Reference:** `03-sla-policies-config.png` *(Shows the live configuration panel of the active SLA plans inside the system).*

---

## 💼 Phase 2: Real-World Ticket Scenarios (Lifecycles)

### 📈 Scenario 1: Active Directory & Permissions Issue (General IT)
* **The Problem:** An employee from the Finance department ("Abdulrahman") submitted a ticket stating he lost access to the shared network folder Drive Z: and keeps getting an "Access Denied" error message.
* **Ticket Arrival:** The ticket safely landed in the general IT department's inbox with an assigned ticket ID.
  * **Screenshot Reference:** `04-scenario1-ticket-received.png`
* **Investigation & Resolution:** The IT Agent (**Fahad**) picked up the ticket. After running local diagnostics, he determined it was an Active Directory issue. Fahad updated the user's security groups in the AD Domain Controller, verified the access fix, documented the internal technical logs, and successfully marked the ticket as resolved.
  * **Screenshot Reference:** `05-scenario1-active-directory-resolution.png`

---

### 🌐 Scenario 2: Firewall Restriction & Tier-2 Escalation (IT to NOC)
* **The Problem:** A developer ("Khaled") opened a ticket reporting that his development tools (`npm install` and `pip install`) are constantly timing out when trying to download required software packages from the internet.
* **Initial Diagnostics:** The ticket was assigned to the general IT queue.
  * **Screenshot Reference:** `06-scenario2-helpdesk-diagnostic.png` *(Shows the ticket thread where IT Agent Fahad investigated the workstation and left a technical note stating that local networking is fine, but perimeter Firewall rules are blocking the developer's external ports).*
* **The Escalation (Ticket Transfer):** Since altering firewall rules falls outside general IT support, Fahad utilized the system's escalation feature to officially **Transfer** the ticket to the **NOC (Network Operations Center)** department.
* **Resolution by NOC:** The NOC Agent (**Rayan**) took ownership of the escalated ticket. He modified the enterprise Firewall policies to permit outbound developer traffic, confirmed the fix with the user, and closed the ticket.
  * **Screenshot Reference:** `07-scenario2-noc-firewall-resolution.png` *(Shows the complete historical log of the ticket being transferred to NOC and successfully resolved).*

---

## 🎯 Key Takeaways from this Lab:
1. **Hands-on ITSM Practice:** Understood how tickets move from creation, assignment, internal notes, to escalation and resolution.
2. **SLA Management:** Designed and enforced strict response and resolution times based on issue urgency.
**Cross-Department Collaboration:** Practiced how real-world departments escalate complex issues to the specific department capable of resolving them.
