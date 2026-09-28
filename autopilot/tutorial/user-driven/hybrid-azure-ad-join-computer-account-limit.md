---
layout: Conceptual
title: Windows Autopilot user-driven Microsoft Entra hybrid join - Step 3 of 10 - Increase the computer account limit in the Organizational Unit (OU) | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: How to - Windows Autopilot user-driven Microsoft Entra hybrid join - Step 3 of 10 - Increase the computer account limit in the Organizational Unit (OU).
ms.date: 2025-02-27T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: 9dabc8a6-d994-c1d7-9df3-25a00129aa25
document_version_independent_id: 9dabc8a6-d994-c1d7-9df3-25a00129aa25
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/tutorial/user-driven/hybrid-azure-ad-join-computer-account-limit.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 4cb575f8-598b-c225-6322-15e41203c409
---

# Windows Autopilot user-driven Microsoft Entra hybrid join - Step 3 of 10 - Increase the computer account limit in the Organizational Unit (OU) | Microsoft Learn

Windows Autopilot user-driven Microsoft Entra hybrid join steps:

- Step 1: [Set up Windows automatic Intune enrollment](hybrid-azure-ad-join-automatic-enrollment)
- Step 2: [Install the Intune Connector for Active Directory](hybrid-azure-ad-join-intune-connector)

- **Step 3: Increase the computer account limit in the Organizational Unit (OU)**

- Step 4: [Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device)
- Step 5: [Create a device group](hybrid-azure-ad-join-device-group)
- Step 6: [Configure and assign Windows Autopilot Enrollment Status Page (ESP)](hybrid-azure-ad-join-esp)
- Step 7: [Create and assign Microsoft Entra hybrid join Windows Autopilot profile](hybrid-azure-ad-join-autopilot-profile)
- Step 8: [Configure and assign domain join profile](hybrid-azure-ad-join-domain-join-profile)
- Step 9: [Assign Windows Autopilot device to a user (optional)](hybrid-azure-ad-join-assign-device-to-user)
- Step 10: [Deploy the device](hybrid-azure-ad-join-deploy-device)

