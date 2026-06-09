# Creating Roles

This topic describes how to create and manage custom roles in IdentraCore IAM.
## Before You Begin

- You need the `policy:write` permission or the `super-admin` role.
- Plan your role design before creating roles. See [RBAC Overview](rbac-overview.md) for design guidance.

## Creating a Custom Role

1. In the Administration Console, go to **Authorization → Roles → Create Role**.
2. Enter a **Role Name**. Use lowercase with hyphens: `finance-read-only`, `vendor-portal-user`.
3. Enter a **Description** that explains the job function this role supports.
4. Under **Permissions**, select the permissions to include.
5. Optionally, set a **Session Duration** to limit how long a session is valid when this role is active.
6. Click **Save Role**.

## Assigning a Role to a User

```
Admin Console → Users → [User] → Roles → Add Role → Select role → Save
```

Or assign a role to an entire group:

```
Admin Console → Groups → [Group] → Roles → Add Role → Select role → Save
```

!!! tip
    Assign roles to groups rather than individual users wherever possible. Group-based assignments are easier to audit and maintain.

## Assigning a Temporary Role

For elevated access that should expire:

1. Go to **Users → [User] → Roles → Add Role**.
2. Select the role.
3. Enable **Set expiry** and choose an end date and time.
4. Click **Save**.

The role is automatically revoked at the specified time. An audit log entry is created at assignment and revocation.

## Cloning a Role

To create a role similar to an existing one:

```
Authorization → Roles → [Role] → Actions → Clone Role
```

Edit the cloned role's name, description, and permissions as needed.

## Deleting a Role

!!! warning
    Deleting a role immediately revokes access for all users assigned to it. This action cannot be undone.

Before deleting a role:
1. Go to **Authorization → Roles → [Role] → Assignments** to see affected users.
2. Reassign those users to an appropriate role.
3. Then go to **Actions → Delete Role**.
