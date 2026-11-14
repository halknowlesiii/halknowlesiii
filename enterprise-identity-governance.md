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

## 📖 Business Scenario
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

---

# 🏢 # PHASE 02 - Group Management 👥

## 🎯 Objective
Implement scalable identity and access management using Microsoft Entra ID Security Groups to eliminate direct user permission assignments.

---

## 🏢 Business Scenario
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

---

# PHASE 03 - Role-Based Access Control (RBAC) 🔐

## 🎯 Objective
Implement Role-Based Access Control (RBAC) within Microsoft Entra ID to enforce least-privilege administrative access.

## 🏢 Business Scenario
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

---

# 🛡️ PHASE 04 - Privileged Identity Management (PIM)

## 📌 Objective
Implement **Privileged Identity Management (PIM)** within **Microsoft Entra ID** to provide secure, time-bound, just-in-time administrative access and enforce the principle of least privilege.

---

## 💼 Business Scenario
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

---

# PHASE 05 - Conditional Access 🛡️

## 🎯 Objective
Implement Microsoft Entra Conditional Access policies to strengthen authentication security and protect privileged accounts.

## 🏢 Business Scenario
Robinhood305 Financial Services has successfully implemented:

✅ User Accounts

✅ Security Groups

✅ RBAC

✅ Privileged Identity Management

Management now has a new concern. What if:
* Someone steals a password?
* An administrator logs in from an untrusted device?
* A user tries to sign in without MFA?

Leadership wants: **Stronger security controls without making access difficult for employees.**

I have been tasked with implementing: **Conditional Access Policies**

> 💡 **Analogy:**
> 🔓 Old lock.
> 🗝️ Old key.
> 💥 Easy to break.
> 
> 🔐 Modern lock.
> 🛡️ Harder to break.
> 
> ⚠️ **Legacy Authentication is the old lock.**

---

## 📊 Conditional Access Overview
Overview of the Conditional Access dashboard and active policies configured in the tenant:
![Conditional Access Overview](05.1-Conditional-Access-Overview.png)

---

## ⚙️ Policies Created

### 1️⃣ CA-MFA-Administrators
* **Purpose:** Require Multi-Factor Authentication for all administrator accounts.
* **Target Group:** `GRP-IT-ADMINS`
* **Controls:** Require MFA
* **Status:** Report-Only

![MFA Policy Users](05.2-MFA-Policy-Users.png)
![MFA Policy Users Selection](05.2-MFA-Policy-Users2.png)
![All Cloud Apps Target](05.3-All-Cloud-Apps.png)
![Require MFA Control](05.4-Require-MFA-Control.png)
![Report-Only Mode Setup](05.5-Report-Only-Mode.png)

---

### 2️⃣ CA-Block-Legacy-Authentication
* **Purpose:** Prevent access using legacy authentication methods.
* **Target Users:** All Users
* **Controls:** Block Access
* **Status:** Report-Only

![Legacy Auth Users Assignment](05.6-Legacy-Auth-Users.png)
![Legacy Authentication Condition](05.7-Legacy-Authentication-Condition.png)
![Block Access Control](05.8-Block-Access-Control.png)

---

## 📈 Security Benefits
* 🔐 Strengthens authentication security
* 📉 Reduces credential theft risk
* 🛡️ Supports Zero Trust principles
* 👑 Protects privileged accounts
* 🛑 Restricts insecure authentication methods

## ✅ Validation
Verified:
* Policies successfully created
* Correct users and groups assigned
* MFA requirements configured
* Legacy authentication restrictions configured
* Policies available in Conditional Access dashboard

## 💡 Lessons Learned
* Conditional Access provides adaptive access control by evaluating user, application, and authentication conditions before granting access.
* Requiring MFA and blocking legacy authentication reduces risk while supporting modern security best practices.

---

# PHASE 06 - Access Reviews 📋

## 🎯 Objective
Implement access governance controls through Microsoft Entra Access Reviews.

## 🏢 Business Scenario
Robinhood305 Financial Services now has 50 employees.

Leadership is concerned about something called: **Access Creep**

