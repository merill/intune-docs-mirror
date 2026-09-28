---
layout: Conceptual
title: Technical preview 2009 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2020/technical-preview-2009
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2009.
ms.date: 2020-09-14T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 754cbaca-46c2-a41b-b0ef-1ad338911cf9
document_version_independent_id: 0528f0e3-3053-6094-8864-995ea9c9f1cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2020/technical-preview-2009.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2020/technical-preview-2009
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2020/technical-preview-2009.md
platformId: 8480535f-9aba-1f31-5575-30e6e9e00dfc
---

# Technical preview 2009 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2009. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Cloud management gateway with virtual machine scale set

Based on your feedback, cloud management gateway (CMG) deployments now use virtual machine scale sets in Azure. This change introduces support for Azure Cloud Solution Provider (CSP) subscriptions.

Except for the following aspects, the configuration, operation, and functionality of the CMG remains the same:

- A new prerequisite is to register the following resource providers in your Azure subscription:

    - Microsoft.KeyVault
    - Microsoft.Storage
    - Microsoft.Network
    - Microsoft.Compute

    For more information, see [Azure resource providers and types](/en-us/azure/azure-resource-manager/management/resource-providers-and-types).
- When you create a CMG in the Configuration Manager console, the default option to deploy the cloud service is as a **Virtual machine scale set**. If necessary, you can still select **Cloud service (classic)** to use the existing Azure Resource Manager deployment.
- For a CMG deployment to a virtual machine scale set, the service name is different. This name is from the [CMG server authentication certificate](../../clients/manage/cmg/server-auth-cert).

    - With the previous Azure Resource Manager deployment option, the service name is in the **cloudapp.net** domain. For example, **GraniteFalls.CloudApp.Net**.
    - With a virtual machine scale set, the service name uses the **cloudapp.azure.com** domain along with the region. For example, **GraniteFalls.EastUS.CloudApp.Azure.Com** for a deployment in the **East US** Azure region.
- The CMG connection point only communicates with the virtual machine scale set in Azure over HTTPS. It doesn't require TCP-TLS ports 10140-10155 to build the CMG communication channel.

If you already have an existing CMG deployment using Azure Resource Manager, you don't have to [redeploy the service](../../clients/manage/cmg/modify-cloud-management-gateway#redeploy-the-service). This new deployment method is primarily to support CSP customers to use the CMG. If you do redeploy the service to leverage the new architecture, since the service name changes, you'll need to make configuration changes:

- If you issue the CMG server authentication certificate for your own domain name, update the CNAME record in DNS. For example, the certificate uses **GraniteFalls.Contoso.Com**. First deploy the new service with the same certificate. When you're ready to switch, change the CNAME to point to the virtual machine scale set. For example, change the CNAME mapping for **GraniteFalls.Contoso.Com** to **GraniteFalls.EastUS.CloudApp.Azure.Com**.
- If you're using a CMG server authentication certificate from a third-party provider, they issued the certificate in the cloudapp.net domain. You need to get a new certificate for the new service domain. For example, **GraniteFalls.EastUS.CloudApp.Azure.Com**. Create the new service with the new certificate, and add a second CMG connection point. Then wait at least one day before you delete the old CMG and remove the original CMG connection point. If clients are turned off or without an internet connection, you may need to wait longer.

For more general information on the cloud management gateway, see [Overview of CMG](../../clients/manage/cmg/overview).

### Preview limitations for CMG with virtual machine scale sets

The following CMG configurations are currently not supported in this release:

- Azure US Government Cloud
- Enforce TLS 1.2

## Improvements to remote control

This release continues to improve the functionality of remote control as first introduced in technical preview version 1906. You can now connect to any Configuration Manager client with an online status.

The following prerequisites now apply:

