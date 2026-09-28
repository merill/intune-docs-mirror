---
layout: Conceptual
title: Enable cloud attach - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/cloud-attach/enable
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
description: Enable cloud attach for Configuration Manager
ms.date: 2022-08-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: cf10ea9a-477b-38c5-3728-87b3b5f161e6
document_version_independent_id: cf10ea9a-477b-38c5-3728-87b3b5f161e6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/cloud-attach/enable.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/cloud-attach/enable
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/cloud-attach/enable.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 9b6b1886-8bb2-3ff6-e331-7a47a8df8559
---

# Enable cloud attach - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in version 2111, it's simpler to cloud attach your Configuration Manager environment. You can choose a streamlined set of recommended defaults, or customize your cloud attach features. If you're not running version 2111 yet, use the [Tenant attach](../tenant-attach/device-sync-actions?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), [Endpoint analytics](../../endpoint-analytics/?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), and [Co-management](../comanage/tutorial-co-manage-clients?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) articles to enable cloud attach features.

![Screenshot of the cloud attach configuration wizard](media/10964629-cloud-attach-wizard.png)

## Simplified cloud attach configuration

(*Applies to version 2111 or later*)

By using the recommended default settings, your eligible devices will be cloud attached. You'll enable capabilities like rich analytics, cloud console, and real-time device querying. The default settings include the following features:

