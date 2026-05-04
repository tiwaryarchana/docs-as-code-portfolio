# Audit Logs

IdentraCore IAM records all authentication events, administrative actions, and policy changes. Audit logs are retained for 12 months by default and can be exported for long-term storage.

## What Is Logged

| Event Category | Examples |
|---|---|
| **Authentication** | Login success, login failure, MFA challenge, session timeout |
| **User Management** | User created, password reset, account suspended, role assigned |
| **Application** | Application added, SSO configuration changed, attribute mapping updated |
| **Policy** | Policy created, policy modified, policy evaluation result |
| **Administrative** | Admin login, configuration export, API key created |

## Viewing Audit Logs

1. Go to **Reports → Audit Log**.
2. Use filters to narrow results:
   - **Date range**
   - **Event type**
   - **User** (the user the event relates to)
   - **Actor** (the administrator who performed the action)
   - **Outcome** (Success / Failure)
3. Click any row to view the full event detail, including the IP address, user agent, and raw event payload.

## Searching Logs

Use the search bar to find events by keyword. Example searches:

```
user:jsmith@example.com
event:login_failure
actor:admin@example.com
app:Salesforce
```

## Exporting Logs

To export for SIEM or compliance:

```
Reports → Audit Log → Export → Select format (CSV or JSON) → Download
```

For automated export, configure a **Log Streaming** integration under **Settings → Integrations → SIEM**. Supported targets include Splunk, Microsoft Sentinel, and generic syslog.

## Compliance Reports

Pre-built compliance reports are available under **Reports → Compliance**:

| Report | Description |
|---|---|
| **Privileged Access Review** | All users with admin-level roles |
| **Failed Login Summary** | Repeated authentication failures by user and IP |
| **Role Change History** | All role assignments and revocations over a period |
| **Dormant Accounts** | Active accounts with no login in 90+ days |

!!! note
    Compliance reports can be scheduled for automatic delivery to a distribution list. Go to **Reports → Compliance → [Report] → Schedule**.