- In the **Remote Tools** group of client settings:

    - Enable remote control
    - Add the user as a permitted viewer for remote control.

    For more information, see [About client settings - Remote Tools](../../clients/deploy/about-client-settings#remote-tools).
- Configuration Manager client requirements:

    - Update the client to the latest version.
    - The client status needs to be online.
    - If the client is internet-based, use a [cloud management gateway (CMG)](../../clients/manage/cmg/overview).

        Important

        This feature was removed in Configuration Manager technical preview branch version 2112. For more information, see [A new remote assistance tool](../2021/technical-preview-2112#bkmk_cmgrc).

    Note

    Remote control now supports all available client authentication methods. For example, internet-based clients might authenticate using one of the following methods:

    - A valid PKI [client certificate](../../clients/manage/cmg/configure-authentication#pki-certificate)
    - [Microsoft Entra ID](../../clients/deploy/deploy-clients-cmg-azure)
    - [Token-based authentication](../../clients/deploy/deploy-clients-cmg-token)

    These requirements aren't unique to remote control. If you properly configure clients to communicate with a CMG, HTTPS management points, or sites with enhanced HTTP, then they already use a supported authentication method.

For more information on how to use remote control, see [the instructions from version 1906](../2019/technical-preview-1906#connect-to-a-client-from-the-console).

1. When you start a remote control session, select the option to **Connect via CMG or HTTPS MP** for any of the following scenarios:

    - CMG
    - HTTPS management point
    - Enhanced HTTP site

    ![Remote Control Address Connection window with CMG selection](media/4575930-remote-control-address-connection.png)
2. Enter the fully qualified domain name (FQDN) of the applicable service. For example:

    - CMG: `granitefalls.cloudapp.net`
    - HTTPS management point: `mp1.contoso.com`

If you specify a CMG, the permitted viewer and the target client device need a connection to the internet. This connection is required even if they're on the internal network.

## Deploy an OS over CMG using boot media

Starting in current branch version 2006, the cloud management gateway (CMG) supports running a task sequence with a boot image when you start it from Software Center. With this release, you can now use boot media to reimage internet-based devices that connect through a CMG. This scenario helps you better support remote workers. If Windows won't start so that the user can access Software Center, you can now send them a USB drive to reinstall Windows.

### Prerequisites for boot media via CMG

- [Set up a CMG](../../clients/manage/cmg/setup-cloud-management-gateway)
- For all content referenced in the task sequence, distribute it to a content-enabled CMG or a cloud distribution point. For more information, see [Distribute content](../../servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).
- Enable the following client settings in the [Cloud services](../../clients/deploy/about-client-settings#cloud-services) group:

    - **Allow access to cloud distribution point**
    - **Enable clients to use a cloud management gateway**
- Configure the **Apply Network Settings** task sequence step to join a workgroup. During the task sequence, the device can't join the on-premises Active Directory domain. It doesn't have connectivity to a domain controller to join the domain.
- When you [deploy the task sequence](../../../osd/deploy-use/deploy-a-task-sequence) to a collection, configure the following settings:

    - User experience page: **Allow task sequence to run for client on the internet**
    - Deployment settings page: Make available to an option that includes media.
    - Distribution points page, deployment options: **Download content locally when needed by the running task sequence**. For more information, see [Deployment options](../../../osd/deploy-use/deploy-a-task-sequence#bkmk_deploy-options).
- Make sure the device has a constant internet connection while the task sequence runs. Windows PE doesn't support wireless networks, so the device needs a wired network connection.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

Start the create task sequence media wizard for bootable media. For more information, see [Create bootable media](../../../osd/deploy-use/create-bootable-media). Modify the standard process using the following steps:

- On the **Media Management** page of the wizard, select the option for **Internet-based media**.
- On the **Security** page, set a strong password to protect this media.
- On the **Boot Image** page, select the **Cloud management gateway** for this boot media to use.

When you boot an internet-connected device using this media, it communicates with the specified CMG. The boot media downloads the policy for the task sequence deployment via the CMG. As the task sequence runs, it downloads any additional content and policies over the internet.

After the task sequence runs, the client uses token-based authentication.

## View collection relationships

Based on your feedback, you can now view dependency relationships between collections in a graphical format. It shows limiting, include, and exclude relationships.

[![View collection dependency relationships in a graphical format](media/3608121-view-dependent-relationships.png)](media/3608121-view-dependent-relationships.png#lightbox)

If you want to change or delete collections, view the relationships to understand the impact of the proposed change. Before you create a deployment, look at the potential target collection for any include or exclude relationships that might affect the deployment.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Device Collections** node.
2. Select a collection, and then in the ribbon, select **View Relationships**. On the main page:

    - To view the relationships with parent collections, select **Dependency**.
    - To view the relationships with child collections, select **Dependent**.

    For example, if you select the **All Systems** collection to view its relationships, the **Dependency** node will be **0** as it has no parent collections.

Use the following tips to navigate the relationship viewer:

- Select the plus (`+`) or minus (`-`) icons next to the collection name to expand or collapse members of a node.
- The number in parentheses after the collection name is the number of relationships. If the number is **0**, then that collection is the final or leaf node in that relationship tree.
- The style and color of the line between the collections determines the type of relationship:

    ![Collection dependency relationship line style legend](media/3608121-collection-relationship-legend.png)

    If you hover over a specific line, a tooltip shows the relationship type.
- When the width of the tree is larger than the window, use the green arrows to the right or the left to view more.
- When a node of the relationship tree is larger than the available space, select **More** to change the view to just that node.
- To navigate to a prior view, select the **Back** arrow in the upper right corner. Select the **Home** icon to return to the main page.
- Use the **Search** box in the upper right corner to locate a collection in the current tree view.
- Use the **Navigator** in the lower right corner to zoom and pan around the tree. You can also print the current view.

## Wake machine at deployment deadline using peer clients on the same remote subnet

Wake on LAN (WoL) has always posed a problem in complex, subnetted networks. Good networking best practice reduces the size of broadcast domains to mitigate against the risk of broadcast traffic adversely affecting the network. The most common way to limiting network broadcast is by not allowing broadcast packets to be routed between subnets. Another option is to enable subnet directed broadcasts but most organizations don't allow the magic packet to traverse internal routers.

In version 1810, the introduction of [peer wake up](../../clients/deploy/configure-wake-on-lan#bkmk_wol-1810) allowed an administrator to wake a device or collection of devices, on demand using the client notification channel. Overcoming the need for the server to be in the same broadcast domain as the client.

This latest improvement allows the Configuration Manager site to wake devices at the deadline of a deployment, using that same client notification channel. Instead of the site server issuing the magic packet directly, the site uses the client notification channel to find an online machine in the last known subnet of the target device(s) and instructs the online client to issue the WoL packet for the target device.

### Try it out!

Try to complete the tasks. Then send [Feedback](technical-preview-2003#bkmk_feedback) with your thoughts on the feature.

1. At the site level, enable [Wake on LAN](../../clients/deploy/configure-wake-on-lan).

    1. Go to **Administration &gt; Site Configuration &gt; Sites**.
    2. Right-click on the site and select **Properties**.
    3. On the **Wake on LAN** tab, select **Enable Wake on LAN for this site**.
2. Verify **Allow network wake-up** under the [**Power Management** client settings](../../clients/deploy/about-client-settings#power-management) is enabled.
3. Deploy an application as **Required** with the **Send wake-up packages** option and a **Deadline**.

    [![Send wake-up packets option in the deployment wizard](media/3734819-wol-deployment.png)](media/3734819-wol-deployment.png#lightbox)

## Improvements to in-console notifications

You now have an updated look and feel for in-console notifications. Notifications are more readable and the action link is easier to find. Additionally, the age of the notification is displayed to help you find the latest information. If you dismiss or snooze a notification, that action is now persistent for your user across consoles.

Right-click or select `...` on the notification to take one of the following actions:

- **Translate text**: Launches [Bing Translator](https://www.bing.com/translator/) for the text.
- **Copy text**: Copies the notification text to the clipboard.
- **Snooze**: Snoozes the notification for the specified duration:
    - One hour
    - One day
    - One week
    - One month
- **Dismiss**: Dismisses the notification.

To see these improvements for notifications, update the Configuration Manager console to the latest version.

## Notifications for devices no longer receiving updates

To help you manage security risk in your environment, you'll be notified in-console about devices with operating systems that are past the end of support date and that are no longer eligible to receive security updates. Additionally, a new **Management Insights** rule was added to detect Windows 7, Windows Server 2008, and Windows Server 2008 R2 without [Extended Security Updates (ESU)](https://support.microsoft.com/help/4497181/lifecycle-faq-extended-security-updates).

Environments with the following operating systems installed on client devices receive a notification:

- [Windows 7](/en-us/lifecycle/products/windows-7), [Windows Server 2008 (non-Azure)](/en-us/lifecycle/products/windows-server-2008), and [Windows Server 2008 R2 (non-Azure)](/en-us/lifecycle/products/windows-server-2008-r2) without ESU.
- Versions of Windows 10 Semi-Annual Channel that are past the end-of-support date.
    - [Enterprise and Education](/en-us/lifecycle/products/windows-10-enterprise-and-education)
    - [Home and Pro](/en-us/lifecycle/products/windows-10-home-and-pro)

![Screenshot of in-console notifications for operating systems past the end of support date](media/7520646-notification.png)

Selecting **More info** on either of these notifications takes you to **All Insights** in **Management Insights**. Choose from the following options for review:

- For Windows 10 clients, review the **Update clients to a supported Windows 10 version** rule in the **Simplified Management** group. The rule shows clients running Windows 10 versions that are no longer supported or will reach end of service within the next three months.

    ![Screenshot of the Simplified Management group in Management Insights](media/7520646-windows-10-more-info.png)
- For Windows 7, Windows Server 2008, and Windows Server 2008 R2 without [Extended Security Updates (ESU)](https://support.microsoft.com/help/4497181/lifecycle-faq-extended-security-updates), review the new rule, **Update clients running Windows 7 and Windows Server 2008** in the **Security** group. The rule shows clients running Windows 7, Windows Server 2008, and Windows Server 2008 R2 that are no longer receiving security updates.

    ![Screenshot of the Security group in Management Insights](media/7520646-windows-7-more-info.png)

## Improved Windows Server restart experience for non-administrator accounts

For a low-rights user on a device that runs Windows Server, by default they aren't assigned the user rights to restart Windows. When you target a deployment to this device, this user can't manually restart. For example, they can't restart Windows to install software updates.

Starting in this release, you can now control this behavior as needed. In the **Computer Restart** group of client settings, enable the following setting: **When a deployment requires a restart, allow low-rights users to restart a device running Windows Server**.

Important

Allowing low-rights users to restart a server can potentially impact other users or services.

For more information on client settings, see [How to configure client settings](../../clients/deploy/configure-client-settings).

## Improvements to OS deployment

This release includes the following improvements to OS deployment:

- After you update the site to version 2009, the Configuration Manager console shows the size in KB for all existing task sequences. Previously, the console showed a size of **0** for existing task sequences, which only updated when you modified the task sequence.
- It resolves a bug with boot image metadata on PXE-enabled distribution points that have multiple content library drives. This bug could cause the client to fail to download the boot image over TFTP.