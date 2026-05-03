# RBAC Overview

Role-Based Access Control (RBAC) is the primary authorization model in NetSecure IAM. Access to resources is granted through roles, not directly to individual users.

## How RBAC Works

```
User → assigned to → Role → grants → Permissions → on → Resources
```

A user can hold multiple roles. Permissions are additive — a user with two roles gets the combined permissions of both.

## RBAC Components

**Role**
A named set of permissions. Roles represent job functions: `helpdesk-agent`, `app-owner`, `security-auditor`.

**Permission**
A specific action on a resource. Permissions follow the format `resource:action`. Examples:

| Permission | What it allows |
|---|---|
| `user:read` | View user profiles |
| `user:write` | Create and update users |
| `user:delete` | Delete users |
| `group:manage` | Create, modify, and delete groups |
| `report:export` | Export audit and compliance reports |
| `policy:write` | Create and modify access policies |

**Role Assignment**
The link between a user (or group) and a role. Assignments can include conditions such as time-based access or IP restrictions.

## Default Roles

NetSecure IAM includes the following built-in roles:

| Role | Description |
|---|---|
| `super-admin` | Full administrative access. Assign to primary admins only. |
| `user-admin` | Manage users and groups. Cannot modify security policies. |
| `helpdesk-agent` | Reset passwords and unlock accounts. Read-only user profiles. |
| `auditor` | Read-only access to audit logs and reports. |
| `app-admin` | Manage application configurations. No user management. |

!!! warning
    The `super-admin` role should be assigned to no more than two to three people. All `super-admin` sessions are logged and reviewed.

## Principle of Least Privilege

When designing roles, follow least privilege:

1. Start with the minimum permissions needed for the job function.
2. Do not create roles that combine unrelated responsibilities (for example, combining `user:delete` with `report:export`).
3. Review role assignments quarterly and remove unused access.
4. Use time-limited assignments for temporary elevated access rather than permanent role grants.
