---
layout: Conceptual
title: Using Azure Virtual Desktop multi-session with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/azure-virtual-desktop-multi-session
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Guidelines for using Azure Virtual Desktop multi-session with Microsoft Intune
ms.date: 2025-02-13T00:00:00.0000000Z
ms.topic: article
ms.reviewer: madakeva
ms.collection:
- M365-identity-device-management
locale: en-us
document_id: 53c6ebc0-5850-6907-0bd1-77516ac574df
document_version_independent_id: 53c6ebc0-5850-6907-0bd1-77516ac574df
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/azure-virtual-desktop-multi-session.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/azure-virtual-desktop-multi-session
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/azure-virtual-desktop-multi-session.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: e500f8db-f1d6-661f-f5e1-3817667ff207
---

# Using Azure Virtual Desktop multi-session with Microsoft Intune - Microsoft Intune | Microsoft Learn

Azure Virtual Desktop multi-session with Microsoft Intune is now generally available.

You can now use Microsoft Intune to manage Windows Enterprise multi-session remote desktops in the Microsoft Intune admin center just as you can manage a shared Windows client device. When managing such virtual machines (VMs), you can use device-based configuration targeted to devices or user-based configuration targeted to users.

Windows Enterprise multi-session is a new Remote Desktop Session Host exclusive to [Azure Virtual Desktop](/en-us/azure/virtual-desktop/) on Azure. It provides the following benefits:

- Allows multiple concurrent user sessions.
- Gives users a familiar Windows experience.
- Supports use of existing per-user Microsoft 365 licensing.

You can manage **Windows Enterprise multi-session** VMs created in Azure Government Cloud in US Government Community (GCC), GCC High, and DoD.

Important

