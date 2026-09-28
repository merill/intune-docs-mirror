---
layout: Conceptual
title: Configure Endpoint Protection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-configure
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
description: Learn how to set up Configuration Manager to update and distribute malware definitions for Windows Defender.
ms.date: 2018-03-22T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e996a842-ae21-c222-97ba-fa6065e68b36
document_version_independent_id: e106333d-9fae-25e3-a643-10ea1c71aed3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-protection-configure.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-protection-configure
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-protection-configure.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: ae209c14-b7f6-6805-a8a6-c1b78f3914eb
---

# Configure Endpoint Protection - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Before you can use Endpoint Protection to manage security and malware on Configuration Manager client computers, you must perform the configuration steps detailed in this article.

## How to Configure Endpoint Protection in Configuration Manager

Endpoint Protection in Configuration Manager has external dependencies and dependencies in the product.

### Steps to Configure Endpoint Protection in Configuration Manager

Use the following table for the steps, details, and more information about how to configure Endpoint Protection.

Important

If you manage endpoint protection for Windows 10 or later computers, then you must configure Configuration Manager to update and distribute malware definitions for Windows Defender. Windows Defender is included in Windows 10 and later but custom client settings for Endpoint Protection (**Step 5** below) are still required. 

| Steps | Details |
| --- | --- |
| **Step 1:**[Create an Endpoint Protection point site system role](endpoint-protection-site-role) | The Endpoint Protection point site system role must be installed before you can use Endpoint Protection. It must be installed on one site system server only, and it must be installed at the top of the hierarchy on a central administration site or a stand-alone primary site. |
| **Step 2:**[Configure alerts for Endpoint Protection](endpoint-configure-alerts) | Alerts inform the administrator when specific events have occurred, such as a malware infection. Alerts are displayed in the **Alerts** node of the **Monitoring** workspace, or optionally can be emailed to specified users. |
| **Step 3:**[Configure definition update sources for Endpoint Protection clients](endpoint-definition-updates) | Endpoint Protection can be configured to use various sources to download definition updates. |
| **Step 4:**[Configure the default antimalware policy and create custom antimalware policies](endpoint-antimalware-policies) | The default antimalware policy is applied when the Endpoint Protection client is installed. Any custom policies you have deployed are applied by default, within 60 minutes of deploying the client. Ensure that you have configured antimalware policies before you deploy the Endpoint Protection client. |
| **Step 5:**[Configure custom client settings for Endpoint Protection](endpoint-protection-configure-client) | Use custom client settings to configure Endpoint Protection settings for collections of computers in your hierarchy. Note: Do not configure the default Endpoint Protection client settings unless you are sure that you want these settings applied to all computers in your hierarchy. |