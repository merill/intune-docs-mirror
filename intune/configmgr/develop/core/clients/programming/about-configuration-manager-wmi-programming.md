---
layout: Conceptual
title: About Configuration Manager WMI Programming - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming
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
description: Programming the Configuration Manager client WMI provider differs according to the programming language you use.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: a6a5cf4d-e2ef-ceb6-5c4f-d1b915fd0ed2
document_version_independent_id: ec4ef975-b1d6-4624-1134-be57df957132
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a9a2236e-abe5-41f1-5acc-f163719a2afa
---

# About Configuration Manager WMI Programming - Configuration Manager | Microsoft Learn

Programming the Configuration Manager client Windows Management Instrumentation (WMI) provider differs according to the programming language you use.

## C#

If you use C#, use the System.Management namespace. It provides access to a rich set of management information and management events about the system, devices, and applications that are instrumented to the WMI infrastructure.

Note

The managed Configuration Manager library is for use with a Configuration Manager site server and cannot be used to access client WMI namespaces.

For more information about connecting to the Configuration Manager client WMI namespace by using the System.Management namespace, see [How to connect to the Configuration Manager client WMI namespace by using System.Management](how-to-connect-to-the-client-wmi-namespace).

For more information about using Configuration Manager client WMI namespace objects by using the System.Management namespace, see [How to read a WMI object by using System.Management](how-to-read-a-wmi-object-by-using-system.management).

For more information about using the System.Management namespace, see [System.Management Namespace](/en-us/dotnet/api/system.management).

## VBScript

If you use VBScript, you access and use Configuration Manager client WMI objects by using the same coding techniques that are used for accessing other WMI objects, including the Configuration Manager WMI objects. For more information, see the [Windows Management Instrumentation](/en-us/windows/win32/wmisdk/wmi-start-page).

## Client WMI namespace

The Configuration Manager client WMI namespace begins at `\\<client>\root\ccm`. For example, `root\ccm` contains the [SMS_Client](../../../reference/core/clients/client-classes/sms_client-client-wmi-class) class that can be used to get and set client information.