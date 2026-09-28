---
layout: Conceptual
title: Microsoft Defender for Endpoint - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/defender-advanced-threat-protection
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
description: Learn how to manage and monitor Microsoft Defender for Endpoint, a new service that helps enterprises respond to advanced attacks.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 4ea5be34-a969-e46b-4fc0-ccca775265bb
document_version_independent_id: 209b8abb-88f7-f3a0-385a-56a6a9fdce23
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/defender-advanced-threat-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/defender-advanced-threat-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/defender-advanced-threat-protection.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 386d41f6-4154-25a8-03c7-70c35589e758
---

# Microsoft Defender for Endpoint - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Endpoint Protection can help manage and monitor [Microsoft Defender for Endpoint](/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection). Microsoft Defender for Endpoint helps enterprises detect, investigate, and respond to advanced attacks on their networks. Configuration Manager policies can help you onboard and monitor Windows 10 or later clients.

Microsoft Defender for Endpoint's cloud-based portal is [Microsoft Defender Security Center](https://securitycenter.windows.com). By adding and deploying a client onboarding configuration file, Configuration Manager can monitor deployment status and Microsoft Defender for Endpoint agent health. Microsoft Defender for Endpoint is supported on PCs running the Configuration Manager client or [managed by Microsoft Intune](/en-us/mem/intune-service/protect/advanced-threat-protection).

## Prerequisites

- Subscription to Microsoft Defender for Endpoint
- Clients computers running the Configuration Manager client
- Clients using an OS listed in the supported client operating systems section below.
- Your administrative user account needs the **Endpoint Protection Manager** security role.

### Supported client operating systems

You can onboard the following operating systems using Configuration Manager:

- Windows 11
- Windows 10, version 1709 or newer
- Windows Server 2025
- Windows Server 2022
- Windows Server 2019
- Windows Server Semi-Annual Channel (SAC), version 1803 or newer
- Windows Server 2016

Important

Operating systems that have reached the end of their [product lifecycle](/en-us/lifecycle/faq/general-lifecycle) aren't typically supported for onboarding unless they have been enrolled into the [Extended Security Updates (ESU program)](/en-us/lifecycle/faq/extended-security-updates). For more information about supported operating systems and capabilities with Microsoft Defender for Endpoint, see [Minimum requirements for Microsoft Defender for Endpoint](/en-us/microsoft-365/security/defender-endpoint/minimum-requirements#supported-windows-versions). 

Instructions to Onboarding to Microsoft Defender for Endpoint with Configuration Manager 2207 and later versions

Instructions to Updating onboarding information for Microsoft Defender for Endpoint devices with Configuration Manager

## Onboarding to Microsoft Defender for Endpoint with Configuration Manager 2207 and later versions

Different operating systems have different needs for onboarding to Microsoft Defender for Endpoint. Up-level devices, such as Windows Server version 1803, need the onboarding configuration file. Starting Current Branch 2207, For down-level server operating system devices, you can choose between Microsoft Defender for Endpoint (MDE) Client (recommended) or Microsoft Monitoring Agent (MMA) (legacy) in the Client Settings. For Windows 8.1 devices, you need to use Microsoft Monitoring Agent (MMA) (legacy) in the Client Settings.

