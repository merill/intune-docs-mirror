---
layout: Conceptual
title: Technical preview 2202 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2022/technical-preview-2202
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2202.
ms.date: 2022-02-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 3fd672b7-bc06-4b35-0d80-77a08bb8e80c
document_version_independent_id: 3fd672b7-bc06-4b35-0d80-77a08bb8e80c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2022/technical-preview-2202.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2022/technical-preview-2202
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2022/technical-preview-2202.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5f52c775-6670-130c-88de-df2ecb65aae5
---

# Technical preview 2202 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2202. Install this version to update and add new features to your technical preview site. When you install a new technical preview site, this release is also available as a baseline version.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Delete collection references

Previously, when you would delete a collection with dependent collections, you first had to delete the dependencies. The process of finding and deleting all of these collections could be difficult and time consuming. Now when you delete a collection, you can review and delete its dependent collections at the same time.

A new **Details** window shows more information about the relationship types, and lets you [view collection relationships](../../clients/manage/collections/view-relationships) in a graphical chart.

[![View collection dependencies in list and graphical form when deleting a collection](media/9708999-delete-collection-references.png)](media/9708999-delete-collection-references.png#lightbox)

There are several reasons why the site can't delete a dependent collection:

- **Assigned to user**: For more information, see [Modify the administrative scope of an administrative user](../../servers/deploy/configure/configure-role-based-administration#modify-the-administrative-scope-of-an-administrative-user).
- **Used by cloud attach**: For more information, see [Enable cloud attach for Configuration Manager](../../../cloud-attach/enable).
- **Use for upload to Microsoft Intune**: For more information, see [Make Configuration Manager collections available to assign Endpoint security policies](../../../tenant-attach/endpoint-security-get-started#bkmk_collections).

The details window lists collections that can't be deleted with the reason why.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Create multiple collections that are dependent on each other. Use relationships such as **Limiting**, **Include**, and **Exclude**. For more information, see [How to create collections in Configuration Manager](../../clients/manage/collections/create-collections).
2. Delete a collection that has dependent collections. For more information on how to delete a collection, see [Collection actions](../../clients/manage/collections/manage-collections#collection-actions).
3. In the **Delete Collection Error** window, select **Details**.
4. Once the relationship types finish loading, select **View Relationships** to see the graph.
5. If all of the dependent collections can be deleted, select **Delete all listed collections**.
6. Review the list of collections and any software deployments that the site will also remove. You also can **Delete each collection member from the database**.

### Known issue when deleting collection references

Consider the scenario where you're deleting collections with references, and another administrative user is simultaneously creating a reference to a collection that you're deleting. When this behavior occurs, the console displays an error, and the collection isn't deleted.

## Pre-download content for available software updates

Admins can now pre-download content for software updates that are included in available deployments. Required deployments already pre-download content by default. Enabling this new setting reduces installation wait times for clients since installation notifications aren't visible in Software Center until the content has fully downloaded.

The **Pre-download content for this deployment** setting is available in the following locations:

- The **Deployment Settings** page of the **Deploy Software Updates Wizard** for [manually created](../../../sum/deploy-use/manually-deploy-software-updates) software update deployments
- The **Deployment Settings** page of the **Automatic Deployment Rules Wizard** for update deployments created with an [automatic deployment rule](../../../sum/deploy-use/automatically-deploy-software-updates)
- The **Deployment Settings** tab in the **Properties** page for a deployment created manually or with an automatic deployment rule.

Note

If an update is in multiple deployments for a client and the **Pre-download content for this deployment** setting is enabled for a least one of the deployments, then the content will pre-download.

## Added folder support for nodes in the Software Library

Admins can now organize software update groups and packages by using folders. This change allows for better categorization and management of software updates.

![Screenshot of right-click menu displaying folder options for the Deployment Packages node.](media/3601129-sum-deployment.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Open the Configuration Manager console and go to the **Software Library** workspace.
2. From the ribbon or right-click menu, in the **Software Updates Groups** or **Deployment Packages**nodes, select from the following options:
    - **Create Folder**
    - **Delete Folder**
    - **Rename Folder**
    - **Move Folders**
    - **Set Security Scopes**

## New client health checks

Based on your feedback, there are two new [Client health checks](../../clients/manage/client-health-checks) in this release:

- Verify disk space not near capacity
- Verify CCMCache is not near drive capacity

Configuration Manager client functionality can be limited when the disk is full. These checks help you maintain healthy clients, which help you better manage the devices.

This release also includes performance improvements to the [Client health dashboard](../../clients/manage/client-health-dashboard).

### Verify disk space not near capacity

Verify that the device's primary disk drive isn't close to full.

The client compares the WMI entry for free disk space against total disk space. If the space remaining is lower than 15% of total disk space, the check fails.

To remediate a failure with this check, free disk space on the primary drive.

### Verify CCMCache is not near drive capacity

Verify that the remaining cache space isn't near the available disk drive space.

The client compares the remaining cache space against free space on the drive with the client cache. If the space remaining on the drive is less than 1% of the total default size, or the remaining cache space is greater than the available drive space, the check fails.

To remediate a failure with this check, free disk space on the drive that contains the cache.

## Improvements to implicit uninstall

If you deploy an application or app group to a user collection that's based on a security group, and you enable [implicit uninstall](../../../apps/deploy-use/uninstall-applications#implicit-uninstall), changes to the security group are now honored. When the site discovers the change in group membership, Configuration Manager uninstalls the app for the user that you removed from the security group.

## Improvements for sending feedback

- You now have the ability to connect feedback you send to Microsoft through the Configuration Manager console to an authenticated Microsoft Entra user account. User authentication will help Microsoft ensure the privacy of your feedback and diagnostic data.
    - Currently, Microsoft Entra authentication for government clouds isn't available.
- The feedback button is now displayed in additional console locations.
    - The following keyboard shortcuts for opening the feedback wizard have also been added to more locations in the console:
        - **Send a smile**: ALT + SHIFT + 7
        - **Send a frown**: ALT + SHIFT + 8

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, select the feedback icon in the upper right corner.
2. Select either **Send a smile** or **Send a frown**.
3. Select **Sign in**and sign in with your Microsoft Entra user account.
    - Selecting **Continue without signing in** will allow you to send feedback, but we won't be able to contact you with questions or updates.
4. Once you're signed in, select **Next** then [provide your feedback](../../understand/product-feedback). If you need to use a different account, you can select **Sign out** to start again.

## Improvements to Management Insights

A new management insights group was added to [Management Insights](../../servers/manage/management-insights). The **Deprecated and unsupported features** group contains the following new rules:

- **Site system roles associated with deprecated or removed features**: This insight checks for installed site system roles for deprecated features that will be removed in a future release.
- **Check if the site uses the asset intelligence sync point role**: This insight checks for installation of the asset intelligence synchronization point role.
- **Configuration Manager client for macOS end of support**: This insight lists the clients running macOS. Support for the Configuration Manager client for macOS and Mac client management ends on December 31, 2022.
- **Certificate registration point is no longer supported**: This insight checks for installation of the certificate registration point site system role. This feature is no longer supported as of March 2022. Configuration Manager versions released before March 2022 will still be able to install and use certificate registration points.
- **Company resource access policies are no longer supported**: This insight checks for company resource access policies. These features are no longer supported as of March 2022. Company resource access includes email, certificate, VPN, Wi-Fi, and Windows Hello for Business profiles. Configuration Manager versions released before March 2022 will still be able to use company resource access policies.

Note

The [prerequisite checker](../../servers/deploy/install/prerequisite-checker) will also check for deprecated and unsupported features.

## Improvements to dashboards

Dashboards, such as the [Windows Servicing](../../../osd/deploy-use/manage-windows-as-a-service#bkmk_2103-dashboard) and [Microsoft Edge Management](../../../apps/deploy-use/deploy-edge#view-the-dashboard) dashboards, now use the Microsoft Edge WebView2 Runtime. To use dashboards, install the [WebView2 console extension](../../servers/manage/admin-console-extensions#get-console-extensions) then reopen the console.

## ADR scheduling improvements for deployments

The **Software available time** and **Installation deadline** for deployments created by an [automatic deployment rule (ADR)](../../../sum/deploy-use/automatically-deploy-software-updates) are now calculated based on the time the ADR evaluation is scheduled and starts. Previously, these times were calculated based on when the ADR evaluation completed. This change makes the **Software available time** and **Installation deadline** consistent and predictable for deployments.

## Console improvements

In this technical preview we've made the following improvements to the Configuration Manager console:

- Added a search filter to the **Products** and **Classifications** tabs in the **Software Update Point Component Properties**
- You can now exclude subcontainers when doing **Active Directory System Discovery** and **Active Directory User Discovery** in untrusted domains
- Added a **Cloud Sync** column to collections to indicate if the collection is synchronizing with Microsoft Entra ID
- Added the **Collection ID** to the collection summary details tab
- Increased the size of the **Membership Rules** pane in the **Properties** page for collections
- Added a **View Script** option for **Run PowerShell Script** steps when using the **View** action for a task sequence

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### Deprecated cmdlets

The following cmdlets for asset intelligence are deprecated and may be removed in a future release:

- Add-CMAssetIntelligenceSynchronizationPoint
- Get-CMAssetIntelligenceProxy
- Get-CMAssetIntelligenceSynchronizationPoint
- Remove-CMAssetIntelligenceSynchronizationPoint
- Send-CMAssetIntelligenceCatalogUpdateRequest
- Set-CMAssetIntelligenceSynchronizationPoint
- Sync-CMAssetIntelligenceCatalog

### Modified cmdlets

#### Add-CMSoftwareUpdatePoint

For more information, see [Add-CMSoftwareUpdatePoint](/en-us/powershell/module/configurationmanager/Add-CMSoftwareUpdatePoint).

**Non-breaking changes**

Added new parameter **Wledbat** to support LEDBAT configuration for software update points.

#### New-CMBoundary

For more information, see [New-CMBoundary](/en-us/powershell/module/configurationmanager/New-CMBoundary).

**Non-breaking changes**

Updated value validation for VPN boundary.

#### New-CMPackage

For more information, see [New-CMPackage](/en-us/powershell/module/configurationmanager/New-CMPackage).

**Non-breaking changes**

Added parameter **IconLocationFile** to use a custom icon from the specified file. For more information, see [Custom icon support for task sequences and packages](technical-preview-2201#bkmk_tsico).

#### Set-CMBoundary

For more information, see [Set-CMBoundary](/en-us/powershell/module/configurationmanager/Set-CMBoundary).

**Non-breaking changes**

Updated value validation for VPN boundary.

#### Set-CMPackage

For more information, see [Set-CMPackage](/en-us/powershell/module/configurationmanager/Set-CMPackage).

**Non-breaking changes**

Added parameter **IconLocationFile** to use a custom icon from the specified file. For more information, see [Custom icon support for task sequences and packages](technical-preview-2201#bkmk_tsico).

#### Set-CMSoftwareUpdatePoint

For more information, see [Set-CMSoftwareUpdatePoint](/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdatePoint).

**Non-breaking changes**

Added new parameter **Wledbat** to support LEDBAT configuration for software update points.