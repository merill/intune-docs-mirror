---
layout: Conceptual
title: Capabilities in Technical Preview 1603 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1603
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
description: Learn about features available in the Technical Preview for Configuration Manager, version 1603.
ms.date: 2017-01-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 653dfc1b-3372-9cf1-c02e-d3f090f097b9
document_version_independent_id: 6fd4e5f4-a8b8-8d37-6284-7dd3a5b17272
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1603.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1603
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1603.md
platformId: 52cff789-6f86-a117-41a1-65d9aa3b97c6
---

# Capabilities in Technical Preview 1603 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the Technical Preview for Configuration Manager, version 1603. You can install this version to update and add new capabilities to your Configuration Manager technical preview site. Alternately, when you use System Center Technical Preview 5, this version installs as a baseline version of the Configuration Manager Technical Preview. Before installing this version of the technical preview, review the introductory topic, [Technical Preview for Configuration Manager](technical-preview), to become familiar with general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback about the features in a technical preview.

**Known Issues for this Technical Preview:**

- This release includes updates for previously released features but does not introduce new features. Therefore, the Features page of the Update Wizard will be empty if you have previously upgraded to 1602 and enabled all of the features included in 1602.
- After your site server updates to the Technical Preview 1603, clients are unable to use any remote control features until they also update to version 1603.

    **The following are new features you can try out with this version.**

## Improvements to Software Center

### New tiled view for apps

End users can now choose between a list of apps, or a tiled view of apps in the **Applications** tab of Software Center.

### Select multiple updates in Software Center

In the **Updates** tab of Software Center, you can now select multiple updates, or select **Update All** to begin installing multiple updates simultaneously.

## Improvements to remote control

### Limit shared clipboard access in a remote control session

You can now enable the new remote tools client setting **Prompt user for shared clipboard file transfer permission** to limit access to the shared clipboard in a remote control session.

When enabled, the end user who is sharing a remote session must grant permissions to the viewer of that session before the viewer can transfer files from the session to their local machine via the shared clipboard.

This adds a layer of protection for the end user as previously, if the viewer was granted full control of the end user's computer, they would be able to use the shared clipboard to transfer files from the session to their local computer in a way that was entirely transparent to the end user.

## Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points

In the 1603 Technical Preview, you can customize the RamDisk TFTP block size and window size for PXE-enabled distribution points. If you have customized your network, it could cause the boot image download to fail with a time-out error because the block or window size is too large. The RamDisk TFTP block size and window size customization allow you to optimize TFTP traffic when using PXE to meet your specific network requirements. You will need to test the customized settings in your environment to determine what is most efficient.

- **TFTP block size**: The block size is the size of the data packets that are sent by the server to the client that is downloading the file (as discussed in RFC 2347). A larger block size allows the server to send fewer packets, so there are fewer round-trip delays between the server and the client. However, a large block sizes leads to fragmented packets, which most PXE client implementations do not support.
- **TFTP window size**: TFTP requires an acknowledgment (ACK) packet for each block of data that is sent. The server does not send the next block in the sequence until it receives the ACK packet for the previous block. TFTP windowing is a feature in Windows Deployment Services that enables you to define how many data blocks it takes to fill a window. The server sends the data blocks back-to-back until the window is filled, and then the client sends an ACK packet. Increasing this window size reduces the number of round-trip delays between the client and server and decreases the overall time that is required to download a boot image.

### Try it out!

Try to complete the following tasks and then use the feedback information near the top of this topic to let us know how it worked:

- I can customize the RamDisk TFTP window size on the PXE-enabled distribution point.
- I can customize the RamDisk TFTP block size on the PXE-enabled distribution point.

### To modify the RamDisk TFTP window size

- Add the following registry key on PXE-enabled distribution points to customize the RamDisk TFTP window size:

    **Location**: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\SMS\DP Name: RamDiskTFTPWindowSize

    **Type**: REG\_DWORD

    **Value**: &lt;customized window size&gt;

    The default value is 1 (1 data block fills the window)

### To modify the RamDisk TFTP block size

- Add the following registry key on PXE-enabled distribution points to customize the RamDisk TFTP window size:

    **Location**: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\SMS\DP Name: RamDiskTFTPBlockSize

    **Type**: REG\_DWORD

    **Value**: &lt;customized block size&gt;

    The default value is 4096 (4k).