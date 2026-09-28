---
layout: Conceptual
title: Role-Based Administration - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration
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
description: This section provides topics about programmatically managing role-based administration in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 782eda4a-7370-e0a1-2720-8106030a4516
document_version_independent_id: 4b60ed59-c364-c873-f5dc-0fd8c200e53e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/role-based-administration.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/role-based-administration
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/role-based-administration.md
cmProducts: []
platformId: 85bb64d0-fb02-4142-3a02-dc2c503a884e
---

# Role-Based Administration - Configuration Manager | Microsoft Learn

This section provides topics about programmatically managing role-based administration in Configuration Manager.

Note

For more information, see [Fundamentals of role-based administration](../../../../core/understand/fundamentals-of-role-based-administration).

## About role-based administration

Role-based administration security rights are applied to a domain user or a security group. In Configuration Manager security rights are replicated to all sites in the hierarchy. You can use any single site to change the security rights of a user or security group and it will be automatically replicated to all other sites in that same hierarchy.

Security consists of two basic concepts: security roles and security scopes.

### Security Roles

A security role in Configuration Manager grants permissions to the types of objects a user can interact with, and the actions they can perform with those objects. Configuration Manager provides multiple built-in security roles.

### Security Scopes

A security scope in Configuration Manager establishes security restrictions between the user and object instances. The permissions the user will have with that object instance are determined by their assigned security roles.

### Administrative Users and Security Groups

Domain users and security groups can be granted access to Configuration Manager. The permissions set on an administrator consist of a combination of a security role and scope. A scope is applied to a role that the administrator has. It can never be applied independently of the role.