---
layout: Conceptual
title: Enable Microsoft Intune tenant attach - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions
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
description: Upload your Configuration Manager devices to the cloud service and take actions from the admin center.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: core-infra
ms.collection: tier3
ms.custom:
- sfi-ga-nochange
- sfi-image-nochange
locale: en-us
document_id: a2eb4acb-7311-79d3-3daa-6f27ea42aee7
document_version_independent_id: 123f2a5c-04c1-8184-05a4-689d9c591981
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/device-sync-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/device-sync-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/device-sync-actions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 03a307b7-c3b6-d9f4-7025-23744abcaedc
---

# Enable Microsoft Intune tenant attach - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. You can upload your Configuration Manager devices to the cloud service and take actions from the **Devices** blade in the admin center.

Important

When you attach your Configuration Manager site with a Microsoft Intune tenant, the site sends more data to Microsoft. [Tenant attach data collection](data-collection) article summarizes the data that is sent.

## Enable device upload when co-management is already enabled

If you have co-management enabled currently, you must use the co-management properties to enable device upload. When co-management isn't already enabled, Use the **Cloud Attach Configuration Wizard** to enable device upload instead. Before you enable tenant attach, verify that the [prerequisites for tenant attach](prerequisites) are met.

When co-management is already enabled, edit the co-management properties to enable device upload using the instructions below:

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Cloud Attach**.

    - For version 2103 and earlier, select the **Co-management** node.
2. In the ribbon, select **Properties** for your co-management production policy.
3. In the **Configure upload** tab, select **Upload to Microsoft Endpoint Manager admin center**. Select **Apply**.

    - The default setting for device upload is **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.
    - When a single collection is selected, its child collections are also uploaded.