**Example:**
* A person starts in Finance.
* Then moves to HR.
* But they still keep their Finance access.
* Years later nobody remembers.
* ⚠️ **This is a security risk.**

 I have been asked to create **Quarterly Access Reviews** to ensure users only keep access they actually need.

> 💡 **Analogy:**
> 📋 Imagine your teacher has a classroom roster.
> 📅 Every few months, the teacher checks:
> 
> ❓ **Does this student still belong in my class?**
> 
> 🚫 If the answer is no:
> 
> ❌ **The student is removed.**
> 
> 🔄 **Access Reviews work exactly the same way.**

---

## 📊 Access Reviews Dashboard
Initial view of the Microsoft Entra Identity Governance Access Reviews dashboard:
![Access Review Dashboard](06.1-Access-Review-Dashboard.png)

---

## ⚙️ Access Review Created
* **Name:** Quarterly Finance Access Review
* **Scope:** `GRP-FINANCE-USERS`
* **Reviewer:** `usr-manager01`
* **Frequency:** Quarterly
* **Duration:** 30 Days

### 1️⃣ Template Selection & Review Scope
![New Access Review Form](06.2-New-Access-Review-Form.png)
![Review Scope Configuration](06.3-Review-Scope.png)

### 2️⃣ Reviewer Assignment & Recurrence Schedule
![Reviewer Assignment](06.4-Reviewer-Assignment.png)
![Review Frequency and Duration](06.5-Review-Frequency.png)

### 3️⃣ Completion & Decision Helper Settings
![Review Settings Configuration](06.6-Review-Settings.png)

---

## 📈 Security Benefits
* 🛑 Prevents access creep
* 🧹 Removes unnecessary access
* ⚖️ Improves governance
* 📑 Enhances audit readiness
* 🔒 Supports least privilege

## ✅ Validation
Verified:
* Finance Group selected
* Reviewer assigned
* Quarterly schedule configured
* Review successfully created

![Access Review Created Confirmation](06.7-Access-Review-Created.png)
![Quarterly Finance Access Review Overview](06.8-Review-Overview.png)

---

# PHASE 07 - Entitlement Management 📦

## 🎯 Objective
Implement Microsoft Entra Entitlement Management to automate access provisioning, approval workflows, access reviews, and lifecycle governance for business users.

## 🏢 Business Scenario
Robinhood305 Financial Services employs approximately 50 users across multiple departments.

As the environment continued to grow, manually assigning user access became inefficient and increased the risk of incorrect permissions.

To improve governance and streamline access management, Microsoft Entra Entitlement Management was implemented using Access Packages.

> 💡 **Analogy:**
> 🍔 Imagine a school cafeteria.
> Instead of ordering each item separately:
> * 🥪 Sandwich
> * 🍟 Chips
> * 🥤 Drink
> 
> 🍱 **You order a combo meal.**
> The combo meal already contains everything you need.
> 
> 📦 **An Access Package works the same way.**
> * Employees request one package.
> * Microsoft automatically gives them the correct access.
> * Every few months a manager checks if they still need it.
> * If they don't need it anymore, the access expires and gets removed.
> 
> 🔒 **This prevents people from keeping access forever and helps keep the environment secure.**

---

## 📊 Entitlement Management Overview
Initial view of the Microsoft Entra Identity Governance & Entitlement Management dashboard:
![Entitlement Management Dashboard](07.1-Entitlement-Management-Dashboard.png)

---

## ⚙️ Solution Implemented
A governed access request process was created using Microsoft Entra Entitlement Management. The following components were configured:

### 📁 Catalog
* **Created:** Robinhood305 Employee Access Catalog
* **Purpose:** Provide a central location for employee access resources and access packages.

![New Catalog Form](Robinhood305%20Employee%20Access%20Catalog.png)
![Catalog Created](07.2-Catalog-Created.png)

### 🔗 Resource Assignment & Roles
* **Added Resource:** `GRP-FINANCE-USERS` (Role: `Member`)
* **Purpose:** Provide Finance department users with appropriate group-based access.

