---
layout: Conceptual
title: Assign Microsoft Intune licenses - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/assign-licenses
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
description: Assign licenses to users so they can enroll in Intune
ms.date: 2025-01-24T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e7bc23d4-d542-efb4-875c-7a7ea0bc2b53
document_version_independent_id: e7bc23d4-d542-efb4-875c-7a7ea0bc2b53
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/assign-licenses.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/assign-licenses
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/assign-licenses.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: db3f175d-6dcd-4a36-8a5d-e9762ec52168
---

# Assign Microsoft Intune licenses - Microsoft Intune | Microsoft Learn

Whether you manually add users or synchronize from your on-premises Active Directory, you must first assign each user license before users can enroll their devices in Intune. For a list of licenses, see [Microsoft Intune licensing](licensing).

Note

Users assigned Intune app protection policy and not enrolling their devices into Microsoft Intune will also require an Intune license to receive the policy.

## Assign an Intune license in the Microsoft 365 admin center

You can use the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854) to manually add cloud-based users and assign licenses to both cloud-based user accounts and accounts synchronized from your on-premises Active Directory to Microsoft Entra ID.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), select **Users** &gt; **Active users** &gt; *choose an unlicensed user* &gt; **Licenses and apps**.
2. Choose the box for **Intune** &gt; **Save changes**. If you want to use the Enterprise Mobility + Security E5 or other license, choose that box instead. For more information about Microsoft Intune licenses, see [Microsoft Intune licensing](licensing).

The user account now has the permissions needed to use the service and enroll devices into Intune management.

## Use School Data Sync to assign licenses to users in Intune for Education

If you're an educational organization, you can use School Data Sync (SDS) to assign Intune for Education licenses to synced users. Just choose the Intune for Education checkbox when you're setting up your SDS profile.

![Screenshot of the School Data Sync profile setup with the Intune for Education license checkbox.](media/assign-licenses/i4e-sds-profile-setup-setting.png)

When you assign an Intune for Education license, make sure that Intune A Direct license is also assigned.

![Screenshot of the product license assignment page showing the Intune A Direct license selected.](media/assign-licenses/i4e-set-licenses.png)

See this [overview of School Data Sync](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91) to learn more about SDS.

## How user and device licenses affect access to services

- Each **user** that you assign a user software license to may access and use the online services and related software (including System Center software) to manage applications and up to 15 MDM devices.
- You can purchase licenses for any devices separately from user licenses. Device licenses don't need to be assigned to the devices. Each device that accesses and uses the online services and related software (including System Center software) must have a device license available in the Microsoft 365 tenant.
- If a device is used by more than one user, each device requires a device based software license or all users require a user software license.
- If you remove a license from a user that has managed devices, it may affect the compliance or management of those devices.

## How to restore users accidentally unlicensed

- If you have accidentally removed the license for one or more users, you can restore their device compliance and management by re-assigning the license for those users. For more information, see Assign Microsoft Intune licenses.

## Understanding the type of licenses you have purchased

How you purchased Intune determines your subscription information:

- If you purchased Intune through an Enterprise Agreement, you can find your subscription information in the Volume License portal under **Subscriptions**.
- If you purchased Intune through a Cloud Solution Provider, check with your reseller.
- If you purchased Intune with a CC# or Invoice, then your licenses will be user-based.

## Look up current licenses

You must use [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854) to manage your licenses. However, you can view license details in Microsoft Intune admin center and Microsoft Entra admin center.

### Microsoft 365 admin center

Using the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), you can manage the subscription licenses your organization has available. To find these details, sign-in to the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854), select **Billing** &gt; **Licenses**, then select the **Subscriptions** tab. Additionally, you can view the products owned by your organization in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854) by selecting **Billing** &gt; **Your products**, then select the **Products** tab. The [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?LinkId=698854) also provides licenses details for users by selecting **Users** &gt; **Active users** &gt; *select a user* &gt; **Licenses and apps**.

Note

