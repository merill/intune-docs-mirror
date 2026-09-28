---
layout: Conceptual
title: Manually register Microsoft Entra apps - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/manually-register-azure-ad-apps
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Manually create the required apps in Microsoft Entra ID to integrate the Configuration Manager site to support the cloud management gateway (CMG).
ms.date: 2026-08-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: e5da6c8b-447a-d0c7-4243-095745d85306
document_version_independent_id: 64b13b3d-22b4-2f04-0a7d-7d34a7b62395
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/manually-register-azure-ad-apps.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/manually-register-azure-ad-apps
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/manually-register-azure-ad-apps.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 1eef292d-9011-cfcd-2874-10339210b966
---

# Manually register Microsoft Entra apps - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The [second primary step](configure-azure-ad) to set up a cloud management gateway (CMG) is to integrate the Configuration Manager site with your Microsoft Entra tenant. This integration allows the site to authenticate with Microsoft Entra ID, which it uses to deploy and monitor the CMG service. If you can't use Configuration Manager to automate the creation of the apps during the Azure Service Wizard, you can use the wizard to import a previously created app. For example, if your Azure administrators require that they manually create all Microsoft Entra app registrations, then use this process.

Tip

This article provides prescriptive guidance to integrate the site specifically for the cloud management gateway. For more information on this process and other uses of the **Azure Services** node in the Configuration Manager console, see [Configure Azure services](../../../servers/deploy/configure/azure-services-wizard).

When you integrate the site, you create app registrations in Microsoft Entra ID. The CMG requires two app registrations:

- **Web app** (also referred to as a *server* app in Configuration Manager)
- **Native app** (also referred to as a *client* app in Configuration Manager)

There are two methods to create these apps, both of which require a **Global Administrator** role in Microsoft Entra ID:

- Use Configuration Manager to automate the creation of the apps when you integrate the site.
- Manually create the apps in advance, and then import them when you integrate the site.

This article provides the specific details for the second method. Pair these instructions with the procedures in the [Configure Microsoft Entra ID for CMG](configure-azure-ad) article to complete the process.

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../../understand/fundamentals-of-role-based-administration).

## Get tenant details

Tip

During this process, you'll need to note several values to use later. Open an app like Windows Notepad to paste in the values that you'll copy from the Azure Portal.

First, you need to make note of the **Microsoft Entra tenant name** and **tenant ID**. These values are the first two pieces of information that you need to import the app registrations in Configuration Manager.

