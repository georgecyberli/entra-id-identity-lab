# Microsoft Entra ID — Identity & Access Management Lab

**Topics:** Microsoft Entra ID, Conditional Access, SAML SSO, RBAC, Zero Trust, Identity Management

![Cloud](https://img.shields.io/badge/Cloud-Azure-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![Focus](https://img.shields.io/badge/Focus-Identity%20%26%20Access%20Management-red?style=flat-square)
![Focus](https://img.shields.io/badge/Focus-Zero%20Trust-green?style=flat-square)
![Practice](https://img.shields.io/badge/Practice-SAML%20SSO-blue?style=flat-square)
![Output](https://img.shields.io/badge/Output-Runbooks-grey?style=flat-square)

A hands-on lab series demonstrating enterprise identity management using Microsoft Entra ID (Azure AD), built as part of a self-directed sysadmin training program. Each lab simulates real-world scenarios found in healthcare and enterprise IT environments.

**Environment:** Microsoft 365 E5 Trial | Tenant-based lab, fully isolated from production

---

## Overview

| # | Lab | Skills Demonstrated |
|---|---|---|
| 1 | [Conditional Access Policies](#lab-1--conditional-access-policies) | Zero Trust, MFA enforcement, geo-blocking |
| 2 | [Self-Service Password Reset (SSPR)](#lab-2--self-service-password-reset-sspr) | Identity self-service, helpdesk reduction |
| 3 | [RBAC & Administrative Units](#lab-3--rbac-role-based-access-control) | Least privilege, scoped delegation |
| 4 | [Enterprise Apps & SAML SSO](#lab-4--enterprise-applications--saml-sso) | Federated identity, SAML, third-party integration |

---

## Lab 1 — Conditional Access Policies

**Objective:** Implement Zero Trust access controls that adapt based on user location and risk level — a core requirement for HIPAA-aligned environments.

### What I Built
- **Policy 1:** Required MFA for all users signing in from outside the United States
- **Policy 2:** Blocked access entirely from high-risk countries
- Configured named locations using IP-based geolocation
- Properly excluded break-glass admin account to prevent tenant lockout

### Key Concepts
- Conditional Access policies are evaluated simultaneously; **Block always overrides Grant**
- Security Defaults must be disabled before Conditional Access can be used
- Layered policies (multiple MFA triggers) are additive, not conflicting — users see one prompt regardless of how many policies match

### Skills Demonstrated
`Zero Trust Architecture` `MFA Enforcement` `Geo-Blocking` `Named Locations` `Policy Design`

---

## Lab 2 — Self-Service Password Reset (SSPR)

**Objective:** Reduce helpdesk ticket volume and enable 24/7 password recovery for shift-based staff (nurses, on-call doctors).

### What I Built
- Enabled SSPR scoped to a specific department group (least-privilege rollout)
- Configured dual-method verification (Authenticator app, SMS, Email OTP)
- Set up mandatory registration on first sign-in
- Enabled 180-day re-confirmation cycle for contact info accuracy
- Configured security notifications for unexpected resets, including admin-to-admin alerts

### Key Concepts
- Security Questions are deprecated industry-wide (Microsoft retiring March 2027)
- Requiring 2 verification methods protects against single-channel compromise
- Phased rollout (Selected group vs All users) reduces risk during adoption

### Skills Demonstrated
`Identity Self-Service` `Risk-Based Rollout` `MFA Methods` `Security Notifications`

---

## Lab 3 — RBAC (Role-Based Access Control)

**Objective:** Apply least-privilege principles to administrative access, preventing the kind of over-permissioning that leads to security incidents (e.g. helpdesk staff inheriting full admin rights).

### What I Built
- Direct role assignment (User Administrator → single user)
- Role-assignable security group creation (`Helpdesk-Admins`)
- Administrative Unit creation to scope delegated access (`Billing-AU`)
- Combined group + scope assignment — delegated admins can only manage users within their assigned business unit

### Key Concepts
- Role-assignable groups must be configured at creation time — this setting cannot be changed retroactively
- Scoping a role to an Administrative Unit must be done from within the AU itself, not from the role blade
- This mirrors a real incident from prior healthcare IT experience where lack of granular RBAC led to over-permissioning

### Skills Demonstrated
`Least Privilege` `Delegated Administration` `Administrative Units` `Scoped RBAC`

---

## Lab 4 — Enterprise Applications & SAML SSO

**Objective:** Configure federated single sign-on between Entra ID and a third-party SaaS application (Salesforce), enabling centralized identity governance across cloud apps.

### What I Built
- Added Salesforce from the Entra ID application gallery
- Configured a SAML 2.0 trust relationship between Entra ID (Identity Provider) and Salesforce (Service Provider)
- Resolved cross-platform metadata import issues (Remote Site Settings allowlisting)
- Assigned users via Entra ID for centralized access governance
- Validated SAML handshake via SP-initiated SSO test

### Key Concepts
- SAML requires bidirectional trust configuration — both IdP and SP must agree on Entity ID, ACS URL, and certificates
- Metadata URL exchange eliminates manual certificate/endpoint entry errors
- User identity mapping (Federation ID) is a common SSO failure point — distinct from the SAML trust configuration itself

### Skills Demonstrated
`SAML 2.0` `Federated Identity` `SaaS Integration` `Cross-Platform Troubleshooting`



## Tech Stack
`Microsoft Entra ID` `Microsoft 365 E5` `Conditional Access` `SAML 2.0` `Salesforce` `Azure`

