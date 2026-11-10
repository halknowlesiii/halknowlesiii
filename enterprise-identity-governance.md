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

# 🏢 # Phase 02 - Group Management 👥

## 🎯 Objective
Implement scalable identity and access management using Microsoft Entra ID Security Groups to eliminate direct user permission assignments.

---

## 🏢 Scenario & Context
Robinhood305 Financial Services has grown to 50 employees across multiple departments. 
As the Identity Engineer, my manager told me to:
> *"Stop assigning access directly to users & We need a scalable way to manage permissions."*

To take ownership of the problem and enforce the principle of least privilege, I took the initiative to replace direct user assignments with centralized departmental security groups.

> 💡 **Analogy:** Imagine a teacher has 50 students. Instead of handing a textbook to every student one at a time, the teacher creates a class called:
> Math Class.
> 
> Everyone inside the class automatically gets the book.
> A group works exactly the same way.

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
  * ![Finance Members](./02.7-Finance-Members.png)
  * ![Finance Users 1](./GRP-FINANCE-USERS1.png)
  * ![Finance Users 2](./GRP-FINANCE-USERS2.png)

### 📋 HR
* `usr-hr01`
* `usr-hr02`
* **Evidence:**
  * ![HR Members](./02.8-HR-Members.png)
  * ![HR Users 1](./GRP-HR-USERS1.png)
  * ![HR Users 2](./GRP-HR-USERS2.png)

### 👔 Management
* `usr-manager01`
* **Evidence:**
  * ![Manager Membership](./02.9-Manager-Membership.png)
  * ![Managers 1](./GRP-MANAGERS1.png)
  * ![Managers 2](./GRP-MANAGERS2.png)

### 💻 IT Administration
* `adm-global01`
* `adm-helpdesk01`
* `adm-identity01`
* **Evidence:**
  * ![IT Admin Members](./02.10-IT-Admin-Members.png)
  * ![IT Admin 1](./GRP-IT-ADMIN1.png)
  * ![IT Admin 2](./GRP-IT-ADMIN2.png)

### 🛡️ Security
* `adm-security01`
* **Evidence:**
  * ![Security Team Members](./02.11-Security-Team-Members.png)
  * ![Security Team 1](./GRP-SECURITY-TEAM1.png)
  * ![Security Team 2](./GRP-SECURITY-TEAM2.png)

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
  * ![All Groups Created](./02.6-All-Groups-Created.png)
  * ![Group Membership Validation](./02.12-Group-Membership-Validation.png)