1. In the [Azure portal](https://portal.azure.com/), select **Microsoft Entra ID**.
2. In the Microsoft Entra ID menu, select **Custom domain names**.
3. Note the tenant name. For example, `contoso.onmicrosoft.com`.
4. In the Microsoft Entra ID menu, select **Properties**.
5. Copy the **Tenant ID** GUID value.

## Register the web (server) app

1. In the Microsoft Entra ID menu, select **App registrations**. Select **New registration** to create a new app.
2. In the *Register an application* pane, specify the following information:

    - **Name**: A friendly name for the app. For example, `CMG-ServerApp`.
    - **Supported account types**: Leave this setting as the default option, **Accounts in this organizational directory only**.
    - **Redirect URI**: Select: **Web** and type **http://localhost** as URI
3. Select **Register** to create the app.
4. In the properties of the new app, copy the following values:

    - **Display name**: This value is the friendly name for this app registration that you'll use later as the *application name*.
    - **Application (client) ID**: You'll use this GUID value later as the *client ID*.
5. In the menu of the app properties, select **Certificates & secrets**, then select **New client secret**.

    - **Description**: You can use any name for the secret or leave it blank.
    - **Expires**: Select either **12 months** or **24 months**.

    Select **Add**. Immediately copy the client secret string **Value** and **Expires**. If you leave this pane, you can't retrieve the same secret again. You'll use these values later as the *secret key* and *secret key expiry* values.
6. If you're going to use Microsoft Entra user Discovery in Configuration Manager, you need to adjust the permissions on this app. In the menu of the app properties, select **API permissions**. By default it should have the **User.Read** permission for the **Microsoft Graph** API, which needs to change.

    1. Select **Microsoft Graph** to enumerate the list of available API permissions, then select **Application permissions**.
    2. Expand **Directory**, and then select **Directory.Read.All**.
    3. Switch to **Delegated permissions**.
    4. Expand **User**, and remove the **User.Read** permission.
    5. Select **Update permissions**.
    6. On the API permissions pane, select **Grant admin consent for...**, then select **Yes**.
7. In the menu of the app properties, select **Expose an API**.

    1. For the Application ID URI, select **Add**. Specify a URI that's unique for the tenant. You'll use this value later as the *App ID URI*. Use one of the following recommended formats:

        - `api://{tenantId}/{string}`, for example, `api://aaaabbbb-0000-cccc-1111-dddd2222eeee/ConfigMgrService`
        - `https://{verifiedCustomerDomain}/{string}`, for example, `https://contoso.onmicrosoft.com/ConfigMgrService`

        Select **Save**.
    2. Select **Add a scope**, and specify the following required information:

        - **Scope name**: `user_impersonation`
        - **Who can consent**: Select **Admins and users**
        - **Admin consent display name**: Specify a meaningful name. For example, `Access CMG-ServerApp`
        - **Admin consent description**: Specify a meaningful description. For example, `Allow the application to access CMG-ServerApp on behalf of the signed-in user.`
    3. Select **Add scope** to save.

The web (server) app for CMG is now registered in Microsoft Entra ID.

## Register the native (client) app

1. In the Microsoft Entra ID menu, select **App registrations**. Select **New registration** to create a new app.
2. In the *Register an application* pane, specify the following information:

    - **Name**: A friendly name for the app. For example, `CMG-ClientApp`.
    - **Supported account types**: Leave this setting as the default option, **Accounts in this organizational directory only**.
    - **Redirect URI**: Leave this optional value blank.
3. Select **Register** to create the app.
4. In the properties of the new app, copy the following values:

    - **Display name**: This value is the friendly name for this app registration that you'll use later as the *application name*.
    - **Application (client) ID**: You'll use this GUID value later as the *client ID*.
5. In the menu of the app properties, select **Authentication**.

    1. Under Platform configurations, select **Add a platform**.

        1. In the Configure platforms pane, select **Mobile and desktop applications**.
        2. In the **Configure Desktop + devices** pane, under Custom redirect URIs, specify `ms-appx-web://Microsoft.AAD.BrokerPlugin/<ClientID>`. Use the app's client ID GUID, for example: `ms-appx-web://Microsoft.AAD.BrokerPlugin/00001111-aaaa-2222-bbbb-3333cccc4444`.
        3. Select **Configure**.
    2. Under Advanced settings, set **Allow public client flows** to **Yes**. Select **Save**.
6. Adjust the permissions on this app. In the menu of the app properties, select **API permissions**. By default it should have the **User.Read** delegated permission for the **Microsoft Graph** API.

    1. On the API permissions pane, select **Add a permission**.
    2. Switch to the **My APIs** tab, and select your web (server) app. For example, **CMG-ServerApp**. Select the **user\_impersonation** permission, and then select **Add permissions** to save.
    3. On the API permissions pane, select **Grant admin consent for...**, and then select **Yes**.

The native (client) app for CMG is now registered in Microsoft Entra ID. This step also concludes the process in the Azure portal. The role of the Microsoft Entra Global Administrator is done.

## Import the apps to Configuration Manager

After you manually register the two apps in the Azure portal, use the process in the article to [Configure Microsoft Entra ID for CMG](configure-azure-ad#start-the-azure-services-wizard), but select the option to **Import** each of the apps.

These processes import metadata about the Microsoft Entra apps into Configuration Manager. You don't require any Microsoft Entra permissions to import these apps.

### Import web (server) app

When you select **Import** from the *Server app* window, it opens the *Import apps* window. Enter the following information about the Microsoft Entra web app that's already registered in the Azure portal:

- **Microsoft Entra tenant Name**: The name of your Microsoft Entra tenant.
- **Microsoft Entra tenant ID**: The GUID of your Microsoft Entra tenant.
- **Application Name**: A friendly name for the app, the display name in the app registration.
- **Client ID**: The **Application (client) ID** value of the app registration. The format is a standard GUID.
- **Secret Key**: Copy the secret key when you register the app in Microsoft Entra ID and create the secret key.
- **Secret Key Expiry**: Specify the same date as from the Azure portal.
- **App ID URI**: The value is the **Application ID URI** of the app registration entry in the Microsoft Entra admin center. The format is similar to `https://contoso.onmicrosoft.com/ConfigMgrService`.

After entering the information, select **Verify**. Then select **OK** to close the *Import apps* window.

Important

When you use an imported Microsoft Entra app, you aren't notified of an upcoming expiration date from [console notifications](../../../servers/manage/admin-console-notifications). 

### Import native (client) app

When you select **Import** from the *Client app* window, it opens the *Import apps* window. Enter the following information about the Microsoft Entra native app that's already registered in the Azure portal:

- The wizard autopopulates the Microsoft Entra tenant name and tenant ID based on the web (server) app that you already specified.
- **Application Name**: A friendly name for the app.
- **Client ID**: The **Application (client) ID** value of the app registration. The format is a standard GUID.

After entering the information, select **Verify**. Then select **OK** to close the *Import apps* window.