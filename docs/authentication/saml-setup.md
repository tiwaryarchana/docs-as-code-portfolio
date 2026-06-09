# SAML 2.0 Setup

This section describes how to configure SAML 2.0 federation between IdentraCore IAM (as the Identity Provider) and an external application (as the Service Provider).

## Before You Begin

Collect the following values from your Service Provider:

- **ACS URL** (Assertion Consumer Service URL) — where IdentraCore IAM posts the SAML response
- **Entity ID** (SP Entity ID) — unique identifier for the SP
- **NameID Format** — typically `emailAddress` or `persistent`
- **SP Certificate** (optional) — required if the SP expects signed requests

## IdentraCore IAM SAML Endpoints

Provide these values to your SP administrator:

| Field | Value |
|---|---|
| **IdP Entity ID** | `https://auth.netsecure.example.com/saml/metadata` |
| **SSO URL (POST)** | `https://auth.netsecure.example.com/saml/sso` |
| **SSO URL (Redirect)** | `https://auth.netsecure.example.com/saml/sso/redirect` |
| **SLO URL** | `https://auth.netsecure.example.com/saml/slo` |
| **Metadata URL** | `https://auth.netsecure.example.com/saml/metadata.xml` |

!!! note
    Replace `auth.netsecure.example.com` with your tenant's actual hostname.

## Configuration Steps

1. In the Admin Console, go to **Applications → Add Application → Custom SAML App**.
2. Enter a display name for the application.
3. In the **SAML Settings** section, enter:
   - **ACS URL**
   - **SP Entity ID**
   - **NameID Format**
4. Under **Signing**, select whether to sign the assertion, the response, or both. Most SPs require **Assertion signed**.
5. Add any required attribute statements under **Attribute Mapping**.
6. Click **Save**.

## Downloading the IdP Metadata

After saving, download the IdP metadata XML to provide to your SP:

```
Admin Console → Applications → [Your App] → SAML Settings → Download Metadata
```

Import this file into your SP's SAML configuration to complete the trust relationship.

## Verifying the Configuration

Run a test login from **Applications → [Your App] → Test SSO**. A successful test shows a green confirmation with the SAML assertion details.

!!! warning
    If the test fails with a `Response not valid` error, check that the system clocks on both the IdP and SP are synchronized. SAML assertions are time-sensitive and will be rejected if the timestamps differ by more than 5 minutes.
