---
layout: Conceptual
title: Security and privacy for compliance settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/plan-design/security-and-privacy-for-compliance-settings
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
description: Learn about the security guidance and recommendations for compliance settings in Configuration Manager.
ms.date: 2021-05-05T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 03271e7d-17e2-1dfd-00cc-973288d27430
document_version_independent_id: 5e4da36d-303c-8b7f-c1af-81ee4bd50841
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/plan-design/security-and-privacy-for-compliance-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/plan-design/security-and-privacy-for-compliance-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/plan-design/security-and-privacy-for-compliance-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d2465a34-0a10-9af4-2a15-08efd3585221
---

# Security and privacy for compliance settings - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

## Security guidance

### Don't monitor sensitive data

To help avoid information disclosure, don't configure configuration items to monitor potentially sensitive information.

### Don't configure compliance rules that use data that can be modified by end users

If you create a compliance rule based on data that users can modify, such as registry settings for configuration choices, the compliance results won't be reliable.

### Only import configuration packs from external sources that are digitally signed

Import configuration packs and other configuration data from external sources only if they have a valid digital signature from a trusted publisher.

Published configuration data can be digitally signed so that you can verify the publishing source and make sure that the data hasn't been tampered with. If the digital signature verification check fails, you're warned and prompted to continue with the import. If you can't verify the source and integrity of the data, don't import unsigned data.

### Implement access controls to protect reference computers

Make sure that when an administrative user configures a registry or file system setting by browsing to a reference computer, the reference computer isn't compromised.

### Secure the communication channel when you browse to a reference computer

To prevent tampering of the data when it's transferred over the network, use internet protocol security (IPsec) or server message block (SMB) signing between the computer that runs the Configuration Manager console and the reference computer.

### Restrict and monitor role-based administration for compliance settings

Restrict and monitor the administrative users who are granted the **Compliance Settings Manager** role-based security role.

Administrative users with this role can deploy configuration items to all devices and all users in the hierarchy. Configuration items are powerful and can include, for example, scripts and registry reconfiguration.

## Privacy information

You can use compliance settings to evaluate whether your client devices are compliant with configuration items that you deploy in configuration baselines. Some settings can be automatically remediated if they out of compliance. Compliance information is sent to the site server by the management point and stored in the site database. The information is encrypted when devices send it to the management point, but not stored in encrypted format in the site database. Compliance information isn't sent to Microsoft.

By default, devices don't evaluate compliance settings. You configure the configuration items and configuration baselines, and then deploy them to devices.