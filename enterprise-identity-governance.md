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

# 🏢 PHASE 1 - Building The Company Directory & Provisioning Identities

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

# 🏢 # PHASE 02 - Group Management 👥

## 🎯 Objective
Implement scalable identity and access management using Microsoft Entra ID Security Groups to eliminate direct user permission assignments.

---

## 🏢 Scenario & Context
Robinhood305 Financial Services has grown to 50 employees across multiple departments. 
As the Identity Engineer, my manager told me to:
> *"Stop assigning access directly to users & We need a scalable way to manage permissions."*

To take ownership of the problem and enforce the principle of least privilege, I took the initiative to replace direct user assignments with centralized departmental security groups.

> 💡 **Analogy:** Imagine a teacher has 50 students.
> Instead of handing a textbook to every student one at a time, the teacher creates a class called:
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

# PHASE 03 - Role-Based Access Control (RBAC) 🔐

## 🎯 Objective
Implement Role-Based Access Control (RBAC) within Microsoft Entra ID to enforce least-privilege administrative access.

## 🏢 Scenario & Context
Robinhood305 Financial Services has grown to 50 employees. The company already has:
✅ User accounts & ✅ Security groups

Now leadership has identified a problem. Currently, everyone in IT could potentially have too much access.

Leadership wants: Least Privilege Access
Meaning: People should only have enough permissions to perform their jobs.

Nothing more.

To address this requirement, administrative responsibilities were separated into distinct roles.

> 💡 Analogy: Imagine your school.
> 
> The principal has a master key.
> The teacher has classroom keys.
> The janitor has cleaning closet keys.
> Each person gets the keys they need. Not every key.
> 
> RBAC works the same way.

---

## 📂 Roles Catalog Overview
Here is the overview of the role assignments catalog configured in the tenant:
![Roles Catalog Overview](03.1-Roles-Catalog.png)

---

## 👥 Roles Assigned

### 🎧 Helpdesk Administrator: This user can now help people reset passwords. They still do NOT have full administrator access.
- **Assigned To:** `adm-helpdesk01`
- **Responsibilities:**
  * Password resets
  * User support
  * Basic account management

![Helpdesk Assignment 1](03.2-Helpdesk-Assignment.png)
![Helpdesk Assignment 2](03.2-Helpdesk-Assignment2.png)
![Helpdesk Assignment 3](03.2-Helpdesk-Assignment3.png)

### 🪪 User Administrator: This account can manage users. But it still cannot control everything. That's safer.
- **Assigned To:** `adm-identity01`
- **Responsibilities:**
  * Create users
  * Modify users
  * Manage user properties

![User Admin Assignment 1](03.3-UserAdmin-Assignment.png)
![User Admin Assignment 2](03.3-UserAdmin-Assignment2.png)
![User Admin Assignment 3](03.3-UserAdmin-Assignment3.png)

### 🛡️ Security Reader: This person can look at security information. They're allowed to read. Not change. Like reading a report card without being allowed to edit it.
- **Assigned To:** `adm-security01`
- **Responsibilities:**
  * Review security information
  * View reports
  * Monitor security posture

![Security Reader Assignment 1](03.4-SecurityReader-Assignment.png)
![Security Reader Assignment 2](03.4-SecurityReader-Assignment2.png)
![Security Reader Assignment 3](03.4-SecurityReader-Assignment3.png)

---

## 📈 Security Benefits
- 🔒 Enforces least privilege
- 📉 Reduces attack surface
- ⚖️ Supports separation of duties
- 📋 Improves administrative accountability
- 🛑 Prevents unnecessary access

## ✅ Validation
Validated role assignments through Microsoft Entra ID Roles and Administrators.

Confirmed each administrative account was assigned only the permissions required for its specific job function.

![RBAC Validation 1](03.5-RBAC-Validation1.png)
![RBAC Validation 2](03.5-RBAC-Validation2.png)
![RBAC Validation 3](03.5-RBAC-Validation3.png)

## 💡 Lessons Learned
- RBAC improves security by assigning permissions based on job responsibilities instead of granting broad administrative access.
- Using dedicated administrative roles reduces organizational risk and supports enterprise security best practices.

# 🛡️ PHASE 04 - Privileged Identity Management (PIM)

## 📌 Objective
Implement **Privileged Identity Management (PIM)** within **Microsoft Entra ID** to provide secure, time-bound, just-in-time administrative access and enforce the principle of least privilege.

---

## 💼 Scenario & Context
**Robinhood305 Financial Services** identified a significant security exposure associated with permanent administrative privileges assigned to user accounts. To reduce the attack surface, prevent privilege creep, and support least-privilege administrative access, Microsoft Entra PIM was implemented.

