---
layout: FAQ
title: Product and licensing FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/product-and-licensing-faq
summary: >
  <p><em>Applies to: Configuration Manager (current branch) &amp; System Center Configuration Manager (long-term servicing branch)</em></p>

  <p>This FAQ addresses common licensing questions about Configuration Manager current branch and the long-term servicing branch (LTSB) versions, available through Microsoft Volume Licensing programs. This article is for informational purposes. It doesn't supersede or replace any documentation covering Configuration Manager licensing. For more information, see the <a href="https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=53">Product Terms</a>. The Product Terms describe the use terms for all Microsoft products in Volume Licensing.</p>
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
description: Find answers for common product and license questions for Configuration Manager.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: faq
ms.collection: highpri
locale: en-us
document_id: 6f3023a8-ab6c-1d77-0111-77cc7583347c
document_version_independent_id: 26debf60-c3c1-caa6-7f78-a04a8b8e73af
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/product-and-licensing-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/product-and-licensing-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/product-and-licensing-faq.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b8932893-874f-48e4-b2d5-5521fe75a61e
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e757ef92-a039-44aa-8ed6-705843b26fea
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fe44311e-a92d-2862-6049-8e92409b4824
---

# Product and licensing FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch) & System Center Configuration Manager (long-term servicing branch)*

This FAQ addresses common licensing questions about Configuration Manager current branch and the long-term servicing branch (LTSB) versions, available through Microsoft Volume Licensing programs. This article is for informational purposes. It doesn't supersede or replace any documentation covering Configuration Manager licensing. For more information, see the [Product Terms](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=53). The Product Terms describe the use terms for all Microsoft products in Volume Licensing.

## What's current branch?

The current branch is the production-ready build of Configuration Manager that provides an active servicing model. This servicing model is like the experience with Windows. This approach supports customers who are moving at a cloud cadence and wish to innovate more quickly. With the current branch servicing model, you continue to receive new features and functionality. For this reason, only customers with active Software Assurance on Configuration Manager licenses, or with equivalent subscription rights, may install and use the current branch of Configuration Manager.

## What's the long-term servicing branch (LTSB)?

The LTSB is a production-ready build of Configuration Manager. It's intended for customers who allow Software Assurance or equivalent subscription rights to expire. When compared to the current branch, the LTSB has [reduced functionality](introduction-to-the-ltsb#features-that-arent-available). Customers who allow Software Assurance or equivalent subscription rights to expire must uninstall the current branch of Configuration Manager. Customers who have perpetual license rights to Configuration Manager may then install and use the LTSB build of the Configuration Manager version that's current at the time of expiration.

## What do the acronyms 'SA' and 'L&SA' mean in regard to Configuration Manager?

Both **Software Assurance** (SA) and **License and Software Assurance** (L&SA) are license options that grant rights to use Configuration Manager. SA is an option for a customer that's renewing SA coverage from a prior agreement. L&SA is an option for a customer buying a new license and SA coverage.