![Catalog Resources](07.3-Catalog-Resources.png)
![Add Resources to Catalog](07.3-Catalog-Resources1.png)
![Resource Role Assignment Overview](07.5-Resource-Role-Assignment.png)
![Add Resource Roles to Access Package](07.5-Resource-Role-Assignment1.png)

### 📦 Access Package
* **Created:** Finance Employee Access Package
* **Purpose:** Provide approved Finance employees with required departmental access through a single request process.

![New Access Package Basics](07.4-Access-Package-Created1.png)
![Access Package Review and Create](07.4-Access-Package-Created2.png)
![Access Package Created Confirmation](07.4-Access-Package-Created3.png)

### 📜 Policy Configuration
* **Configured:** Initial Policy
* **Purpose:** Control who can request access, collect justification questions, require manager approval, and configure custom extensions.

![Initial Policy Basics](07.6-Initial-Policy-Basics.png)
![Requestor Configuration](07.7-Requestor-Configuration.png)
![Requestor Information Questions](07.8-Requestor-Information.png)
![Approval Workflow Configuration](07.9-Approval-And-Expiration1.png)
![Custom Extensions Configuration](07.10-Custom-Extensions.png)

---

## 🔄 Lifecycle Governance Controls

### ⏳ Access Expiration
* **Assignments expire after:** 90 Days
* **Purpose:** Prevent unnecessary long-term access.

### 🔁 Access Extensions
* **Enabled:**
  * Allow users to request extension
  * Require approval for extension requests
* **Purpose:** Ensure continued access remains justified and approved.

### 📋 Access Reviews
* **Review Frequency:** Quarterly
* **Review Duration:** 25 Days
* **Reviewer Type:** Manager (Fallback: `usr-manager01`)
* **Purpose:** Verify users continue to require Finance access.

![Lifecycle Expiration, Extensions, and Access Reviews](07.9-Access-Expiration-90-Days.png)

---

## 📈 Security Benefits
Implementation of Entitlement Management provided the following security improvements:
* 🤖 Automated access provisioning
* 📉 Reduced manual administration
* ✅ Approval-based access assignment
* 🔍 Periodic access validation
* 🛑 Prevention of access creep
* 📑 Improved auditability
* ⏱️ Lifecycle-based access expiration
* ⚖️ Governance-driven access management

## ✅ Validation Performed
Validated the following:
* ✅ Catalog Created
* ✅ Finance Resource Added
* ✅ Access Package Created
* ✅ Resource Roles Assigned
* ✅ Initial Policy Configured
* ✅ Access Expiration Enabled
* ✅ Quarterly Access Reviews Enabled
* ✅ Manager Reviewer Configured
* ✅ Extension Approval Enabled
* ✅ Policy Successfully Saved

![Final Policy Configuration Validation](07.11-Policy-Configured.png)

## 💡 Lessons Learned
* Microsoft Entra Entitlement Management allows organizations to package access into a structured approval process rather than manually provisioning resources.
* By combining Access Packages, Access Reviews, Expiration Policies, and Approval Workflows, organizations can establish identity governance controls that improve security while reducing administrative overhead.
* This approach supports least-privilege access principles and provides a scalable access governance framework.

---

## 🎤 Interview Talking Points

### 🛠️ What Was Implemented
* Implemented Microsoft Entra Entitlement Management using Access Packages for Finance department users.
* Created lifecycle governance controls including access expiration, access reviews, manager-based approval processes, and extension approval workflows.

### 🎯 Why It Was Implemented
* To reduce manual provisioning, improve identity governance, prevent access creep, and ensure that access remained aligned with business requirements.

### 💼 Business Value
* ⚖️ Improved governance
* 🛡️ Reduced risk
* 🚀 Simplified user onboarding
* 🤖 Automated access management
* 📑 Increased audit readiness
* 🔒 Supported least privilege access

## 💡 Lessons Learned
* Access Reviews provide a governance mechanism for periodically validating user permissions.
* Regular review cycles help organizations maintain least-privilege access and reduce the risks associated with excessive or outdated permissions.
