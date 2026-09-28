---
layout: FAQ
title: Admin service FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/faq
summary: >
  <p><em>Applies to: Configuration Manager (current branch, technical preview branch, long-term servicing branch)</em></p>
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
description: Frequently asked questions (FAQ) about the Configuration Manager administration service
ms.date: 2021-04-16T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: faq
locale: en-us
document_id: 8f16bbd8-4bdb-6e7f-2efe-b53225ced246
document_version_independent_id: 6f46d7f5-ce87-a5e6-19ac-63f55627bb74
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/adminservice/faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/adminservice/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/adminservice/faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 73f95004-d5ba-9317-1152-392e7c775b2c
---

# Admin service FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch, technical preview branch, long-term servicing branch)*

## Technical

### Should I rewrite my existing automation to use the administration service?

It depends. There are some benefits to using the administration service over other APIs like WMI or PowerShell. For example, some PowerShell cmdlets loop on a single interaction, so there's multiple calls to set up, query, and tear down. With the administration service, the same query may be faster as it makes a single call for the group.

Existing WMI and PowerShell cmdlets are still supported and will continue to work. Configuration Manager may only expose some new features through the administration service, and not have comparable WMI or PowerShell APIs.

### What if an existing WMI class or method doesn't work over the administration service?

If you find an existing WMI class or method that doesn't GET or PUT as expected, send a frown to inform the engineering team. For more information, see [Product feedback](../../core/understand/product-feedback).

### Are Swagger definitions available?

No, the administration service currently doesn't publish an [OpenAPI (Swagger) document](https://swagger.io/docs/).

## Remote access

### Can I use the administration service with internet-based client management?

No, internet-based client management (IBCM) doesn't support exposing the SMS Provider role to the internet. For internet access to the administration service, you need a cloud management gateway. For more information, see [Enable internet access](set-up#enable-internet-access).

### Isn't it too risky to open this API to the internet?

It depends upon your organization's risk level, and what controls you use or put in place to help mitigate the risks:

- The administration service still uses Configuration Manager built-in role-based authorization.
- Control access to the web service with the certificate trust. If a device doesn't trust the certificate chain, a user on that device can't query the administration service.
- Add additional security layers. For example, [Azure App Proxy](/en-us/entra/identity/app-proxy/).

### Can I use it with Conditional Access?

Yes, and that configuration is easiest if you use [Azure App Proxy](/en-us/entra/identity/app-proxy/).

## Miscellaneous

### How do I learn about what's new with the administration service in each Configuration Manager release?

For more information, see [Release notes](release-notes).