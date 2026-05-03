# SSO Configuration

Single Sign-On (SSO) allows users to authenticate once with NetSecure IAM and access all connected applications without re-entering credentials.

## Prerequisites

Before configuring SSO, ensure you have:

- Administrator access to the NetSecure IAM Admin Console
- Administrator access to the application you want to connect
- The application's SP metadata URL or metadata XML file

## Supported SSO Protocols

=== "SAML 2.0"

    SAML 2.0 is recommended for enterprise applications. See [SAML 2.0 Setup](saml-setup.md) for detailed steps.

=== "OIDC"

    OpenID Connect is recommended for modern web and mobile applications. Configure under **Applications → Add Application → OIDC**.

=== "Legacy (Header-Based)"

    For applications that do not support SAML or OIDC, NetSecure IAM supports header-based SSO via the Access Gateway component.

## Adding an Application

1. In the Admin Console, go to **Applications → Add Application**.
2. Search for your application in the catalog, or select **Custom SAML App**.
3. Enter the application name and upload the SP metadata.
4. Map the required attributes (see [Attribute Mapping](#attribute-mapping) below).
5. Assign the application to the relevant roles or groups.
6. Click **Save and Activate**.

## Attribute Mapping

Most applications require specific user attributes in the SAML assertion. Common mappings:

| SAML Attribute | NetSecure IAM Source |
|---|---|
| `NameID` | `user.email` |
| `firstName` | `user.firstName` |
| `lastName` | `user.lastName` |
| `groups` | `user.groups` |
| `department` | `user.department` |

!!! note
    Attribute names are case-sensitive. Check your application's documentation for required attribute names.

## Testing SSO

After saving the configuration:

1. Open a private/incognito browser window.
2. Navigate to your application's login URL.
3. You should be redirected to the NetSecure IAM login page.
4. Log in with a test user account.
5. Verify that you are redirected back to the application and logged in successfully.

!!! tip
    Use the **SSO Test** button in the application settings to run a guided test without leaving the Admin Console.
