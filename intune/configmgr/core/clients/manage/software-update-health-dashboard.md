---
layout: Conceptual
title: Troubleshooting dashboard - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/software-update-health-dashboard
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
description: Use a dashboard in the console to view information about the software update health status of clients in your environment.
ms.date: 2024-04-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
ms.topicc: troubleshooting-general
ms.custom: sfi-image-nochange
locale: en-us
document_id: 5af3d4b5-124b-386f-b3db-e4703a242c45
document_version_independent_id: 5af3d4b5-124b-386f-b3db-e4703a242c45
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/software-update-health-dashboard.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/software-update-health-dashboard
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/software-update-health-dashboard.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: d61058ad-a43f-06ae-060d-2d61c56ba1e1
---

# Troubleshooting dashboard - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Troubleshooting dashboard gives you information about different scenarios, which needs administrator's attention in your environment at a single glance.

In the Configuration Manager console, go to the **Monitoring** workspace. Expand **Troubleshooting dashboard** node.

[![Screenshot of an example of the updated Troubleshooting Dashboard in version 2403 or later.](media/17668422-troubleshooting-dashboard.png)](media/17668422-troubleshooting-dashboard.png#lightbox)

## Software update health dashboard

You deploy software updates to help secure your environment, but these deployments only reach healthy error free clients. Configuration Manager update errors adversely affect overall compliance. Determining software update errors can be challenging depending upon the error details.

Configuration Manager provides a dashboard with information about the software update deployment status health and common top errors, which most of the devices have in their environment. View your overall software update errors, common errors.

In the Configuration Manager console, go to the **Monitoring** workspace. Expand **Troubleshooting dashboard**, and select the **software update health** node.

[![Screenshot of an example of the updated Software update Health Dashboard in version 2403 or later.](media/17668422-software-update-health.png)](media/17668422-software-update-health.png#lightbox)

### Overall software update health

You can browse the **update group** in the dashboard:

When you set the update group, the total number of devices in the collection, active software update success percentage is updated. This shows current percentage compliance for the update group at the run time.

### Error details for overall clients

The various top error details are covered in this dashboard, If the number is 0 then your environments doesn't have any of these errors:

- Software Distribution - File not Found -(80070002, C80003F3)
- File or folder not accessible -(80004005, 87D00692, 8024402C, 80070005)
- Access denied for opening a file or registry -(80070005)
- No space available for installation -(80091007, 80070070)
- Missing or damaged file -(8007000D, 800B0100)
- Not connected to Windows Update Servers -(8024401B)
- Unable to get content location -(87D00662)
- Update content not available on DP -(80004002, 87D00605)
- Update files missing or corrupted -(8007000E)
- Applications with Multiple Versions -(8007066F)
- Missing / Conflicting Boundary -(800705B4, 87D00200)
- WUA Not responding -(87D00600, 87D00662)
- Disable Branch Cache -(87D00314, 87D0027C)

### Lets discuss the possible solutions for these errors.

| Error details | Possible solution |
| --- | --- |
| Software Distribution - File not Found -(80070002, C80003F3) | 1. Type CMD in Start Menu and right click the result & run as administrator.  2. Type cmd and press enter.  3. Type net stop wuauserv and press enter. 4. Type rename c:\windows\SoftwareDistribution softwaredistribution.old and press enter. 5. Type net start wuauserv and press enter. 6. Type exit and press enter. 7. Restart the ConfigMgr Agent Service. 8. Start the Software Update Scan and Deployment Cycles. |
| File or folder not accessible - (80004005 87D00692 8024402C 80070005) | 1. Check the WUAHandler.log for Group policy settings were overwritten by a higher authority Error Code 0x87d00692. 2. Rename C:\Windows\System32\GroupPolicy\Machine\registry.pol 3. Restart the ConfigMgr Agent Service. 4. Start the Software Update Scan and Deployment Cycles. |
| Access denied for opening a file or registry - (80070005) | 1. Check the WUAHandler.log for Group policy settings were overwritten by a higher authority Error Code 0x87d00692. 2. Rename C:\Windows\System32\GroupPolicy\Machine\registry.pol 3. Restart the ConfigMgr Agent Service. 4. Start the Software Update Scan and Deployment Cycles. |
| No space available for installation -(80091007, 80070070) | 1. Check whether UpdateDeployment.log has "Update (Site\_*/SUM\_*) Progress: Status = ciStateError, PercentComplete = \*, DownloadSize = \*, Result = 0x80091007". 2. Check whether CAS.log has "Successfully raised SoftDistHashMismatchEvent event. ContentAccess \* Error: DeleteDirectory:- Failed to delete Directory with Error 0x00000003. ContentAccess \* Releasing content request \* ContentAccess \* There are 0 files in the directory compared to \* expected files ContentAccess * 3. If the above conditions are true, then the issue can be because of space issue Check the space available in the disk. 4. If the Space is less try clearing the temporary files to free up space. 5. Once you complete get free space or you already have space available Start the Software Update Scan and Deployment Cycles. Note:- the "*" in the log references are variables. |
| Missing or damaged file -(8007000D, 800B0100) | Issue may be related to the windows update agent. Run the Update readiness tool to verify the same. https://support.microsoft.com/en-in/help/971058/how-do-i-reset-windows-update-components |
| Not connected to Windows Update Servers -(8024401B) | 1. Check whether the Windows update log has Proxy specified. If yes continue. 2. Type CMD in Start Menu and right click the result & run as administrator. 3. Type netsh winhttp reset proxy. 4. Type net stop wuauserv and press enter. 5. Type rename c:\windows\SoftwareDistribution softwaredistribution.old and press enter. 6. Type net start wuauserv and press enter. 7. Type exit and press enter. 8. Restart the ConfigMgr Agent Service. 9. Start the Software Update Scan and Deployment Cycles. |
| Unable to get content location -(87D00662) | 1. Restart Windows Update Agent. 2. Restart SMS Agent. 3. Initiate the Update Evaluation Cycle. |
| Update content not available on DP -(80004002, 87D00605) | 1. Check whether the UpdatesHandler.log has the following entries. WSUS update (689c410a-44d7-45c7-ae51-9806fcb177f5) installation result = 0x80004002, Reboot State = NoReboot Update execution failed. 2. Check whether the WUAHandler.log has the following entries Failed to get final installation result of updates. Error = 0x80004002. Update 1 (unique update id) finished installing (0x80004002). Update 2 (unique update ID) finished installing (0x80004002). Installation of updates completed. 3. Check whether the WUAHandler.log has "WARNING: WU client failed to install updates with error 0x80004002" 4. The WUA installation on the client might be missing files or be corrupt. Reinstall WUA (https://blogs.technet.microsoft.com/enterprisemobility/2014/07/14/how-to-install-the-windows-update-agent-on-client-computers/) 5. Restart the ConfigMgr Agent Service. 6. Start the Software Update Scan and Deployment Cycles. |
| Update files missing or corrupted -(8007000E) | 1. Open Command prompt as administrator execute the commands on the given sequence. a. Net stop wuauserv  b. Sc config wuauserv type= own c. Net start wuauser |
| Applications with Multiple Versions -(8007066F) | 1. Find the update getting failed and check the client has different versions of the application getting updated. 2. If the client has different versions of the application Open the Registry editor. 3. Navigate to the following registry keys HKEY\_USERS.DEFAULT\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders. 4. The correct and default value for AppData should be: %USERPROFILE%\AppData\Roaming 5. Close the Registry editor, and try again Windows Update again. (A reboot shouldn't be required.) 6. If the problem persists, repeat the steps 3 through 5 with the following registry keys: HKEY\_CURRENT\_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders\ HKEY\_LOCAL\_MACHINE\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders&lt;br&gt; |
| Missing / Conflicting Boundary -(800705B4, 87D00200) | 1. Add Missing IP Subnets to Boundary |
| WUA Not responding -(87D00600, 87D00662) | 1. Restart Windows Update Agent. 2. Restart SMS Agent. 3. Initiate the Update Evaluation Cycle.' |
| Disable Branch Cache -(87D00314, 87D0027C) | 1. Restart BITS. 2. Disable Branch Cache(HKLM\Software\Policies\Microsoft\PeerDist\Service. 3. Start the Update Evaluation cycle' |

In the Configuration Manager console, go to the **Monitoring** workspace. Expand **Troubleshooting dashboard**, select the **software update health** node and select the **Software Distribution - File not Found -80070002, C80003F3**.

[![Screenshot of an example of the error devices in version 2403 or later.](media/17668422-error-software-dist-file-error.png)](media/17668422-error-software-dist-file-error.png#lightbox)

You can export the devices or create collection to perform manual remediation to these devices.

### Next steps

In future releases, we add remediation for few issues.