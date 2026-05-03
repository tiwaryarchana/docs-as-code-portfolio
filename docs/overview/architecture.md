# Architecture

## Component Overview

NetSecure IAM consists of the following core components:

| Component | Description |
|---|---|
| **Identity Engine** | Processes authentication requests and evaluates policies |
| **Directory Service** | Stores user profiles, groups, and credentials |
| **Token Service** | Issues and validates SAML assertions, JWT tokens, and OAuth access tokens |
| **Admin Console** | Web UI for administrators to manage users, roles, and configuration |
| **Audit Service** | Captures and stores all system events for reporting and compliance |
| **SCIM Endpoint** | Accepts provisioning requests from connected HR or directory systems |

## Authentication Flow

The following describes a typical SSO login flow using SAML 2.0:

1. User attempts to access a connected application (the Service Provider).
2. The SP redirects the user to NetSecure IAM with a SAML authentication request.
3. NetSecure IAM presents the login page.
4. The user enters credentials. If MFA is enabled, a second factor is requested.
5. NetSecure IAM validates credentials and generates a SAML assertion.
6. The assertion is posted back to the SP's Assertion Consumer Service (ACS) URL.
7. The SP validates the assertion and creates a user session.

## Network Requirements

!!! warning
    Ensure the following ports are open before deployment.

| Port | Protocol | Purpose |
|---|---|---|
| 443 | HTTPS | All user and admin traffic |
| 636 | LDAPS | Secure LDAP directory sync |
| 8443 | HTTPS | Admin API (internal only) |
