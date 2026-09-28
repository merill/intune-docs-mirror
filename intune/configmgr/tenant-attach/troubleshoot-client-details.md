---
layout: Conceptual
title: Troubleshoot client details - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-client-details
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
description: Troubleshoot client details for Intune tenant attach
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: troubleshooting
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 4fafeabf-b2df-2bfc-3282-f0ed148c45c5
document_version_independent_id: 50f1e3f9-a7fd-4954-e288-5b9c79e81c06
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/troubleshoot-client-details.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/troubleshoot-client-details
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/troubleshoot-client-details.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 56d213e7-8bae-f05a-3c23-27dee0e5e885
---

# Troubleshoot client details - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When viewing the ConfigMgr client details, you may run across a common error. Use the following information of common error messages to troubleshoot ConfigMgr client details in the Microsoft Intune admin center:

## You don’t have access to view this information

**Error message:** You don’t have access to view this information. Make sure a proper user role is assigned from Intune.

**Possible cause:** The user account needs an [Intune role](../../fundamentals/role-based-access-control/overview) assigned. In some cases, this error may also occur during replication of information and it resolves without intervention after a few minutes.

## Unable to get device information

### Error message 1: Device can't be found or you don't have permission to access the device

**Possible causes**:

- Verify that Configuration Manager's [role based access control](../core/understand/fundamentals-of-role-based-administration) for the admin user has the device in scope.
- The machine account of [SMS Provider role](../core/plan-design/hierarchy/plan-for-the-sms-provider) of the primary site (or standalone site) isn't a member of either the **Pre-Windows 2000 Compatible Access** or **Windows Authorization Access** (WAA) groups in on-premises Active Directory. For more information, see [Some applications and APIs require access to authorization information on account objects](/en-us/troubleshoot/windows-server/identity/apps-apis-require-access).

### Error message 2: Unable to get client details (or collection) information. Make sure Microsoft Entra ID and AD user discovery are configured and the user is discovered by both. Verify that the user has proper permissions in Configuration Manager

**Possible causes:**

Typically, this error is caused by an issue with the admin account. Below are the most common issues with the administrative user account:

1. Use the same account to sign in to the admin center. The on-premises identity must be synchronized with and match the cloud identity.
2. Make sure that Configuration Manager has discovered the administrative user account you're using to access the tenant attach features within Microsoft Intune admin center. In the Configuration Manager console, go to the **Assets and Compliance** workspace. Select the **Users** node, and find your user account.

    If your account isn't listed in the **Users** node, check the configuration of the site's [Active Directory User discovery](../core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser).

## Error loading your content

**Error message:** Getting results timed out. Make sure the Configuration Manager service connection point is operational and has a connection to the cloud. 

**Possible causes**:

- Make sure the hierarchy is still tenant-attached and connected. For more information, see the **CMGatewayNotificationWorker.log** file.
- If the service connection point or site server were recently rebooted, this error occurs temporarily.
- A site upgrade or a transient network error can cause this message to occur temporarily.
- For Configuration Manager versions 2103 and earlier, it's possible that the cache has expired and the SQL connection is stale. Restart **SMS\_Executive** service on the machine running the [service connection point (SCP)](../core/servers/deploy/configure/about-the-service-connection-point) role if you see errors similar to the following in the SCP's **CMGatewayNotificationWorker.log**: 

    ```text
    [Critical][CMGatewayNotificationWorker][0][System.InvalidOperationException][0x80131509]
    ExecuteReader requires an open and available Connection. The connection's current state is closed.
    ```

## Error validating request

**Error message:** Error validating request. Verify that the Configuration Manager service connection point can reach the internet endpoints required for tenant attach.

**Possible causes:** Typically this error is seen when URLs that are needed by tenant attach are blocked. If the service connection point can't access the needed internet endpoints, a validation error will occur. For more information, see [Internet endpoints](prerequisites#internet-endpoints).

## Unexpected error occurred

**Error message:** Unexpected error occurred

**Possible causes:** Unexpected errors are typically caused by either [service connection point](../core/servers/deploy/configure/about-the-service-connection-point), [administration service](../develop/adminservice/overview), or connectivity issues.

1. Verify the service connection point has connectivity to the cloud using the **CMGatewayNotificationWorker.log**.
2. Verify the administrative service is healthy by reviewing the SMS\_REST\_PROVIDER component from site component monitoring on both the central site and primary site that owns the device.
3. IIS must be installed on provider machine. For more information, see [Prerequisites for the administration service](../develop/adminservice/overview#prerequisites).

## Known issues

### When the Configuration Manager site is configured to require multi-factor authentication, most tenant attach features don't work

**Scenario:** If the [SMS provider](../core/plan-design/hierarchy/plan-for-the-sms-provider) machine that communicates with the [service connection point](../core/servers/deploy/configure/about-the-service-connection-point) is configured to use multi-factor authentication, you can't install applications, run CMPivot queries, and perform other actions from the admin console. You receive an error code 403, forbidden.

**Workaround:** The current workaround is to configure the on-premises hierarchy to the default authentication level of **Windows authentication**. For more information, see the [Authentication section in the SMS provider article](../core/plan-design/hierarchy/plan-for-the-sms-provider#authentication).