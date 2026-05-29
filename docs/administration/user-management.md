# User Management

This topic describes how to create, modify, and deactivate user accounts in IdentraCore IAM.

## User Lifecycle

```
Provisioned → Active → Suspended → Deactivated → Deleted
```

| State | Description |
|---|---|
| **Provisioned** | Account created; awaiting first login or activation |
| **Active** | User can authenticate and access assigned resources |
| **Suspended** | Temporarily blocked from logging in; data retained |
| **Deactivated** | Access permanently revoked; retained for compliance |
| **Deleted** | Account and data removed after retention period |

## Creating a User

=== "Admin Console"

    1. Go to **Users → Create User**.
    2. Enter the user's first name, last name, and email address.
    3. Select the **User Type**: Employee, Contractor, or Service Account.
    4. Assign roles and groups.
    5. Choose the activation method:
       - **Send activation email** — user sets their own password
       - **Set temporary password** — admin sets a password the user must change on first login
    6. Click **Create User**.

=== "SCIM Provisioning"

    Users can be automatically provisioned from your HR system or directory via SCIM 2.0. See the SCIM Integration guide for setup instructions.

=== "CSV Import"

    For bulk user creation:

    ```
    Users → Import Users → Download Template → Fill in data → Upload CSV
    ```

    Required columns: `firstName`, `lastName`, `email`, `userType`

## Modifying a User

To update a user's profile, roles, or group membership:

```
Users → [User] → Edit
```

All changes are recorded in the audit log with the administrator's identity and timestamp.

## Suspending a User

Suspend a user to immediately block login without deleting the account. Use this when an employee is on extended leave or under investigation.

```
Users → [User] → Actions → Suspend User
```

To restore access: **Actions → Reactivate User**.

## Offboarding a User

When a user leaves the organization:

1. Go to **Users → [User] → Actions → Deactivate User**.
2. All active sessions are immediately terminated.
3. All role assignments are revoked.
4. The account is retained for 90 days (configurable) for audit purposes before deletion.

!!! warning
    Do not delete a user account immediately upon offboarding. Retain the account in Deactivated state to preserve audit trail and access history.

## A New Section