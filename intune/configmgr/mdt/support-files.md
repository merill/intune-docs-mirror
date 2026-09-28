---
layout: Conceptual
title: Toolkit reference - Microsoft Deployment Toolkit (MDT) Support Files - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdt/support-files
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
description: Reference details for Microsoft Deployment Toolkit (MDT) Support Files
ms.date: 2016-09-09T00:00:00.0000000Z
ms.subservice: mdt
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1a50a42e-f00c-521a-7dbe-518df907c349
document_version_independent_id: 1a50a42e-f00c-521a-7dbe-518df907c349
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdt/support-files.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdt/support-files
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdt/support-files.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e3e53a21-5c86-4f87-b1fb-893b77a777ba
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/383e0c27-53d0-4bef-b930-1e0b0ae37c07
platformId: 909cc671-13a1-9883-d22d-b5fed293a254
---

# Toolkit reference - Microsoft Deployment Toolkit (MDT) Support Files - Configuration Manager | Microsoft Learn

The utilities and scripts used in LTI and ZTI deployments reference external configuration files to determine the process steps and configuration settings used during the deployment process.

The following information is provided for each utility:

- **Name**. Specifies the name of the file
- **Description**. Provides a description of the purpose of the file
- **Location**. Indicates the folder where the file can be found; in the information for the location, the following variables are used:

    - **program\_files**. This variable points to the location of the Program Files folder on the computer where MDT is installed.
    - **distribution**. This variable points to the location of the Distribution folder for the deployment share.
    - **platform**. This variable is a placeholder for the operating system platform (x86 or x64).

## ApplicationGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## Applications.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## BootStrap.ini

The configuration file used when the target computer is not able to connect to the appropriate deployment share. This situation occurs in the New Computer and the Replace Computer scenarios.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## CustomSettings.ini

The primary configuration file for the MDT processing rules used in all scenarios.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## Deploy.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *program\_files*\Microsoft Deployment Toolkit\Control |

## DriverGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## Drivers.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | Description |
| --- | --- |
| **Location** | *distribution*\Control |

## LinkedDeploymentShares.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## ListOfLanguages.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## MediaGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## Medias.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## OperatingSystemGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## OperatingSystems.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## PackageGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## Packages.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## SelectionProfileGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## SelectionProfiles.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## ServerManager.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *program\_files*\Microsoft Deployment Toolkit\Bin |

## Settings.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## TaskSequenceGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## TaskSequences.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control |

## TS.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Control\*task\_sequence\_id* |

Note

*Task\_sequence\_id* is a placeholder for the task sequence ID that was assigned to each task sequence when it was created in the Task Sequences node in the Deployment Workbench.

## Wimscript.ini

This .ini file is an ImageX configuration file that contains the list of folders and files that will be excluded from an image. It is referenced by ImageX during the LTI Capture Phase.

For assistance with customizing this file, see the section, "Create an ImageX Configuration File," in the *Windows Preinstallation Environment (Windows PE) User's Guide*.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Tools\*platform* |

## ZTIBIOSCheck.xml

This XML file contains metadata about BIOSes for target computers. This file is edited manually and is read by [ZTIBIOSCheck.wsf](scripts#ztibioscheckwsf). Extract the necessary information from a target computer to create an entry in this XML file using the Microsoft Visual Basic® Scripting Edition (VBScript) program (ZTIBIOS\_Extract\_Utility.vbs) that is embedded in this XML file.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## ZTIConfigure.xml

This XML file is used by the [ZTIConfigure.wsf](scripts#zticonfigurewsf) script to translate property values (specified earlier in the deployment process) to configure settings in the Unattend.xml file. This file is already customized to make the appropriate translations and should not require further modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## ZTIGather.xml

Note

This XML file is preconfigured and should not require modification. Define custom properties in the CustomSettings.ini file or the MDT DB.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## ZTIUserState\_config.xml

This XML file is used by the [ZTIUserState.wsf](scripts#ztiuserstatewsf) script as a default USMT configuration file. This file is used by default if no custom configuration file is specified by the [USMTConfigFile](properties#usmtconfigfile) property. See the [Config.xml File](/en-us/windows/deployment/usmt/usmt-configxml-file) topic in the USMT documentation for more information on syntax and use.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |

## ZTITatoo.mof

This .mof file, when imported into the WMI repository of the target computer using Mofcomp.exe, creates the **Microsoft\_BDD\_Info** WMI class. This class contains deployment-related information, such as:

- DeploymentMethod
- DeploymentType
- DeploymentTimestamp
- BuildID
- BuildName
- BuildVersion
- OSDPackageID
- OSDProgramName
- OSDAdvertisementID
- TaskSequenceID
- TaskSequenceName
- TaskSequenceVersion

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\Scripts |