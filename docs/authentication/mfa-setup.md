# MFA Setup

Multi-Factor Authentication (MFA) adds a second layer of verification after password authentication. IdentraCore IAM supports several MFA methods.

## Supported MFA Methods

| Method | Description | Recommended For |
| --- | --- | --- |
| **TOTP** | Time-based one-time passwords via authenticator apps (Google Authenticator, Authy) | Most users |
| **Push Notification** | Approve login via the IdentraCore mobile app | High-volume users |
| **Hardware Token (FIDO2)** | Physical security keys (YubiKey, etc.) | Privileged accounts |
| **SMS OTP** | One-time code via SMS | Fallback only — not recommended as primary |

!!! warning
    SMS OTP is susceptible to SIM-swapping attacks. Use TOTP or push notifications as the primary MFA method.

## Enabling MFA for a Policy

1. Go to **Security → Authentication Policies**.
2. Select the policy to modify, or click **Create Policy**.
3. Under **Authentication Requirements**, enable **Require MFA**.
4. Select the MFA methods users can enroll in.
5. Set the **MFA frequency** — for example, require MFA every login, or once per device per 30 days.
6. Click **Save**.

## Assigning the Policy

Attach the policy to a group, application, or individual user:

- **Group:** Security → Authentication Policies → [Policy] → Assign → Groups
- **Application:** Applications → [App] → Sign-On Policy → Select policy

## User Enrollment

On first login after MFA is enforced, users are prompted to enroll. The enrollment flow guides them through setting up their chosen MFA method.

To pre-enroll users or reset a user's MFA:

```text
Admin Console → Users → [User] → Security → MFA → Reset
```

!!! tip
    For privileged administrator accounts, set MFA frequency to **Every login** and restrict allowed methods to **FIDO2 only**.
