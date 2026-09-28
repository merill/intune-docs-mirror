---
layout: Conceptual
title: Get started - Create and deploy endpoint security policies from the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/endpoint-security-get-started
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
description: Create and deploy endpoint security policies from the Microsoft Intune admin center and for Configuration Manager collections.
ms.date: 2022-03-21T00:00:00.0000000Z
ms.topic: get-started
ms.subservice: core-infra
ms.collection: tier3
locale: en-us
document_id: 0253fa20-e8ac-36c7-badc-d1c6ae3cfaf2
document_version_independent_id: c87ccbee-d68e-fc31-85fa-0c9da39d72f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/endpoint-security-get-started.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/endpoint-security-get-started
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/endpoint-security-get-started.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: f3f9a907-9ed6-f4a6-93b2-4189f20473e3
---

# Get started - Create and deploy endpoint security policies from the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**.

## Prerequisites

- Access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- An environment that's [tenant attached with uploaded devices](device-sync-actions).
- A supported version of Configuration Manager and the corresponding version of the console installed.
    - Upgrade the target devices to the latest version of the Configuration Manager client.
- At least one Configuration Manager collection that's [available for assigning Endpoint security policies](endpoint-security-get-started#bkmk_collections)
- Windows Devices that [support this profile for tenant attached devices](endpoint-security-get-started#bkmk_supportedprofiles)

## Supported endpoint security profiles for tenant attached devices

| Platform | Endpoint security policy | Profile | Endpoint Protection (Configuration Manager) | Endpoint Security (Tenant Attach) |
| --- | --- | --- | --- | --- |
| Windows 10, Windows 11, and Windows Server | Antivirus | Antivirus | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Antivirus | Antivirus Exclusions | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Antivirus | Tamper Protection | ![Not Supported](media/red-wrong.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Attack Surface Reduction | Attack Surface Reduction Rules | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11 | Attack Surface Reduction | Application Guard Settings | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Attack Surface Reduction | Exploit protection | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Endpoint detection and response | Endpoint detection and response | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Firewall | Firewall | ![Supported](media/green-check.png) | ![Supported](media/green-check.png) |
| Windows 10, Windows 11, and Windows Server | Firewall | Firewall Rules | ![Not Supported](media/red-wrong.png) | ![Supported](media/green-check.png) |

The following profiles are supported for devices you manage with Configuration Manager current branch, through the tenant attach scenario:

- Platform: **Windows 10, Windows 11, and Windows Server (ConfigMgr)**

    - Profile: **Microsoft Defender Antivirus** - Manage [Antivirus policy settings for Configuration Manager devices](../../device-configuration/endpoint-security/ref-antivirus-defender-settings-windows-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)
        - Windows Server 2019 and later (x64)
        - Windows Server 2016 (x64)
        - Windows 8.1 (x86, x64)
        - Windows Server 2012 R2 (x64)
    - Profile: **Windows Security experience (ConfigMgr)** - Manage [Windows Security app settings for Configuration Manager devices](../../device-configuration/endpoint-security/ref-windows-security-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)
        - Windows Server 2019 and later (x64)

    Important

    To support managing tamper protection your environment must additionally meet the [prerequisites for managing tamper protection with Intune](/en-us/windows/security/threat-protection/microsoft-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection#turn-tamper-protection-on-or-off-for-your-organization-using-intune) as detailed in the Windows documentation.

    - Profile: **Endpoint detection and response (ConfigMgr)** - Manage [Endpoint detection and response policy settings](../../device-configuration/endpoint-security/ref-edr-settings?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)
        - Windows 8.1 (x84, x64)
        - Windows Server 2019 and later (x64)
        - Windows Server 2016 (x64)
        - Windows Server 2012 R2 (x64)
        - Profile: **Attack Surface Reduction Rules (ConfigMgr)** - Manage Attack Surface Reduction Rules for Configuration Manager devices as part of Attack surface reduction policy, when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)
        - Windows Server 2019 and later (x64)
        - Windows Server 2016 (x64)
        - Windows Server 2012 R2 (x64)

        Note

        Attack Surface Reduction rules may not be available on Windows Server 2012 R2 and Windows Server 2016. For more information please refer to [Attack Surface Reduction rules documentation](/en-us/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#supported-operating-systems).
- Platform: **Windows 10 and later**

    - Profile: **Microsoft Defender Firewall (ConfigMgr)** - Manage [firewall policy settings for Configuration Manager devices](../../device-configuration/endpoint-security/ref-firewall-settings-tenant-attach?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json), when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)

        Important

        A supported version of Configuration manager is required to support firewall policies.
    - Profile: **Exploit Protection (ConfigMgr)** - Manage [Exploit Protection settings for Configuration Manager devices](../../device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr) as part of Attack surface reduction policy, when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)
    - Profile: **Web Protection (ConfigMgr)** - Manage [Web Protection settings for Configuration Manager devices](../../device-configuration/endpoint-security/ref-attack-surface-reduction-settings?toc=/mem/configmgr/tenant-attach/toc.json&amp;bc=/mem/configmgr/tenant-attach/breadcrumb/toc.json#attack-surface-reduction-configmgr) as part of Attack surface reduction policy, when you use tenant attach.

        This profile is supported with devices that are tenant attached and run the following platforms:

        - Windows 10 and later (x86, x64, ARM64)

## Make Configuration Manager collections available to assign Endpoint security policies

When you enable collections of devices to work with endpoint security policies from Intune, you're configuring devices in those collections to onboard with Microsoft Defender for Endpoint.

1. From a Configuration Manager console connected to your top-level site, right-click on a device collection that you synchronize to Microsoft Intune admin center and select **Properties**.
2. On the **Cloud Sync** tab, enable the option to **Make this collection available to assign Endpoint security policies from Microsoft Intune admin center**.

    - You can't select this option if your Configuration Manager hierarchy isn't tenant attached.
    - The collections available for this option are limited by the [collection scope selected for tenant attach upload](device-sync-actions#bkmk_edit).

    ![Configure cloud sync](../../fundamentals/media/tenant-attach/cloud-sync.png)
3. Select **Add** and then select the Microsoft Entra group that you would like to synchronize with **Collect membership results**.
4. Select **OK** to save the configuration.

    Devices in this collection can now onboard with Microsoft Defender for Endpoint, and support use of Intune endpoint security policies.