# 🚀 PROJECT 1: Enterprise Identity Governance Program

## 📖 Story
I am the **Privileged IAM Engineer** for **Robinhood305 & Robinhoodh3a015**. 

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
You are the **Privileged IAM Engineer** for **Robinhood305**. 

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

Below is the verified record from the **Microsoft Entra admin center** demonstrating all 9 newly created accounts active in the tenant:

![Microsoft Entra Users Verification](./images/phase1-users-verification.png)

> **Key Takeaway:** Identity is the new security perimeter. By standardizing UPN formats (`@Robinhood305...`) and separating standard accounts from administrative roles from day one, we eliminate account drift and maintain strict audit readiness.
