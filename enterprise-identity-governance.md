# 🚀 PROJECT 1: Enterprise Identity Governance Program

## 📖 Story
I am the **Privileged IAM Engineer** for **Robinhood305 Financial**. 

The company recently hired **50 employees** and needs a production-grade identity architecture.

---

## 📋 Management Requirements:

* 🔒 **Least Privilege:** Enforce minimal baseline access controls across resources.
* 📲 **MFA:** Require Multi-Factor Authentication for all identity sign-ins.
* 🔑 **PIM:** Configure Privileged Identity Management for just-in-time elevation.
* 🔍 **Access Reviews:** Set up automated governance audits to prune stale access.
* ⚡ **Automated Onboarding:** Programmatically provision users via Graph PowerShell.
* 🛑 **Automated Offboarding:** Instantly revoke access and terminate active sessions.

---

### 🛠️ Execution Plan
I will build and document everything step-by-step.

---

# 🏢 PHASE 1: Building The Company Directory & Provisioning Identities

## 📖 Scenario & Context
I am the **Privileged IAM Engineer** for **Robinhood305**. 

A new branch office has opened, and **9 new employees** have been onboarded. As the Privileged IAM Engineer, my core responsibility is to provision digital identities in **Microsoft Entra ID** to establish baseline access controls across the tenant.

> 💡 **Analogy:** Imagine a new school opening. Before students can enter classrooms or access campus resources, their student IDs must be created and registered in the school database. No ID = No access.

---

## 🎯 Objectives & Scope
* 🆔 Provision unique user identities in Microsoft Entra ID for the 9 new hires.
* 🏷️ Maintain standard naming conventions (`usr-` for standard users, `adm-` for admin roles).
* 🔒 Establish strict identity lifecycle boundaries prior to applying access policies.

---

## 👥 Provisioned Identities

### 🛡️ Administrative Accounts
* `adm-global01` — Global Administrator (Break-Glass / Admin Identity)
* `adm-helpdesk01` — Helpdesk Administrator
* `adm-identity01` — Identity Governance Specialist
* `adm-security01` — Security Operations Administrator

### 💼 Standard User Accounts
* `usr-finance01` — Finance Department Representative
* `usr-finance02` — Finance Department Representative
* `usr-hr01` — Human Resources Representative
* `usr-hr02` — Human Resources Representative
* `usr-manager01` — Operations Manager

---

## 📸 Verification & Evidence

Below is the verified record from the **Microsoft Entra Admin Center** demonstrating all 9 newly created accounts active in the tenant:

![Microsoft Entra Users Verification](./phase1-users-verification.png)
> **Key Takeaway:** Identity is the new security perimeter. By standardizing UPN formats (`@Robinhood305...`) and separating standard accounts from administrative roles from Day 1, we eliminate account drift and maintain strict audit readiness.

# 🏢 Phase 02: Group Management 👥

## 🎯 Objective
Implement scalable identity and access management using Microsoft Entra ID Security Groups to eliminate direct user permission assignments.

---

## 🏢 Business Scenario
Robinhood305 Financial Services has grown to 50 employees across multiple departments. 

As the Identity Engineer, my manager tells me to:
> *"Stop assigning access directly to users. We need a scalable way to manage permissions."*

To take ownership of the problem and enforce the principle of least privilege, I start the initiative to replace direct user assignments with centralized departmental security groups.

---

## 📁 Groups Created
* `GRP-FINANCE-USERS`
* `GRP-HR-USERS`
* `GRP-IT-ADMINS`
* `GRP-MANAGERS`
* `GRP-SECURITY-TEAM`

---

## 👥 Membership Assignments & Evidence

### 💰 Finance
* `usr-finance01`
* `usr-finance02`
* **Evidence:**
  * `02.7-Finance-Members.png`
  * `GRP-FINANCE-USERS1.png`
  * `GRP-FINANCE-USERS2.png`

### 📋 HR
* `usr-hr01`
* `usr-hr02`
* **Evidence:**
  * `02.8-HR-Members.png`
  * `GRP-HR-USERS1.png`
  * `GRP-HR-USERS2.png`

### 👔 Management
* `usr-manager01`
* **Evidence:**
  * `02.9-Manager-Membership.png`
  * `GRP-MANAGERS1.png`
  * `GRP-MANAGERS2.png`

### 💻 IT Administration
* `adm-global01`
* `adm-helpdesk01`
* `adm-identity01`
* **Evidence:**
  * `02.10-IT-Admin-Members.png`
  * `GRP-IT-ADMIN1.png`
  * `GRP-IT-ADMIN2.png`

### 🛡️ Security
* `adm-security01`
* **Evidence:**
  * `02.11-Security-Team-Members.png`
  * `GRP-SECURITY-TEAM1.png`
  * `GRP-SECURITY-TEAM2.png`

---

## ⭐ Security Benefits
* 🔒 Centralized permission management
* ⚡ Reduced administrative effort
* 🔍 Easier auditing
* ✨ Simplified onboarding
* 🛡️ Supports Role Based Access Control (RBAC)

---

## ✅ Validation
Verified user membership assignments within each security group and confirmed administrative and departmental separation.

* **Validation Evidence:**
  * `02.6-All-Groups-Created.png`
  * `02.12-Group-Membership-Validation.png`
