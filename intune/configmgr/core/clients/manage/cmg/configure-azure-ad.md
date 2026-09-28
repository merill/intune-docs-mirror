---
layout: Conceptual
title: Configure Microsoft Entra ID for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad
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
description: Integrate the Configuration Manager site with Microsoft Entra ID to support the cloud management gateway.
ms.date: 2022-09-26T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 73637c76-0466-8a0f-f614-c5ef3607d4a4
document_version_independent_id: 15fd3771-a7f3-f233-51bd-0be30cd0a020
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/configure-azure-ad.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/configure-azure-ad
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/configure-azure-ad.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 45cdb48b-623d-e0b6-aca3-f991963748f6
---

# Configure Microsoft Entra ID for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The second primary step to set up a cloud management gateway (CMG) is to integrate the Configuration Manager site with your Microsoft Entra tenant. This integration allows the site to authenticate with Microsoft Entra ID, which it uses to deploy and monitor the CMG service. If you choose the Microsoft Entra authentication method for clients in the next step, then this integration is a prerequisite for that authentication method.

Tip

This article provides prescriptive guidance to integrate the site specifically for the cloud management gateway. For more information on this process and other uses of the **Azure Services** node in the Configuration Manager console, see [Configure Azure services](../../../servers/deploy/configure/azure-services-wizard).

When you integrate the site, you create app registrations in Microsoft Entra ID. The CMG requires two app registrations:

- **Web app** (also referred to as a *server* app in Configuration Manager)
- **Native app** (also referred to as a *client* app in Configuration Manager)

There are two methods to create these apps, both of which require a **Microsoft Entra Global Administrator**:

- Use Configuration Manager to automate the creation of the apps when you integrate the site.
- Manually create the apps in advance, and then import them when you integrate the site.

This article primarily follows the first method. For more information on the other method, see [Manually register Microsoft Entra apps for CMG](manually-register-azure-ad-apps).

Before you start, make sure you have a Microsoft Entra **Global Administrator** available.

Important

- The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../../understand/fundamentals-of-role-based-administration).
- If you plan to import precreated app registrations, you first need to create them in Microsoft Entra ID. Start with the article to [Manually register Microsoft Entra apps for CMG](manually-register-azure-ad-apps). Then return to this article to run the Azure Services wizard and import the apps to Configuration Manager.

## Purpose of app registrations

These two Microsoft Entra app registrations represent the server and client side of the CMG.

- The *client app* represents managed clients and users that connect to the CMG. It defines what resources they have access to within Azure, including the CMG itself.
- The *server app* represents the CMG components that are hosted in Azure. It defines what resources they have access to within Azure. The server app is used to facilitate authentication and authorization from managed clients, users, and the CMG connection point to the Azure-based CMG components. This communication includes traffic to on-premises management points and software update points, initial CMG provisioning in Azure, and Microsoft Entra discovery.

If clients use PKI-issued client authentication certificates, then the two client apps aren't used for device-centric activity. For example, software distribution targeted to a device collection. User-centric activity always uses these two app registrations for authentication and authorization purposes.

## Start the Azure Services wizard

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select the **Azure Services** node.
2. On the *Home* tab of the ribbon, in the *Azure Services*\* group, select **Configure Azure Services**.
3. On the *Azure Services* page of the Azure Services Wizard:

    1. Specify a **Name** for the object in Configuration Manager. This name is only to identify the connection in Configuration Manager.
    2. Specify an optional **Description** to further identify this service connection.
    3. Select the **Cloud Management** service.
4. On the *App* page of the *Azure Services Wizard*, select the **Azure environment** for your tenant:

    - **AzurePublicCloud**: Your tenant is in the global Azure cloud.
    - **AzureUSGovernmentCloud**: Your tenant is in the Azure US Government cloud.

## Create the web (server) app registration

1. On the *App* page of the *Azure Services Wizard* window, for the **Web app**, select **Browse**.
2. In the *Server App* window, select **Create** to use Configuration Manager to automate the creation of the app.
3. In the *Create Server Application* window, specify the following information:

    - **Application name**: A friendly name for the app.
    - **HomePage URL**: This value isn't used by Configuration Manager, but required by Microsoft Entra ID. By default this value is `https://ConfigMgrService`.
    - **App ID URI**: This value needs to be unique in your Microsoft Entra tenant. It's in the access token used by the Configuration Manager client to request access to the service. By default this value is `https://ConfigMgrService`. Change the default to one of the following recommended formats:

        - `api://{tenantId}/{string}`, for example, `api://aaaabbbb-0000-cccc-1111-dddd2222eeee/ConfigMgrService`
        - `https://{verifiedCustomerDomain}/{string}`, for example, `https://contoso.onmicrosoft.com/ConfigMgrService`
    - **Secret key validity period**: choose either **1 year** or **2 years** from the drop-down list. One year is the default value.
    - **Microsoft Entra admin account**: Select **Sign in** to authenticate to Microsoft Entra ID as a Global Administrator. Configuration Manager doesn't save these credentials. This persona doesn't require permissions in Configuration Manager, and doesn't need to be the same account that runs the Azure Services Wizard. After successfully authenticating to Azure, the page shows the **Microsoft Entra tenant name** for reference.
