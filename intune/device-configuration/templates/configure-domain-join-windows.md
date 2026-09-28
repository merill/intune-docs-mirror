---
layout: Conceptual
title: Domain join profile settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-domain-join-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Create a domain join device configuration profile for Microsoft Entra hybrid joined devices. Use this profile to deploy on-premises Active Directory domain information to devices provisioned with Windows Autopilot and Microsoft Intune.
ms.date: 2025-10-22T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: d7ba9ac5-11a9-085a-ae04-886bb4054a2d
document_version_independent_id: d7ba9ac5-11a9-085a-ae04-886bb4054a2d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-domain-join-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-domain-join-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-domain-join-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: eacc4817-1d8c-ce67-e296-e78baaf1d8e2
---

# Domain join profile settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Many environments use on-premises Active Directory (AD). When AD domain-joined devices are also joined to Microsoft Entra ID, they're called Microsoft Entra hybrid joined devices. Using Windows Autopilot, you can [enroll Microsoft Entra hybrid joined devices](/en-us/autopilot/windows-autopilot-hybrid) in Intune. To enroll, you also need a **Domain Join** configuration profile.

A **Domain Join** configuration profile includes on-premises Active Directory domain information. When devices are provisioning (and typically offline), this profile deploys the AD domain details so devices know which on-premises domain to join. If you don't create a domain join profile, these devices might fail to deploy.

This feature applies to:

- Windows
- Microsoft Entra hybrid joined devices
- Hybrid deployment with Windows Autopilot + Intune

This article shows you how to create a domain join profile for a hybrid Windows Autopilot deployment. You can also see the available settings.

## Prerequisites

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Domain Join**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy. Name your policies so you can easily identify them later. For example, a good policy name is **Windows Autopilot domain join**.
    - **Description**: Enter a description for the policy. This setting is optional, but recommended. For example, enter **Windows: Domain join profile that includes on-premises domain information to enroll hybrid AD joined devices with Windows Autopilot**.
6. Select **Next**.
7. In **Configuration settings**, enter the following properties:

    - **Computer name prefix**: Enter a prefix for the device name. Computer names are 15 characters long. After the prefix, the remaining 15 characters are randomly generated.
    - **Domain name**: Enter the Fully Qualified Domain Name (FQDN) the devices are to join. For example, enter `americas.corp.contoso.com`.
    - **Organizational unit** (optional): Enter the full path ([distinguished name](/en-us/windows/win32/ad/object-names-and-identities#distinguished-name)) to the organizational unit (OU) the computer accounts are to be created. For example, enter `OU=Mine,DC=Contoso,DC=com`. Don't enter quotation marks. To use the well-known computer object container (CN=Computers, DC=Contoso, DC=Com), leave this property blank.

        For more information and advice on this setting, go to [Deploy Microsoft Entra hybrid joined devices](/en-us/autopilot/windows-autopilot-hybrid).
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the device groups that will receive your profile. For more information about assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    If you need to join devices to different domains or OUs, create different device groups.

    Select **Next**.
11. In **Applicability rules**, use the **Rule**, **Property**, and **Value** options to define how this profile applies within assigned groups. For more information on applicability rules, go to [Applicability rules](../create-device-profile#applicability-rules).

    Select **Next**.
12. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

It's now ready for you to [deploy Microsoft Entra hybrid joined devices by using Intune and Windows Autopilot](/en-us/autopilot/windows-autopilot-hybrid).