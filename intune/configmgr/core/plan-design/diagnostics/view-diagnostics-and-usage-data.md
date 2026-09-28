---
layout: Conceptual
title: View diagnostics data - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/view-diagnostics-and-usage-data
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
description: View diagnostic and usage data to confirm that your Configuration Manager hierarchy contains no sensitive information.
ms.date: 2021-11-15T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 144fb3b4-0e56-ee21-fa9c-5b22fab148c6
document_version_independent_id: 6ec76df7-94fc-3fbb-6ec1-2a13753525f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/view-diagnostics-and-usage-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/view-diagnostics-and-usage-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/view-diagnostics-and-usage-data.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 88343e08-e58b-7a0f-e1fb-85fa39fe0d89
---

# View diagnostics data - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can view diagnostic and usage data from your Configuration Manager hierarchy to confirm that it includes no sensitive or identifiable information. The site summarizes and stores its diagnostic data in the **TEL\_TelemetryResults** table of the site database. It formats the data to be programmatically usable and efficient.

The information in this article gives you a view of the exact data sent to Microsoft. It's not intended to be used for other purposes, like data analysis.

## View data in database

Use the following SQL command to view the contents of this table and show the exact data that's sent:

```SQL
SELECT * FROM TEL_TelemetryResults
```

## Export the data

When the service connection point is in offline mode, use the service connection tool to export the current data to a comma-separated values (CSV) file. Run the service connection tool on the service connection point with the **-Export** parameter.

For more information, see [Use the service connection tool](../../servers/manage/use-the-service-connection-tool).

## One-way hashes

Some data consists of strings of random alphanumeric characters. Configuration Manager uses the SHA-256 algorithm to create one-way hashes. This process makes sure that Microsoft doesn't collect potentially sensitive data. The hashed data can still be used for correlation and comparison purposes.

For example, instead of collecting the names of tables in the site database, it captures the one-way hash for each table name. This behavior makes sure that any custom table names aren't visible. Microsoft then does the same one-way hash process of the default SQL Server table names. Comparing the results of the two queries determines the deviation of your database schema from the product default. This information is then used to improve updates that require changes to the SQL Server schema.

When you view the raw data, a common hashed value appears in each row of data. This hash is the **support ID**, also known as the hierarchy ID. It's used to correlate data with the same hierarchy without identifying the customer or source.

### How the one-way hash works

1. Get your support ID from the Configuration Manager console. Select the arrow in the upper left corner of the ribbon, and then choose **About Configuration Manager**. You can select and copy the support ID from the window that opens.
2. Use the following Windows PowerShell script to do the one-way hash of your support ID.

    ```PowerShell
    Param( [Parameter(Mandatory=$True)] [string]$value )
      $guid = [System.Guid]::NewGuid()
      if( [System.Guid]::TryParse($value,[ref] $guid) -eq $true ) {
      #many of the values we hash are Guids
      $bytesToHash = $guid.ToByteArray()
    } else {
      #otherwise hash as string (unicode)
      $ue = New-Object System.Text.UnicodeEncoding
      $bytesToHash = $ue.GetBytes($value)
    }
      # Load Hash Provider (https://en.wikipedia.org/wiki/SHA-2)
    $hashAlgorithm = [System.Security.Cryptography.SHA256Cng]::Create()
    # Hash the input
    $hashedBytes = $hashAlgorithm.ComputeHash($bytesToHash)
    # Base64 encode the result for transport
    $result = [Convert]::ToBase64String($hashedBytes)
    return $result
    ```
3. Compare the script output against the GUID in the raw data. This process shows how the data is obscured.