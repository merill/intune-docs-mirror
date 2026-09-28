---
layout: Conceptual
title: Unicode and ASCII support - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/unicode-and-ascii-support
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
description: Learn about support for Unicode and ASCII characters in Configuration Manager objects.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6af050ee-489a-79d3-9857-f7941bb5f0f6
document_version_independent_id: 17e18455-8232-25ad-8e2b-f46749671643
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/unicode-and-ascii-support.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/unicode-and-ascii-support
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/unicode-and-ascii-support.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: c88878c2-3a47-b383-8a47-f23b700848d2
---

# Unicode and ASCII support - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager creates most objects by using Unicode characters. However, several objects only support ASCII characters, or they have other limitations.

## Objects that use ASCII characters

When you create the following objects, Configuration Manager only supports the ASCII character set:

- Site code
- All site system server computer names
- The following Configuration Manager accounts:

    Note

    These accounts support ASCII characters, and RUS characters on a site that runs in Russian.

    - Client push installation account
    - Management point database connect account
    - Network access account
    - Package access account
    - Standard sender account
    - Site system installation account
    - Software update point connection account
    - Software update point proxy server account

        Note

        The accounts that you specify for role-based administration support Unicode.

        The reporting services point account supports Unicode, with the exception of RUS characters.
- Fully qualified domain name (FQDN) for site servers and site systems
- Installation path for Configuration Manager
- SQL Server instance name
- The path for the following site system roles:

    - Enrollment point
    - Enrollment proxy point
    - Reporting services point
    - State migration point
- The path for the following folders:

    - The folder that stores client state migration data
    - The folder that contains the Configuration Manager reports
    - The folder that stores the Configuration Manager backup
    - The folder that stores the installation source files for site setup
    - The folder that stores the prerequisite downloads for use by setup
- The path for the following objects:

    - IIS website
    - Virtual application installation path
    - Virtual application name
- Boot media ISO file names
- [Custom property](../../../develop/adminservice/custom-properties)*names*

## Other limitations

The following limitations are for supported character sets and language versions:

- Configuration Manager doesn't support changing the locale of the site server computer.
- An enterprise certificate authority (CA) doesn't support client computer names that use double-byte character sets (DBCS). The client computer names that you can use are restricted by the PKI limitation of the IA5 character set. Configuration Manager doesn't support CA names or subject name values that use DBCS.

## Objects that aren't localized

The Configuration Manager database supports Unicode for most objects that it stores. When possible, it displays this information in the OS language that matches the locale of a computer. For the client interface or Configuration Manager console to display information in the computer's OS language, the computer's locale must match a client or server language that you install at a site.

Several Configuration Manager objects don't support Unicode. They're stored in the database by using ASCII, or they have other language limitations. This information is always displayed by using the ASCII character set, or in the language that was in use when you created the object.