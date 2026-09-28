---
layout: Conceptual
title: Configure a custom domain name - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/configure-custom-domain
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Add a custom domain name for your Microsoft Intune subscription
ms.date: 2025-05-21T00:00:00.0000000Z
ms.topic: article
locale: en-us
document_id: 8ec1e536-3333-f71f-40e0-d9f413d7fffb
document_version_independent_id: 8ec1e536-3333-f71f-40e0-d9f413d7fffb
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/configure-custom-domain.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/configure-custom-domain
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/configure-custom-domain.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: b64d93b9-a225-7a23-db92-347e56317c6b
---

# Configure a custom domain name - Microsoft Intune | Microsoft Learn

This article tells administrators how you can create a DNS CNAME to simplify and customize your sign in experience using Microsoft Intune.

When your organization signs up for a Microsoft cloud-based service like Intune, you're given an initial domain name hosted in Microsoft Entra ID that looks like **your-domain.onmicrosoft.com**. In this example, **your-domain** is the domain name that you chose when you signed up. **onmicrosoft.com** is the suffix assigned to the accounts you add to your subscription. You can configure your organization's custom domain to access Intune instead of the domain name provided with your subscription.

Before you create user accounts or synchronize your on-premises Active Directory, we strongly recommend that you decide whether to use only the *.onmicrosoft.com* domain or to add one or more of your custom domain names. Set up a custom domain before adding users to simplify user management. Setting up a customer domain lets users sign in with the credentials they use to access other domain resources.

When you subscribe to a cloud-based service from Microsoft, your instance of that service becomes a [Microsoft Entra tenant](/en-us/entra/fundamentals/whatis). Your Entra tenant provides identity and directory services for Intune and your other cloud-based services. Because the tasks to configure Intune to use your organizations custom domain name are the same as for other services, you can use the information and procedures in [Managing custom domain names in your Microsoft Entra ID](/en-us/entra/fundamentals/add-custom-domain).

Tip

You can add, verify, or remove custom domain names used with Intune to keep your business identity clear, but you can't rename or remove the initial *onmicrosoft.com* domain name.

To learn more about custom domains, see [Conceptual overview of custom domain names in Microsoft Entra ID](/en-us/entra/identity/users/domains-manage).

## Role-based access controls

The following Microsoft Entra built-in RBAC role is the least privileged role that includes sufficient permissions to manage custom domain names:

- [Domain Name Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#domain-name-administrator) - This role provides permissions sufficient to [manage custom domain names](/en-us/entra/identity/role-based-access-control/delegate-by-task#custom-domain-names-least-privileged-roles) (read, add, verify, update, and delete). Users assigned this role can also read directory information about users, groups, and applications, as these objects possess domain dependencies.

When working with role-based access controls (RBAC), Microsoft recommends following the principle of least-permissions by using only accounts that have the minimum required permissions for a task, and **limiting** use and assignment of [privileged](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) administrative roles.

## Add and verify your custom domain

Managing custom domains for your Microsoft Entra organization requires use of an account with sufficient permissions in Entra ID. For guidance to add and then verify that your custom domain name is valid in Microsoft Entra, see [Add your custom domain name to your tenant](/en-us/entra/fundamentals/add-custom-domain) in the Entra ID documentation.

Learn more [about the initial onmicrosoft.com domain in Microsoft 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A).