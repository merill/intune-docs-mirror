---
layout: Conceptual
title: Use Windows Defender Application Control on HoloLens 2 devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wdac-hololens
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
description: Configure the Windows Defender Application Control (WDAC) CSP to allow or block apps from opening on HoloLens 2 devices in Microsoft Intune. Use PowerShell and a custom configuration profile.
ms.date: 2024-06-06T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: 1b553cd1-995c-9a2b-ff57-3200b18f047f
document_version_independent_id: 1b553cd1-995c-9a2b-ff57-3200b18f047f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-wdac-hololens.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-wdac-hololens
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-wdac-hololens.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/05616262-6974-4662-ac87-15adf94b9c3a
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/25c95491-bd10-484c-89ce-1fa29173d007
platformId: ec7ec880-bd9e-1dad-7acb-7dbc64d9b259
---

# Use Windows Defender Application Control on HoloLens 2 devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft HoloLens 2 devices support the [Windows Defender Application Control (WDAC) CSP](/en-us/windows/client-management/mdm/applicationcontrol-csp), which replaces the [AppLocker CSP](/en-us/windows/client-management/mdm/applocker-csp).

Using Windows PowerShell and Microsoft Intune, you can use the WDAC CSP to allow or block specific apps from opening on Microsoft HoloLens 2 devices. For example, you might want to allow or prevent an app from opening on HoloLens 2 devices in your organization.

This feature applies to:

- HoloLens 2 devices running Windows Holographic for Business
- Windows

The WDAC CSP is based on the [Windows Defender Application Control (WDAC) feature](/en-us/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control). You can also [use multiple WDAC policies](/en-us/windows/security/threat-protection/windows-defender-application-control/deploy-multiple-windows-defender-application-control-policies).

This article shows you how to:

1. Use Windows PowerShell to create WDAC policies.
2. Use Windows PowerShell to convert the WDAC policy rules to XML, update the XML, and then convert the XML to a binary file.
3. In Microsoft Intune, create a [custom device configuration profile](ref-custom-settings-windows-holographic), add this WDAC policy binary file, and apply the policy to your HoloLens 2 devices.

In Intune, you must create a custom configuration profile to use the Windows Defender Application Control (WDAC) CSP.

Use the steps in this article as a template to allow or deny specific apps from opening on HoloLens 2 devices.

## Prerequisites

- Be familiar with Windows PowerShell. For information on the execution policy options, go to [Windows PowerShell about_Execution_Policies](/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies).
- To configure the Intune policy, at a minimum, sign in to the Intune admin center as a member of the **Policy and Profile Manager** built-in Intune role.

    For information on the Intune built-in roles, and what they can do, go to:

    - [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview)
    - [Built-in role permissions for Microsoft Intune](../../fundamentals/role-based-access-control/ref-built-in-roles)
