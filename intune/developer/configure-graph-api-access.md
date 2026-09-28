---
layout: Conceptual
title: How to Use Microsoft Entra ID to Access Intune APIs in Microsoft Graph - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/configure-graph-api-access
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.subservice: developer
description: Describes steps needed for apps to use Microsoft Entra ID to access the Intune APIs in Microsoft Graph.
ms.date: 2025-07-31T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: jamiesil
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: b6b56079-01be-cfe6-bad2-092cadd90ca8
document_version_independent_id: b6b56079-01be-cfe6-bad2-092cadd90ca8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/configure-graph-api-access.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/configure-graph-api-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/configure-graph-api-access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5fc61396-d075-4560-aece-fdbda73d243f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/ad9437c1-8cda-4537-ad69-b4b263652e13
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: b5d40ced-e7ff-c60d-854c-0a6c5535066e
---

# How to Use Microsoft Entra ID to Access Intune APIs in Microsoft Graph - Microsoft Intune | Microsoft Learn

The [Microsoft Graph API](https://developer.microsoft.com/graph/) now supports Microsoft Intune with specific APIs and permission roles. The Microsoft Graph API uses Microsoft Entra ID for authentication and access control. Access to the Intune APIs in Microsoft Graph requires:

- An application ID with:

    - Permission to call Microsoft Entra ID and the Microsoft Graph APIs.
    - Permission scopes relevant to the specific application tasks.
- User credentials with:

    - Permission to access the Microsoft Entra tenant associated with the application.
    - Role permissions required to support the application permission scopes.
- The end user to grant permission to the app to perform applications tasks for their Azure tenant.

This article:

- Shows how to register an application with access to the Microsoft Graph API and relevant permission roles.
- Describes the Intune API permission roles.
- Provides Intune API authentication examples for C# and PowerShell.
- Describes how to support multiple tenants.

To learn more, see:

- [Authorize access to web applications using OAuth 2.0 and Microsoft Entra ID](/en-us/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Getting start with Microsoft Entra authentication](/en-us/azure/devops/integrate/get-started/authentication/oauth)
- [Integrating applications with Microsoft Entra ID](/en-us/azure/active-directory/develop/active-directory-integrating-applications)
- [Understand OAuth 2.0](https://oauth.net/2/)

## Register apps to use the Microsoft Graph API

To register an app to use Microsoft Graph API:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using administrative credentials.

    As appropriate, you may use:

    - The tenant admin account.
    - A tenant user account with the **Users can register applications** setting enabled.
2. In the admin center, expand **Identity** &gt; **Applications**, and then select **App registrations**.

    ![Screenshot of Entra admin center app registrations menu location.](media/configure-graph-api-access/entra-app-reg.png)
3. Either choose **New registration** to create a new application or choose an existing application. (If you choose an existing application, skip the next step.)
4. In the **Register an application** pane, specify the following:

    - A **Name** for the application (displayed when users sign in).
    - The **Supported account type**.
    - A **Redirect URI** value. *This value is optional.*

        Note

        Azure AD Graph API is in its retirement phase. For more information, see [Update your applications to use Microsoft Authentication Library (MSAL) and Microsoft Graph API](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/update-your-applications-to-use-microsoft-authentication-library/ba-p/1257363).

        ![Screenshot of the new app properties and value page.](media/configure-graph-api-access/entra-add-new-app.png)

        To learn more, see [Authentication Scenarios for Microsoft Entra ID](/en-us/azure/active-directory/develop/active-directory-authentication-scenarios).
5. Select **Register** to add your new application.

    By selecting *Register*, you agree to the [Microsoft Platform Policies](https://go.microsoft.com/fwlink/?linkid=2090497&amp;clcid=0x409).
6. From the application pane for your app:

    1. Note the **Application (client) ID** value.
    2. Then, from the navigation menu, select **API permissions**.
7. From the **API permissions** pane:

    1. Select **Add a permission**, and then on the **Microsoft APIs** tab, select the **Microsoft Graph** tile.
    2. Select the **Application permissions** option to show all of the available permissions, and then select the type of permissions your application requires.
    3. Choose the roles required for your app by placing a checkmark to the left of the relevant names. To learn about specific Intune permission scopes, see Intune permission scopes. To learn about other Graph API permission scopes, see [Microsoft Graph permissions reference](/en-us/graph/permissions-reference).

    For best results, choose the fewest roles needed to implement your application.

### Data warehouse and reporting permissions

When you add an application through the Microsoft Entra admin center, you can choose the Intune API permissions based on the requirements of your application.

- **get\_data\_warehouse** - Use this API permission to grant access to the Intune data warehouse API from Microsoft Intune. For more information, see [Using the Microsoft Intune Data Warehouse](data-warehouse/create-reports).

### Partner solution APIs

The following Intune API permissions are available when adding an application through the Microsoft Entra admin center:

- **get\_device\_compliance** - This API permission is used to get device state and compliance information from Microsoft Intune. This API permission is used by Network Access Control partners. For more information, see [Network Access Control integration with Intune](../device-security/integrate-network-access-control).
- **manage\_partner\_compliance\_policy** - This API permission is used to manage partner compliance policies with Microsoft Intune. This API permission allows the app to send partner compliance policies and its Microsoft Entra group assignment to Microsoft Intune without a signed-in user. It is used by device compliance partners. For more information, see [Third party device compliance partners](../device-security/compliance/third-party-partners).
- **pfx\_cert\_provider** - This API permission is used to send PFX certificates to Intune for a specific user. Intune delivers the certificate to all devices enrolled by the user. For more information, see [PFX Import Powershell](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).
- **scep\_challenge\_provider** - This API permission is used to send SCEP challenges to Intune for certificate request validation. It is used by Certification Authority partners. For more information, see [Partner Certification Authority](../fundamentals/certificates/third-party-ca-scep).
- **update\_device\_attributes** - This API permission is used to send device information to Intune from device compliance and mobile threat defense partners. For more information, see [Mobile Threat Defense integration with Intune](../device-security/mobile-threat-defense/overview) and [Third party device compliance partners](../device-security/compliance/third-party-partners).
- **update\_device\_health** - This API permission is used to send device health and threat status information to Intune from mobile threat defense partners. For more information, see [Mobile Threat Defense integration with Intune](../device-security/mobile-threat-defense/overview).

If you are a partner interested in integrating with Intune using these API permissions, contact the [Microsoft Intelligent Security Association](https://www.microsoft.com/security/business/intelligent-security-association)] team for information.

When finished, choose **Add permissions** to save your changes.

At this point, you may also:

- Choose to grant permission for all tenant accounts to use the app without providing credentials.

    To do so, you can grant permissions and accept the confirmation prompt.

    When you run the application for the first time, you're prompted to grant the app permission to perform the selected roles.
- Make the app available to users outside your tenant. (This is typically only required for partners supporting multiple tenants/organizations.)

    To do so:

    1. Choose **Manifest** from the application pane.
    2. Change the value of the `availableToOtherTenants` setting to `true`.
    3. Save your changes.

## App listing

If you receive a large amount of data while requesting your app listing when using Graph API, you may encounter a 503 Service Unavailable error. We recommended that you try again with a smaller page size, such as 20 or fewer elements.

## Intune permission scopes

Microsoft Entra ID and Microsoft Graph use permission scopes to control access to corporate resources.

Permission scopes (also called the *OAuth scopes*) control access to specific Intune entities and their properties. This section summarizes the permission scopes for Intune API features.

To learn more:

- [Microsoft Entra authentication](/en-us/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Application permission scopes](/en-us/azure/active-directory/develop/active-directory-v2-scopes)

When you grant permission to Microsoft Graph, you can specify the following scopes to control access to Intune features: The following table summarizes the Intune API permission scopes. The first column shows the name of the feature as displayed in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and the second column provides the permission scope name.

| *Enable Access*setting | Scope name |
| --- | --- |
| **Perform user-impacting remote actions on Microsoft Intune devices** | DeviceManagementManagedDevices.PrivilegedOperations.All |
| **Read and write Microsoft Intune devices** | DeviceManagementManagedDevices.ReadWrite.All |
| **Read Microsoft Intune devices** | DeviceManagementManagedDevices.Read.All |
| **Read and write Microsoft Intune RBAC settings** | DeviceManagementRBAC.ReadWrite.All |
| **Read Microsoft Intune RBAC settings** | DeviceManagementRBAC.Read.All |
| **Read Microsoft Intune scripts** | DeviceManagementScripts.Read.All |
| **Read and write Microsoft Intune scripts** | DeviceManagementScripts.ReadWrite.All |
| **Read and write Microsoft Intune apps** | DeviceManagementApps.ReadWrite.All |
| **Read Microsoft Intune apps** | DeviceManagementApps.Read.All |
| **Read and write Microsoft Intune Device Configuration and Policies** | DeviceManagementConfiguration.ReadWrite.All |
| **Read Microsoft Intune Device Configuration and Policies** | DeviceManagementConfiguration.Read.All |
| **Read and write Microsoft Intune configuration** | DeviceManagementServiceConfig.ReadWrite.All |
| **Read Microsoft Intune configuration** | DeviceManagementServiceConfig.Read.All |

The table lists the settings as they appear in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). The following sections describe the scopes in alphabetical order.

At this time, all Intune permission scopes require administrator access. This means you need corresponding credentials when running apps or scripts that access Intune API resources.

### DeviceManagementApps.Read.All

- **Enable Access** setting: **Read Microsoft Intune apps**
- Permits read access to the following entity properties and status:

    - Client Apps
    - Mobile App Categories
    - App Protection Policies
    - App Configurations

### DeviceManagementApps.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune apps**
- Allows the same operations as **DeviceManagementApps.Read.All**
- Also permits changes to the following entities:

    - Client Apps
    - Mobile App Categories
    - App Protection Policies
    - App Configurations

### DeviceManagementConfiguration.Read.All

- **Enable Access** setting: **Read Microsoft Intune device configuration and policies**
- Permits read access to the following entity properties and status:

    - Device Configuration
    - Device Compliance Policy
    - Notification Messages

Note

As of July 31, 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.Read.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts

### DeviceManagementConfiguration.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune device configuration and policies**
- Allows the same operations as **DeviceManagementConfiguration.Read.All**
- Apps can also create, assign, delete, and change the following entities:

    - Device Configuration
    - Device Compliance Policy
    - Notification Messages

Note

As of July 31, 2025, Microsoft Graph replaced use of the *DeviceManagementConfiguration.ReadWrite.All* permission with *DeviceManagementScripts.ReadWrite.All* for the following API calls:

- ~/deviceManagement/deviceShellScripts
- ~/deviceManagement/deviceHealthScripts
- ~/deviceManagement/deviceComplianceScripts
- ~/deviceManagement/deviceCustomAttributeShellScripts
- ~/deviceManagement/deviceManagementScripts

### DeviceManagementManagedDevices.PrivilegedOperations.All

- **Enable Access** setting: **Perform user-impacting remote actions on Microsoft Intune devices**
- Permits the following remote actions on a managed device:

    - Retire
    - Wipe
    - Reset/Recover Passcode
    - Remote Lock
    - Enable/Disable Lost Mode
    - Clean PC
    - Reboot
    - Delete User from Shared Device

### DeviceManagementManagedDevices.Read.All

- **Enable Access** setting: **Read Microsoft Intune devices**
- Permits read access to the following entity properties and status:

    - Managed Device
    - Device Category
    - Detected App
    - Remote actions
    - Malware information

### DeviceManagementManagedDevices.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune devices**
- Allows the same operations as **DeviceManagementManagedDevices.Read.All**
- Apps can also create, delete, and change the following entities:

    - Managed Device
    - Device Category
- The following remote actions are also allowed:

    - Locate devices
    - Disable Activation Lock
    - Request remote assistance

### DeviceManagementRBAC.Read.All

- **Enable Access** setting: **Read Microsoft Intune RBAC settings**
- Permits read access to the following entity properties and status:

    - Role Assignments
    - Role Definitions
    - Resource Operations

### DeviceManagementRBAC.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune RBAC settings**
- Allows the same operations as **DeviceManagementRBAC.Read.All**
- Apps can also create, assign, delete, and change the following entities:

    - Role Assignments
    - Role Definitions

### DeviceManagementScripts.Read.All

- **Enable Access** setting: **Read Microsoft Intune scripts**
- Apps can view (read) a script, specifically:

    - Device Shell Scripts
    - Device Health Scripts
    - Device Compliance Scripts
    - Device Custom Attribute Shell Scripts
    - Device Management Scripts

### DeviceManagementScripts.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune scripts** Allows the same operations as *DeviceManagementScripts.Read.All*
- Apps can create, update or delete a script, specifically:

    - Device Shell Scripts
    - Device Health Scripts
    - Device Compliance Scripts
    - Device Custom Attribute Shell Scripts
    - Device Management Scripts

### DeviceManagementServiceConfig.Read.All

- **Enable Access** setting: **Read Microsoft Intune configuration**
- Permits read access to the following entity properties and status:

    - Device Enrollment
    - Apple Push Notification Certificate
    - Apple Device Enrollment Program
    - Apple Volume Purchase Program
    - Exchange Connector
    - Terms and Conditions
    - Cloud PKI
    - Branding
    - Mobile Threat Defense

### DeviceManagementServiceConfig.ReadWrite.All

- **Enable Access** setting: **Read and write Microsoft Intune configuration**
- Allows the same operations as DeviceManagementServiceConfig.Read.All\_
- Apps can also configure the following Intune features:

    - Device Enrollment
    - Apple Push Notification Certificate
    - Apple Device Enrollment Program
    - Apple Volume Purchase Program
    - Exchange Connector
    - Terms and Conditions
    - Cloud PKI
    - Branding
    - Mobile Threat Defense

## Microsoft Entra authentication examples

This section shows how to incorporate Microsoft Entra ID into your C# and PowerShell projects.

In each example, you'll need to specify an application ID that has at least the `DeviceManagementManagedDevices.Read.All` permission scope (discussed earlier).

When testing either example, you may receive HTTP status 403 (Forbidden) errors similar to the following:

```json
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

If this happens, verify that:

- You've updated the application ID to one authorized to use the Microsoft Graph API and the `DeviceManagementManagedDevices.Read.All` permission scope.
- Your tenant credentials support administrative functions.
- Your code is similar to the displayed samples.

### Authenticate Microsoft Entra ID in C#

This example shows how to use C# to retrieve a list of devices associated with your Intune account.

Note

Azure AD Graph API is in its retirement phase. For more information, see [Update your applications to use Microsoft Authentication Library (MSAL) and Microsoft Graph API](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/update-your-applications-to-use-microsoft-authentication-library/ba-p/1257363).

1. Start Visual Studio and then create a new Visual C# Console app (.NET Framework) project.
2. Enter a name for your project and provide other details as desired.
![Creating a C# console app project in Visual Studio](media/configure-graph-api-access/entra-auth-cpp-new-console.png)
3. Use the Solution Explorer to add the Microsoft MSAL NuGet package to the project:

    1. Right-click the Solution Explorer.
    2. Choose **Manage NuGet Packages…** &gt; **Browse**.
    3. Select `Microsoft.Identity.Client` and then choose **Install**.
4. Add the following statements to the top of **Program.cs**:

    ```csharp
    using Microsoft.Identity.Client;
    using System.Net.Http;
    ```
5. Add a method to create the authorization header:

    ```csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Remember to change the value of `application_ID` to match one granted at least the `DeviceManagementManagedDevices.Read.All` permission scope, as described earlier.
6. Add a method to retrieve the list of devices:

    ```csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```
7. Update **Main** to call **GetMyManagedDevices**:

    ```csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```
8. Compile and run your program.

When you first run your program, you should receive two prompts. The first requests your credentials and the second grants permissions for the `managedDevices` request.

For reference, here's the completed program:

```csharp
using Microsoft.Identity.Client;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### Authenticate Microsoft Entra ID using Microsoft Graph PowerShell

PowerShell scripts can use the Microsoft Graph PowerShell module for authentication. To learn more, see [Microsoft Graph PowerShell](/en-us/powershell/microsoftgraph/overview) and the [Intune PowerShell examples](https://github.com/microsoftgraph/powershell-intune-samples).

## Support multiple tenants and partners

If your organization supports organizations with their own Microsoft Entra tenants, you may want to permit your clients to use your application with their respective tenants.

To do so:

1. Verify that the client account exists in the target Microsoft Entra tenant.
2. Verify that your tenant account allows users to register applications (see **User settings**).
3. Establish a relationship between each tenant.

    To do so, either:

    a. Use the [Microsoft Partner Center](https://partnercenter.microsoft.com/) to define a relationship with your client and their email address.

    b. Invite the user to become a guest of your tenant.

To invite the user to be a guest of your tenant:

1. Choose **Add a guest user** from the **Quick tasks** panel.
2. Enter the client's email address and (optionally) add a personalized message for the invite.
3. Choose **Invite**.

This sends an invite to the user.

The user needs to choose the **Get Started** link to accept your invitation.

When the relationship is established (or your invitation has been accepted), add the user account to the **Directory role**.

Remember to add the user to other roles as needed. For example, to allow the user to manage Intune settings, they need to be at least an **Intune Service administrator**.

Also:

- Use https://admin.microsoft.com to assign an Intune license to your user account.
- Update application code to authenticate to the client's Microsoft Entra tenant domain, rather than your own.

    For example, suppose your tenant domain is `contosopartner.onmicrosoft.com` and your client's tenant domain is `northwind.onmicrosoft.com`, you would update your code to authenticate to your client's tenant.

    To do so in a C# application based on the earlier example, you'd change the value of the `authority` variable:

    ```csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    to

    ```csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```