4. Check the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager** if you also want to get insights for optimizing the end-user experience in [endpoint analytics](../../endpoint-analytics/).
5. Check the option to **Enforce Role-based Access Control** for the devices uploading to cloud service. By default, SCCM RBAC is enforced along with Intune RBAC when you're uploading your Configuration Manager devices to the cloud service. Hence, the checkbox is checked by default. If you want to enforce only Intune RBAC or if you're using cloud-only account, you must uncheck the option.
6. Check the option to **Enable Uploading Microsoft Defender for Endpoint data for reporting on devices uploaded to Microsoft Intune admin center** if you want to use [Endpoint Security reports in Intune admin center](deploy-antivirus-policy#bkmk_mdereports)

    Important

    When you enable Endpoint analytics data upload, your default client settings is automatically updated to allow managed endpoints to send relevant data to your Configuration Manager site server. If you use custom client settings, you may need to update and re-deploy them for data collection to occur. For more information on this, as well as how to configure data collection, such as to limit collection only to a specific set of devices, see the section on [Configuring Endpoint analytics data collection](../../endpoint-analytics/).

    [![Screenshot that shows how to upload devices to Microsoft Intune admin center.](media/13058986-configure-upload-configmgr.png)](media/13058986-configure-upload-configmgr.png#lightbox)
7. Sign in with a **Global Administrator** account when prompted.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../core/understand/fundamentals-of-role-based-administration).
8. Select **Yes** to accept the **Create Microsoft Entra Application** notification. This action provisions a service principal and creates a Microsoft Entra application registration to facilitate the sync.
9. Choose **OK** to exit the co-management properties once you've done making changes.

## Enable device upload when co-management isn't enabled

If you don't have co-management enabled, use the **Cloud Attach Configuration Wizard** to enable device upload. You can upload your devices without enabling automatic enrollment for co-management or switching workloads to Intune. All Devices managed by Configuration Manager that have **Yes** in the **Client** column is uploaded. If needed, you can limit upload to a single device collection. If co-management is already enabled in your environment, Edit co-management properties to enable device upload instead. Before you enable tenant attach, verify that the [prerequisites for tenant attach](prerequisites) have been met.

When co-management isn't enabled, use the instructions below to enable device upload:

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Cloud Attach**. For version 2103 and earlier, select the **Co-management** node.

    - Starting in Configuration Manager version 2111, the tenant attach onboarding experience changed. The cloud attach wizard makes it easier to enable tenant attach and other [cloud features](../cloud-attach/overview). You can choose a streamlined set of recommended defaults, or customize your cloud attach features. For more information on enabling tenant attach with the new wizard, see [Enable cloud attach](../cloud-attach/enable).
2. In the ribbon, select **Configure Cloud Attach** to open the wizard. For version 2103 and earlier, select **Configure co-management** to open the wizard.
3. On the onboarding page, select **AzurePublicCloud** for your environment. Azure Government Cloud and Azure China 21Vianet aren't supported.

    - Starting in version 2107, US Government customers can select **AzureUSGovernmentCloud**.
4. Select **Sign In** and sign in with the **Global Administrator** account.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../core/understand/fundamentals-of-role-based-administration).
5. Ensure the **Enable Microsoft Endpoint Manager admin center** option is selected on the **Cloud attach** page. For version 2103 and earlier, select the **Upload to Microsoft Endpoint Manager admin center** option on the **Tenant onboarding** page.

    - Make sure the option **Enable automatic client enrollment for co-management** isn't checked if you don't want to enable co-management now. If you do want to enable co-management, select the option.
    - If you enable co-management along with device upload, there will be given additional pages in the wizard to complete. For more information, see [Enable co-management](../comanage/how-to-enable).

    [![Co-management Configuration Wizard](media/3555758-comanagement-wizard.png)](media/3555758-comanagement-wizard.png#lightbox)
6. Choose **Next** and then **Yes** to accept the **Create Microsoft Entra Application** notification. This action provisions a service principal and creates a Microsoft Entra application registration to facilitate the sync.

    - Optionally, you can import a previously created Microsoft Entra application during tenant attach onboarding. For more information, see the Import a previously created Microsoft Entra application section.
7. On the **Configure upload** page, select the recommended device upload setting for **All my devices managed by Microsoft Endpoint Configuration Manager**. If needed, you can limit upload to a single device collection.

    - When a single collection is selected, its child collections are also uploaded.
8. Check the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager** if you also want to get insights to optimize the end-user experience in [endpoint analytics](../../endpoint-analytics/).
9. Check the option to **Enforce Role-based Access Control** for the devices uploading to cloud service. By default, SCCM RBAC is enforced along with Intune RBAC when you're uploading your Configuration Manager devices to the cloud service. Hence, the checkbox is checked by default. If you want to enforce only Intune RBAC or if you're using cloud-only account, you must uncheck the option.
10. Check the option to **Enable Uploading Microsoft Defender for Endpoint data for reporting on devices uploaded to Microsoft Intune admin center** if you want to use [Endpoint Security reports in Intune admin center](deploy-antivirus-policy#bkmk_mdereports)
11. Select **Summary** to review your selection, then choose **Next**.
12. When the wizard is complete, select **Close**.

## Scope tags

Tenant-attached devices receive the [default scope tag](../../fundamentals/role-based-access-control/scope-tags#default-scope-tag) from Microsoft Intune. If you remove the default scope tag from a tenant-attached device, the device won't be displayed at all in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Currently, tenant-attached devices can't be assigned scope tags unlike [co-managed devices](../comanage/overview?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) can.

However, sometimes you don't want certain [Intune roles](../../fundamentals/role-based-access-control/overview#built-in-roles) to see tenant-attached devices. For instance, you may not want someone with Intune's **Help Desk Operator** role to see tenant-attached devices because they're servers. In these cases, create or use a custom role in Intune that doesn't have **Default** listed for its **Scope tags**. When [creating custom Intune roles](../../fundamentals/role-based-access-control/create-custom-role#to-create-a-custom-role), keep in mind that the default scope tag is automatically added to all untagged objects.

## Perform device actions

1. In a browser, navigate to `intune.microsoft.com`
2. Select **Devices** then **All devices** to see the uploaded devices. You'll see **ConfigMgr** in the **Managed by** column for uploaded devices. [![All devices in Microsoft Intune admin center](media/3555758-all-devices.png)](media/3555758-all-devices.png#lightbox)
3. Select a device to load its **Overview** page.
4. Choose any of the following actions:

    - **Sync Machine Policy**
    - **Sync User Policy**
    - **App Evaluation Cycle**

    [![Device overview in Microsoft Intune admin center](media/3555758-device-overview-actions.png)](media/3555758-device-overview-actions.png#lightbox)

## Display the Configuration Manager connector status from the admin console

From the Microsoft Intune admin center, you can review the status of your Configuration Manager connector. To display the connector status, go to **Tenant administration** &gt; **Connectors and tokens** &gt; **Microsoft Endpoint Configuration Manager**. Select a Configuration Manager hierarchy to display additional information about it.

[![Microsoft Configuration Manager connector in the admin center](media/7138634-connector-status.png)](media/7138634-connector-status.png#lightbox)

### View recommendations and insights to enrich the Configuration Manager site health and device management experience

You can view recommendations and insights for your Configuration Manager sites. These recommendations can help you improve the site health and infrastructure and enrich the device management experience.

Recommendations include:

- How to simplify your infrastructure
- Enhance device management
- Provide device insights
- Improve the health of the site

To view recommendations, go to **Tenant administration &gt; Connectors and tokens &gt; Microsoft Endpoint Configuration Manager**, and select a *site* to view recommendations for that. Once selected, you'll find the *Recommendations* tab that displays each insight along with a *Learn more* link that opens details on how to apply that recommendation.

## Offboard from tenant attach

While we know customers get enormous value by enabling tenant attach, there are rare cases where you might need to offboard a hierarchy. You can offboard from either the Configuration Manager console (recommend method) or from the Microsoft Intune admin center.

### Offboard from the Configuration Manager console

When tenant attach is already enabled, edit the co-management properties to disable device upload and offboard.

1. In the Configuration Manager admin console, go to **Administration** &gt; **Overview** &gt; **Cloud Services** &gt; **Cloud Attach**.
    - For version 2103 and earlier, select the **Co-management** node.
2. In the ribbon, select **Properties** for your co-management production policy.
3. In the **Configure upload** tab, remove the **Upload to Microsoft Endpoint Manager admin center** selection.
4. Select **Apply**.

### Offboard from the Microsoft Intune admin center

If needed, you can offboard a Configuration Manager hierarchy from the Microsoft Intune admin center. For example, you may need to offboard from the admin center following a disaster recovery scenario where the on-premises environment was removed. Follow the steps below to remove your Configuration Manager hierarchy from the Microsoft Intune admin center:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** then **Connectors and tokens**.
3. Select **Microsoft Endpoint Configuration Manager**.
4. Choose the name of the site you would like to offboard, then select **Delete**.
    - The connector may be listed as **Unknown** if the site information is lacking.

When you offboard a hierarchy from the admin center, it may take up to two hours to remove from the Microsoft Intune admin center. If you offboard a Configuration Manager 2103 or later site that's online and healthy, the process may only take a few minutes.

Note

If you are using custom [RBAC roles with Intune](../../fundamentals/role-based-access-control/overview#rbac-roles), you will need to grant the **Organization** &gt; **Delete** permission to offboard a hierarchy.

## Import a previously created Microsoft Entra application (optional)

During a new onboarding, an administrator can specify a previously created application during onboarding to tenant attach. Don't share or reuse Microsoft Entra applications across multiple hierarchies. If you have multiple hierarchies, create separate Microsoft Entra applications for each.

From the onboarding page in the **Cloud Attach Configuration Wizard** (**Co-management Configuration Wizard** in versions 2103 and earlier), select **Optionally import a separate web app to synchronize Configuration Manager client data to Microsoft Intune Endpoint Manager center**. This option will prompt you to specify the following information for your Microsoft Entra app:

- Microsoft Entra tenant name
- Microsoft Entra tenant ID
- Application name
- Client ID
- Secret key
- Secret key expiry
- App ID URI

Important

- The App ID URI must use one of the following formats:

    - `api://{tenantId}/{string}`, for example, `api://aaaabbbb-0000-cccc-1111-dddd2222eeee/ConfigMgrService`
    - `https://{verifiedCustomerDomain}/{string}`, for example, `https://contoso.onmicrosoft.com/ConfigMgrService`

    For more information on creating a Microsoft Entra app, see [Configure Azure services](../core/servers/deploy/configure/azure-services-wizard).
- When you use an imported Microsoft Entra app, you aren't notified of an upcoming expiration date from [console notifications](../core/servers/manage/admin-console-notifications).

### Microsoft Entra application permissions and configuration

Using a previously created application during onboarding to tenant attach requires the following permissions:

- Configuration Manager Microservice permissions:

    - CmCollectionData.read
    - CmCollectionData.write
- Microsoft Graph permissions:

    - Directory.Read.All [Applications permission](/en-us/graph/permissions-reference#application-permissions)
    - Directory.Read.All [Delegated directory permission](/en-us/graph/permissions-reference#directory-permissions)
- Ensure **Grant admin consent for Tenant** is selected for the Microsoft Entra application. For more information, see [Grant admin consent in App registrations](/en-us/azure/active-directory/manage-apps/grant-admin-consent).
- The imported application needs to be configured as follows:

    - Registered for **Accounts in this organizational directory only**. For more information, see [Change who can access your application](/en-us/azure/active-directory/develop/quickstart-modify-supported-accounts#to-change-who-can-access-your-application).
    - Has a valid application ID URI and secret.