Microsoft Intune support for Azure Virtual Desktop multi-session is not currently available for Citrix DaaS and VMware Horizon Cloud. Because Intune cannot offer support for Citrix DaaS, review the Citrix documentation, and be aware of Citrix support options for multi-session support. All questions, concerns or help should be directed to Citrix for multi-session support. See [Citrix support](https://docs.citrix.com/en-us/citrix-daas/install-configure/machine-identities/microsoft-intune).

## Overview

Device configuration support in Microsoft Intune for Windows Enterprise multi-session is generally available (GA). This means [policies defined in the OS scope](/en-us/windows/client-management/mdm/policy-configuration-service-provider) and apps configured to install in the system context can be applied to Azure Virtual Desktop multi-session VMs when assigned to device groups.

Note

Device-based configuration cannot be assigned to users and user-based configuration cannot be assigned to devices. It's reported as **Error** or **Not applicable**.

User configuration support in Microsoft Intune for Windows Enterprise multi-session VMs is generally available. With this you are able to:

- Configure user scope policies using **Settings catalog** and assign to groups of users. You can use the search bar to search all configurations with scope set to "user".
- Configure user certificates and assign to users.
- Configure PowerShell scripts to install in the user context and assign to users.

## Prerequisites

This feature supports Windows Enterprise multi-session VMs, which are:

- Set up as remote desktops in pooled host pools that have been deployed through Azure Resource Manager.
- Under the same tenant as Intune.
- Running an Azure Virtual Desktop agent version of 1.0.2944.1400 or later.
- [Microsoft Entra hybrid joined](/en-us/azure/active-directory/devices/hybrid-azuread-join-plan)and enrolled in Microsoft Intune using one of the following methods:
    - Configured with [Active Directory group policy](/en-us/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy), set to use Device credentials, and set to automatically enroll devices that are Microsoft Entra hybrid joined.
    - [Configuration Manager co-management](/en-us/configmgr/comanage/overview).
- Microsoft Entra joined and enrolled in Microsoft Intune by enabling [Enroll the VM with Intune](/en-us/azure/virtual-desktop/deploy-azure-ad-joined-vm#deploy-azure-ad-joined-vms) in the Azure portal.
- Licensing: The appropriate Azure Virtual Desktop and Microsoft Intune license is required if a user or device benefits directly or indirectly from the Microsoft Intune service, including access to the Microsoft Intune service through a Microsoft API. For more information, go to [Microsoft Intune licensing](../fundamentals/licensing).
- See [Licensing Azure Virtual Desktop](/en-us/azure/virtual-desktop/licensing) for more information about Azure Virtual Desktop licensing requirements.

## Limitations

Intune does not support using a cloned image of a computer that is already enrolled. This includes both physical and virtual devices such as Azure Virtual Desktop (AVD). When device enrollment or identity tokens are replicated between devices, Intune device enrollment or synchronization failures will occur.

- For more information, see [Mobile device enrollment - Windows Client Management](/en-us/windows/client-management/mobile-device-enrollment) and [Certificate authentication device enrollment - Windows Client Management](/en-us/windows/client-management/certificate-authentication-device-enrollment).
- For information on troubleshooting issues related to image cloning, see [Error hr 0x8007064c: The machine is already enrolled](/en-us/troubleshoot/mem/intune/troubleshoot-windows-enrollment-errors#error-hr-0x8007064c-the-machine-is-already-enrolled).

Note

If you're joining session hosts to Microsoft Entra Domain Services, you can't manage them using Intune.

Important

- Intune does not currently support token roaming functionality between devices. If [FSLogix](/en-us/fslogix), or a similar technology, is used to manage Windows user profiles and settings, you must ensure that tokens are not unexpectedly roamed or duplicated across devices. To confirm that you are running a supported version and configuration of FSLogix with token roaming disabled, please see the [FSLogix RoamIdentity Configuration Settings Reference](/en-us/fslogix/reference-configuration-settings?tabs=profiles#roamidentity).

Windows Enterprise multi-session VMs are treated as a separate OS edition and some Windows Enterprise configurations won't be supported for this edition. Using Microsoft Intune doesn't depend on or interfere with Azure Virtual Desktop management of the same VM.

## Create the configuration profile

To configure configuration policies for Windows Enterprise multi-session VMs, use the [Settings catalog](../device-configuration/settings-catalog/) in the Microsoft Intune admin center.

Only the following configuration profile templates are supported for Windows Enterprise multi-session VMs:

- [Trusted certificate](../device-configuration/certificates/trusted-root-profiles#create-trusted-certificate-profiles) - Device (machine) when targeting devices and User when targeting users
- [SCEP certificate](../device-configuration/certificates/scep-profiles#create-a-scep-certificate-profile) - Device (machine) when targeting devices and User when targeting users
- [PKCS certificate](../device-configuration/certificates/pkcs-profiles#create-a-pkcs-certificate-profile) - Device (machine) when targeting devices and User when targeting users
- [VPN](../device-configuration/templates/configure-vpn#step-2---create-the-profile) - Device Tunnel only

Microsoft Intune won't deliver unsupported templates to multi-session devices, and those policies appear as *Not applicable* in reports.

Note

If you use co-management for Intune and Configuration Manager, in Configuration Manager, [set the workload slider](/en-us/configmgr/comanage/how-to-switch-workloads) for Resource Access Policies to **Intune** or **Pilot Intune**. This setting allows Windows clients to start the process of requesting the certificate.

### To configure policies

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and choose **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New Policy**.
2. For **Platform**, select **Windows 10 and later**.
3. For **Profile type**, select **Settings catalog**, or when deploy settings by using a Template, select **Templates** and then the name of the supported Template.
4. Select **Create**.
5. On the **Basics** page, provide a **Name** and (optionally) **Description** &gt; **Next**.
6. On the **Configuration settings** page, select **Add settings**.
7. Under **Settings picker**, select **Add filter**and select the following options:
    - **Key**: **OS edition**
    - **Operator**: **==**
    - **Value**: **Enterprise multi-session**
    - Select **Apply**. The filtered list now shows all configuration profile categories that support Windows Enterprise multi-session. The scope for a policy is shown in parentheses. For user scope it shows as (User) and all the rest are policies with device scope.
8. From the filtered list, pick the categories that you want.
    - For each category you pick, select the settings that you want to apply to your new configuration profile.
    - For each setting, select the value that you want for this configuration profile.
9. Select **Next** when you're done adding settings.
10. On the **Assignments** page, choose the Microsoft Entra groups containing the devices to which you want this profile assigned &gt; **Next**.
11. On the **Scope tags** page, optionally add the scope tags you want to apply to this profile &gt; **Next**. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../fundamentals/role-based-access-control/scope-tags).
12. On the **Review + create** page, choose **Create** to create the profile.

### Administrative templates

Administrative Templates in the [Intune settings catalog](../device-configuration/settings-catalog/) are supported for Windows Enterprise multi-session with some limitations:

- ADMX-backed policies are supported. Some policies aren't yet available in the Settings catalog.
- ADMX-ingested policies are supported. For a complete list of ADMX-ingested policy categories, see [Win32 and Desktop Bridge app policy configuration](/en-us/windows/client-management/mdm/win32-and-centennial-app-policy-configuration#overview). Some ADMX ingested settings won't be applicable to Windows Enterprise multi-session.

## Compliance and Conditional Access

You can secure your Windows Enterprise multi-session VMs by configuring compliance policies and Conditional Access policies in the Microsoft Intune admin center. The following compliance policies are supported on Windows Enterprise multi-session VMs:

- Minimum OS version
- Maximum OS version
- Valid operating system builds
- Simple passwords
- Password type
- Minimum password length
- Password Complexity
- Password expiration (days)
- Number of previous passwords to prevent reuse
- Microsoft Defender Antimalware
- Microsoft Defender Antimalware security intelligence up-to-date
- Firewall
- Antivirus
- Antispyware
- Real-time protection
- Microsoft Defender Antimalware minimum version
- Defender ATP Risk score

All other policies report as **Not applicable**.

Important

You'll need to create a new compliance policy and target it to the device group containing your multi-session VMs. User-targeted compliance configurations aren't supported.

[Conditional Access policies](../device-security/conditional-access-integration/overview) support both user and device based configurations for Windows Enterprise multi-session.

## Endpoint security

You can configure profiles under Endpoint security for multi-session VMs by selecting Platform Windows. If that Platform is not available, the profile is not supported on multi-session VMs.

For more information, see [Manage device security with endpoint security policies in Microsoft Intune](../device-configuration/endpoint-security/manage-policies)

## Application deployment

All Windows apps can be deployed to Windows Enterprise multi-session with the following restrictions:

- All apps must be configured to install in the system/device context and be targeted to devices. Web apps are always applied in the user context by default so they won't apply to multi-session VMs.
- All apps must be configured with **Required** or **Uninstall** app assignment intent. The **Available apps** deployment intent isn't supported on multi-session VMs.
- If a Win32 app configured to install in the system context has dependencies or supersedence relationship on any apps configured to install in the user context, the app won't be installed. To apply to a Windows Enterprise multi-session VM, create a separate instance of the system context app or make sure all app dependencies are configured to install in the system context.
- Azure Virtual Desktop RemoteApp and MSIX app attach aren't currently supported in Microsoft Intune.

## Script deployment

Scripts configured to run in the system context and assigned to devices are supported on Windows Enterprise multi-session. This can be configured under Script settings by setting **Run this script using the logged on credentials** to **No**.

Scripts configured to run in the user context and assigned to users are supported on Windows Enterprise multi-session. This can be configured under Script settings by setting **Run this script using the logged on credentials** to **Yes**.

## Windows Update client policies

You can use the [settings catalog](../device-configuration/settings-catalog/) to manage Windows Update settings for quality (security) updates for Windows Enterprise multi-session VMs. To find the supported settings in the catalog, configure a settings filter for *Enterprise multi-session* and then expand the *Windows Update for Business* category.

The following settings are available in the catalog, with the links opening the Windows CSP documentation:

- [Active Hours End](/en-us/windows/client-management/mdm/policy-csp-Update#update-activehoursend)
- [Active Hours Max Range](/en-us/windows/client-management/mdm/policy-csp-Update?#update-activehoursmaxrange)
- [Active Hours Start](/en-us/windows/client-management/mdm/policy-csp-Update#update-activehoursstart)
- [Block "Pause Updates" ability](/en-us/windows/client-management/mdm/policy-csp-Update#update-setdisablepauseuxaccess)
- [Configure Deadline Grace Period](/en-us/windows/client-management/mdm/policy-csp-Update#update-configuredeadlinegraceperiod)
- [Defer Quality Updates Period (Days)](/en-us/windows/client-management/mdm/policy-csp-Update#update-deferqualityupdatesperiodindays)
- [Pause Quality Updates Start Time](/en-us/windows/client-management/mdm/policy-csp-Update#update-pausequalityupdatesstarttime)
- [Quality Update Deadline Period (Days)](/en-us/windows/client-management/mdm/policy-csp-Update?#update-configuredeadlineforqualityupdates)

## Remote actions

The following Windows desktop device remote actions aren't supported and will be grayed out in the UI and disabled in Graph for Windows Enterprise multi-session VMs:

- Windows Autopilot reset
- BitLocker key rotation
- Fresh Start
- Remote lock
- Reset password
- Wipe

## Retirement

Deleting VMs from Azure will leave orphaned device records in the Microsoft Intune admin center. AVD machines are deleted automatically after 30 days and removed permanently after 60 days. For more information, see:

- [Using Intune device cleanup rules](https://techcommunity.microsoft.com/t5/device-management-in-microsoft/using-intune-device-cleanup-rules-updated-version/ba-p/3760854).
- [Automatically remove devices with cleanup rules](../governance/configure-cleanup-rules)

## Security baselines

Security baselines are available for Windows Enterprise multi-session. We recommend that you review the [Available security baselines](../device-security/security-baselines/overview) and configure the recommended policies and values in the [Settings catalog](../device-configuration/settings-catalog/).

## Additional configurations that aren't supported on Windows Enterprise multi-session VMs

Out of Box Experience (OOBE) enrollment isn't supported for Windows Enterprise multi-session. This restriction means that:

- Windows Autopilot and Commercial OOBE aren't supported.
- Enrollment status page isn't supported.

Windows Enterprise multi-session managed by Microsoft Intune isn't currently supported for China Sovereign Cloud.

## Troubleshooting

The following sections provide troubleshooting guidance for common issues.

### Enrollment issues

| Issue | Detail |
| --- | --- |
| Enrollment of Microsoft Entra hybrid joined virtual machine fails | - Auto-enrollment is configured to use user credentials. Windows Enterprise multi-session virtual machines must be enrolled using device credentials.<br>- The Azure Virtual Desktop agent you're using must be version 1.0.2944.1400 or later.<br>- You've more than one MDM provider, which isn't supported.<br>- Windows Enterprise multi-session VM is configured outside of a host pool. Microsoft Intune only supports VMs provisioned as part of a host pool.<br>- The Azure Virtual Desktop host pool wasn't created through the Azure Resource Manager template. |
| Enrollment of Microsoft Entra joined virtual machine fails | - The Azure Virtual Desktop agent you're using isn't updated. The agent must be version 1.0.2944.1400 or above.<br>- Azure Virtual Desktop host pool wasn't created through the Azure Resource Manager template. |

### Configuration issues

| Issue | Detail |
| --- | --- |
| Settings catalog policy fails | Confirm the VM is enrolled using device credentials. Enrollment with user credentials isn't currently supported for Windows Enterprise multi-session. |
| Configuration policy didn't apply | Templates (except for Certificates) aren't supported on Windows Enterprise multi-session. All policies must be created via the settings catalog. |
| Configuration policy reports as Not applicable | Some policies aren't applicable to Azure Virtual Desktop VMs. |
| Microsoft Edge/Microsoft Office ADMX policy doesn't show up when I apply the filter for Windows Enterprise multi-session edition | Applicability for these settings isn't based on the Windows version or edition but on whether those apps have been installed on the device. To add these settings to your policy, you may have to remove any filters applied in the settings picker. |
| App configured to install in system context didn't apply | Confirm the app doesn't have a dependency or supersedence relationship on any apps configured to install in user context. User context apps aren't currently supported on Windows Enterprise multi-session. |
| Update rings for Windows policy didn't apply | Windows update rings policies aren't currently supported. Quality updates can be managed via settings available in the [settings catalog](../device-configuration/settings-catalog/). |