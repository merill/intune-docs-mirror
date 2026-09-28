---
layout: Conceptual
title: Find a package family name (PFN) for per-app VPN - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn
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
description: Learn about the two ways to find a package family name so that you can configure a per-app VPN.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 37fe1293-c091-34fd-8a00-0951ca8daf8f
document_version_independent_id: 4507030e-4b36-fc49-875c-6d3a9b9a19c8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 071a57de-a5b3-5958-d205-89dd83c4d2de
---

# Find a package family name (PFN) for per-app VPN - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

There are two ways to find a PFN so that you can configure a per-app VPN.

## Find a PFN for an app that's installed on a Windows 10 computer

If the app you're working with is already installed on a Windows 10 computer, you can use the [Get-AppxPackage](/en-us/powershell/module/appx/get-appxpackage) PowerShell cmdlet to get the PFN.

The syntax for Get-AppxPackage is:

```Syntax
Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]
```

Note

You may have to run PowerShell as an admin in order to retrieve the PFN

For example, to get info on all the universal apps installed on the computer use `Get-AppxPackage`.

To get info on an app you know the name of, or part of the name of, use `Get-AppxPackage *<app_name>`. Note the use of the wildcard character, particularly helpful if you're not sure of the full name of the app. For example to get the info for OneNote, use `Get-AppxPackage *OneNote`.

Here's the information retrieved for OneNote:

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`

## Find a PFN if the app is not installed on a computer

1. Go to https://www.microsoft.com/store/apps
2. Enter the name of the app in the search bar. In our example, search for OneNote.
3. Click the link to the app. The URL that you access has a series of letters at the end. In our example, the URL looks like this: `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`
4. In a different tab, paste the following URL, `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`, replacing `<app id>` with the app ID you obtained from https://www.microsoft.com/store/apps - that series of letters at the end of the URL in step 3. In our example, example of OneNote, you'd paste: `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`.

In Microsoft Edge, the information you want is displayed; in Internet Explorer, click **Open** to see the information. The PFN value is given on the first line. Here's how the results look for our example:

```JSON
{
  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",
  "packageIdentityName": "Microsoft.Office.OneNote",
  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",
  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
}
```