- **Software Assurance (SA)**: Customers must have active SA on Configuration Manager licenses, or equivalent subscription rights, in order to install and use the current branch option of Configuration Manager.

    While SA is optional for some Microsoft products, the only way to get rights to use Configuration Manager current branch is with SA *or equivalent subscription rights*. For more information, see the [Software Assurance FAQ](https://www.microsoft.com/licensing/licensing-programs/FAQ-Software-Assurance.aspx).
- **Microsoft License and Software Assurance (L&SA)**: Customers buying new licenses for Configuration Manager must acquire L&SA (the license and SA coverage).

    - The SA grants rights to use the current branch.
    - If your SA expires, and you still have a license for Configuration Manager, you can no longer use the current branch. For more information, see the FAQ If my SA expires and I had L&SA, what do I get?

For more information about license offerings, see [Ways to buy](https://www.microsoft.com/Licensing/licensing-programs/licensing-programs) and [Licensing Product Terms](https://www.microsoftvolumelicensing.com/ProductResults.aspx?doc=Product%20Terms,OST&amp;fid=64).

## What are 'equivalent subscriptions'?

Equivalent subscriptions refer to programs like [Enterprise Mobility + Security](https://www.microsoftvolumelicensing.com/ProductResults.aspx?doc=Product%20Terms,OST&amp;fid=51) (EMS) or [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise). There can be others, but these programs are the most common. The Microsoft Volume Licensing Product Terms refers to these programs as Management License Equivalent Licenses.

Configuration Manager is included in the following plans:

- Intune user subscription license (USL)
- EMS E3
- EMS E5
- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 F3 (formerly Microsoft 365 F1)

Important

Configuration Manager isn't included in the [Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business) plan.

## What changes with licensing for co-management in the Microsoft Intune family of products?

The co-management license lets Configuration Manager customers with Software Assurance get Intune PC management rights without having to purchase and assign individual Intune licenses to users. This license makes it easier for you to manage Windows devices with Microsoft Intune and Configuration Manager.

- Devices already managed by Configuration Manager that you enroll to Intune for co-management have almost the same rights as an Intune standalone-managed PC. If you reset Windows on this device, you can't provision it with Windows Autopilot. Windows Autopilot requires a full Intune license.
- If you enroll a Windows device to Intune by other means, it still requires a full Intune license. For example, you use Windows Autopilot to provision a device, or a user manually does self-service enrollment.
- For existing Configuration Manager-managed devices to enroll into Intune for co-management at scale without user interaction, co-management uses an Azure Active Directory (Azure AD) feature called Windows auto-enrollment. Auto-enrollment with co-management requires licenses for both Microsoft Entra ID P1 or P2 (AADP1) and Intune. Starting on December 1, 2019, you no longer need to assign individual Intune licenses for this scenario. Microsoft Intune and Configuration Manager each include the licenses for co-management. The separate AADP1 licensing requirement remains the same for this scenario to work. You still need to assign Intune licenses for other enrollment scenarios.
- If you want to use Intune for managing iOS, Android, or macOS devices, then you need the appropriate Intune subscription through a standalone Intune license, Enterprise Mobility + Security (EMS), or Microsoft 365.
- If you don't have any Intune-related subscription plan, to support co-management you need to purchase at least one Intune license. This license is for an administrator to activate the subscription plan and get access to the Microsoft Intune admin center.
- If you use the Microsoft 365 built-in [Basic Mobility and Security](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0), you can't use the new co-management license for a user that also has devices managed by Basic Mobility and Security. To use the co-management license for the user's Configuration Manager-managed device, do one of the following actions:

    - Assign a full Intune license to the user, and manage their devices through Intune.
    - Unenroll the devices from Basic Mobility and Security.
- The licensing that you previously had for System Center Configuration Manager still applies to Microsoft Configuration Manager. If installing a new site, use existing product keys.

| Feature | Co-management license | Full Intune license |
| --- | --- | --- |
| Windows enrollment | Yes (only for existing ConfigMgr-managed devices) | Yes |
| iOS, Android, macOS enrollment | No | Yes |
| Windows Autopilot | No | Yes |
| Mobile Application Management (MAM) | No | Yes |
| Conditional Access(additional AADP1 required) | Yes | Yes |
| Device profiles | Yes | Yes |
| Software update management | Yes | Yes |
| Inventory | Yes | Yes |
| App management | Yes | Yes |
| Remote Full/Selective wipe | Yes | Yes |
| Remote assistance(TeamViewer license required) | Yes | Yes |
| Tenant attach | Yes | N/A |
| Endpoint analytics | Yes | Yes |

For more information, see the following articles:

- [Co-management prerequisites](../../comanage/overview#prerequisites)
- [Windows Autopilot requirements](/en-us/windows/deployment/windows-autopilot/windows-autopilot-requirements)
- [Tenant attach prerequisites](../../tenant-attach/prerequisites)
- [Endpoint analytics licensing prerequisites](../../../endpoint-analytics/#prerequisites)
- [Use Conditional Access with Intune](../../../device-security/conditional-access-integration/overview#ways-to-use-conditional-access-with-intune)
- [TeamViewer prerequisites](../../../device-management/tools/teamviewer-legacy#prerequisites)

## I have Enterprise Mobility + Security and it expired, what must I do now?

EMS grants rights to use Configuration Manager current branch and long-term service branch. When these rights expire, you no longer have rights to use either branch and must uninstall.

## If my SA expires, and I had L&SA, what do I get?

If your SA expired after October 1, 2016, depending on what program you acquired L&SA under, you could retain a perpetual license to use the LTSB. If you currently use the current branch, you must uninstall it, and then install the LTSB. There's no support to migrate or convert to the LTSB from the current branch.

If your SA expired before October 1, 2016, and you retained a perpetual license to Configuration Manager, then your only option for ongoing use is to install and use System Center 2012 R2 Configuration Manager and its available service packs. You're required to uninstall the current branch when your SA expires, and reinstall that earlier version of the product. There's no support to migrate to or downgrade from Configuration Manager current branch to prior versions of Configuration Manager.

If you use System Center Endpoint Protection, and your SA expires, you must uninstall it. System Center Endpoint Protection offers no *L (License)* rights, and no perpetual rights.

## Do I "own" the current branch?

No. You're licensed to use the current branch while you have active SA. For example, via *L&SA*, when *SA* expires, you then have only *L (License)* rights, which don't include rights to use the current branch. If your L provides perpetual rights, you can use the Configuration Manager LTSB in place of the current branch. If your SA expired prior to October 1, 2016, you can also use System Center 2012 R2 Configuration Manager.

## Can I purchase Configuration Manager standalone without SA?

No. The only way to get rights to use Configuration Manager is to acquire a license with SA or through an equivalent subscription. There are developer programs like MSDN where Configuration Manager is offered for development and test purposes, but not production usage.

## Does a non-production environment for testing or development require an explicit license?

- If you use the same current branch software as your production environment, you need an explicit license. Check with your account team to determine if your specific license agreement covers multiple instances in multiple environments.
- Some developer programs like MSDN offer products like Configuration Manager for development and test, but not production use.
- For a temporary environment, you can use the [evaluation version](https://www.microsoft.com/evalcenter/download-microsoft-endpoint-configuration-manager) for 180 days.
- For a lab environment, you can use the [technical preview branch](../get-started/technical-preview). Technical preview has the same functionality as current branch, but has some limitations in terms of scale and supported platforms.

## Do I have rights to install any update in the Configuration Manager console?

If you have active *SA*, you do have rights.

If you don't have active SA, uninstall the current branch, and then install the LTSB of Configuration Manager. The LTSB doesn't receive updates for incremental versions of Configuration Manager, but does receive security updates based on the Support Lifecycle.

## I have purchased EMS or Microsoft 365 through a Cloud Solution Provider (CSP), do I have rights to use Configuration Manager?

Yes, you have rights to use Configuration Manager to manage clients covered by the EMS license. First download and install the [evaluation software](https://www.microsoft.com/evalcenter/download-microsoft-endpoint-configuration-manager). Then contact your CSP partner to obtain the license key from the Microsoft Partner Center support team, specifically CSP. When your CSP partner talks with Microsoft Support, they should ask them to reference the internal article ID 5037094.

## Is my subscription end-date the same as an SA expiration date?

If *SA* or your subscription is active, you have use rights for Configuration Manager current branch. An active subscription is equivalent of having active *SA*, but no perpetual *"L" (license)*. Once your subscription is over, uninstall the current branch. At this time, you don't have rights to use the LTSB.

## What are the use rights associated with the SQL Server technology provided with Configuration Manager?

Configuration Manager includes SQL Server technology. Microsoft's licensing terms for this product allows your use of SQL Server technology only to support Configuration Manager components. SQL Server client access licenses are not required for that use.

Approved use rights for the SQL Server capabilities with Configuration Manager include:

- Site database role
- Windows Server Update Services (WSUS) for software update point role
- SQL Server Reporting Services (SSRS) for reporting point role
- Data warehouse service point role
- Database replicas for management point roles

The SQL Server license that's included with Configuration Manager supports each instance of SQL Server that you install to host a database for Configuration Manager. However, only databases for Configuration Manager in the preceding list can run on that SQL Server when you use this license. If a database for any additional Microsoft or third-party product shares the SQL Server, you must have a separate license for that SQL Server instance.

## Does on-premises mobile device management (MDM) require an Intune subscription?

No. An Intune connection isn't required for new on-premises MDM deployments. Your organization still requires Intune licenses to use this feature. For more information, see the [Intune support blog post](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).