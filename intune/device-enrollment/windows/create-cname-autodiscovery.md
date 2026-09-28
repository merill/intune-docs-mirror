---
layout: Conceptual
title: Enable autodiscovery of Intune enrollment server - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/create-cname-autodiscovery
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: maholdaa
ms.subservice: enrollment
description: Simplify enrollment for users by enabling automatic discovery of the Intune enrollment server.
ms.date: 2025-11-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 82e695dd-c2b2-d799-05dc-1881f919d4af
document_version_independent_id: 82e695dd-c2b2-d799-05dc-1881f919d4af
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/create-cname-autodiscovery.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/create-cname-autodiscovery
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/create-cname-autodiscovery.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6cfd7edb-e69c-a7f2-14e6-a05203e9c455
---

# Enable autodiscovery of Intune enrollment server - Microsoft Intune | Microsoft Learn

If you're not using automatic enrollment as part of your enrollment or provisioning solution, we recommend creating a domain name server (DNS) alias, called a *CNAME* record type, for your MDM servers. The CNAME redirects enrollment requests to Intune servers so that device users don't have to enter the server address during device enrollment. Although the CNAME configuration is optional, it makes enrollment easier for users by enabling automatic discovery of the Intune enrollment server and reducing the amount of user interaction required.

If you're enrolling Windows devices by using [MDM automatic enrollment](enable-automatic-mdm), you don’t have to worry about configuring CNAME records for your MDM server. The MDM server is configured by default when you enable MDM automatic enrollment in your tenant.

This article applies to Windows.

## Step 1: Create CNAME

Create CNAME DNS resource records for your organization's domain. For example, if your organization's website is contoso.com, create a CNAME record in DNS that redirects *EnterpriseEnrollment.contoso.com* to *enterpriseenrollment-s.manage.microsoft.com*.

If no enrollment CNAME record is found, users are prompted to manually enter the MDM server name: *enrollment.manage.microsoft.com*.

| Type | Host name | Points to | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.company\_domain.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
| CNAME | EnterpriseRegistration.company\_domain.com | EnterpriseRegistration.windows.net | One hour |

If your organization uses more than one UPN suffix, create one CNAME for each domain name and point each one to *EnterpriseEnrollment-s.manage.microsoft.com*.

For example:

1. Contoso users use the following formats as their email address/UPN:

    - name@contoso.com
    - name@us.contoso.com
    - name@eu.contoso.com
2. As the Contoso DNS admin, you should configure CNAME records as described in the following table:

    | Type | Host name | Points to | TTL |
    | --- | --- | --- | --- |
    | CNAME | EnterpriseEnrollment.contoso.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
    | CNAME | EnterpriseEnrollment.us.contoso.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |
    | CNAME | EnterpriseEnrollment.eu.contoso.com | EnterpriseEnrollment-s.manage.microsoft.com | One hour |

`EnterpriseEnrollment-s.manage.microsoft.com` – Supports a redirect to the Intune service with domain recognition from the email's domain name

Changes to DNS records might take up to 72 hours to propagate. You can't verify the DNS change in Intune until the DNS record propagates.

## Step 2: Verify CNAME

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Device onboarding** and select **Enrollment**.
4. Select the **Windows** tab.
5. Under **Enrollment options**, select **CNAME Validation**.
6. For **Domain**, enter the company website, and then choose **Test**.

## Best practices and recommendations

*EnterpriseEnrollment-s.manage.microsoft.com* is the preferred FQDN for enrollment. *EnterpriseEnrollment.manage.microsoft.com* (without the *-s*) and *manage.microsoft.com* both work as the target for the autodiscovery server, but require users to acknowledge a confirmation message. We recommend using *EnterpriseEnrollment-s.manage.microsoft.com* because there is no confirmation required, which means one less step for the device user.

Alternate redirection methods aren't supported with Intune. For example, you can't use a proxy server to redirect *enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc* to *enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc* or *manage.microsoft.com/EnrollmentServer/Discovery.svc*.

## Registration CNAME

Microsoft Entra ID uses a different CNAME during device registration for iOS/iPadOS, Android, and Windows devices. Intune Conditional Access requires devices to be registered to Microsoft Entra ID (also called *workplace joined*). If you plan to use Conditional Access, you should configure the *EnterpriseRegistration* CNAME for each company name you have.

| Type | Host name | Points to | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseRegistration.contoso.com | EnterpriseRegistration.windows.net | One hour |

For more information about device registration, see [Manage device identities using the Azure portal](/en-us/azure/active-directory/devices/device-management-azure-portal)

## Windows auto enrollment and device registration

This section applies to US government cloud customers on devices running Windows.

Although creating CNAME DNS entries is optional, CNAME records make enrollment easier for users. If no enrollment CNAME record is found, users are prompted to manually enter the MDM server name, enrollment.manage.microsoft.us.

| Type | Host name | Points to | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.contoso.com | EnterpriseEnrollment-s.manage.microsoft.us | One hour |
| CNAME | EnterpriseRegistration.contoso.com | EnterpriseRegistration.windows.net | One hour |

For Intune operated in China and by 21Vianet, use the following details.

| Type | Host name | Points to | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.contoso.com | enterpriseenrollment-s.manage.microsoftonline.cn | One hour |

For more information about automatic enrollment for Windows, see [Set up automatic enrollment](enable-automatic-mdm).