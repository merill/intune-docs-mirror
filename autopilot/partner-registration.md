---
layout: Conceptual
title: Reseller, distributor, or partner registration of Windows Autopilot devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/partner-registration
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: How partners add devices to Windows Autopilot.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 3ce11420-cb07-005f-2f7a-61e9a1721a1c
document_version_independent_id: 3ce11420-cb07-005f-2f7a-61e9a1721a1c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/partner-registration.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: partner-registration
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/partner-registration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: b8f9b589-60ed-b59b-4dfd-6d3e063ccd46
---

# Reseller, distributor, or partner registration of Windows Autopilot devices | Microsoft Learn

Customers can purchase devices from resellers, distributors, or other partners. As long as these resellers, distributors, and partners are part of the [Cloud Solution Partners (CSP) program](https://partner.microsoft.com/cloud-solution-provider), they too can register devices for the customer.

As with OEMs, CSP partners must be granted permission to register devices for an organization. This process is described in the [CSP authorization](registration-auth#csp-authorization) section of the Windows Autopilot customer consent article. In summary:

- The CSP partner requests a relationship with the organization. That organization's Global Administrator approves the request.
- After the approval, CSP partners add devices using [Partner Center](https://partner.microsoft.com/pcv/dashboard/overview), either directly through the web site or via available APIs that can automate the same tasks.

For Surface devices, Microsoft Support can help with device registration. For more information, see [Surface Registration Support for Windows Autopilot](/en-us/surface/surface-autopilot-registration-support).

Windows Autopilot doesn't require delegated administrator permissions when establishing the relationship between the CSP partner and the organization. As part of the Global Administrator's approval process, they can choose to uncheck the **Include delegated administration permissions** checkbox.

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role that should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions.

Tip

While resellers, distributors, or partners could boot each new Windows device to obtain the hardware hash for purposes of providing them to customers or direct registration by the partner, this method isn't recommended. Instead, these partners should register devices using the PKID information obtained from the device packaging, such as the barcode, or obtained electronically from the OEM or upstream partner/distributor.

Note

Partner Center doesn't have access to profiles created in Intune or Microsoft Store for Business. It only has access to the Windows Autopilot profiles created through Partner Center.