- Enables automatic enrollment of all eligible devices into Intune
    - Enrolls your clients into [co-management](../comanage/tutorial-co-manage-clients?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), with all [workloads](../comanage/workloads?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) pointed to Configuration Manager
    - Devices are eligible if they meet the [prerequisites for co-management](../comanage/overview?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json#prerequisites). These devices are listed in the built-in **Co-management Eligible Devices** collection.
    - This option is the only one currently available for China21Vianet (Azure China Cloud).
- Enables [Endpoint analytics](../../endpoint-analytics/scores?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json)
- Enables automatic upload of all your devices to Microsoft Intune admin center ([tenant attach](../tenant-attach/device-sync-actions?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json))
- Enables Uploading of Microsoft Defender for Endpoint data for [reporting](../tenant-attach/deploy-antivirus-policy#bkmk_mdereports) on devices uploaded to Microsoft Intune admin center

Important

When you attach your Configuration Manager site with a Microsoft Intune tenant, the site sends more data to Microsoft. [Tenant attach data collection](../tenant-attach/data-collection) article summarizes the data that is sent.

Note

Ensure that prerequisites for each of the cloud attach features are met. For more information about prerequisites, see, [prerequisites for tenant attach](../tenant-attach/device-sync-actions?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), [prerequisites for Endpoint analytics](../../endpoint-analytics/?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json), and [prerequisites for co-management](../comanage/overview?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json#prerequisites).

## Cloud attach using the default settings

Use the following steps to cloud attach your environment with the default settings:

1. From the Configuration Manager console, go to **Administration** &gt; **Cloud services** &gt; **Cloud Attach**.
2. Select **Configure Cloud Attach** from the ribbon to open the wizard.
3. Select your **Azure environment** from the following list:

    - Azure Public Cloud
    - Azure US Government Cloud
    - Azure China Cloud
        - Endpoint analytics and device upload to Microsoft Intune admin center can't be enabled for Azure China Cloud
4. Select **Sign In**. Sign in to your account when prompted.
5. Ensure that **Use default settings (recommended)** is selected, then choose **Next** and **Yes** when the app registration notice appears.
6. Review the summary and select **Next** to cloud attach your environment and complete the wizard.

## Cloud attach using custom settings

(*Applies to version 2111 or later*)

Use the following steps to cloud attach your environment with custom settings:

1. From the Configuration Manager console, go to **Administration** &gt; **Cloud services** &gt; **Cloud Attach**.
2. Select **Configure Cloud Attach** from the ribbon to open the wizard.
3. Select your **Azure environment** from the following list:

    - Azure Public Cloud
    - Azure US Government Cloud
    - Azure China Cloud
        - Endpoint analytics and device upload to Microsoft Intune admin center can't be enabled for Azure China Cloud
4. Select **Sign In**. Sign in to your account when prompted.
5. Choose the **Customize settings** option to enable cloud features individually.
6. By default, Configuration Manager uses your credentials to register an app in your Microsoft Entra tenant. This app to authorize synchronization of data between your on-premises site and Intune. To use an app that you already created, select **Optionally import a separate web app to synchronize Configuration Manager client data to Microsoft Endpoint Manager admin center**. For more information, see Import a previously created Microsoft Entra application.
7. Choose **Next** to continue. You may also be prompted to confirm Microsoft Entra application registration. Select **Yes** to confirm the app registration.
8. The **Devices** section of the **Configure Upload** page, enables [tenant attach](../tenant-attach/device-sync-actions?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json). Tenant attach uploads your Configuration Manager devices to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) cloud-based console. You can take certain actions on uploaded devices such as run queries, run scripts, install apps, or display an event timeline for the device.

    **Select which devices to upload to Microsoft Endpoint Manager** has the following two options:

    - **All devices managed my Microsoft Endpoint Configuration Manager (recommended)**: Upload all devices
    - **Specific Collection**: Upload a specific collection, including any subcollections.
9. The **Endpoint Analytics** section of the **Configure Upload** page, enables [Endpoint analytics](../../endpoint-analytics/scores?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) for devices uploaded to Microsoft Intune. Endpoint analytics reports focus on the quality of the experience you're delivering to your users and helps you identify issues to proactively make improvements.

    Ensure the **Enable Endpoint Analytics for devices uploaded to Microsoft Endpoint Manager** option is selected to enable Endpoint Analytics.
10. In the **Role-based access control** section of the **Configure Upload** page, determine if you need to clear the checkbox for the **Enforce Configuration Manager RBAC for cloud console requests that interact with Configuration Manager** option. (*Introduced in version 2207*)

    - This option is used for setting Intune as the role-based access control authority for tenant-attached clients. For more information about configuring this option, see [Intune role-based access control for tenant-attached clients](use-intune-rbac).

        Important

        When this checkbox is cleared, [settings in Intune need to be configured](use-intune-rbac) too.
11. Check the option to **Enable Uploading Microsoft Defender for Endpoint data for reporting on devices uploaded to Microsoft Intune admin center** if you want to use [Endpoint Security reports in Intune admin center](../tenant-attach/deploy-antivirus-policy#bkmk_mdereports)
12. Select **Next** to get to the **Enablement** page for [co-management](../comanage/tutorial-co-manage-clients?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json). Co-management simplifies management by enrolling devices into Intune and allowing you to lift selected [workloads](../comanage/workloads?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) to the cloud. For instance, you can choose to enable workloads for [Conditional Access](../comanage/quickstart-conditional-access?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) so only trusted users can access organizational resources on trusted devices using trusted apps.

    Choose your co-management setting from the following options under **Automatic enrollment in Intune**:

    - **All**: Enrolls all eligible devices into Intune
        - Devices are eligible if they meet the [prerequisites for co-management](../comanage/overview?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json#prerequisites). These devices are listed in the built-in **Co-management Eligible Devices** collection.
    - **Pilot**: Enrolls all eligible devices in a specified collection into Intune
        - Select **Browse** to choose the collection for **Intune auto enrollment**
    - **None**: Don't enable co-management or enroll any clients

    Note

    Enrolling devices, doesn't move any workloads to Intune. [Specify workloads to move](../comanage/how-to-switch-workloads?toc=/mem/configmgr/cloud-attach/toc.json&amp;bc=/mem/configmgr/cloud-attach/breadcrumb/toc.json) by editing the co-management settings in the **Cloud Attach** node when you're ready.
13. When you're finished with your selections, select **Next** to display the **Summary** page. Select **Next** after reviewing the summary to cloud attach your Configuration Manager environment.

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