# Access Control Policy

**Company:** AcmeCloud Analytics  
**Product:** AcmeCloud Analytics cloud analytics platform for business reporting  
**Document Type:** Synthetic internal policy for demo use  
**Version:** 1.0  
**Effective Date:** 2026-01-15  
**Owner:** Security Operations Team  

## 1. Purpose

This Access Control Policy defines how AcmeCloud Analytics manages employee, administrator, and production access to systems that support the AcmeCloud Analytics platform. The policy is designed for a fictional RAG demonstration and contains synthetic control details that may be cited by an automated security questionnaire response workflow.

The goal of access control at AcmeCloud Analytics is to limit access to systems, data, and administrative functions based on business need. Access decisions are based on job responsibilities, approved roles, and least-privilege principles. This policy applies to employees, contractors, temporary staff, and approved support personnel who access company-managed systems.

## 2. Scope

This policy applies to:

- Internal identity accounts used by AcmeCloud Analytics personnel.
- Administrative access to production systems.
- Access to customer support tools that may display customer metadata.
- Access to internal code repositories, deployment systems, logging systems, and monitoring dashboards.
- Access requests, access changes, quarterly reviews, and termination procedures.

This policy does not define customer user permissions inside each customer workspace. Customer-side user management is described in the product administrator guide, which is not included in this evidence set.

## 3. Identity and Authentication

All AcmeCloud Analytics employees and administrators are required to use multi-factor authentication before accessing company-managed systems. MFA is required for email, internal collaboration tools, code repositories, deployment consoles, production monitoring dashboards, and administrative interfaces.

Shared employee accounts are not permitted for standard business operations. Named accounts must be used so activity can be associated with an individual user. Service accounts may be used for automated processes, but they must have a documented owner, a business purpose, and permissions limited to their intended function.

Password-only access is not considered sufficient for internal systems. Temporary MFA exceptions require written approval from the Security Operations Team and must include an expiration date. The maximum duration for a temporary MFA exception is seven calendar days.

## 4. Role-Based Access Control

Production access is role-based and granted according to approved job functions. AcmeCloud Analytics maintains role groups for engineering operations, customer support, security operations, and platform administration. Each role group has a defined purpose and a standard permission set.

Production database access is limited to approved engineering operations and security operations personnel. Customer support personnel may access support dashboards containing account metadata, but direct production database access is not part of the standard customer support role.

Access to production systems must be requested through the internal access request workflow. Each request must identify the requester, requested role, business justification, approving manager, and expected duration if access is temporary. Access is not considered active until approval is recorded.

## 5. Privileged Access

Privileged access includes permissions that can modify production infrastructure, change security settings, alter deployment pipelines, or view restricted customer data. Privileged access must be approved by the requester’s manager and the Security Operations Team.

Administrative access is not granted automatically based on seniority. Administrators must use named accounts with MFA. Emergency access may be granted during a production incident, but the access must be reviewed after the incident is closed. The incident review must confirm why access was needed, who approved it, and when access was removed or returned to normal.

## 6. Access Reviews

Production access is reviewed quarterly. The review includes role membership, privileged access, service accounts, and access granted for temporary projects. Managers are responsible for confirming whether their team members still require assigned access. The Security Operations Team coordinates the review and tracks completion.

Any access no longer required must be removed within five business days after the review decision. Unresolved review items are escalated to the department owner and the incident response lead if the access presents a security concern.

## 7. Onboarding, Transfer, and Offboarding

New employee access is provisioned based on role templates after manager approval. Role templates are reviewed at least annually by Security Operations.

When an employee changes teams or responsibilities, their access must be re-evaluated. Access that is no longer required for the new role must be removed. Temporary project access must include an expiration date.

When employment ends, standard internal access is disabled as part of the offboarding process. The policy does not specify the exact number of hours within which all accounts must be disabled after termination. That timing requires human review using the HR offboarding procedure, which is not included in this evidence set.

## 8. Logging and Monitoring

Administrative actions in production systems are logged where technically supported. Logs may include user ID, timestamp, source system, action performed, and target resource. Security Operations reviews selected administrative events during investigations, access reviews, and incident response activities.

This policy does not specify a universal log retention period for all access logs. Log retention may vary by system and is not fully defined in this document.

## 9. Exceptions

Exceptions to this policy require approval from the Security Operations Team. Exceptions must document the reason, compensating controls, owner, and expiration date. Open-ended exceptions are not permitted.

## 10. Limitations

This synthetic policy does not claim that AcmeCloud Analytics is certified under any external framework. It describes internal controls inspired by common security practices for demonstration purposes only.
