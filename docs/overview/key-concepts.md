# Key Concepts

Understanding these terms is essential before configuring IdentraCore IAM.

## Identity and Authentication

**Identity Provider (IdP)**
The system that stores and verifies user identities. IdentraCore IAM can act as an IdP, or connect to an external IdP such as Active Directory, Okta, or Azure AD.

**Service Provider (SP)**
An application that relies on the IdP to authenticate users. When a user tries to access an SP, they are redirected to the IdP for authentication.

**Authentication**
The process of verifying that a user is who they claim to be — typically via username/password, MFA, or certificates.

**Federation**
A trust relationship between two systems (typically an IdP and an SP) that allows users to authenticate across organizational or domain boundaries without separate credentials.

---

## Authorization

**Authorization**
The process of determining what an authenticated user is allowed to do. Authorization is separate from authentication.

**Role**
A named collection of permissions. Users are assigned roles; roles grant access. Example: `helpdesk-agent`, `app-admin`, `read-only-auditor`.

**Permission**
A specific action a role grants. Example: `user:read`, `group:write`, `report:export`.

**Policy**
A rule that defines who can access what, under which conditions. Policies are evaluated at runtime during access decisions.

**Least Privilege**
A security principle: users should have only the minimum permissions required for their job function.

---

## Key Abbreviations

| Abbreviation | Full Form |
|---|---|
| IAM | Identity and Access Management |
| SSO | Single Sign-On |
| MFA | Multi-Factor Authentication |
| RBAC | Role-Based Access Control |
| SAML | Security Assertion Markup Language |
| OIDC | OpenID Connect |
| SCIM | System for Cross-domain Identity Management |
| IdP | Identity Provider |
| SP | Service Provider |

