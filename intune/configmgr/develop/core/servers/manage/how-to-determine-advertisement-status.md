---
layout: Conceptual
title: Determine Advertisement Status - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-advertisement-status
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
description: To determine advertisement status in Configuration Manager, you can use the queries described in this section.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 62e7b20a-7d6a-d871-a534-716cc9a31eb5
document_version_independent_id: 6e899457-b34d-b68b-fd0c-e6018b4ebbad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/how-to-determine-advertisement-status.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/how-to-determine-advertisement-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/how-to-determine-advertisement-status.md
cmProducts: []
platformId: 40b45e23-e4df-db6e-4a96-d83008b8c961
---

# Determine Advertisement Status - Configuration Manager | Microsoft Learn

To determine advertisement status in Configuration Manager, you can use the queries described in this section.

Note

These queries query the status messages directly and might take some time to complete because there can be many status messages.

For more information about using these queries, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](../../understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) and [How to Perform a Synchronous Configuration Manager Query by Using WMI](../../understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For more queries about advertisement status and summarization, you can use [SMS_ClientAdvertisementStatus Server WMI Class](../../../reference/core/servers/configure/sms_clientadvertisementstatus-server-wmi-class) and [SMS_ClientAdvertisementSummary Server WMI Class](../../../reference/core/servers/configure/sms_clientadvertisementsummary-server-wmi-class).

## Queries

### Client Program Install

The following query returns the clients that have successfully installed a program. You need to check for both message identifiers because the program can report status with an exit code (10008) or an install status MIF file (10009).

```
' Returns clients that have successful installed a program
SELECT msg.MachineName, msg.SiteCode, ad.ProgramName
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
     JOIN SMS_Advertisement ad ON attr.AttributeValue = ad.AdvertisementID
WHERE msg.Component = "Software Distribution"
AND   (msg.MessageID = 10008 or msg.MessageID = 10009)
AND   attr.AttributeID = 401
ORDER BY ad.ProgramName
```

### Clients That Have Installed a Specific Advertised Program

This query returns the clients that have successfully installed a specific advertised program.

```
' Returns clients that have successfully installed a specific advertised program
SELECT msg.MachineName, msg.SiteCode
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
WHERE msg.Component = "Software Distribution"
and   (msg.MessageID = 10008 or msg.MessageID = 10009)
and   attr.AttributeID = 401
and   attr.AttributeValue = "<AdvertisementID>"
```

### Clients That Have Not Installed a Specific Advertised Program

The previous queries show which clients successfully installed an advertised program. Determining which collection members have not installed the advertised program can be more involved if the advertisement specified subcollections. The following query determines which clients of the **All Systems** (SMS00001) collection (substitute your collection member class for SMS\_CM\_RES\_COLL\_SMS00001) have not installed the advertised program. If the advertisement specified subcollections, the query must be run for each subcollection.

```
' Returns which clients of a collection have not installed the advertised program
SELECT Name
FROM SMS_CM_RES_COLL_SMS00001
WHERE NOT Name IN (SELECT msg.MachineName
FROM SMS_StatusMessage msg
     JOIN SMS_StatMsgAttributes attr ON msg.RecordID = attr.RecordID
WHERE msg.Component = "Software Distribution"
AND   (msg.MessageID = 10008 or msg.MessageID = 10009)
AND   attr.AttributeID = 401
AND   attr.AttributeValue = "<AdvertisementID>")
```