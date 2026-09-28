---
layout: Conceptual
title: Evaluation of the computer information for a specific computer report - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/evaluation-computer-information-report-configuration-manager
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
description: A predefined report in Configuration Manager that combines multiple SQL views to obtain the required data.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 90b5fde0-f416-c4e9-d946-49fcd8c14eb5
document_version_independent_id: 2f4ceadf-2a1a-f7ff-19db-52b5c5a8aa98
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/evaluation-computer-information-report-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/evaluation-computer-information-report-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/evaluation-computer-information-report-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 9bb34e28-493b-ee5d-f18a-2643032e52e3
---

# Evaluation of the computer information for a specific computer report - Configuration Manager | Microsoft Learn

The **Computer information for a specific computer** report is one of the predefined reports in Configuration Manager, and is a good example of a report that combines multiple SQL views to obtain the required data. To open the report properties, use the following procedure:

## To examine the Computer information for a specific computer report

1. In the Configuration Manager console, select **Monitoring**.
2. In the **Monitoring** workspace, select Reporting, and then select **Reports**.
3. From the list of displayed reports, select **Computer information for a specific computer** and then, in the **Home** tab, in the **Report Group** group, select **Edit**.
4. After Report Builder opens, in the **Report Data** pane, expand **Datasets** and then double-click **DataSet0** to examine the SQL statement for the report which appears as follows:

    ```sql
         SELECT distinct SYS.Netbios_Name0, SYS.User_Name0, SYS.User_Domain0,  SYS.Resource_Domain_OR_Workgr0,
                     OPSYS.Caption0 as C054, OPSYS.Version0,
                     MEM.TotalPhysicalMemory0,
                     STUFF((SELECT (N','+IPAddr.IP_Addresses0) AS [text()]
                     FROM fn_rbac_RA_System_IPAddresses(@UserSIDs)  IPAddr
                     WHERE SYS.ResourceID = IPAddr.ResourceID for xml path(N''))
                     ,1,1,N'') as IP_Addresses0, -- if there are multiple IP address then combine them together
                     Processor.Manufacturer0,
                     CSYS.Model0, Processor.Name0, Processor.MaxClockSpeed0, SYS.Is_AOAC_Capable0
                     FROM fn_rbac_R_System(@UserSIDs)  SYS
                     LEFT JOIN  fn_rbac_GS_X86_PC_MEMORY(@UserSIDs)  MEM on SYS.ResourceID = MEM.ResourceID
                     LEFT JOIN  fn_rbac_GS_COMPUTER_SYSTEM(@UserSIDs)  CSYS on SYS.ResourceID = CSYS.ResourceID
                     LEFT JOIN  fn_rbac_GS_PROCESSOR(@UserSIDs)  Processor  on Processor.ResourceID = SYS.ResourceID
                     LEFT JOIN fn_rbac_GS_OPERATING_SYSTEM(@UserSIDs)  OPSYS on SYS.ResourceID=OPSYS.ResourceID
                     WHERE SYS.Netbios_Name0 = @variable
                     ORDER BY SYS.Netbios_Name0, SYS.Resource_Domain_OR_Workgr0
    ```
5. Close the **Dataset Properties** dialog box and then double-click **DataSetAdminID** to examine the SQL statement that presents a list of possible computers for the user to choose. This appears as follows:

    ```sql
         SELECT dbo.fn_rbac_GetAdminIDsfromUserSIDs(@UserTokenSIDs) as userSIDs
    ```

    This report contains a more complex SQL statement that combines multiple SQL views to obtain the desired data. The query results will list the NetBIOS name, user name, operating system, memory, and more with the NetBIOS name used as the variable in the report prompt \*\*(WHERE SYS.Netbios\_Name0 = @variable)\*\*. The query retrieves information from six different SQL Server views (**v\_R\_System**, **v\_RA\_System\_IPAddresses**, **v\_GS\_X86\_PC\_MEMORY**, **v\_GS\_COMPUTER\_SYSTEM**, **v\_GS\_PROCESSOR**, and **v\_GS\_OPERATING\_SYSTEM**) that are joined together by using the **ResourceID** column from the **v\_R\_System** view and where the NetBIOS name in the **v\_R\_System** view is equal to the one provided in the report prompt. Finally, the results are ordered first by the **Netbios Name** column and then the **User Domain** column.

    The report prompt will display **Computer Name** as the prompt text and has a variable named **variable** that will be populated by the user. You can examine details about the variables and parameters used by the report in the **Parameters** node of the **Report Data** pane.
6. Close Report Builder.