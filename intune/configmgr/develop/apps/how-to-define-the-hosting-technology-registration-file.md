---
layout: Conceptual
title: Define the Hosting Technology Registration File - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-define-the-hosting-technology-registration-file
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
description: To define a hosting technology registration file, create an XML file based on the http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest schema. This file registers the custom hosting technology with Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c47b00e5-a535-9245-13c7-708317e76206
document_version_independent_id: 93bfa1ee-8b89-a43a-7f93-f79217057f04
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-define-the-hosting-technology-registration-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-define-the-hosting-technology-registration-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-define-the-hosting-technology-registration-file.md
cmProducts: []
platformId: 56a996cf-578e-49f9-a9d8-b4823f100039
---

# Define the Hosting Technology Registration File - Configuration Manager | Microsoft Learn

To define a hosting technology registration file, create an XML file based on the `http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest` schema. Used in the installation process, the registration file registers the custom hosting technology with Configuration Manager. The hosting technology registration file is required for the installation of the custom hosting technology.

### To define the hosting technology registration file

1. Create a hosting technology registration file.

    The following example from the RPC sample project demonstrates how to define a hosting technology registration file.

    ```
    <AppMgmtDigest xmlns="http://schemas.microsoft.com/SystemCenterConfigurationManager/2009/AppMgmtDigest" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <HostingTechnology AuthoringScopeId="GLOBAL" LogicalName="RdpHostingTechnology" HostingId="Rdp" AssemblySuffix="Rdp" Version="1">
        <Requirements>
          <Rule xmlns="http://schemas.microsoft.com/SystemsCenterConfigurationManager/2009/06/14/Rules" id="Rule_63d22cd6-7f11-4769-8900-9c0ff5c177c5" Severity="None">
            <Annotation>
              <DisplayName Text="Operating System" />
              <Description Text="" />
            </Annotation>
            <OperatingSystemExpression>
              <Operator>OneOf</Operator>
              <Operands>
                <RuleExpression RuleId="Windows/All_x86_Windows_XP" />
                <RuleExpression RuleId="Windows/x86_Windows_XP_Professional_Service_Pack_3" />
                <RuleExpression RuleId="Windows/All_x64_Windows_Server_2003_Non_R2" />
                <RuleExpression RuleId="Windows/All_x86_Windows_Server_2003_Non_R2" />
                <RuleExpression RuleId="Windows/All_x64_Windows_Server_2003_R2" />
                <RuleExpression RuleId="Windows/All_x86_Windows_Server_2003_R2" />
                <RuleExpression RuleId="Windows/x64_Windows_Server_2003_R2_original_release_SP1" />
                <RuleExpression RuleId="Windows/x86_Windows_Server_2003_R2_original_release_SP1" />
                <RuleExpression RuleId="Windows/All_x64_Windows_XP_Professional" />
                <RuleExpression RuleId="Windows/x64_Windows_Server_2003_SP2" />
                <RuleExpression RuleId="Windows/x86_Windows_Server_2003_SP2" />
                <RuleExpression RuleId="Windows/x64_Windows_XP_Professional_SP2" />
                <RuleExpression RuleId="Windows/All_x64_Windows_Vista" />
                <RuleExpression RuleId="Windows/All_x86_Windows_Vista" />
                <RuleExpression RuleId="Windows/All_x64_Windows_Server_2008" />
                <RuleExpression RuleId="Windows/All_x86_Windows_Server_2008" />
                <RuleExpression RuleId="Windows/x64_Windows_Vista_SP1" />
                <RuleExpression RuleId="Windows/x86_Windows_Vista_SP1" />
                <RuleExpression RuleId="Windows/x64_Windows_Server_2008_original_release" />
                <RuleExpression RuleId="Windows/x86_Windows_Server_2008_original_release" />
                <RuleExpression RuleId="Windows/x64_Windows_Server_2008_SP2" />
                <RuleExpression RuleId="Windows/x86_Windows_Server_2008_SP2" />
                <RuleExpression RuleId="Windows/x64_Windows_Vista_SP2" />
                <RuleExpression RuleId="Windows/x86_Windows_Vista_SP2" />
                <RuleExpression RuleId="Windows/All_x64_Windows_Server_2008_R2" />
                <RuleExpression RuleId="Windows/All_x64_Windows_7_Client" />
                <RuleExpression RuleId="Windows/All_x86_Windows_7_Client" />
                <RuleExpression RuleId="Windows/x64_Windows_7_Client" />
                <RuleExpression RuleId="Windows/x86_Windows_7_Client" />
                <RuleExpression RuleId="Windows/x64_Windows_Server_2008_R2" />
              </Operands>
            </OperatingSystemExpression>
          </Rule>
        </Requirements>
      </HostingTechnology>
    </AppMgmtDigest>
    ```

| Attributes | Description |
| --- | --- |
| AuthoringScopeID | AuthoringScopeId will always be "GLOBAL". |
| LogicalName | LogicalName must match the name of the SDK class created in the SDK assembly for HostingTechnology. |
| HostingId | HostingId must match the constant declared and used in the SDK assembly for HostingTechnolgy. |
| AssemblySuffix | AssemblySuffix must match the filename of the SDK assembly (Microsoft.ConfigurationManagement.ApplicationManagement.&lt; `AssemblySuffix`&gt;.dll). |
| Version | Version is the version number for the release of the deployment type extension. This version number is used for in-place revisions. |

| Element | Description |
| --- | --- |
| Requirements | The requirements section is based on DCM requirement rules. The supported platforms for the custom technology must be specified here. |