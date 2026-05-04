# Managing Policies

Access policies define the conditions under which users can access resources. Policies are evaluated at runtime for every access request.

## Policy Types

| Policy Type | Purpose |
|---|---|
| **Authentication Policy** | Controls how users must authenticate (password strength, MFA requirements) |
| **Authorization Policy** | Controls which roles can access which resources |
| **Session Policy** | Controls session duration, idle timeout, and re-authentication requirements |
| **Network Policy** | Restricts access based on IP address or geographic location |

## Creating an Authorization Policy

1. Go to **Authorization → Policies → Create Policy**.
2. Enter a **Policy Name**.
3. Under **Conditions**, define when the policy applies. Examples:
   - User is a member of group `contractors`
   - Request comes from outside the corporate IP range
   - Time is outside 09:00–18:00 IST
4. Under **Effect**, choose **Allow** or **Deny**.
5. Under **Applies To**, select the roles or applications this policy governs.
6. Click **Save Policy**.

## Policy Evaluation Order

When multiple policies apply to a request, IdentraCore IAM evaluates them in this order:

1. **Explicit Deny** — any policy with a Deny effect takes precedence.
2. **Explicit Allow** — if no Deny applies, an Allow grants access.
3. **Default Deny** — if no policy explicitly allows the request, access is denied.

!!! note
    This means you cannot override a Deny with an Allow. If a user is denied by one policy, they are denied regardless of other Allow policies.

## Network-Based Restrictions

To block access from outside the corporate network:

```yaml
Policy Name:  corporate-network-only
Condition:    source_ip NOT IN [203.0.113.0/24, 10.0.0.0/8]
Effect:       Deny
Applies To:   All applications tagged "internal"
```

## Testing a Policy

Before activating a policy, use the **Policy Simulator**:

```
Authorization → Policies → [Policy] → Simulate
```

Enter a test user and resource. The simulator shows whether access would be allowed or denied, and which rule triggered the outcome.

!!! tip
    Always test Deny policies with at least one user who should be allowed and one who should be denied before activating in production.
