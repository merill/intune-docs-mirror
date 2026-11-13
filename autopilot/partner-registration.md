---
layout: Conceptual
title: Reseller, Distributor, or Partner Registration of Windows Autopilot Devices | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/partner-registration
author: madakeva
ms.author: madakeva
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Windows Autopilot device registration by CSP partners lets resellers and distributors add customer devices through Partner Center.
ms.date: 2026-10-30T00:00:00.0000000Z
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

# Reseller, Distributor, or Partner Registration of Windows Autopilot Devices | Microsoft Learn

Customers can purchase devices from resellers, distributors, or other partners. If these resellers, distributors, and partners are part of the [Cloud Solution Partners (CSP) program](https://partner.microsoft.com/cloud-solution-provider), they can register devices for the customer.

As with manufacturers, CSP partners must be granted permission to register devices for an organization. This process is described in the [CSP authorization](registration-auth#csp-authorization) section of the Windows Autopilot customer consent article. In summary:

- The CSP partner requests a relationship with the organization. That organization's Global Administrator approves the request.
- After the approval, CSP partners add devices by using [Partner Center](https://partner.microsoft.com/pcv/dashboard/overview), either directly through the website or by using available APIs that can automate the same tasks.

For Surface devices, Microsoft Support can help with device registration. For more information, see [Surface Registration Support for Windows Autopilot](/en-us/surface/surface-autopilot-registration-support).

Windows Autopilot doesn't require delegated administrator permissions when it establishes the relationship between the CSP partner and the organization. As part of the Global Administrator's approval process, they can choose to unselect **Include delegated administration permissions**.

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role that should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions.

Tip

While resellers, distributors, or partners could boot each new Windows device to get the hardware hash so they can provide it to customers or register the device directly, we don't recommend this method. Instead, register devices by using the PKID information from the device packaging, such as the barcode, or get it electronically from the manufacturer or upstream partner or distributor.

Note

Partner Center doesn't have access to profiles you create in Intune or Microsoft Store for Business. It only has access to the Windows Autopilot profiles you create through Partner Center.