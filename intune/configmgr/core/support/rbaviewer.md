---
layout: Conceptual
title: Role-based administration tool - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/rbaviewer
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
description: Use the role-based administration and auditing tool to model and audit security roles and scopes in Configuration Manager.
ms.date: 2021-04-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c6b490c5-2f4f-a987-b5a6-5c926bf47ad4
document_version_independent_id: 93d71469-de90-2eb3-654f-a898198bf74d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/rbaviewer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/rbaviewer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/rbaviewer.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
platformId: 2e27d28b-2f46-219a-756b-0447fdfcf6c6
---

# Role-based administration tool - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The role-based administration and auditing tool is one of the [Configuration Manager tools](tools). Use this tool for the following tasks:

- Model security roles with specific permissions
- Audit the security scopes and security roles that other users have

## Requirements

- Run it on the same computer as the Configuration Manager site server
- You have the **Full Administrator**, **Read-only Analyst**, or **Security Administrator** role
- Assign your account to the **All** security scope and all collections
- (*Optional*) To analyze report folder security, you need SQL Server access
- (*Optional*) To analyze report drill-through, run this tool on the site system server with the reporting services point role

## Procedures

### Model permissions for a new role

Use the following procedure to model permissions for a new role that you want to create:

1. Run **RBAViewer.exe**.
2. Select the base security roles you want to build on, or start from an empty permission set. Select the necessary permissions.
3. Select **Analyze** to see the user interface this custom role will see.

    Note

    To see whether there's an existing security role that meets your requirements, switch to the **Similarity** tab.
4. Select **Export** to save the role as an XML file. Then import it to the Configuration Manager console. For more information, see [Create custom security roles](../servers/deploy/configure/configure-role-based-administration#create-custom-security-roles).

### Audit existing security scopes

Use the following procedure to audit all existing administrative users, collections, and security scopes in Configuration Manager:

1. Run **RBAViewer.exe**.
2. Select the **Audit RBA** button in the toolbar.

    1. To view the collection-limited relationships in a tree view, switch to the **Collection Summary** tab.
    2. To view objects assigned to a security role, switch to the **Scope Summary** tab.

### Audit a specific user

Use the following procedure to audit the role-based administration configuration for a specific user:

1. Run **RBAViewer.exe**.
2. Select the **Run As** button in the toolbar.
3. Input the specific user name to check the permissions for that account.
4. The tool displays the security roles assigned to the user or the security group the user belongs to. It also displays the objects this user can see and the actions they can take in the console.