[![Screenshot of Client Settings for Endpoint Protection.](media/9265511-mde-downlevel-support-client-settings.png)](media/9265511-mde-downlevel-support-client-settings.png#lightbox)

If you choose to use MMA, you need the **Workspace key** and **Workspace ID** to onboard. Configuration Manager also installs the Microsoft Monitoring Agent (MMA) when needed by onboarded devices but it doesn't update the agent automatically.

Up-level operating systems include:

- Windows 10, version 1607 and later
- Windows 11
- Windows Server Semi-Annual Channel (SAC), version 1803 or later
- Windows Server 2019
- Windows Server 2022
- Windows Server 2025

Down-level operating systems that support MDE Client include:

- Windows Server 2016

Note

Currently, the [modern, unified Microsoft Defender for Endpoint for Windows Server 2012 R2 & 2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/bc-p/2904464) is generally available. Configuration Manager version 2107 with the update rollup supports configuration using Endpoint Protection policies, including those policies created in the Microsoft Intune admin center using tenant attach. Configuration Manager version 2207 now supports automatic deployment of MDE Client, if you choose to use through Client Settings. For older supported versions, see [Server migration scenarios](/en-us/microsoft-365/security/defender-endpoint/server-migration).

When you onboard devices to Microsoft Defender for Endpoint with Configuration Manager, you deploy the Defender policy to a target collection or multiple collections. Sometimes the target collection contains devices running any number of the supported operating systems. The instructions for onboarding these devices vary based on if you're targeting a collection containing devices with operating systems that are only up-level and devices that support MDE Client or if the collection also includes down-level clients that require MMA.

- If your collection contains only up-level devices and/or down-level server operating system devices that require MDE Client (based on the client settings), then you can use the onboarding instructions using Microsoft Defender for Endpoint Client (recommended).
- If your target collection contains down-level server operating system devices that require MMA (based on the client settings) or Windows 8.1 devices, then use the instructions to onboard devices using Microsoft Monitoring Agent.

Warning

If your target collection contains down-level devices that require MMA, and you use the instructions for onboarding using MDE Client, then the down-level devices won't be onboarded. The optional **Workspace key** and **Workspace ID** fields are used for onboarding down-level devices that require MMA, but if they aren't included then the policy will fail on down-level clients that require MMA.

### Onboard devices using MDE Client to Microsoft Defender for Endpoint (recommended)

Up-level clients require an onboarding configuration file for onboarding to Microsoft Defender for Endpoint. Up-level operating systems include:

- Windows 11
- Windows 10, version 1607 and later
- Windows Server Semi-Annual Channel (SAC), version 1803 and later
- Windows Server 2019
- Windows Server 2022
- Windows Server 2025

Down-level operating systems that support MDE Client include:

- Windows Server 2016

#### Prerequisites

##### Prerequisites for Windows Server 2012 R2

If you have fully updated your machines with the latest [monthly rollup](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) package, there are **no** additional prerequisites.

The installer package will check if the following components have already been installed via an update:

- [Update for customer experience and diagnostic telemetry](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Update for Universal C Runtime in Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

##### Prerequisites for Windows Server 2016

- The Servicing Stack Update (SSU) from September 14, 2021 or later must be installed.
- The Latest Cumulative Update (LCU) from September 20, 2018 or later must be installed. It is recommended to install the latest available SSU and LCU on the server. - The Microsoft Defender Antivirus feature must be enabled/installed and up to date. You can download and install the latest platform version using Windows Update. Alternatively, download the update package manually from the [Microsoft Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) or from [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&amp;arch=x64).

#### Get an onboarding configuration file for up-level devices

1. Go to the [Microsoft Defender Security Center](https://security.microsoft.com/securitysettings/endpoint) and sign in.
2. Select **Settings**, then select **Onboarding** under the **Endpoint** heading.
3. For the operating system, select **Windows 10 and 11**.
4. Choose **Microsoft Endpoint Configuration Manager current branch and later** for the deployment method.
5. Select **Download package**.
6. Download the compressed archive (.zip) file and extract the contents. 
    Note

    The steps have you download the onboarding file for Windows 10 and 11 but this file is also used for up-level Server operating systems.

Important

- The Microsoft Defender for Endpoint configuration file contains sensitive information which should be kept secure.
- If your target collection contains down-level devices that require MMA, and you use the instructions for onboarding using MDE Client, then the down-level devices won't be onboarded. The optional **Workspace key** and **Workspace ID** fields are used for onboarding down-level devices, but if they aren't included then the policy will fail on down-level clients.

#### Onboard the up-level devices

1. In the Configuration Manager console, navigate to **Administration** &gt; **Client Settings**.
2. Create custom Client Device Settings or go to the properties of the required client setting and select **Endpoint Protection**
3. For **Microsoft Defender for Endpoint Client on Windows Server 2012 R2 and Windows Server 2016** setting, The default value is set as **Microsoft Monitoring Agent (legacy)** which needs to be changed to **MDE Client (recommended)**. [![Screenshot of Client Settings for Endpoint Protection showing different options for down-level server operating system devices.](media/9265511-mde-downlevel-support-client-settings.png)](media/9265511-mde-downlevel-support-client-settings.png#lightbox)
4. In the Configuration Manager console, navigate to **Assets and Compliance** &gt; **Endpoint Protection** &gt; **Microsoft Defender ATP Policies** and select **Create Microsoft Defender ATP Policy**. The policy wizard opens.
5. Type the **Name** and **Description** for the Microsoft Defender for Endpoint policy and select **Onboarding**.
6. **Browse** to the configuration file you extracted from the downloaded .zip file.
7. Specify the file samples that are collected and shared from managed devices for analysis.
    - **None**
    - **All file types**
8. Review the summary and complete the wizard.
9. Right-click on the policy you created, then select **Deploy** to target the Microsoft Defender for Endpoint policy to clients.

### Onboard devices with MDE Client and MMA to Microsoft Defender for Endpoint

You can onboard devices running any of the supported operating systems to Microsoft Defender for Endpoint by providing the configuration file, **Workspace key**, and **Workspace ID** to Configuration Manager.

#### Get the configuration file, workspace ID, and workspace key

1. Go to the [Microsoft Defender for Endpoint online service](https://security.microsoft.com/) and sign in.
2. Select **Settings**, then select **Onboarding** under the **Endpoints** heading.
3. For the operating system, select **Windows 10 and 11**.
4. Choose **Microsoft Endpoint Configuration Manager current branch and later** for the deployment method.
5. Select **Download package**.

    [![Screenshot of onboarding configuration file download.](media/5229962-onboarding-configuration.png)](media/5229962-onboarding-configuration.png#lightbox)
6. Download the compressed archive (.zip) file and extract the contents.
7. Select **Settings**, then select **Onboarding** under the **Device management** heading.
8. For the operating system, select either **Windows 7 SP1 and 8.1** or **Windows Server 2008 R2 Sp1, 2012 R2 and 2016** from the list.

    - The **Workspace key** and **Workspace ID** will be the same regardless of which of these options you choose.
9. Copy the values for the **Workspace key** and **Workspace ID** from the **Configure connection** section.

    Important

    The Microsoft Defender for Endpoint configuration file contains sensitive information which should be kept secure.

#### Onboard the devices

1. In the Configuration Manager console, navigate to **Administration** &gt; **Client Settings**.
2. Create custom Client Device Settings or go to the properties of the required client setting and select **Endpoint Protection**
3. For **Microsoft Defender for Endpoint Client on Windows Server 2012 R2 and Windows Server 2016** setting, ensure the value is set as **Microsoft Monitoring Agent (legacy)**.
4. In the Configuration Manager console, navigate to **Assets and Compliance** &gt; **Endpoint Protection** &gt; **Microsoft Defender ATP Policies**.
5. Select **Create Microsoft Defender ATP Policy** to open the policy wizard.
6. Type the **Name** and **Description** for the Microsoft Defender for Endpoint policy and select **Onboarding**.
7. **Browse** to the configuration file you extracted from the downloaded .zip file.
8. Supply the **Workspace key** and **Workspace ID** then select **Next**.

    - Verify that the **Workspace key** and **Workspace ID** are in the correct fields. The order in the console may vary from the order in Microsoft Defender for Endpoint online service. [![Screenshot of Microsoft Defender for Endpoint policy configuration wizard.](media/5229962-create-atp-policy-wizard.png)](media/5229962-create-atp-policy-wizard.png#lightbox)
9. Specify the file samples that are collected and shared from managed devices for analysis.

    - **None**
    - **All file types**
10. Review the summary and complete the wizard.
11. Right-click on the policy you created, then select **Deploy** to target the Microsoft Defender for Endpoint policy to clients.

## Monitor

1. In the Configuration Manager console, navigate **Monitoring** &gt; **Security** and then select **Microsoft Defender ATP**.
2. Review the Microsoft Defender for Endpoint dashboard.

    - **Microsoft Defender ATP Agent Onboarding Status**: The number and percentage of eligible managed client computers with active Microsoft Defender for Endpoint policy onboarded
    - **Microsoft Defender ATP Agent Health**: Percentage of computer clients reporting status for their Microsoft Defender for Endpoint agent

        - **Healthy** - Working properly
        - **Inactive** - No data sent to service during time period
        - **Agent state** - The system service for the agent in Windows isn't running
        - **Not onboarded** - Policy was applied but the agent hasn't reported policy onboard

## Create an offboarding configuration file

1. Sign in to the [Microsoft Defender Security Center](https://securitycenter.windows.com/).
2. Select **Settings**, then select **Offboarding** under the **Endpoint** heading.
3. Select **Windows 10 and 11** for the operating system and **Microsoft Endpoint Configuration Manager current branch and later** for the deployment method.

    - Using the **Windows 10 and 11** option ensures that all devices in the collection are off boarded and the MMA is uninstalled when needed.
4. Download the compressed archive (.zip) file and extract the contents. Offboarding files are valid for 30 days.
5. In the Configuration Manager console, navigate to **Assets and Compliance** &gt; **Endpoint Protection** &gt; **Microsoft Defender ATP Policies** and select **Create Microsoft Defender ATP Policy**. The policy wizard opens.
6. Type the **Name** and **Description** for the Microsoft Defender for Endpoint policy and select **Offboarding**.
7. **Browse** to the configuration file you extracted from the downloaded .zip file.
8. Review the summary and complete the wizard.

Select **Deploy** to target the Microsoft Defender for Endpoint policy to clients.

Important

The Microsoft Defender for Endpoint configuration files contains sensitive information which should be kept secure.

## Updating the onboarding information for existing devices

Organizations may need to update the onboarding information on a device via Microsoft Configuration Manager.

This can be necessary due to a change in the onboarding payload for Microsoft Defender for Endpoint, or when directed by Microsoft support.

Updating the onboarding information will direct the device to start utilizing the new onboarding payload at the next *Restart*.

This process compromises of actions to update the existing onboarding policy, and executing a one time action on all existing devices to update the onboarding payload. Utilize the **Group Policy** onboarding script to perform a one time uplift of devices from the old payload to the new payload.

Note

This information will not necessarily move a device between tenants without fully offboarding the device from the original tenant. For options migrating devices between Microsoft Defender for Endpoint organizations, engage Microsoft Support.

### Validate the new onboarding payload

1. Download the **Group Policy** onboarding package from the Microsoft Defender for Endpoint portal.
2. **Create** a collection for validation of the new onboarding payload
3. **Exclude** this collection from the existing Microsoft Defender for Endpoint collection targeted with the onboarding payload.
4. **Deploy** the **Group Policy** onboarding script to the test collection.
5. **Validate** the devices are utilizing the new onboarding payload.

### Migrate to the new onboarding payload

1. Download the **Microsoft Configuration Manager** onboarding package from the Microsoft Defender for Endpoint portal.
2. **Update** the existing Microsoft Defender for Endpoint onboarding policy with the new onboarding payload.
3. **Deploy** the script from [Validate the new onboarding payload](defender-advanced-threat-protection#validate-the-new-onboarding-payload) to the existing target collection for the Microsoft Defender for Endpoint onboarding policy.
4. **Validate** the devices are utilizing the new onboarding payload and successfully consuming the payload from the script

Note

Once all devices are migrated you can remove the script and validation collections from your environment, using the onboarding policy moving forward.