---
layout: Conceptual
title: OS Deployment Site Role Configuration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
description: Learn about the different operating system deployment site roles and how to configure these roles by using the SMS_SiteControlFile class.
locale: en-us
document_id: 1b44e9c9-b3ee-9469-7dee-1a6665512e4c
document_version_independent_id: 88060bc8-153d-321a-9b37-2a53689e0ec7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-operating-system-deployment-site-role-configuration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-operating-system-deployment-site-role-configuration.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 2e0b7f7e-6f23-87eb-8284-c690b6dc9f5c
---

# OS Deployment Site Role Configuration - Configuration Manager | Microsoft Learn

The following two site roles are of particular importance to Operating System Deployment in Configuration Manager.

## State Migration Point Site Role

The state migration point (SMP) is a Configuration Manager site role that provides a secure location to store user state information before an operating system deployment. You can store the user state on the SMP while the operating system deployment proceeds and then restore the user state to the new computer from the SMP. Each SMP site role can only be a member of one Configuration Manager site.

## PXE Service Point Site Role

You use the PXE protocol to initiate operating system deployments to Configuration Manager clients. Configuration Manager uses the PXE service point site role to initiate the operating system deployment process. The PXE service point must be configured to respond to PXE boot requests made by Configuration Manager clients on the network and then interact with Configuration Manager infrastructure to determine the appropriate installation actions to take.

## Programming the Site Roles

Most information about Configuration Manager site roles is stored in the Configuration Manager site control file.

You can make updates to the site control file through Windows Management Instrumentation (WMI) by using the [SMS_SiteControlFile](../reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class) class. In managed code, `IResultObject` allows access to the site control file. For more information, see [About the Configuration Manager Site Control File](../core/understand/about-the-configuration-manager-site-control-file).

The properties you will need to access are stored as system resources in the site control file. For example, the following site control file section shows the properties for the PXE service point site role.

```
BEGIN_SYSTEM_RESOURCE_USE
    RESOURCE<Windows NT Server><["Display=\\SERVERNAME\"]MSWNET:["SMS_SITE=ABC"]\\SERVERNAME\>
    ROLE<SMS PXE Service Point>
    PROPERTY <Server Remote Name><><><0>
    PROPERTY <IsActive><><><1>
    PROPERTY <BindPolicy><><><1>
    PROPERTY <ResponseDelay><><><15>
    PROPERTY <PXEPassword><><><0>
    PROPERTY <AuthType><><><0>
    PROPERTY <UserName><><><0>
    PROPERTY <CertificateType><><><0>
    PROPERTY <CertificateExpirationDate><128568119567070000><><0>
    PROPERTY <CertificateFile><><><0>
    PROPERTY <PXECertGUID><XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX><><0>
    BEGIN_PROPERTY_LIST
        <BindExcept>
        <11:11:11:11:11:11>
        <22:22:22:22:22:22>
    END_PROPERTY_LIST
    BEGIN_PROPERTY_LIST
        <Objects Polled By Site Status>
        <["Display=\\SERVERNAME\C$\Program Files\Microsoft Configuration Manager\"]MSWNET:["SMS_SITE=ABC"]\\SERVERNAME\C$\Program Files\Microsoft Configuration Manager\>
    END_PROPERTY_LIST
END_SYSTEM_RESOURCE_USE
```

When you have access to the site control file, the various properties are stored as embedded properties or in embedded property lists. For example `UserName` in the sample above is an embedded property. Other properties are stored as embedded property lists. In the example above, the MAC addresses in `BindExcept` are stored in an embedded property list.