> 💡 Analogy: Imagine your school has a master key.
> Instead of letting someone keep the master key forever:
> The principal locks the key in a cabinet.
>
> When somebody needs it:
>
> They request it.
> They explain why.
> They take it temporarily.
> They return it.
>
> PIM is a digital key cabinet.

---

## ⚙️ Solution & Policy Configuration

The **User Administrator** role was assigned as an **Eligible Assignment** to the administrative account `adm-identity01`. 

### 🔐 Security Controls Enforced:
- 🔑 **Multi-Factor Authentication (MFA)** required upon activation.
- 📝 **Justification Requirement** mandating business reasons for role requests.
- ⏱️ **Time-Limited Access** capped at a maximum of **8 Hours**.
- 🛡️ **Approval Workflow** requiring explicit approval from authorized administrators prior to activation.

---

## 📊 Security Benefits
- 🚫 **Eliminates Standing Privileges:** Reduces permanent admin access across the tenant.
- ⏳ **Just-In-Time (JIT) Access:** Restricts permissions strictly to operational windows.
- 🔍 **Enhanced Auditability:** Captures request reasons, approver actions, and activation timestamps.
- 🛡️ **Reduced Attack Surface:** Limits the impact of credential compromise on administrative accounts.

---

## 🛠️ Step-by-Step Execution & Evidence

### 1️⃣ Step 1: PIM Dashboard & Overview
*Accessing the Microsoft Entra Privileged Identity Management portal to manage privileges, configure roles, and monitor active assignments.*

![PIM Overview](04.1-PIM-Overview.png)

---

### 2️⃣ Step 2: Reviewing Entra ID Roles & Eligible Assignments
*Evaluating current role assignments and verifying eligible privileges assigned to administrative accounts.*

![Entra Roles](04.2-Entra-Roles.png)

---

### 3️⃣ Step 3: Assigning the User Administrator Role
*Configuring `adm-identity01` with an eligible assignment for the User Administrator role.*

![User Administrator Role Assignment](04.3-User-Administrator-Role.png)

---

### 4️⃣ Step 4: Adding Member & Scope Selection
*Selecting member `adm-identity01` and setting assignment properties within Entra PIM.*

![Eligible Assignment Configuration](04.4-Eligible-Assignment.png)

---

### 5️⃣ Step 5: Configuring Role Guardrails & Settings
*Enforcing maximum 8-hour duration, Azure MFA requirements, mandatory business justification, and designated approvers.*

![PIM Role Settings](04.5-PIM-Role-Settings.png)

---

### 6️⃣ Step 6: Initial Sign-In & Password Update
*Signing in as `adm-identity01` to update initial credentials before performing role activation requests.*

![Password Update Request](04.6-PIM-Activation-Request2.png)

---

### 7️⃣ Step 7: Initiating PIM Role Activation
*Selecting the eligible User Administrator role and triggering the activation sequence.*

![Activation Request Selection](04.6-PIM-Activation-Request.png)

---

### 8️⃣ Step 8: Providing Activation Justification & Duration
*Entering required business justification ("User Onboarding Activities") and requesting activation for the 8-hour duration.*

![PIM Activation Justification](04.6-PIM-Activation-Request3.png)

---

### 9️⃣ Step 9: Request Pending Approval
*The activation request enters the **Pending Approval** state, awaiting review by a Privileged Role Administrator.*

![Pending Approval State](image_65fa70.png)

---

### 🔟 Step 10: Role Activation Confirmation
*Notification bar confirms the active pending status while awaiting administrative sign-off.*

![Role Activated Pending Status](04.7-PIM-Role-Activated.png)

---

### 1️⃣1️⃣ Step 11: Audit History & Compliance Logging
*Reviewing the comprehensive audit log history capturing role activations, justifications, request timestamps, and administrative actions.*

![PIM Audit History](04.8-PIM-Audit-History.png)

---

## ✅ Validation & Verification

- [x] **Eligible Role Assignment:** Successfully assigned to `adm-identity01`.
- [x] **Policy Enforcement:** MFA, business justification, and max 8-hour limits successfully applied.
- [x] **Approval Workflow:** Request logged and queued for administrative approval.
- [x] **Audit Trail:** All activation events logged in Entra Audit Logs for compliance reporting.

---

## 💡 Lessons Learned
Transitioning from **standing administrative access** to **Just-In-Time (JIT) access** through Microsoft Entra PIM significantly hardens identity security. Requiring step-up MFA, mandatory business justifications, and approval workflows ensures complete visibility over privileged actions without hindering daily operational workflows.