For an overview of the Windows Autopilot user-driven Microsoft Entra hybrid join workflow, see [Windows Autopilot user-driven Microsoft Entra hybrid join overview](hybrid-azure-ad-join-workflow#workflow).

Note

If the computer account limit for the proper Organizational Unit (OU) is already increased, skip this step and move on to [Step 4: Register devices as Windows Autopilot devices](hybrid-azure-ad-join-register-device).

## Increase the computer account limit in the Organizational Unit (OU)

# [Updated Connector](#tab/updated-connector)
Important

This step is only needed under one of the following conditions:

- The administrator that installed and configured the Intune Connector for Active Directory didn't have appropriate rights as outlined in [Intune Connector for Active Directory Requirements](../../windows-autopilot-hybrid?tabs=intune-connector-requirements#requirements).
- The administrator that installed and configured the Intune Connector had appropriate rights as outlined above, but the [Managed Service Account (MSA)](/en-us/windows-server/identity/ad-ds/manage/understand-service-accounts#standalone-managed-service-accounts) could not be granted permission to create computer objects in the organizational unit(s) specified during the Intune Connector installation. For more information, see [Configure the new Microsoft Intune connector for Active Directory with the least privilege principle](https://techcommunity.microsoft.com/blog/intunecustomersuccess/configure-the-new-microsoft-intune-connector-for-active-directory-with-the-least/4432478).
- The `ODJConnectorEnrollmentWizard.exe.config` XML file wasn't modified to add OUs that the MSA should have permissions for.

The purpose of Intune Connector for Active Directory is to join computers to a domain and add them to an OU. For this reason, the Managed Service Account being used for the Intune Connector for Active Directory needs to have permissions to create computer accounts in the OU where the computers are joined to the on-premises domain.

With default permissions in Active Directory, domain joins by the Intune Connector for Active Directory might initially work without any permission modifications to the OU in Active Directory. However after MSA attempts to join more than 10 computers to the on-premises domain, it would stop working because by default, Active Directory only allows any single account to join up to 10 computers to the on-premises domain.

The following users aren't restricted by the 10 computer domain join limitation:

- Users in the Administrators or Domain Administrators groups: In order to comply with the least privilege principles model, Microsoft doesn't recommend making the MSA an administrator or domain administrator.
- Users with delegated permissions on Organizational Unit (OUs) and containers in Active Directory to create computer accounts: This method is recommended since it follows the least privilege principles model.

To fix this limitation, the MSA needs the **Create computer accounts** permission in the Organizational Unit (OU) where the computers are joined to in the on-premises domain. The Intune Connector for Active Directory sets the permissions for the MSAs to the OUs as long as one of the following conditions is met:

- The administrator installing the Intune Connector for Active Directory has the necessary permissions to set permissions on the OUs.
- The administrator configuring the Intune Connector for Active Directory has the necessary permissions to set permissions on the OUs.

If the administrator installing or configuring the Intune Connector for Active Directory doesn't have the necessary permissions to set permissions on the OUs, then the following steps need to be followed:

1. Sign in to a computer that has access to the **Active Directory Users and Computers** console with an account that as the necessary permissions to set permissions on OUs.
2. Open the **Active Directory Users and Computers** console by running **DSA.msc**.
3. Expand the desired domain and navigate to the organizational unit (OU) that computers are joining to during Windows Autopilot.

    Note

    The OU that computers join during the Windows Autopilot deployment is specified later during the **Configure and assign domain join profile** step.
4. Right-click on the OU and select **Properties**.

    Note

    If computers are joining the default **Computers** container instead of an OU, right-click on the **Computers** container and select **Delegate Control**.
5. In the OU **Properties** windows that opens, select the **Security** tab.
6. In the **Security** tab, select **Advanced**.
7. In the **Advanced Security Settings** window, select **Add**.
8. In the **Permission Entry** windows, next to **Principal**, select the **Select a principal** link.
9. In the **Select User, Computer, Service Account, or Group** window, select the **Object Types...** button.
10. In the **Object Types** window, select the **Service Accounts** check box, and then select **OK**.
11. In the **Select User, Computer, Service Account, or Group** window, under **Enter the object name to select**, enter the name of the MSA being used for the Intune Connector for Active Directory.

    Tip

    The MSA was created during the **Install the Intune Connector for Active Directory** step/section and has the name format of `msaODJ#####` where **#####** are five random characters. If the MSA name isn't known, follow these steps to find the MSA name:

    1. On the server running the Intune Connector for Active Directory, right-click on the **Start** menu and then select **Computer Management**.
    2. In the **Computer Management** window, expand **Services and Applications** and then select **Services**.
    3. In the results pane, locate the service with the name **Intune ODJConnector for Active Service**. The name of the MSA is listed in the **Log On As** column.
12. Select **Check Names** to validate the MSA name entry. Once the entry is validated, select **OK**.
13. In the **Permission Entry** windows, select the **Applies to:** drop-down menu and then select **This object only**.
14. Under **Permissions**, unselect all items, and then only select the **Create Computer objects** check box.
15. Select **OK** to close the **Permission Entry** window.
16. In the **Advanced Security Settings** window, select either **Apply** or **OK** to apply the changes.

# [Legacy Connector](#tab/legacy-connector)
The purpose of Intune Connector for Active Directory is to join computers to a domain and add them to an OU. For this reason, the server running the Intune Connector for Active Directory needs to have permissions to create computer accounts in the OU where the computers are joined to the on-premises domain.

With default permissions in Active Directory, domain joins by the Intune Connector for Active Directory might initially work without any permission modifications to the OU in Active Directory. However after the server running the Intune Connector for Active Directory attempts to join more than 10 computers to the on-premises domain, it would stop working because by default, Active Directory only allows any single account to join up to 10 computers to the on-premises domain.

The following users aren't restricted by the 10 computer domain join limitation:

- Users in the Administrators or Domain Administrators groups - in order to comply with the least privilege principles model, Microsoft doesn't recommend making the computer account running the Intune Connector for Active Directory an administrator or domain administrator.
- Users with delegated permissions on Organizational Unit (OUs) and containers in Active Directory to create computer accounts - this method is recommended since it follows the least privilege principles model.

To fix this limitation, the server running the Intune Connector for Active Directory needs the **Create computer accounts** permission in the Organizational Unit (OU) where the computers are joined to in the on-premises domain:

To increase the computer account limit in the Organizational Unit (OU) that computers are joining to during Windows Autopilot, follow these steps on a computer that has access to the **Active Directory Users and Computers** console:

1. Open the **Active Directory Users and Computers** console by running **DSA.msc**.
2. Expand the desired domain and navigate to the organizational unit (OU) that computers are joining to during Windows Autopilot.

    Note

    The OU that computers join during the Windows Autopilot deployment is specified later during the **Configure and assign domain join profile** step.
3. Right-click on the OU and select **Delegate Control**.

    Note

    If computers are joining the default **Computers** container instead of an OU, right-click on the **Computers** container and select **Delegate Control**.
4. In the **Welcome to the Delegation of Control Wizard** window of the **Delegation of Control Wizard**, select **Next**.
5. In the **Users or Groups** window, under **Selected users and groups**, select **Add**.
6. Next to **Select this object type:** in the **Select Users, Computers, or Groups** window, select **Object Types**.
7. In the **Object Types** window, select the **Computers** check box, and then select **OK**. The other items in this window can be left at their default.
8. In the **Select Users, Computers, or Groups** window, under the **Enter the object names to select** box, enter the name of the computer where the Intune Connector for Active Directory was installed during the **Install the Intune Connector for Active Directory** step.
9. Select **Check Names** to validate the entry. Once the entry is validated, select **OK**.
10. In the **Users or Groups** window, verify that the correct computer is shown under **Selected users and groups:**, and then select **Next**.
11. In the **Tasks to Delegate** window, select **Create a custom task to delegate**, and then select **Next**.
12. In the **Active Directory Object Type** window:

    1. Select **Only the following objects in the folder**.
    2. Under **Only the following objects in the folder**, select **Computer objects**.
    3. Select the **Create selected objects in this folder** checkbox.
    4. Select **Next**.
13. In the **Permissions** window, under **Permissions:**, select the **Full Control** check box, and then select **Next**.

    Note

    After selecting the **Full Control** check box, all other options under **Permissions:** are automatically selected. The automatic selection of the checkboxes is normal and expected. Don't unselect any of the check boxes after they're automatically selected.
14. In the **Completing the Delegation of Control Wizard** window, select **Finish**.

---

## Next step: Register devices as Windows Autopilot devices