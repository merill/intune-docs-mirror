---
layout: Conceptual
title: Use PXE for OSD over the network - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network
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
description: Use PXE-initiated OS deployments to refresh a computer's operating system or to install a new version of Windows on a new computer.
ms.date: 2025-09-02T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: bce1206a-d7e8-c37a-79e3-74e44e395582
document_version_independent_id: cc54a729-cb96-5cb1-3416-d0ac9380673e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 8bf60695-2824-15c6-220a-3d237fc591ac
---

# Use PXE for OSD over the network - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Preboot execution environment (PXE)-initiated OS deployments in Configuration Manager let clients request and deploy operating systems over the network. For this deployment method, you send the OS image and the boot images to a PXE-enabled distribution point.

Note

When you create an OS deployment that targets only x64 BIOS computers, both the x64 boot image and x86 boot image must be available on the distribution point.

You can use PXE-initiated OS deployments in the following scenarios:

- [Refresh an existing computer with a new version of Windows](refresh-an-existing-computer-with-a-new-version-of-windows)
- [Install a new version of Windows on a new computer (bare metal)](install-new-windows-version-new-computer-bare-metal)

Complete the steps in one of the OS deployment scenarios, and then use the sections in this article to prepare for PXE-initiated deployments.

Warning

If you use PXE deployments, and configure device hardware with the network adapter as the first boot device, these devices can automatically start an OS deployment task sequence without user interaction. [Deployment verification](../../core/servers/manage/settings-to-manage-high-risk-deployments) doesn't manage this configuration. While this configuration may simplify the process and reduce user interaction, it puts the device at greater risk for accidental reimage.