Managing licenses is only available with in the Microsoft 365 Admin Center.

### Microsoft Intune admin center

Using the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), you can view the **Total licensed users** and the **Total Intune licenses**. To find these details, sign-in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Tenant administration** &gt; **Tenant status** and select the **Tenant details** tab. Additionally, you can view the assigned licenses available for a user in Intune by selecting **Users** &gt; *select a user* &gt; **Licenses**.

### Microsoft Entra admin center

Much like Microsoft Intune admin center, you can use the [Microsoft Entra admin center](https://entra.microsoft.com) to view available product licenses and assigned user license. To view product licenses in the [Microsoft Entra admin center](https://entra.microsoft.com), select **Licenses** under the **Billing** section, and select **All products**. To view the assigned licenses available for a user, select **Users** &gt; **All users** &gt; *select a user* &gt; **Licenses**.

## Look up current licenses using PowerShell

To view the number of free and used licenses on a Microsoft Intune subscription, you can use the following steps to run PowerShell commands.

1. From a PowerShell prompt, run the following command:

    ```powershell
    $creds = Get-Credential
    ```
2. A pop-up window will prompt for credentials. Enter your Microsoft Intune credentials.
3. Run the following command:

    ```powershell
    Connect-MgGraph -Credential $creds
    ```
4. Run the following command:

    ```powershell
    Get-MgSubscribedSku
    ```

    A list of the **Account ID**, the **Active Units**, and the **Consumed Units** will appear. Note that this will also display any Microsoft Office 365 licenses on the subscription.

Note

To confirm your Microsoft Entra ID P1 or P2 and Microsoft Intune using Microsoft Intune admin center, see [Confirm your licenses](licensing#confirm-your-licenses).

## Use PowerShell to selectively manage EMS user licenses

Organizations that use Microsoft Enterprise Mobility + Security (formerly Enterprise Mobility Suite) might have users who only require Microsoft Entra ID P1 or P2 or Intune services in the EMS package. You can assign one or a subset of services using [Microsoft Graph PowerShell cmdlets](/en-us/powershell/module/microsoft.graph.users.actions/set-mguserlicense).

To selectively assign user licenses for EMS services, open PowerShell as an administrator on a computer with the [Microsoft Graph PowerShell](/en-us/powershell/microsoftgraph/installation) installed. You can install PowerShell on a local computer or on an ADFS server.

You must create a new license SKU definition that applies only to the desired service plans. To do this, disable the plans you don't want to apply. For example, you might create a license SKU definition that doesn't assign an Intune license. To see a list of available services, type:

```powershell
(Get-MgSubscribedSku | Where {$_.SkuPartNumber -eq "EMS"}).ServiceStatus
```

You can run the following command to exclude the Intune service plan. You can use the same method to expand to an entire security group or you can use more granular filters.

**Example 1** Create a new user on the command line and assign an EMS license without enabling the Intune portion of the license:

```powershell
Connect-MgGraph

New-MgUser -DisplayName "Test User" -FirstName FName -LastName LName -UserPrincipalName user@<TenantName>.onmicrosoft.com –Department DName -UsageLocation US

$CustomEMS =     Set-MgUserLicense -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
Set-MgUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -AddLicenses <TenantName>:EMS -LicenseOptions $CustomEMS
```

Verify with:

```powershell
(Get-MgUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus
```

**Example 2** Disable the Intune portion of EMS license for a user that is already assigned with a license:

```powershell
Connect-MgGraph

$CustomEMS =     Set-MgUserLicense -AccountSkuId "<TenantName>:EMS" -DisabledPlans INTUNE_A
Set-MgUserLicense -UserPrincipalName user@<TenantName>.onmicrosoft.com -LicenseOptions $CustomEMS
```

Verify with:

```powershell
(Get-MgUser -UserPrincipalName "user@<TenantName>.onmicrosoft.com").Licenses.ServiceStatus
```

![PowerShell output showing user license and service status verification.](media/assign-licenses/posh-addlic-verify.png)