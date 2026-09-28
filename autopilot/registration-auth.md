---
layout: Conceptual
title: Windows Autopilot customer consent | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/registration-auth
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
description: Learn how a cloud service provider (CSP) partner or an OEM can get customer authorization to register Windows Autopilot devices on the customer's behalf.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: reference
ms.custom:
- sfi-ga-nochange
- sfi-image-nochange
locale: en-us
document_id: 14a38eab-4bee-7c13-f4ad-6926c4e20d91
document_version_independent_id: 14a38eab-4bee-7c13-f4ad-6926c4e20d91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/registration-auth.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: registration-auth
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/registration-auth.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b1515367-9f16-464a-875b-f8be3ed7154a
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/803ddb93-80fd-4a15-aea5-c9d217aa1f76
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 9adb087f-82f2-2b12-7abd-d110b84ed5e2
---

# Windows Autopilot customer consent | Microsoft Learn

This article describes how a cloud service provider (CSP) partner (direct bill, indirect provider, or indirect reseller) or an OEM can get customer authorization to register Windows Autopilot devices on the customer's behalf.

## CSP authorization

CSP partners can get customer authorization to register Windows Autopilot devices on the customer's behalf per the following restrictions:

| **Method** | **Description** |
| --- | --- |
| **Direct CSP** | Gets direct authorization from the customer to register devices. |
| **Indirect CSP Provider** | Gets implicit permission to register devices through the relationship their CSP Reseller partner has with the customer. Indirect CSP Providers register devices through Microsoft Partner Center. |
| **Indirect CSP Reseller** | Gets direct authorization from the customer to register devices. At the same time, their indirect CSP Provider partner also gets authorization, which means that either the Indirect Provider or the Indirect Reseller can register devices for the customer. However, the Indirect CSP Reseller must register devices through the Microsoft Partner Center UI (manually uploading CSV file). The Indirect CSP Provider can register devices using the Microsoft Partner Center APIs. |

### Steps

For a CSP to register Windows Autopilot devices for a customer, the customer must first grant that CSP partner permission using the following process:

1. CSP sends link to customer requesting authorization/consent to register/manage devices on their behalf. To do so:

    1. CSP logs into Microsoft Partner Center.
    2. Select **Dashboard** on the top menu.
    3. Select **Customer** on the side menu.
    4. Select the **Request a reseller relationship** link:

        [![Request a reseller relationship.](images/csp1.png)](images/csp1.png#lightbox)
    5. Select the checkbox indicating if delegated admin rights are desired:

        [![Delegated rights.](images/csp2.png)](images/csp2.png#lightbox)

        Note

        Depending on the partner, they might request Delegated Admin Permissions (DAP) when requesting this consent. If possible, it's better to use the newer DAP-free process (shown in this document). If not, their DAP status can be easily removed from the [Microsoft 365 admin center](https://admin.microsoft.com/). For more information, see [Obtain permissions to manage a customer's service or subscription](/en-us/partner-center/customers_revoke_admin_privileges).
    6. Send the template in the previous step to the customer via email.
2. Customer with Microsoft 365 admin center Global Administrator privileges selects the link in email. The link takes them to the following [Microsoft 365 admin center](https://admin.microsoft.com/) page:

    [![Screenshot of Accept agreement and authorize partner page - delegated admin rights.](images/csp3a.png)](images/csp3a.png#lightbox)

    The above image is what the customer sees if they requested delegated admin rights (DAP). The page says what Admin roles are being requested. If the customer didn't request delegated admin rights, they would see the following page:

    [![Screenshot of Accept agreement and authorize partner page.](images/csp3b.png)](images/csp3b.png#lightbox)

    A user without Global Administrator privileges who selects the link sees a message similar to the following message:

    [![Screenshot of permission page.](images/csp4.png)](images/csp4.png#lightbox)
3. Customer selects the **Yes** checkbox, followed by the **Accept** button. Authorization happens instantaneously.
4. To check that the authorization request is complete, the CSP can check the **Customers** list in their Microsoft Partner Center account. If the customer is in the list, the request is complete. For example:

    [![Customers.](images/csp5.png)](images/csp5.png#lightbox)

Important

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role that should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions.

## OEM authorization

OEM authorization is only available for those OEMs who are eligible to use OEM Direct API for Windows Autopilot registration and deregistration.

OEMs who are eligible of using Direct API solution have a unique link to provide to their respective customers, which the OEM can request from Microsoft via the **msoemops support** alias. Contact the organization's account manager to obtain this support alias.

1. OEM emails link to their customer.
2. Customer signs into the [Microsoft 365 admin center](https://admin.microsoft.com/) using a cloud-native account (for example, [domain].onmicrosoft.com) with Global Administrator privileges.
3. Customer selects the link in the email, which takes them directly to the following page:

    [![Screenshot of Accept partner invitation page.](images/csp6.png)](images/csp6.png#lightbox)

    A user without Global Administrator privileges who selects the link sees a message similar to the following message:

    [![Screenshot of MSfB permission required page.](images/csp7.png)](images/csp7.png#lightbox)
4. Customer selects the **Yes** checkbox, followed by the **Accept** button, and they're done. Authorization happens instantaneously.

    Note

    Once this process is completed, it isn't currently possible for an administrator to remove an OEM. To remove an OEM or revoke their permissions, send a request to msoemops@microsoft.com
5. The OEM can use the Validate Device Submission Data API to verify the consent is completed.

    Note

    - This API is discussed in the [API Whitepaper, p. 14ff](https://devicepartner.microsoft.com/assets/detail/windows-autopilot-integration-with-oem-api-design-whitepaper-docx). This link is only accessible by Microsoft Device Partners. As discussed in this article, it's a best practice recommendation for OEM partners to run the API check to confirm customer consent is received before attempting to register devices. This check can help avoid errors in the registration process.
    - During the OEM authorization registration process, no delegated admin permissions are granted to the OEM.

## Summary

At this stage of the process, Microsoft is no longer involved. The consent exchange happens directly between the OEM and the customer. It all also happens instantaneously - as quickly as buttons are selected.