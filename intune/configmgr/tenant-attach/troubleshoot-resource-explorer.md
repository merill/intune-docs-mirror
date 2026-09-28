---
layout: Conceptual
title: Troubleshooting resource explorer - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-resource-explorer
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
description: Troubleshooting resource explorer for Intune tenant attach
ms.date: 2022-01-25T00:00:00.0000000Z
ms.topic: troubleshooting
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: f50e4883-17b1-3500-ae8b-8ea4e17ec854
document_version_independent_id: fc420368-c0eb-fd7b-e930-d836dc55b425
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/troubleshoot-resource-explorer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/troubleshoot-resource-explorer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/troubleshoot-resource-explorer.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: e31265ce-ad1c-b5f5-0d0c-14eed69db853
---

# Troubleshooting resource explorer - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the following to troubleshoot resource explorer for ConfigMgr devices in the Microsoft Intune admin center:

## Common errors from the Microsoft Intune admin center

### You don’t have access to view this information

**Error message:** You don’t have access to view this information. Make sure a proper user role is assigned from Intune.

**Possible cause:** The user account needs an [Intune role](../../fundamentals/role-based-access-control/overview) assigned. In some cases, this error may also occur during replication of information and it resolves without intervention after a few minutes.

### Unable to get resource information

**Error message 1:** Unable to get resource information. Make sure Microsoft Entra ID and AD user discovery are configured and the user is discovered by both. Verify that the user has proper permissions in Configuration Manager.

**Possible causes:** Typically, this error is caused by an issue with the admin account. Below are the most common issues with the administrative user account:

1. Use the same account to sign in to the admin center. The on-premises identity must be synchronized with and match the cloud identity.
2. Verify the account has **Read** permission for the device's **Collection** in Configuration Manager.
3. Make sure that Configuration Manager has discovered the administrative user account you're using to access the tenant attach features within Microsoft Intune admin center. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

    If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).
4. Verify the discovery data. Select your user account. In the ribbon, on the **Home** tab select **Properties**. In the properties window, confirm the following discovery data:

    - **Microsoft Entra tenant ID**: This value should be a GUID for the Microsoft Entra tenant.
    - **Microsoft Entra user ID**: This value should be a GUID for this account in Microsoft Entra ID.
    - **User Principal Name**: The format of this value is user@domain. For example, `jqpublic@contoso.com`.

    If the Microsoft Entra properties are empty, check the configuration of the site's [Microsoft Entra user discovery](../core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### The site information hasn't yet synchronized

**Error message:** The site information hasn't yet synchronized from Configuration Manager to the Microsoft Intune admin center.

**Possible causes:**

- This error typically occurs when newly onboarding to tenant attach. Wait an hour for the information to synchronize.
- This error may also appear if the central administration site has been upgraded to a new Configuration Manager version but some child primary sites haven't been upgraded yet.

### Unable to load inventory classes

**Error message:** Unable to load inventory classes for your environment.

**Possible causes:**

- The list of entities may not have been uploaded from on-premises. Wait an hour then see if the error persists.
- An invalid **Tenant ID** or **Support ID** may have been specified. Check the service connection point and make sure it's functioning.
- Unable to successfully execute query to get classes. Wait 15 minutes to see if the error persists.

### Failed to get inventory classes with data

**Error message:** Failed to get inventory classes with data. On-premises error 500.

**Possible causes:** Unexpected errors are typically caused by either [service connection point](../core/servers/deploy/configure/about-the-service-connection-point), [administration service](../develop/adminservice/overview), or connectivity issues.

1. Verify the service connection point has connectivity to the cloud using the **CMGatewayNotificationWorker.log**.
2. Verify the administrative service is healthy by reviewing the SMS\_REST\_PROVIDER component from site component monitoring on the central site.
3. IIS must be installed on provider machine. For more information, see [Prerequisites for the administration service](../develop/adminservice/overview#prerequisites).

### The user does not have permissions

**Error message:** Failed to get inventory classes with data. The user does not have permissions.

**Possible causes:** The user may not have access to the collection that the device is a part of. Verify the following items:

1. Use the same account to sign in to the admin center. The on-premises identity must be synchronized with and match the cloud identity.
2. Verify the account has **Read** permission for the device's **Collection** in Configuration Manager.
3. Make sure that Configuration Manager has discovered the administrative user account you're using. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

    If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

## Known issues

### Newly imported inventory classes fail to load

**Scenario:** New hardware inventory classes are imported. You can see the newly imported classes in **Resource Explorer** from the Configuration Manager console. When you open **Resource explorer** from Microsoft Intune admin center, the newly imported class doesn't have data and **Failed** appears at the bottom of the results pane.

**Workaround:** The current workaround is to restart the `SMS_Executive` service on the provider machine for which the [administration service](../develop/adminservice/overview) handles service requests. You can determine where your administration service is by reviewing the **CMGatewayNotification.log** and looking for your server in the URL.

```log
Sending AdminService request with URL: https://CMsite.contoso.com/AdminService/v1.0/ ...
```

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](../core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](../core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](../core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).