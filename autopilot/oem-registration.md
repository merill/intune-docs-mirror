---
layout: Conceptual
title: Windows Autopilot OEM registration process | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/oem-registration
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
description: How OEMs add devices to Windows Autopilot.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-modern-desktop
- m365initiative-coredeploy
ms.custom: sfi-ga-nochange
locale: en-us
document_id: d912a1d2-3c4d-b170-7b59-7e395289abb9
document_version_independent_id: d912a1d2-3c4d-b170-7b59-7e395289abb9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/oem-registration.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: oem-registration
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/oem-registration.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 969968b6-9bef-5401-c980-6da760206ad0
---

# Windows Autopilot OEM registration process | Microsoft Learn

## Device registration process

When devices are purchased from an OEM, the OEM can automatically register the devices with the Windows Autopilot. For the list of OEMs that support registration, see the **Participant device manufacturers and resellers** section of the [Windows Autopilot page](https://aka.ms/windowsautopilot).

Note

While the hardware hashes, also known as hardware IDs, are generated as part of the OEM device manufacturing process, the hardware hashes aren't normally provided directly to customers or Cloud Solution Partners (CSPs). Instead, the OEM should register devices on the customer's behalf. In cases where CSPs register devices, OEMs might provide PKID information to those partners to support the device registration process.

OEMs must follow [device guidelines](autopilot-device-guidelines) for Windows Autopilot devices.

### Service data

Microsoft manages and maintains Windows Autopilot. This service provides the backend database that associates hardware hashes with customer tenants. When an OEM registers devices for a customer, they're writing that data to this database and not directly to the customer's tenant. No permissions to the customer's tenant are granted or required for OEMs to register devices on the customer's behalf.

### Customer consent

Before an OEM can register devices for an organization, the organization's Microsoft Entra Global Administrator must approve the OEM. For more information, see [OEM authorization](registration-auth#oem-authorization).

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role that should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions.

## Microsoft Surface registration

For Surface devices, see [Surface registration support for Windows Autopilot](/en-us/surface/surface-autopilot-registration-support).