Starting in version 2006, PXE-based task sequences can download cloud-based content. The PXE-enabled distribution point still requires the boot image, and the device needs an intranet connection to the management point. It can then get additional content from a content-enabled cloud management gateway (CMG). For more information, see [Bootable media support for cloud-based content](deploy-task-sequence-over-internet#bootable-media-support-for-cloud-based-content).

## Configure distribution points for PXE

To deploy operating systems to Configuration Manager clients that make PXE boot requests, configure one or more distribution points to accept PXE requests. Then the distribution point responds to PXE boot requests, and determines the appropriate deployment action. For more information, see [Install or modify a distribution point](../../core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

Note

When you configure a single PXE-enabled distribution point to support multiple subnets, it's not supported to use DHCP options. To allow the network to forward client PXE requests to PXE-enabled distribution points, configure IP helpers on the routers.

When you enable a PXE responder on a distribution point without Windows Deployment Service, it can be on the same server as the DHCP service. When the PXE responder and DHCP are on the same server, add the following settings to support this configuration:

- Set the DWord value **DoNotListenOnDhcpPort** to `1` in the following registry key: `HKLM\Software\Microsoft\SMS\DP`.
- Set DHCP option 60 to `PXEClient`.
- Restart the SCCMPXE and DHCP services on the server.

Important

An on-premises distribution point is required in the following scenarios:

1. Responding to PXE boot requests.
2. When using multicast.

## Prepare a PXE-enabled boot image

To use PXE to deploy an OS, distribute both x86 and x64 PXE-enabled boot images to one or more PXE-enabled distribution points.

- To enable PXE on a boot image, select **Deploy this boot image from the PXE-enabled distribution point** from the **Data Source** tab in the boot image properties.
- When you change the properties for the boot image, update and redistribute the boot image to distribution points. For more information, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

## Manage duplicate hardware identifiers

Configuration Manager may recognize multiple computers as the same device if they have duplicate SMBIOS attributes or you use a shared network adapter. Mitigate these issues by managing duplicate hardware identifiers in hierarchy settings. For more information, see [Manage duplicate hardware identifiers](../../core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## Create an exclusion list for PXE deployments

Note

In some circumstances, the process to [Manage duplicate hardware identifiers](../../core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers) may be easier.

The behaviors of each can cause different results in some scenarios. The exclusion list never boots a client with the listed MAC address, no matter what.

The duplicate ID list doesn't use the MAC address to find the task sequence policy for a client. If it matches the SMBIOS ID, or if there's a task sequence policy for unknown machines, the client still boots.

When you deploy operating systems with PXE, you can create an exclusion list on each distribution point. Add the MAC addresses to the exclusion list of the computers you want the distribution point to ignore. Listed computers don't receive the deployment task sequences that Configuration Manager uses for PXE deployment.

1. Create a text file on the PXE-enabled distribution point. For example, name the file **pxeExceptions.txt**.
2. Use a plain text editor, such as Notepad, to edit the file. Add the MAC addresses of the computers that the PXE-enabled distribution point should ignore. Separate the MAC address values by colons, and enter each address on a separate line. For example: `01:23:45:67:89:ab`
3. Save the text file on the PXE-enabled distribution point. You can save it to any location on the server.
4. Edit the registry on the PXE-enabled distribution point. Browse to the following registry path: `HKLM\Software\Microsoft\SMS\DP`. Create a **MACIgnoreListFile** string value. Add the full path to the text file on the PXE-enabled distribution point.

    Warning

    If you use the Registry Editor incorrectly, you might cause serious problems that may require you to reinstall Windows. Microsoft can't guarantee that you can solve problems that result from using the Registry Editor incorrectly. Use the Registry Editor at your own risk.
5. After you make this registry change, restart the WDS service or PXE responder service. You don't need to restart the server.

## RamDisk TFTP block size and window size

You can customize the RamDisk TFTP block and window sizes for PXE-enabled distribution points. If you've customized your network, a large block or window size could cause the boot image download to fail with a time-out error. The RamDisk TFTP block and window size customizations allow you to optimize TFTP traffic when using PXE to meet your specific network requirements. To determine what configuration is most efficient, test the customized settings in your environment. For more information, see [Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points](../get-started/prepare-site-system-roles-for-operating-system-deployments#customize-the-ramdisk-tftp-block-and-window-sizes-on-pxe-enabled-distribution-points).

## Configure deployment settings

To use a PXE-initiated OS deployment, configure the deployment to make the OS available for PXE boot requests. Configure available operating systems on the **Deployment Settings** tab in the deployment properties. For the **Make available to the following** setting, select one of the following options:

- Configuration Manager clients, media, and PXE
- Only media and PXE
- Only media and PXE (hidden)

## Option 82 during PXE DHCP handshake

Configuration Manager supports option 82 during the PXE DHCP handshake with the PXE responder without WDS. If you require option 82, make sure to use the PXE responder without WDS. Configuration Manager doesn't support option 82 with WDS.

## Deploy the task sequence

Deploy the OS to a target collection. For more information, see [Deploy a task sequence](deploy-a-task-sequence). When you deploy operating systems by using PXE, you can configure whether the deployment is required or available.

- **Required deployment**: Required deployments use PXE without any user intervention. The user can't bypass the PXE boot. However, if the user cancels the PXE boot before the distribution point responds, the OS isn't deployed.
- **Available deployment**: Available deployments require that the user is present at the destination computer. A user must press the **F12** key to continue the PXE boot process. If a user isn't present to press **F12**, the computer boots into the current OS, or from the next available boot device.

You can redeploy a required PXE deployment by clearing the status of the last PXE deployment assigned to a Configuration Manager collection or a computer. For more information on the **Clear Required PXE Deployments** action, see [Manage clients](../../core/clients/manage/manage-clients#manage-clients-from-the-devices-node) or [Manage collections](../../core/clients/manage/collections/manage-collections). This action resets the status of that deployment and reinstalls the most recent required deployments.

Important

The PXE protocol isn't secure. Make sure that the PXE server and the PXE client are located on a physically secure network, such as in a data center, to prevent unauthorized access to your site.

## How the boot image is selected for PXE

When a client boots with PXE, Configuration Manager provides the client with a boot image to use. Configuration Manager uses a boot image with an exact architecture match. If a boot image with the exact architecture isn't available, Configuration Manager uses a boot image with a compatible architecture.

The following list provides details about how a boot image is selected for clients booting with PXE:

1. Configuration Manager looks in the site database for the system record that matches the MAC address or SMBIOS of the client that's trying to boot.

    Note

    If a computer that's assigned to a site boots to PXE for a different site, the policies aren't visible for the computer. For example, if a client is already assigned to site A, the management point and distribution point for site B aren't able to access the policies from site A. The client doesn't successfully PXE boot.
2. Configuration Manager looks for task sequences that are deployed to the system record found in step 1.
3. In the list of task sequences found in step 2, Configuration Manager looks for a boot image that matches the architecture of the client that's trying to boot. If a boot image is found with the same architecture, that boot image is used.

    If it finds more than one boot image, it uses the *highest* or most recent task sequence deployment ID. In the case of a multi-site hierarchy, the *higher* letter site would take precedence in that string comparison. For example, if they're both matched otherwise, a year-old deployment from site ZZZ is selected over yesterday's deployment from site AAA.
4. If a boot image isn't found with the same architecture, Configuration Manager looks for a boot image that's compatible with the architecture of the client. It looks in the list of task sequences found in step 2. For example, a 64-bit BIOS/MBR client is compatible with 64-bit boot images. UEFI clients are only compatible with matching architecture. A 64-bit UEFI client is compatible with only 64-bit boot images and Arm64 bit UEFI client is compatible with only Arm64 boot images.

Important

Starting with the ADK for Windows 11, version 22H2 the 32-bit versions of Windows PE are no longer included in the Windows PE add-ons. The last supported version of 32-bit Windows PE is available in the Windows PE add-on for Windows 10, version 2004.