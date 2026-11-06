---
layout: Conceptual
title: Configure Microsoft Entra ID for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad
author: arob98
ms.author: angrobe
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Integrate the Configuration Manager site with Microsoft Entra ID to support the cloud management gateway.
ms.date: 2026-11-05T00:00:00.0000000Z
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
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
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

## Configure Azure RBAC permissions for the server app

The CMG uses the **server/web application's service principal** to deploy and manage its Azure resources. These Azure role-based access control (RBAC) permissions are separate from the Microsoft Entra directory roles used to create app registrations. Assign permissions to the server application's service principal, not the native/client application or the user who runs the console.

Starting in version 2609, shared-key access is automatically disabled for CMG storage. Existing CMGs that previously used shared-key access also need the permissions for Microsoft Entra-authenticated storage and storage role assignments. A successful deployment or update on an earlier version doesn't confirm that these permissions are present.

Verify the following effective permissions at each CMG resource group:

- **Resource management:** Retain the **Contributor** role or equivalent approved permissions that allow the server application to manage the CMG resources.
- **Storage role assignments:** Allow the server application to manage assignments of the **Storage Blob Data Contributor** and **Storage Table Data Contributor** roles. Contributor alone doesn't grant `Microsoft.Authorization/roleAssignments/write`.

To provide the storage role-assignment permissions with limited delegation:

1. In the Azure portal, open the CMG's resource group and select **Access control (IAM)**.
2. Identify the service principal for the CMG server application. Verify its application (client) ID and service-principal object ID against the application used by Configuration Manager.
3. Review its existing role assignments, including inherited assignments and their conditions. If equivalent effective permissions already exist, don't add a duplicate grant.
4. If the required storage role-assignment permissions are missing, assign **Role Based Access Control Administrator** to this service principal at the CMG resource group. Add a role-assignment condition that allows both `Microsoft.Authorization/roleAssignments/write` and `Microsoft.Authorization/roleAssignments/delete` only for these role definitions:

    - **Storage Blob Data Contributor**: `ba92f5b4-2d11-453d-a403-e96b0029c9fe`
    - **Storage Table Data Contributor**: `0a9a7e1f-b9d0-4cc4-a60d-0319b160aaa3`

    For instructions to select the allowed roles when configuring the condition, see [Delegate Azure role assignment management to others with conditions](/en-us/azure/role-based-access-control/delegate-role-assignments-portal). Don't use an unrestricted Owner or administrator grant as a shortcut.
5. Allow time for changes to propagate, then verify that the server application has the required effective permissions. If a custom condition or deny assignment prevents access, have the Azure resource administrator review it rather than broadening permissions or removing the restriction.

The administrator making the assignment needs Azure RBAC permission to create this constrained administrator assignment at the target scope. Permission to create only storage data-role assignments doesn't necessarily authorize the administrator to delegate the **Role Based Access Control Administrator** role. These operator permissions are separate from the permissions granted to the CMG server application.

Important

A grant at a staging resource group doesn't automatically grant access to a different production resource group or a different service principal. Verify each CMG application and resource group, including any inherited permissions and conditions. Being in the same Microsoft Entra tenant isn't sufficient.

If a CMG deployment update fails with HTTP **403**, `DeploymentFailed`, and a denied `Microsoft.Authorization/roleAssignments/write` action in **CloudMgr.log**, review the application object ID and Azure scope in the error. Verify that the indicated service principal can create the required role assignments at that scope. The signed-in administrator having access doesn't establish that the CMG application has access. Also review the failed deployment operations in the Azure portal.

## Configure Azure resource providers

The CMG service requires that you register specific resource providers in your Azure subscription. When you deploy the CMG to a virtual machine scale set, register the following resource providers:

- Microsoft.KeyVault
- Microsoft.Storage
- Microsoft.Network
- Microsoft.Compute
- Microsoft.Maintenance

**Microsoft.Maintenance** is used for CMG VM scale set maintenance configurations and configuration assignments. Before updating to version 2609, verify its registration for existing CMGs as well as new deployments. Provider registration is subscription-scoped, not tenant-scoped: registering it in a staging subscription doesn't register it in a different production subscription.

Note

If you previously deployed the CMG using a classic cloud service, your Azure subscription requires the following two resource providers:

- Microsoft.ClassicCompute
- Microsoft.Storage

Starting in version 2203, the option to deploy a CMG as a **cloud service (classic)** is removed. All CMG deployments should use a [virtual machine scale set](plan-cloud-management-gateway#virtual-machine-scale-sets). For more information, see [Removed and deprecated features](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

The account registering a provider needs permission to do the `/register/action` operation for that provider at the subscription scope, for example, `Microsoft.Maintenance/register/action`. By default, the **Contributor** and **Owner** roles include this permission when assigned at that scope. A Contributor assignment on only the CMG resource group doesn't grant subscription-level provider-registration permission.

The following steps summarize the process to register a resource provider. For more information, see [Azure resource providers and types](/en-us/azure/azure-resource-manager/management/resource-providers-and-types#azure-portal).

1. Sign in to the [Azure portal](https://portal.azure.com/).
2. On the Azure portal menu, search for **Subscriptions**. Select it from the available options.
3. Select the subscription you want to view.
4. On the left menu, under **Settings**, select **Resource providers**.
5. Find the resource provider you want to register, and select **Register**. To maintain least privileges in your subscription, only register those resource providers that you're ready to use.
6. Wait until the provider's registration state is **Registered** before proceeding with the CMG deployment or update. If the state is **Registering**, allow the registration to complete. Repeat this verification for each subscription containing CMG resources.

## Automate with PowerShell

You can optionally automate aspects of these configurations using PowerShell.

1. Use the [Import-CMAADServerApplication](/en-us/powershell/module/configurationmanager/Import-CMAADServerApplication) cmdlet to define the Microsoft Entra web/server app in Configuration Manager.
2. Use the [Import-CMAADClientApplication](/en-us/powershell/module/configurationmanager/Import-CMAADClientApplication) cmdlet to define the Microsoft Entra native/client app in Configuration Manager.
3. Use the [Get-CMAADApplication](/en-us/powershell/module/configurationmanager/Get-CMAADApplication) cmdlet to get the imported app objects.
4. Then pass the app objects to the [New-CMCloudManagementAzureService](/en-us/powershell/module/configurationmanager/New-CMCloudManagementAzureService) cmdlet to create the Azure service for **Cloud Management** in Configuration Manager.