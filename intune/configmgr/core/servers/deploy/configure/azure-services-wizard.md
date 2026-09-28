---
layout: Conceptual
title: Configure Azure services - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/azure-services-wizard
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
description: Connect your Configuration Manager environment with Azure services for cloud management, Microsoft Store for Business, and Log Analytics.
ms.date: 2021-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 639e477d-6e9d-a7b1-7978-f7d0f0283fc6
document_version_independent_id: 60b40c21-741b-42f8-a3e5-5f5a86811f59
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/azure-services-wizard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/azure-services-wizard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/azure-services-wizard.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 03d0c9b1-a45d-24b9-3c46-85815bc034fc
---

# Configure Azure services - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the **Azure Services Wizard** to simplify the process of configuring the Azure cloud services you use with Configuration Manager. This wizard provides a common configuration experience by using Microsoft Entra web app registrations. These apps provide subscription and configuration details, and authenticate communications with Microsoft Entra ID. The app replaces entering this same information each time you set up a new Configuration Manager component or service with Azure.

## Available services

Configure the following Azure services using this wizard:

- **Cloud Management**: This service enables the site and clients to authenticate by using Microsoft Entra ID. This authentication enables other scenarios, such as:

    - [Install and assign Configuration Manager clients using Microsoft Entra ID for authentication](../../../clients/deploy/deploy-clients-cmg-azure)
    - [Configure Microsoft Entra user Discovery](configure-discovery-methods#azureaadisc)
    - [Configure Microsoft Entra user Group Discovery](configure-discovery-methods#bkmk_azuregroupdisco)
    - Support certain [cloud management gateway scenarios](../../../clients/manage/cmg/overview)
    - [App approval email notifications](../../../../apps/deploy-use/app-approval#bkmk_email-approve)

    Tip

    For more information specific to cloud management, see [Configure Microsoft Entra ID for cloud management gateway](../../../clients/manage/cmg/configure-azure-ad).
- **Administration Service Management**: When configuring Azure Services, for enhanced security you can select Administration Service Management option. Selecting this option allows administrators to segment their admin privileges between [cloud management](../../../clients/manage/cmg/overview) and [administration service](../../../../develop/adminservice/overview). By enabling this option, access is restricted to only administration service endpoints. Configuration Management clients will authenticate to the site using Microsoft Entra ID. *(version 2207 or later)*

    Note

    Only CMG VMSS customers can enable administrative service management option. This option is not applicable for classic CMG customers.

### Service details

The following table lists details about each of the services.

- **Tenants**: The number of service instances you can configure. Each instance must be a distinct Microsoft Entra tenant.
- **Clouds**: All services support the global Azure cloud, but not all services support private clouds, such as the Azure US Government cloud.
- **Web app**: Whether the service uses a Microsoft Entra app of type *Web app / API*, also referred to as a server app in Configuration Manager.
- **Native app**: Whether the service uses a Microsoft Entra app of type *Native*, also referred to as a client app in Configuration Manager.
- **Actions**: Whether you can import or create these apps in the Configuration Manager Azure Services Wizard.

| Service | Tenants | Clouds | Web app | Native app | Actions |
| --- | --- | --- | --- | --- | --- |
| Cloud management withMicrosoft Entra discovery | Multiple | Public, Private | ![Supported](media/green_check.png) | ![Supported](media/green_check.png) | Import, Create |

### About Microsoft Entra apps

Different Azure services require distinct configurations, which you make in the Azure portal. Additionally, the apps for each service can require separate permissions to Azure resources.

You can use a single app for more than one service. There's only one object to manage in Configuration Manager and Microsoft Entra ID. When the security key on the app expires, you only have to refresh one key.

When you create additional Azure services in the wizard, Configuration Manager is designed to reuse information that's common between services. This behavior helps you from needing to input the same information more than once.

For more information about the required app permissions and configurations for each service, see the relevant Configuration Manager article in Available services.

For more information about Azure apps, start with the following articles:

- [Authentication and authorization in Azure App Service](/en-us/azure/app-service/app-service-authentication-overview)
- [Web Apps overview](/en-us/azure/app-service-web/app-service-web-overview)
- [Basics of Registering an Application in Microsoft Entra ID](/en-us/azure/active-directory/develop/authentication-scenarios)
- [Register your application with your Microsoft Entra tenant](/en-us/azure/active-directory/active-directory-app-registration)

## Before you begin

After you decide the service to which you want to connect, refer to the table in Service details. This table provides information you need to complete the Azure Service Wizard. Have a discussion in advance with your Microsoft Entra administrator. Decide which of the following actions to take:

- Manually create the apps in advance in the Azure portal. Then import the app details into Configuration Manager.

    Tip

    For more information specific to cloud management, see [Manually register Microsoft Entra apps for the cloud management gateway](../../../clients/manage/cmg/manually-register-azure-ad-apps).
- Use Configuration Manager to directly create the apps in Microsoft Entra ID. To collect the necessary data from Microsoft Entra ID, review the information in the other sections of this article.

Some services require the Microsoft Entra apps to have specific permissions. Review the information for each service to determine any required permissions. For example, before you can import a web app, an Azure administrator must first create it in the [Azure portal](https://portal.azure.com).

When configuring the Log Analytics Connector, give your newly registered web app *contributor* permission on the resource group that contains the relevant workspace. This permission allows Configuration Manager to access that workspace. When assigning the permission, search for the name of the app registration in the **Add users** area of the Azure portal. This process is the same as when [providing Configuration Manager with permissions to Log Analytics](/en-us/azure/log-analytics/log-analytics-sccm#grant-configuration-manager-with-permissions-to-log-analytics). An Azure administrator must assign these permissions before you import the app into Configuration Manager.

## Start the Azure Services wizard

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Azure Services** node.
2. On the **Home** tab of the ribbon, in the **Azure Services** group, select **Configure Azure Services**.
3. On the **Azure Services** page of the Azure Services Wizard:

    1. Specify a **Name** for the object in Configuration Manager.
    2. Specify an optional **Description** to help you identify the service.
    3. Select the Azure service that you want to connect with Configuration Manager.
4. Select **Next** to continue to the Azure app properties page of the Azure Services Wizard.

## Azure app properties

On the **App** page of the Azure Services Wizard, first select the **Azure environment** from the list. Refer to the table in Service details for which environment is currently available to the service.

The rest of the App page varies depending upon the specific service. Refer to the table in Service details for which type of app the service uses, and which action you can use.

- If the app supports both import and creates actions, select **Browse**. This action opens the Server app dialog or the Client App dialog.
- If the app only supports the import action, select **Import**. This action opens the Import Apps dialog (server) or the Import Apps dialog (client).

After you specify the apps on this page, select **Next** to continue to the Configuration or Discovery page of the Azure Services Wizard.

### Web app

This app is the Microsoft Entra ID type *Web app / API*, also referred to as a server app in Configuration Manager.

#### Server app dialog

When you select **Browse** for the **Web app** on the App page of the Azure Services Wizard, it opens the Server app dialog. It displays a list that shows the following properties of any existing web apps:

- Tenant friendly name
- App friendly name
- Service Type

There are three actions you can take from the Server app dialog:

- To reuse an existing web app, select it from the list.
- Select **Import** to open the Import apps dialog.
- Select **Create** to open the Create Server Application dialog.

After you select, import or create a web app, select **OK** to close the Server app dialog. This action returns to the App page of the Azure Services Wizard.

#### Import apps dialog (server)

When you select **Import** from the Server app dialog or the App page of the Azure Services Wizard, it opens the Import apps dialog. This page lets you enter information about a Microsoft Entra web app that is already created in the Azure portal. It imports metadata about that web app into Configuration Manager. Specify the following information:

- **Microsoft Entra tenant Name**: The name of your Microsoft Entra tenant.
- **Microsoft Entra tenant ID**: The GUID of your Microsoft Entra tenant.
- **Application Name**: A friendly name for the app, the display name in the app registration.
- **Client ID**: The **Application (client) ID** value of the app registration. The format is a standard GUID.
- **Secret Key**: You have to copy the secret key when you register the app in Microsoft Entra ID.
- **Secret Key Expiry**: Select a future date from the calendar.
- **App ID URI**: This value needs to be unique in your Microsoft Entra tenant. It's in the access token used by the Configuration Manager client to request access to the service. The value is the **Application ID URI** of the app registration entry in the Microsoft Entra admin center.

After entering the information, select **Verify**. Then select **OK** to close the Import apps dialog. This action returns to either the App page of the Azure Services Wizard, or the Server app dialog.

Important

When you use an imported Microsoft Entra app, you aren't notified of an upcoming expiration date from [console notifications](../../manage/admin-console-notifications). 

#### Create Server Application dialog

When you select **Create** from the Server app dialog, it opens the Create Server Application dialog. This page automates the creation of a web app in Microsoft Entra ID. Specify the following information:

- **Application Name**: A friendly name for the app.
- **HomePage URL**: This value isn't used by Configuration Manager, but required by Microsoft Entra ID. By default this value is `https://ConfigMgrService`.
- **App ID URI**: This value needs to be unique in your Microsoft Entra tenant. It's in the access token used by the Configuration Manager client to request access to the service. By default this value is `https://ConfigMgrService`. Change the default to one of the following recommended formats:

    - `api://{tenantId}/{string}`, for example, `api://aaaabbbb-0000-cccc-1111-dddd2222eeee/ConfigMgrService`
    - `https://{verifiedCustomerDomain}/{string}`, for example, `https://contoso.onmicrosoft.com/ConfigMgrService`
- **Secret Key validity period**: choose either **1 year** or **2 years** from the drop-down list. One year is the default value.

    Note

    You may see an option for **Never**, but Microsoft Entra no longer supports it. If you previously selected this option, the expiration date is now set for 99 years from the date you created it.

Select **Sign in** to authenticate to Azure as an administrative user. These credentials aren't saved by Configuration Manager. This persona doesn't require permissions in Configuration Manager, and doesn't need to be the same account that runs the Azure Services Wizard. After successfully authenticating to Azure, the page shows the **Microsoft Entra tenant Name** for reference.

Select **OK** to create the web app in Microsoft Entra ID and close the Create Server Application dialog. This action returns to the Server app dialog.

Warning

If you have a Microsoft Entra Conditional Access policy defined and applies to **All Cloud apps** - you *must* exclude the Server Application from this policy. For more information on how to exclude specific apps, see [Microsoft Entra Conditional Access Documentation](/en-us/azure/active-directory/conditional-access/).

### Native Client app

This app is the Microsoft Entra ID type *Native*, also referred to as a client app in Configuration Manager.

#### Client App dialog

When you select **Browse** for the **Native Client app** on the App page of the Azure Services Wizard, it opens the Client App dialog. It displays a list that shows the following properties of any existing native apps:

- Tenant friendly name
- App friendly name
- Service Type

There are three actions you can take from the Client App dialog:

- To reuse an existing native app, select it from the list.
- Select **Import** to open the Import apps dialog.
- Select **Create** to open the Create Client Application dialog.

After you select, import or create a native app, choose **OK** to close the Client App dialog. This action returns to the App page of the Azure Services Wizard.

#### Import apps dialog (client)

When you select **Import** from the Client App dialog, it opens the Import apps dialog. This page lets you enter information about a Microsoft Entra native app that is already created in the Azure portal. It imports metadata about that native app into Configuration Manager. Specify the following information:

- **Application Name**: A friendly name for the app.
- **Client ID**: The **Application (client) ID** value of the app registration. The format is a standard GUID.

After entering the information, select **Verify**. Then select **OK** to close the Import apps dialog. This action returns to the Client App dialog.

Tip

When you register the app in Microsoft Entra ID, you may need to manually specify the following **Redirect URI**: `ms-appx-web://Microsoft.AAD.BrokerPlugin/<ClientID>`. Specify the app's client ID GUID, for example: `ms-appx-web://Microsoft.AAD.BrokerPlugin/00001111-aaaa-2222-bbbb-3333cccc4444`.

#### Create Client Application dialog

When you select **Create** from the Client App dialog, it opens the Create Client Application dialog. This page automates the creation of a native app in Microsoft Entra ID. Specify the following information:

- **Application Name**: A friendly name for the app.
- **Reply URL**: This value isn't used by Configuration Manager, but required by Microsoft Entra ID. By default this value is `https://ConfigMgrService`.

Select **Sign in** to authenticate to Azure as an administrative user. These credentials aren't saved by Configuration Manager. This persona doesn't require permissions in Configuration Manager, and doesn't need to be the same account that runs the Azure Services Wizard. After successfully authenticating to Azure, the page shows the **Microsoft Entra tenant Name** for reference.

Select **OK** to create the native app in Microsoft Entra ID and close the Create Client Application dialog. This action returns to the Client App dialog.

## Configuration or Discovery

After specifying the web and native apps on the **Apps** page, the Azure Services Wizard proceeds to either a **Configuration** or **Discovery** page, depending upon the service to which you're connecting. The details of this page vary from service to service. For more information, see the following:

- **Cloud Management** service, **Discovery** page: [Configure Microsoft Entra user Discovery](configure-discovery-methods#azureaadisc)

Finally, complete the Azure Services Wizard through the Summary, Progress, and Completion pages. You've completed the configuration of an Azure service in Configuration Manager. Repeat this process to configure other Azure services.

## Update application settings

To allow your Configuration Manager clients to request an **Microsoft Entra device token** and to enable the **Reading directory data** permissions, you need to update the web server application settings.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Microsoft Entra tenants** node.
2. Select the Microsoft Entra tenant for the application you want to update.
3. In the **Applications** section, select your Microsoft Entra web server application, then select **Update Application Settings** from the ribbon.
4. When prompted for confirmation, select **Yes** to confirm you want to update the application with the latest settings.

## Renew secret key

You need to renew the Microsoft Entra app's secret key before the end of its validity period. If you let the key expire, Configuration Manager can't authenticate with Microsoft Entra ID, which will cause your connected Azure services to stop working.

Starting in version 2006, the Configuration Manager console displays notifications for the following circumstances:

- One or more Microsoft Entra app secret keys will expire soon
- One or more Microsoft Entra app secret keys have expired

To mitigate both cases, renew the secret key.

For more information on how to interact with these notifications, see [Configuration Manager console notifications](../../manage/admin-console-notifications).

Note

Starting in Configuration Manager 2409, Azure services use Microsoft Graph. Signing in to renew the secret key requires consent for the Microsoft Graph `Directory.Read.All` permission, which the **Cloud Application Administrator** role can't grant. You must sign in with an account that has the **Global Administrator** role (or a role that can grant admin consent for Microsoft Graph permissions, such as **Privileged Role Administrator**). For more information, see [Permissions differences between Azure AD Graph and Microsoft Graph](/en-us/graph/migrate-azure-ad-graph-permissions-differences).

### Renew key for created app

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Microsoft Entra tenants** node.
2. On the Details pane, select the Microsoft Entra tenant for the app.
3. In the ribbon, select **Renew Secret Key**. Enter the credentials of either the app owner or a Microsoft Entra administrator.

### Renew key for imported app

If you imported the Azure app in Configuration Manager, use the Azure portal to renew. Note the new secret key and expiry date. Add this information on the **Renew Secret Key** wizard.

Note

Save the secret key before closing the Azure application properties **Key** page. This information is removed when you close the page.

## Disable authentication

Starting in version 2010, you can disable Microsoft Entra authentication for tenants not associated with users and devices. When you onboard Configuration Manager to Microsoft Entra ID, it allows the site and clients to use modern authentication. Currently, Microsoft Entra device authentication is enabled for all onboarded tenants, whether or not it has devices. For example, you have a separate tenant with a subscription that you use for compute resources to support a cloud management gateway. If there aren't users or devices associated with the tenant, disable Microsoft Entra authentication.

1. In the Configuration Manager console, go to the **Administration** workspace.
2. Expand **Cloud Services** and select the **Azure Services** node.
3. Select the target connection of type **Cloud Management**. In the ribbon, select **Properties**.
4. Switch to the **Applications** tab.
5. Select the option to **Disable Microsoft Entra authentication for this tenant**.
6. Select **OK** to save and close the connection properties.

Tip

It can take up to 25 hours for this change to take effect on clients. For purposes of testing to speed up this change in behavior, use the following steps:

1. Restart the **sms\_executive** service on the site server.
2. Restart the **ccmexec** service on the client.
3. Trigger the client schedule to refresh the default management point. For example, use the [send schedule tool](../../../support/send-schedule-tool): `SendSchedule {00000000-0000-0000-0000-000000000023}`

## View the configuration of an Azure service

View the properties of an Azure service you've configured for use. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select **Azure Services**. Select the service you want to view or edit, and then select **Properties**.

If you select a service and then choose **Delete** in the ribbon, this action deletes the connection in Configuration Manager. It doesn't remove the app in Microsoft Entra ID. Ask your Azure administrator to manually delete the app if it's no longer needed. Or run the Azure Service Wizard to import the app.

## Cloud management data flow

The following diagram is a conceptual data flow for the interaction between Configuration Manager, Microsoft Entra ID, and connected cloud services. This specific example uses the **Cloud Management** service, which includes a Windows 10 client, and both server and client apps. The flows for other services are similar.

![Data flow diagram for Configuration Manager with Microsoft Entra ID and Cloud Management](media/aad-auth.png)

1. The Configuration Manager administrator imports or creates the client and server apps in Microsoft Entra ID.
2. Configuration Manager Microsoft Entra user discovery method runs. The site uses the Microsoft Entra server app token to query Microsoft Graph for user objects.
3. The site stores data about the user objects. For more information, see [Microsoft Entra user Discovery](about-discovery-methods#azureaddisc).
4. The Configuration Manager client requests the Microsoft Entra user token. The client makes the claim using the application ID of the Microsoft Entra client app, and the server app as the audience. For more information, see [Claims in Microsoft Entra Security Tokens](/en-us/azure/active-directory/develop/authentication-scenarios#security-tokens).
5. The client authenticates with the site by presenting the Microsoft Entra token to the cloud management gateway and on-premises management point.

For more detailed information, see [Microsoft Entra authentication workflow](../../../clients/manage/azure-ccmsetup).