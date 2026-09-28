---
layout: Conceptual
title: Set terms and conditions in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/create-terms-and-conditions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Set terms and conditions that users see in the Company Portal for Intune.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 8b73bb7f-0b2d-27ef-bca0-8c7229b3b1cc
document_version_independent_id: 8b73bb7f-0b2d-27ef-bca0-8c7229b3b1cc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/create-terms-and-conditions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/create-terms-and-conditions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/create-terms-and-conditions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: b36804a4-e619-884b-8db7-ad2536a8243d
---

# Set terms and conditions in Microsoft Intune - Microsoft Intune | Microsoft Learn

Use an Intune terms and conditions policy to present relevant disclaimers for legal or compliance requirements to device users. A terms and conditions policy requires targeted users to accept your terms in Company Portal before they can enroll devices or access protected resources.

This article describes how to get started with terms and conditions in Intune.

## Create terms and conditions

Complete these steps to create an Intune terms and conditions policy.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Tenant administration**.
3. Expand **End user experiences**, and then select **Terms and conditions**.
4. Choose **Create**.
5. On the **Basics** page, enter the following information:

    - **Name**: Give your policy a name so that you can recognize it in Intune later. Device users don't see this name.
    - **Description**: Optionally, describe the purpose or intended use for this specific set of terms.
6. Select **Next**.
7. On the **Terms** page, enter the following information:

    - **Title**: The display name for your terms. Users see the title in the Company Portal app.
    - **Terms and conditions**: The terms and conditions that users see and must either accept or reject.
    - **Summary of terms**: Enter a brief, high-level explanation of what the user is agreeing to. This text is visible to device users.

        Example message: *By enrolling your device, you're agreeing to the terms of use set out by Contoso. Read the terms carefully before proceeding.*
8. Select **Next**.
9. Choose **Select scope tags**, and then select a scope tag from the list to add it to the terms and conditions, or select the default scope tag. Then select **Next**.
10. On the **Assignments** page, choose who you want to assign the terms to. Your options:

    - **Add all users**: Choose this option to assign these terms and conditions to all device users.
    - **Add groups**: Choose this option to assign these terms and conditions to users in select groups.
11. Select **Next**.
12. Review the summary of your new terms and conditions, and then select **Create**.

## How it looks to users

Targeted users can see the terms and conditions in the Intune Company Portal app. The following image shows what the title and summary of terms look like in the app. Intune formats the title with bold font to make it stand out, with the summary of terms positioned directly under it.

![Example image of the drafted terms in the Intune and then what it looks like in Company Portal.](media/create-terms-and-conditions/terms-summary-terms.png)

Device users tap **Read terms** to expand the terms and conditions to full-view. The following image shows what the terms and conditions look like when expanded.

![Example image of the drafted terms and conditions message in Intune and then what it looks like in Company Portal.](media/create-terms-and-conditions/terms-properties-terms.png)

## Monitor acceptance of terms

An acceptance report provides the details of an individual's agreement to your terms and conditions. Intune reports the following details:

- User name: The name of the user who accepted the terms.
- Accepted version: The version that was accepted.
- Accepted time: The date and time of acceptance.
- Accepted latest: Shows whether device user accepted the latest terms and conditions available.
- UPN: The user principal name assigned to the device user.

To view and export acceptance reports:

1. Go to **Terms and conditions**.
2. Select your terms from the table.
3. Select **Acceptance Reporting** to view available reports.
4. Select **Export** to save the reports to your device.

Note

Report data is updated every 24 hours and can take up to 12 hours to finish generating. Because of this, data in the report can have up to a 36 hour latency.

## Provide localized terms and conditions

You can create multiple policies using localized text, and then target each policy to the appropriate groups of users.

## Update terms and conditions

Microsoft Intune provides a version control setting so that you can track versions and notify users of changes to your terms. As a best practice, every time you make a significant change to your terms and conditions, you should:

- Increase the version number in Intune.
- Require assigned users to review and reaccept the updated terms.

Tip

Do not change the version number for changes like typo and formatting fixes.

To edit terms and conditions:

1. Go to **Terms and conditions**.
2. From the table, choose the terms and conditions you want to edit.
3. Select **Properties**, and then next to **Terms**, select **Edit.**
4. Adjust the existing content as needed.
5. If you edit the meaning of the terms at all, select the checkbox next to **Require users to re-accept, and increment the version number to *next version*.** In place of *next step*, you'll see the actual version number.
6. Select **Review + save**.
7. Review the summary for your terms and conditions, and then select **Save**.

Users only have to accept the updated terms and conditions once. This means that a user associated with multiple enrolled devices won't need to accept the terms and conditions on each device.

## Use Microsoft Entra Terms of use feature

You can use the [Microsoft Entra terms of use](/en-us/azure/active-directory/conditional-access/terms-of-use) feature to configure stricter compliance requirements. Capabilities include:

- Attach multiple localized versions to a single policy
- Render terms in PDF format for a richer experience that allows for branding, images, and hyperlinks
- Require users to expand the terms of use
- Require users to consent on every device
- Expire consents
- Require users to reaccept terms after a certain period of time
- Provide terms for non-enrollment scenarios

These terms are shown to users when they sign in to targeted apps and resources. If you configure both Microsoft Entra terms of use and Intune terms and conditions, users will be required to accept both. For a comparison of both solutions, see [Choosing the right Terms solution for your organization](https://go.microsoft.com/fwlink/?linkid=2010506&amp;clcid=0x409).