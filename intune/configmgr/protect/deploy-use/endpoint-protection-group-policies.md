---
layout: Conceptual
title: Manage Endpoint Protection using Group Policies - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection-group-policies
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
description: Learn how to manage Endpoint Protection using Group Policies.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 02845125-1875-7355-7007-0b9533538b5f
document_version_independent_id: f78fb19f-c7bb-3c1b-efc3-fc6ce57b1a46
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-protection-group-policies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-protection-group-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-protection-group-policies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: ffe793c1-90aa-eda6-6d30-765d73b4c17f
---

# Manage Endpoint Protection using Group Policies - Configuration Manager | Microsoft Learn

**Applies to:**

- [Microsoft Defender for Endpoint](/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- System Center Endpoint Protection on the following down-level devices:
    - Windows Server 2012 R2
    - Windows 8.1
    - Windows Server 2012
    - Windows 8
    - Windows Server 2008 R2 SP1
    - Windows 7 SP1
    - Windows Server 2008 SP2
    - Windows Vista

You may have a number of down-level or legacy Windows devices that are enabled with Endpoint Protection—but are outside of your Configuration Manager hierarchy. For example, devices in a demilitarized zone or devices that are integrated through mergers and acquisitions.

You can manage Endpoint Protection in such devices using Group Policy settings, described as follows:

- Copy Endpoint Protection policy definitions
- Load Endpoint Protection policy definitions into any of the following locations:
    - Central Store on a Domain Controller (Recommended)
    - Local device

Note

For information on how to use Group Policy settings to manage Microsoft Defender Antivirus in Windows 10, Windows Server 2019, Windows Server 2016, or later as well as [on Windows Server 2012 R2 after installing Microsoft Defender for Endpoint using the modern, unified solution](/en-us/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) see [Use Group Policy settings to configure and manage Microsoft Defender Antivirus](/en-us/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus).

## Copy Endpoint Protection policy definitions

On a down-level Windows device that is managed by Endpoint Protection, copy the Endpoint Protection policy definition files.

1. Go to **C:\Program Files\Microsoft Security Client\Admx**.
2. Compress the following files into a zip file, for example **SCEP\_admx.zip**:

    - **EndPointProtection.adml**
    - **EndPointProtection.admx**
3. Copy the zip file into a temporary folder. For example, **C:\temp\_SCEP\_GPO\_admx**.
4. Extract the file.

Note

The registry keys to configure Endpoint Protection policy settings are located in **Hkey\_Local\_Machine\Software\Policies\Microsoft\Microsoft Antimalware**.

## Load Endpoint Protection Group Policy settings into a Central Store on a domain controller

If you are using a [Central Store for Group Policy Administrative Templates](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra), perform the following steps to load and configure Endpoint Protection Group policy settings. This is the recommended method.

1. Go to the folder where you extracted the Endpoint Protection policy definition files.
2. Copy the .admx and .adml files into the **PolicyDefinitions** folder on the domain controller:

    1. Copy **EndPointProtection.admx** into **\\&lt;forest.root&gt;\SYSVOL\&lt;domain&gt;\Policies\PolicyDefinitions**.
    2. Copy **EndPointProtection.adml** into **\\&lt;forest.root&gt;\SYSVOL\&lt;domain&gt;\Policies\PolicyDefinitions\en-US**.

    For example:

    - Copy **EndPointProtection.admx** into **\DC\SYSVOL\contoso.com\Policies\PolicyDefinitions**.
    - Copy **EndPointProtection.adml** into **\DC\SYSVOL\contoso.com\Policies\PolicyDefinitions\en-US**.

    where **DC** is the name of your Domain Controller and **contoso.com** is your domain.
3. Open the [Group Policy Management Console](/en-us/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) and create a new Group Policy Object (GPO) in your domain, for example **Endpoint Protection**.
4. Right-click the GPO for Endpoint Protection and click **Edit**.
5. In the Group Policy Management Editor, go to **Computer Configuration** &gt; **Policies** &gt; **Administrative Templates: Policy definitions** &gt; **Windows Components** &gt; **Endpoint Protection**.

    The list of Endpoint Protection Group Policies is displayed.
6. Expand the section that contains the setting you want to configure, double-click the setting to open it, and make configuration changes.

## Load Endpoint Protection Group Policy settings into your local device

Instead of using Central Store for loading Endpoint Protection policy definitions, you can store them locally into your device.

1. Go to the folder where you extracted the Endpoint Protection policy definition files.
2. Copy the .admx and .adml files into your local PolicyDefinitions folder.

    1. Copy **EndPointProtection.admx** into **%SystemRoot%/PolicyDefinitions**.
    2. Copy **EndPointProtection.adml** into **%SystemRoot%/PolicyDefinitions/en-US**.

    For example:

    - Copy **EndPointProtection.admx** into **C:\Windows\PolicyDefinitions**.
    - Copy **EndPointProtection.adml** into **C:\Windows\PolicyDefinitions\en-US**.
3. Open Local Group Policy Editor.
4. Go to **Computer Configuration** &gt; **Administrative Templates** &gt; **Windows Components** &gt; **Endpoint Protection**.

    The list of Endpoint Protection Group Policies is displayed.
5. Expand the section that contains the setting you want to configure, double-click the setting to open it, and make configuration changes.