4. Select **OK** to create the web app in Microsoft Entra ID and close the *Create Server Application* window.
5. In the *Server App* window, make sure your new app is selected, then select **OK** to save and close the window.

Note

Starting in Configuration Manager current branch version 2309, We have enhanced security of web (server) app for the creation of CMG. For new CMG creation, users can select tenant and the app name using the Microsoft Entra tenant name. After selecting tenant and app name the sign-in button appears, follow rest of the process as per the setup CMG.

Pre-existing CMG customers must update their web server app by navigating to Microsoft Entra tenants node --&gt; select the tenant --&gt; select the server app --&gt; click on "update application settings".

## Create the native (client) app registration

1. On the *App* page of the *Azure Services Wizard* window, for the **Native Client app**, select **Browse**.
2. In the *Client App* window, select **Create** to use Configuration Manager to automate the creation of the app.
3. In the *Create Client Application* window, specify the following information:

    - **Application name**: A friendly name for the app.
    - **Microsoft Entra admin account**: Select **Sign in** to authenticate to Microsoft Entra ID as a Global Administrator. Configuration Manager doesn't save these credentials. This persona doesn't require permissions in Configuration Manager, and doesn't need to be the same account that runs the Azure Services Wizard. After successfully authenticating to Azure, the page shows the **Microsoft Entra tenant name** for reference.
4. Select **OK** to create the native app in Microsoft Entra ID and close the *Create Client Application* window.
5. In the *Client App* window, make sure your new app is selected, then select **OK** to save and close the window.

## Complete the Azure Services wizard

1. In the *Azure Services Wizard*, confirm both the **Web app** and **Native Client app** values are complete. Select **Next** to continue.
2. The *Discovery* page of the wizard is only necessary in some scenarios. It's optional when you onboard the site to Microsoft Entra ID, and not required to create the CMG. If you need it to support specific functionality in your environment, you can enable it later.

    For more information on the CMG scenarios that may require Microsoft Entra user discovery, see [Configure client authentication: Microsoft Entra ID](configure-authentication#azure-ad) and [Install clients using Microsoft Entra ID](../../deploy/deploy-clients-cmg-azure).

    For more information on this discovery method, see [Configure Microsoft Entra user discovery](../../../servers/deploy/configure/configure-discovery-methods#azureaadisc).
3. Review the settings and complete the wizard.

When the wizard closes, you'll see the new connection in the **Azure Services** node. You can also view the tenant and app registrations in the **Microsoft Entra tenants** node of the Configuration Manager console.

### Disable Microsoft Entra authentication for non-device or user tenants

If your devices are in a Microsoft Entra tenant that's separate from the tenant with a subscription for the CMG compute resources, you can disable authentication for tenants not associated with users and devices.

1. Open the properties of the **Cloud Management** service.
2. Switch to the **Applications** tab.
3. Select the option to **Disable Microsoft Entra authentication for this tenant**.

For more information, see [Configure Azure services](../../../servers/deploy/configure/azure-services-wizard#disable-authentication).

## Configure Azure resource providers

The CMG service requires that you register specific resource providers in your Azure subscription. When you deploy the CMG to a virtual machine scale set, register the following resource providers:

- Microsoft.KeyVault
- Microsoft.Storage
- Microsoft.Network
- Microsoft.Compute

Note

If you previously deployed the CMG using a classic cloud service, your Azure subscription requires the following two resource providers:

- Microsoft.ClassicCompute
- Microsoft.Storage

Starting in version 2203, the option to deploy a CMG as a **cloud service (classic)** is removed. All CMG deployments should use a [virtual machine scale set](plan-cloud-management-gateway#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Your Microsoft Entra account needs permission to do the `/register/action` operation for the resource provider. By default, the **Contributor** and **Owner** roles include this permission.

The following steps summarize the process to register a resource provider. For more information, see [Azure resource providers and types](/en-us/azure/azure-resource-manager/management/resource-providers-and-types#azure-portal).

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. On the Azure portal menu, search for **Subscriptions**. Select it from the available options.
3. Select the subscription you want to view.
4. On the left menu, under **Settings**, select **Resource providers**.
5. Find the resource provider you want to register, and select **Register**. To maintain least privileges in your subscription, only register those resource providers that you're ready to use.

## Automate with PowerShell

You can optionally automate aspects of these configurations using PowerShell.

1. Use the [Import-CMAADServerApplication](/en-us/powershell/module/configurationmanager/Import-CMAADServerApplication) cmdlet to define the Microsoft Entra web/server app in Configuration Manager.
2. Use the [Import-CMAADClientApplication](/en-us/powershell/module/configurationmanager/Import-CMAADClientApplication) cmdlet to define the Microsoft Entra native/client app in Configuration Manager.
3. Use the [Get-CMAADApplication](/en-us/powershell/module/configurationmanager/Get-CMAADApplication) cmdlet to get the imported app objects.
4. Then pass the app objects to the [New-CMCloudManagementAzureService](/en-us/powershell/module/configurationmanager/New-CMCloudManagementAzureService) cmdlet to create the Azure service for **Cloud Management** in Configuration Manager.