- Create a user group or devices group with your HoloLens 2 devices. For information on groups, go to [User groups vs. device groups](../assign-device-profile#user-groups-vs-device-groups).

## Step 1 - Create the WDAC policy using Windows PowerShell

This example uses Windows PowerShell to create a Windows Defender Application Control (WDAC) policy. The policy prevents specific apps from opening.

1. On your desktop computer, open the **Windows PowerShell** app.
2. Get information about the installed application package on your desktop computer and HoloLens:

    ```powershell
    $package1 = Get-AppxPackage -name *<applicationname>*
    ```

    For example, enter:

    ```powershell
    $package1 = Get-AppxPackage -name Microsoft.MicrosoftEdge
    ```

    Next, confirm the package has application attributes:

    ```powershell
    $package1
    ```

    App details similar to the following attributes are shown:

    ```powershell
    Name              : Microsoft.MicrosoftEdge
    Publisher         : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
    Architecture      : Neutral
    ResourceId        :
    Version           : 44.20190.1000.0
    PackageFullName   : Microsoft.MicrosoftEdge_44.20190.1000.0_neutral__8wekyb3d8bbwe
    InstallLocation   : C:\Windows\SystemApps\Microsoft.MicrosoftEdge_8wekyb3d8bbwe
    IsFramework       : False
    PackageFamilyName : Microsoft.MicrosoftEdge_8wekyb3d8bbwe
    PublisherId       : 8wekyb3d8bbwe
    IsResourcePackage : False
    IsBundle          : False
    IsDevelopmentMode : False
    NonRemovable      : True
    IsPartiallyStaged : False
    SignatureKind     : System
    Status            : Ok
    ```
3. Create a WDAC policy, and add the app package to the DENY rule:

    ```powershell
    $rule = New-CIPolicyRule -Package $package1 -Deny
    ```
4. Repeat steps 2 and 3 for any other applications you want to DENY:

    ```powershell
    $rule += New-CIPolicyRule -Package $package<2..n> -Deny
    ```

    For example, enter:

    ```powershell
    $package2 = Get-AppxPackage -name *windowsstore*
    $rule += New-CIPolicyRule -Package $package<2..n>  -Deny
    ```
5. Convert the WDAC policy to **newPolicy.xml**:

    Note

    You can block apps that are only installed on HoloLens devices. For more information, go to [package family names for apps on HoloLens](/en-us/hololens/windows-defender-application-control-wdac#package-family-names-for-apps-on-hololens).

    ```powershell
    New-CIPolicy -rules $rule -f .\newPolicy.xml -UserPEs
    ```

    To target all versions of an app, in newPolicy.xml, be sure `PackageVersion="65535.65535.65535.65535"` is in Deny node:

    ```xml
    <Deny ID="ID_DENY_D_1" FriendlyName="Microsoft.WindowsStore_8wekyb3d8bbwe FileRule" PackageFamilyName="Microsoft.WindowsStore_8wekyb3d8bbwe" PackageVersion="65535.65535.65535.65535" />
    ```

    For `PackageFamilyNameRules`, you can use the following versions:

    - **Allow**: Enter `PackageVersion, 0.0.0.0`, which means "Allow this version and above".
    - **Deny**: Enter `PackageVersion, 65535.65535.65535.65535`, which means "Deny this version and below".
6. If you plan to deploy and run any apps that didn't originate from the Microsoft Store, such as line of business apps (see [App Management](/en-us/hololens/app-deploy-overview)), then explicitly allow these apps by adding their signer to the WDAC policy.

    Note

    Using WDAC and LOB apps is currently only available in [Windows Insiders features for HoloLens](/en-us/hololens/hololens-insider).

    For example, you plan on deploying `ATestApp.msix`. `ATestApp.msix` is signed by the `TestCert.cer` certificate. Use the following Windows PowerShell script to add the signer to the WDAC policy:

    ```powershell
    Add-SignerRule -FilePath .\newPolicy.xml -CertificatePath .\TestCert.cer -User
    ```
7. Merge **newPolicy.xml** with the default policy that's on your desktop computer. This step creates **mergedPolicy.xml**. For example, allow the Windows, WHQL signed drivers, and Store signed apps to run:

    ```powershell
    Merge-CIPolicy -PolicyPaths .\newPolicy.xml,C:\Windows\Schemas\codeintegrity\examplepolicies\DefaultWindows_Audit.xml -o mergedPolicy.xml
    ```
8. Disable the **Audit mode** rule in **mergedPolicy.xml**. When you merge, audit mode is automatically turned on:

    ```powershell
    Set-RuleOption -o 3 -Delete .\mergedPolicy.xml
    ```
9. Enable the **InvalidateEAs on a reboot** rule in **mergedPolicy.xml**:

    ```powershell
    Set-RuleOption -o 15 .\mergedPolicy.xml
    ```

    For information on these rules, go to [Understand WDAC policy rules and file rules](/en-us/windows/security/threat-protection/windows-defender-application-control/select-types-of-rules-to-create).
10. Convert **mergedPolicy.xml** to binary format. This step creates **compiledPolicy.bin**. In Step 2 - Create an Intune policy and deploy the policy to HoloLens 2 devices, you add this **compiledPolicy.bin** binary file to an Intune policy.

    ```powershell
    ConvertFrom-CIPolicy .\mergedPolicy.xml .\compiledPolicy.bin
    ```

## Step 2 - Create an Intune policy and deploy the policy to HoloLens 2 devices

In this step, you create a custom device configuration profile in Intune. In the custom policy, you add the **compiledPolicy.bin** binary file you created in Step 1 - Create the WDAC policy using Windows PowerShell. Then, use Intune to deploy the policy to HoloLens 2 devices.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create a Windows custom device configuration profile.

    For the specific steps, go to [Create a custom profile using OMA-URI in Intune](configure-custom-settings).
2. When you create the profile, enter the following settings:

    - **OMA-URI**: Enter `./Vendor/MSFT/ApplicationControl/Policies/<PolicyGUID>/Policy`. Replace `<PolicyGUID>` with the PolicyTypeID node in the **mergedPolicy.xml** file you created in step 6.

        Using our example, enter `./Vendor/MSFT/ApplicationControl/Policies/A244370E-44C9-4C06-B551-F6016E563076/Policy`.

        The policy GUID **must match** the PolicyTypeID node in the **mergedPolicy.xml** file (created in step 6).

        The OMA-URI uses the [ApplicationControl CSP](/en-us/windows/client-management/mdm/applicationcontrol-csp). For information on the nodes in this CSP, go to [ApplicationControl CSP](/en-us/windows/client-management/mdm/applicationcontrol-csp).
    - **Data type**: Set to **Base64 file**. It automatically converts the file from bin to base64.
    - **Certificate file**: Upload the **compiledPolicy.bin** binary file (created in step 10).

    Your settings look similar to the following settings:

    ![Add a custom OMA-URI to configure ApplicationControl CSP in Microsoft Intune.](media/configure-wdac-hololens/custom-applicationcontrol-omauri.png)
3. When the profile is [assigned](../assign-device-profile) to your HoloLens 2 group, check the profile status. After the profile successfully applies, reboot the HoloLens 2 devices.