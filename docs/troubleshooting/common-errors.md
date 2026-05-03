# Common Errors

This topic lists frequently encountered errors and their resolution steps.

---

## Authentication Errors

### ERR_SSO_001 — Invalid SAML Response

**Message:** `The SAML response could not be validated.`

**Causes:**
- The SP certificate has expired or does not match the configured certificate in NetSecure IAM.
- The assertion has expired (timestamp skew between IdP and SP clocks).
- The ACS URL in the SAML request does not match the configured ACS URL.

**Resolution:**
1. Check the SP certificate: **Applications → [App] → SAML Settings → SP Certificate**.
2. Verify that the system clocks on both IdP and SP are synchronized (NTP recommended). Timestamps must be within 5 minutes.
3. Confirm the ACS URL matches exactly, including trailing slashes.

---

### ERR_SSO_002 — NameID Format Mismatch

**Message:** `NameID format in request does not match configured format.`

**Resolution:**
Go to **Applications → [App] → SAML Settings → NameID Format** and change it to match the format the SP is requesting. Common formats: `emailAddress`, `persistent`, `transient`.

---

### ERR_AUTH_003 — MFA Enrollment Required

**Message:** `Your account requires MFA enrollment before you can log in.`

**Resolution:**
This is expected behavior when MFA has been enforced and the user has not yet enrolled. Direct the user to complete enrollment by logging in and following the enrollment prompt. Administrators can also pre-enroll users under **Users → [User] → Security → MFA → Enroll**.

---

### ERR_AUTH_010 — Account Locked

**Message:** `Your account has been locked due to too many failed login attempts.`

**Resolution:**
Unlock the account:
```
Admin Console → Users → [User] → Actions → Unlock Account
```
Review recent failed login events in the audit log to determine if the lockout was caused by a legitimate error or a potential brute-force attempt.

---

## Provisioning Errors

### ERR_SCIM_404 — User Not Found

**Message:** `SCIM PATCH request failed: user not found.`

**Cause:** The provisioning system is sending requests for a user whose account has been deleted from NetSecure IAM.

**Resolution:** Check whether the user exists in NetSecure IAM. If the account was deleted, re-provision the user or clear the external ID mapping in the source system.

---

## General Troubleshooting Tips

- Always check the **Audit Log** first. Most errors produce a detailed event log entry with the root cause.
- Use the **SSO Test** tool in the Admin Console before testing in a live browser session.
- When reporting an issue to support, include the **Event ID** from the audit log entry. This allows support to locate the full server-side trace.

!!! tip
    For production incidents, go to **Support → Open Ticket** and attach the audit log export for the relevant time window. This significantly reduces resolution time.
