---
layout: Conceptual
title: Import Custom and Third-party Partner ADMX Templates in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/import-custom-admx-templates
author: iceorbital
ms.author: acabello
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: You can add, upload, or import custom and third-party partner ADMX and ADML files in Microsoft Intune.
ms.date: 2026-11-10T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano, kabalu
locale: en-us
document_id: 530ce86c-57a3-4bfe-95f3-2507aa51f358
document_version_independent_id: 530ce86c-57a3-4bfe-95f3-2507aa51f358
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/import-custom-admx-templates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/import-custom-admx-templates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/import-custom-admx-templates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 50532c73-2281-c08d-8232-168b65e5398c
---

# Import Custom and Third-party Partner ADMX Templates in Microsoft Intune - Microsoft Intune | Microsoft Learn

You can import custom and partner ADMX and ADML templates into the Intune admin center. After you import them, you can create a device configuration policy that uses these settings, and then assign the policy to your managed devices.

This feature applies to:

- Windows

This article shows you how to import custom ADMX and ADML files in the Intune admin center.

Tip

The settings catalog has many settings built in to Intune, including Google Chrome. For more information, see:

- [Use the settings catalog to configure settings](./)
- [Common tasks you can complete using the Settings Catalog](common-tasks)

## What you need to know

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

    To modify or update an ADMX policy by using the **Not Configured** setting, RBAC administrators need the **Device configurations** &gt; **Delete** permission. The built-in **Policy and Profile Manager** role has this permission.
- This feature is in [public preview](../../fundamentals/public-preview).
- There are some limits:

    - You can upload up to 20 ADMX files. Each file must be 1 MB or smaller.
    - For each ADMX file, you can upload only one ADML file.
    - Each ADMX file supports one language.
    - Only `en-us` ADML files are supported.
- Some ADMX files have dependency prerequisites. Import any dependency ADMX files first. If you upload an ADMX file without the dependency, an error message lists the missing namespace.

    For example, to import Mozilla Firefox ADMX and ADML files, you:

    1. Import the `mozilla.admx` and `mozilla.adml` files. Ensure the status shows **Available**.
    2. Import the `firefox.admx` and `firefox.adml` files.

    If you upload `firefox.admx` before `mozilla.adml`, the import fails.

    To see if your ADMX has a dependency, open the ADMX file in a text editor, go to the `policyNamespaces` node, and look for `using prefix`. Any dependencies are listed.

    In the following example, the `kerberos.admx` file requires the `Windows.admx` file:

    ```xml
    <policyNamespaces>
        <target prefix="kerberos" namespace="Microsoft.Policies.Kerberos" />
        <using prefix="windows" namespace="Microsoft.Policies.Windows" />
      </policyNamespaces>
    ```

    To remove a dependency prerequisite, delete the associated ADMX file first. Then, delete the dependency prerequisite. In the Mozilla Firefox example, delete `firefox.admx` and then delete `mozilla.admx`.
- Some files might require `Windows.admx` as a prerequisite. You must upload this file first. In a future release (no ETA), this namespace will be automatically included and eventually not be required.

    If `Windows.admx` is required and not uploaded, you might receive the following error message:

    `ADMX file referenced not found NamespaceMissing:Microsoft.Policies.Windows. Please upload it first.`
- Currently, the combo box setting type isn't supported. ADMX files with the combo box setting type fail to import. All other setting types are supported.
- You can't set all areas of the registry by using custom ADMX. For more information about the registry locations you can use, see [Win32 and Desktop Bridge app ADMX policy Ingestion Overview](/en-us/windows/client-management/win32-and-centennial-app-policy-configuration#overview).
- ADMX settings that are built into Windows and located in the `C:\Windows\PolicyDefinitions` folder are enabled through configuration service providers (CSPs).

    - Don't import these built-in settings if your intent is to configure them. Instead, use the [settings catalog](./) or a [custom profile](../templates/configure-custom-settings).
    - Do import these built-in settings if they're a required parent namespace of another file.

    For a list of the ADMX backed CSP settings, see [ADMX-backed policies in Policy CSP](/en-us/windows/client-management/mdm/policies-in-policy-csp-admx-backed).

## Download the ADMX templates

Download the ADMX templates you want to import. Save these files to an easily accessible folder, like `C:\ADMXTemplates`. Some common ADMX template downloads include:

- Adobe Reader
- Mozilla Firefox
- Zoom

## Add the ADMX and ADML files

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Import ADMX** tab &gt; **Import**:

    ![Screenshot that shows how to add or import custom ADMX and ADML by going to Devices &gt; Configuration profiles &gt; Import ADMX in the Microsoft Intune admin center.](media/import-custom-admx-templates/import-admx.png)

    Or, you can also import from **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; **Import ADMX** tab.
3. Upload your files:

    - **ADMX file**: Select the ADMX file you want to upload.
    - **ADML file for the default language**: Select the ADML file you want to upload. You can add only one language file for each ADMX file you upload. For other limitations, see What you need to know (in this article).
    - **Specify the language of the ADML file**: Shows the ADML language of the file you uploaded.
4. Select **Next**.
5. In **Review + Create**, review your changes. Select **Create** to import the files.

When the import finishes, your ADMX templates appear in the list. You can also:

- Select **Refresh** to see the updated state.
- See the upload **Status**.
- **Delete** an imported template.

![Screenshot that shows how to refresh and delete imported custom ADMX and ADML administrative templates in Microsoft Intune and Intune admin center.](media/import-custom-admx-templates/imported-templates-refresh-delete.png)

## Create a profile using your imported files

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Imported Administrative templates (Preview)**:

        ![Screenshot that shows how to select imported administrative templates to create a device configuration profile using the imported ADMX settings in the Microsoft Intune admin center.](media/import-custom-admx-templates/select-imported-administrative-templates.png)
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **ADMX: Mozilla Firefox for Windows devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select and configure the settings you want in your policy. When finished, select **Next**.
8. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
9. In **Assignments**, select the user or groups to receive your profile. For more information on assigning profiles, see [Assign user and device profiles in Intune](../assign-device-profile).

    If you assign the profile to user groups, the configured ADMX settings apply to any device that the user enrolls and signs in to. If you assign the profile to device groups, the configured ADMX settings apply to any user that signs in to that device. This assignment happens if the ADMX setting is a computer configuration (`HKEY_LOCAL_MACHINE`), or a user configuration (`HKEY_CURRENT_USER`). With some settings, a computer setting assigned to a user can also affect the experience of other users on that device.

    For more information, see [User groups vs. device groups when assigning policies](../assign-device-profile#user-groups-vs-device-groups).

    Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, you save your changes and assign the profile. The policy also appears in the profiles list.

## Replace existing ADMX files

If you upload an ADMX file with settings that you already imported, the upload fails.

For example, if you upload a different version of an ADMX file that has the same settings as the original ADMX file, the upload fails with a namespace error.

To update existing ADMX files that you imported, use the following options:

- **Option 1: Replace the existing ADMX file**

    To replace an existing ADMX file with the same settings, use the following steps:

    1. Delete any profiles that use the existing ADMX settings.
    2. Delete the original ADMX file you imported.
    3. Import the new ADMX and ADML files.
- **Option 2: Create a new ADMX file**

    1. Create another version of the ADMX file with a different namespace than the original ADMX file. Add a version number in the namespace so the names are different.
    2. Add the new and different settings to this ADMX file.
    3. Import the new ADMX and ADML files.