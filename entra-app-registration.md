# Entra App Registration Guide for SharePoint and Microsoft Graph APIs

This guide provides step-by-step instructions for registering an application in Microsoft Entra ID (formerly Azure AD) and configuring the required API permissions for the Volentis AI application to access SharePoint and Microsoft Graph.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Overview](#overview)
- [Step 1: Create App Registration](#step-1-create-app-registration)
- [Step 2: Configure API Permissions](#step-2-configure-api-permissions)
- [Step 3: Grant Admin Consent](#step-3-grant-admin-consent)
- [Step 4: Create Client Secret](#step-4-create-client-secret)
- [Step 5: Collect Configuration Values](#step-5-collect-configuration-values)
- [Step 6: Configure Volentis AI App](#step-6-configure-volentis-ai-app)
- [Required Permissions Summary](#required-permissions-summary)
- [Testing Your Configuration](#testing-your-configuration)
- [Troubleshooting](#troubleshooting)

## Prerequisites

- Access to Microsoft Entra admin center (formerly Azure Portal)
- Appropriate permissions to register applications (Application Administrator or Global Administrator role)
- A Microsoft 365 tenant with SharePoint Online
- Access to the Volentis AI application

## Overview

This guide will help you configure an Entra app registration with the following API permissions required for Volentis AI:

**Microsoft Graph API:**
- `Files.Read.All` - Read files in all site collections
- `User.Read` - Sign in and read user profile

**SharePoint API:**
- `MyFiles.Read` - Read user files
- `Sites.Read.All` - Read items in all site collections

---

## Step 1: Create App Registration

### 1.1 Navigate to Entra Admin Center

1. Go to [https://entra.microsoft.com](https://entra.microsoft.com) or [https://portal.azure.com](https://portal.azure.com)
2. Sign in with your administrator account


### 1.2 Access App Registrations

1. In the left navigation pane, select **Identity** → **Applications** → **App registrations**
2. Alternatively, search for "App registrations" in the top search bar


### 1.3 Create New Registration

1. Click the **+ New registration** button at the top of the page


### 1.4 Configure Registration Details

Fill in the application registration form:

**Name:**
- Enter: `Volentis AI Integration` (or your preferred name)

**Supported account types:**
- Select: `Accounts in this organizational directory only (Single tenant)`
- This is recommended for internal organizational apps

**Redirect URI:**
- Platform: Select `Web`
- URI: Enter the redirect URI provided by Volentis AI
- If you don't have this yet, you can leave it blank and add it later


### 1.5 Register the Application

1. Click the **Register** button at the bottom
2. Wait a few seconds for the app to be created
3. You'll be redirected to the app's Overview page


---

## Step 2: Configure API Permissions

### 2.1 Navigate to API Permissions

1. In your app registration, click **API permissions** from the left menu
2. You'll see "Microsoft Graph - User.Read" is already added by default


### 2.2 Add Microsoft Graph Permissions

#### Add Files.Read.All

1. Click **+ Add a permission**
2. Select **Microsoft Graph**
3. Choose **Application permissions**
4. In the search box, type "Files"
5. Expand the **Files** section
6. Check the box for **Files.Read.All**
7. Click **Add permissions** at the bottom


#### Verify User.Read

The `User.Read` permission should already be present. If not:
1. Click **+ Add a permission**
2. Select **Microsoft Graph** → **Delegated permissions**
3. Search for "User" and expand the **User** section
4. Check **User.Read**
5. Click **Add permissions**

### 2.3 Add SharePoint API Permissions

#### Add MyFiles.Read

1. Click **+ Add a permission**
2. Scroll down and select **SharePoint**
3. Choose **Delegated permissions**
4. In the search box, type "MyFiles"
5. Expand the **MyFiles** section
6. Check the box for **MyFiles.Read**
7. Click **Add permissions**


#### Add Sites.Read.All

1. Click **+ Add a permission** again
2. Select **SharePoint**
3. Choose **Application permissions**
4. In the search box, type "Sites"
5. Expand the **Sites** section
6. Check the box for **Sites.Read.All**
7. Click **Add permissions**


### 2.4 Review All Permissions

After adding all permissions, you should see:
- Microsoft Graph: User.Read
- Microsoft Graph: Files.Read.All
- SharePoint: MyFiles.Read
- SharePoint: Sites.Read.All


---

## Step 3: Grant Admin Consent

All the configured permissions require administrator consent before they can be used by the Volentis AI application.

### 3.1 Review Required Consent

1. On the **API permissions** page, look at the "Admin consent required" column
2. You'll see "Yes" for most permissions

### 3.2 Grant Admin Consent

1. Click the **✓ Grant admin consent for [Your Organization Name]** button
2. A confirmation dialog will appear listing all permissions
3. Review the permissions carefully
4. Click **Yes** to grant consent


### 3.3 Verify Consent Status

After granting consent:
1. Check that all permissions now show a green checkmark in the "Status" column
2. Status should display "Granted for [Your Organization]"


> ⚠️ **Important**: If you don't see the "Grant admin consent" button, you may not have sufficient permissions. Contact your Global Administrator or Application Administrator.

---

## Step 4: Create Client Secret

The Volentis AI application needs a client secret to authenticate with Microsoft's identity platform.

### 4.1 Navigate to Certificates & Secrets

1. In your app registration, click **Certificates & secrets** from the left menu
2. Select the **Client secrets** tab


### 4.2 Create New Client Secret

1. Click **+ New client secret**
2. In the dialog that appears:
   - **Description**: Enter a meaningful description (e.g., "Volentis AI Production Secret")
   - **Expires**: Select an expiration period
     - **Recommended**: 12 months (for production environments)
     - **Available options**: 6 months, 12 months, 24 months, or custom
3. Click **Add**


### 4.3 Copy the Secret Value

> ⚠️ **CRITICAL - READ CAREFULLY**: This is the most important step!

1. After creating the secret, you'll see two values:
   - **Secret ID**: This is NOT what you need
   - **Value**: This is your actual secret - **COPY THIS IMMEDIATELY**

2. Click the copy icon next to the **Value** field (NOT the Secret ID)
3. Paste it immediately into a secure location


> 🔒 **SECURITY WARNING**: 
> - The secret value is shown **ONLY ONCE**
> - You **CANNOT** retrieve it later
> - If you lose it, you must create a new secret
> - Never share this secret or commit it to source control
> - Store it in a secure password manager or Azure Key Vault

---

## Step 5: Collect Configuration Values

You need three specific values to configure the Volentis AI application. Let's collect them now.

### 5.1 Navigate to Overview Page

1. Click **Overview** in the left menu of your app registration


### 5.2 Locate and Copy Application (Client) ID

1. Find the **Application (client) ID** field (it's a GUID format like: `12345678-1234-1234-1234-123456789abc`)
2. Click the copy icon next to it
3. Save this value - label it as **Client ID**


**What is the Client ID?**
- This is a unique identifier for your application
- It's public and can be safely shared
- Volentis AI uses this to identify your registered application

### 5.3 Locate and Copy Directory (Tenant) ID

1. Find the **Directory (tenant) ID** field (also a GUID format)
2. Click the copy icon next to it
3. Save this value - label it as **Tenant ID**


**What is the Tenant ID?**
- This identifies your Microsoft 365 organization
- It's also public information
- Volentis AI needs this to authenticate against your tenant

### 5.4 Organize Your Configuration Values

Create a secure note with all three values:

```
=== Volentis AI Configuration Values ===

Tenant ID: [Paste your Directory (tenant) ID here]
Client ID: [Paste your Application (client) ID here]
Client Secret: [Paste your secret Value here]

Created: [Current date]
Expires: [Secret expiration date]
```

> 🔐 **Security Checklist**:
> - ✅ Store this information in a secure password manager
> - ✅ Limit access to authorized personnel only
> - ✅ Never commit these values to Git or version control
> - ✅ Set a calendar reminder for when the secret expires
> - ✅ Document who has access to these credentials


---

## Step 6: Configure Volentis AI App

Now that you have all the required values, you can configure the Volentis AI application.

### 6.1 Access Volentis AI Configuration

1. Log into the Volentis AI application
2. Navigate to **Settings** or **Configuration** section
3. Look for **Microsoft Integration** or **SharePoint Connection** settings


### 6.2 Enter Configuration Values

Enter the three values you collected:

1. **Tenant ID**: Paste the Directory (tenant) ID
2. **Client ID**: Paste the Application (client) ID
3. **Client Secret**: Paste the secret Value


### 6.3 Test the Connection

1. Click **Test Connection** or **Verify** button (if available)
2. You should see a success message confirming:
   - Authentication is working
   - Permissions are correctly configured
   - Access to SharePoint and Graph API is established


### 6.4 Save Configuration

1. Click **Save** or **Apply** to persist your settings
2. The Volentis AI application is now connected to your Microsoft 365 tenant!

---

## Required Permissions Summary

| API | Permission | Type | Purpose for Volentis AI |
|-----|-----------|------|-------------------------|
| Microsoft Graph | `User.Read` | Delegated | Authenticate users and read their profile information |
| Microsoft Graph | `Files.Read.All` | Delegated | Access and analyze files across SharePoint and OneDrive |
| SharePoint | `MyFiles.Read` | Delegated | Read the signed-in user's files in OneDrive for Business |
| SharePoint | `Sites.Read.All` | Delegated | Access content across all SharePoint sites |

### Permission Types Explained

- **Delegated Permissions**: The app acts on behalf of a signed-in user. The app can only access resources that the user has access to.
- **Application Permissions**: The app acts as itself without a signed-in user (not used in this configuration).

---

## Testing Your Configuration

### Test 1: Verify Authentication

1. Log out and log back into Volentis AI
2. You should be able to authenticate successfully
3. No permission errors should appear

### Test 2: Access SharePoint Content

1. Try to access or view SharePoint files through Volentis AI
2. Verify that you can see available sites and documents
3. Test any AI features that depend on document access

### Test 3: Check User Profile

1. Verify that your user profile information displays correctly
2. Check that user-specific features are working

### Test with Microsoft Graph Explorer (Optional)

For advanced testing, you can use Microsoft Graph Explorer:

1. Go to [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)
2. Sign in with your account
3. Try these sample queries:
   ```
   GET https://graph.microsoft.com/v1.0/me
   GET https://graph.microsoft.com/v1.0/me/drive/root/children
   GET https://graph.microsoft.com/v1.0/sites
   ```


---

## Troubleshooting

### Issue 1: "Admin Consent Required" Error

**Symptom**: Users see an error message about needing admin consent

**Solution**:
1. Go back to the Entra portal
2. Navigate to your app → API permissions
3. Verify that all permissions show "Granted" status with green checkmarks
4. If not, click "Grant admin consent" again
5. Wait 5-10 minutes for changes to propagate

### Issue 2: "Invalid Client" Error

**Symptom**: Authentication fails with "invalid_client" error

**Solution**:
1. Verify your **Client ID** is correct (from Overview page)
2. Verify your **Client Secret** is correct (the Value, not Secret ID)
3. Check if the secret has expired - create a new one if needed
4. Ensure there are no extra spaces when copying values

### Issue 3: "Insufficient Privileges" Error

**Symptom**: API calls fail with insufficient privileges

**Solution**:
1. Verify all four permissions are granted:
   - User.Read
   - Files.Read.All
   - MyFiles.Read
   - Sites.Read.All
2. Ensure the signed-in user has access to the SharePoint resources
3. Check that the user's account is not restricted by Conditional Access policies

### Issue 4: Cannot See "Grant Admin Consent" Button

**Symptom**: The button to grant admin consent is missing

**Solution**:
1. You need Application Administrator or Global Administrator role
2. Contact your IT administrator to grant consent
3. Alternatively, they can assign you the necessary role temporarily

### Issue 5: Secret Value Not Showing

**Symptom**: Cannot see or copy the client secret value

**Solution**:
1. If you just created it and navigated away, the value is lost
2. Delete the old secret
3. Create a new client secret
4. Copy the Value immediately this time
5. Store it securely before navigating away

### Issue 6: "AADSTS65001: User Consent Not Granted"

**Symptom**: Error code AADSTS65001 appears

**Solution**:
1. Admin consent must be granted (not just user consent)
2. Go to API permissions page
3. Click "Grant admin consent for [organization]"
4. Wait a few minutes for propagation

### Issue 7: Configuration Values Not Working in Volentis AI

**Symptom**: Volentis AI reports connection failure

**Solution**:
1. Double-check you copied the correct values:
   - **Tenant ID** from "Directory (tenant) ID"
   - **Client ID** from "Application (client) ID"
   - **Client Secret** from "Value" (not "Secret ID")
2. Check for extra spaces or missing characters
3. Verify the secret hasn't expired
4. Try generating a new client secret

---

## Security Best Practices

### 1. Secret Management
- ✅ Store client secrets in Azure Key Vault or a secure password manager
- ✅ Never commit secrets to Git repositories
- ✅ Use environment variables for secrets in applications
- ✅ Limit who has access to the secret values

### 2. Regular Secret Rotation
- ✅ Set calendar reminders before secret expiration
- ✅ Rotate secrets at least annually
- ✅ Have a documented process for secret rotation
- ✅ Create overlap periods when rotating (create new before deleting old)

### 3. Principle of Least Privilege
- ✅ Only grant permissions that are actually needed
- ✅ Review and audit permissions regularly
- ✅ Remove unused app registrations
- ✅ Document why each permission is required

### 4. Monitoring and Auditing
- ✅ Enable audit logging for the app registration
- ✅ Monitor sign-in logs for suspicious activity
- ✅ Review application permissions quarterly
- ✅ Set up alerts for authentication failures

### 5. Access Control
- ✅ Limit who can modify the app registration
- ✅ Use Azure AD groups for permission management
- ✅ Implement Conditional Access policies if needed
- ✅ Document who has admin access to the app

---

## Additional Resources

### Microsoft Documentation
- [Microsoft identity platform documentation](https://learn.microsoft.com/azure/active-directory/develop/)
- [Microsoft Graph API documentation](https://learn.microsoft.com/graph/)
- [SharePoint REST API documentation](https://learn.microsoft.com/sharepoint/dev/sp-add-ins/get-to-know-the-sharepoint-rest-service)
- [App registration best practices](https://learn.microsoft.com/azure/active-directory/develop/security-best-practices-for-app-registration)

### Support Channels
- **Microsoft Q&A**: [https://learn.microsoft.com/answers/](https://learn.microsoft.com/answers/)
- **Volentis AI Support**: [Contact your Volentis AI support team]
- **Your IT Department**: Contact your internal IT or security team for assistance

---

## Frequently Asked Questions

### Q: How long does it take for permissions to take effect?
**A**: Usually 5-10 minutes, but can take up to an hour in some cases. If issues persist, try clearing your browser cache.

### Q: Can I use the same app registration for multiple environments?
**A**: It's recommended to create separate app registrations for development, staging, and production environments.

### Q: What happens when the client secret expires?
**A**: The Volentis AI application will stop working. You must create a new secret and update the configuration before expiration.

### Q: Can regular users grant these permissions?
**A**: No, these permissions require administrator consent. Only Global Administrators or Application Administrators can grant them.

### Q: Do I need to reconfigure if I change my Microsoft 365 password?
**A**: No, the app registration uses the client secret, not user passwords. It will continue to work after password changes.

### Q: Can I revoke access later?
**A**: Yes, you can delete the app registration or remove granted permissions at any time from the Entra portal.

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | November 25, 2025 | Initial documentation created |

---

## Need Help?

If you encounter issues not covered in this guide:

1. Check the [Troubleshooting](#troubleshooting) section
2. Review the Microsoft documentation links
3. Contact your IT administrator for tenant-specific issues
4. Reach out to Volentis AI support for application-specific problems

---

**Document Maintained By**: [Your Organization Name]  
**Last Reviewed**: November 25, 2025  
**Next Review Date**: February 25, 2026
