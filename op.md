# Okta OAuth 2.0 – On-Behalf-Of (OBO) Flow Setup

This repository documents the complete setup for **OAuth 2.0 SSO / IDP authentication using Okta**, including an **On-Behalf-Of (OBO) token exchange flow**.

This setup is typically used when:
- A **frontend (SPA)** authenticates a user via Okta
- A **backend service** securely calls APIs **on behalf of the authenticated user**

---

## 1. Sign Up for Okta Free Trial

1. Go to [Okta Free Trial](https://www.okta.com/free-trial/workforce-identity/).
2. Provide the following details:
   - **First Name**
   - **Last Name**
   - **Work Email**
   - **Country/Region**
   - **Phone Number**
3. Click **Start Free Trial**.
4. You will receive an **activation email**.
   - Activate your account.
   - Set a password.
   - Complete **device setup** for verification.

You will now get a URL like:

```
https://{okta_org}-admin.okta.com/admin/getting-started
```

**Example:**

```
https://trial-8712265-admin.okta.com/admin/getting-started
```



---
## 1. Create OIDC Single-Page Application (Frontend)

This application handles **user login and SSO**.

### Steps

1. Go to **Admin Console → Applications → Applications**
2. Click **Create App Integration**
3. Select:
   - **Sign-in method:** OIDC – OpenID Connect
   - **Application type:** Single-Page Application
   
4. Click **Next**
 Configure Application Settings

- **App integration name:** `SPA WEB APPLICATION`
- **Grant types:**

  - [X] Authorization Code
  - [X] Refresh Token
- **Sign-in redirect URIs:**

  - Production: `https://yourdomain.com/your-chat-page/`
  - Testing: `http://localhost:8080/`
- **Sign-out redirect URIs:**

  - Production: `https://yourdomain.com/your-chat-page/`
  - Testing: `http://localhost:8080/`
- **Controlled access:** Allow everyone in your organization.
- **Uncheck:** *Enable immediate access with Federation Broker Mode*

Click **Save**.

➡️ After saving, copy the **Client ID**:

