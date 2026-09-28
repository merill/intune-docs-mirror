---
layout: Conceptual
title: Create a Data Discovery Record - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-data-discovery-record
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
description: Specify the resource type, the discovery process, the site that discovered the resource, and the resource properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3cf46f15-25d9-6b09-26e3-403b947348ac
document_version_independent_id: eae9cec6-cd61-b1ca-7324-9ddd0b89676c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/configure/how-to-create-a-data-discovery-record.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/configure/how-to-create-a-data-discovery-record
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/configure/how-to-create-a-data-discovery-record.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 5f2cacc3-884e-1ae0-a1ad-f66581fd2d0c
---

# Create a Data Discovery Record - Configuration Manager | Microsoft Learn

The data discovery record (DDR), in Configuration Manager, specifies the resource type, the discovery process, the site that discovered the resource, and the resource properties. Configuration Manager provides six library functions that you use to create your own DDRs. For more information. see [About Creating a Data Discovery Record](about-creating-a-data-discovery-record).

### To create a data discovery record

1. Create a new instance of the `SMSResGen` class.
2. Create a new DDR by using the `NewDDR` method.
3. Add properties to the DDR by using the `ADDPROP_` methods.
4. Write the new DDR to a file by using the `DDRWrite` method.

## Example

The following example creates a DDR.

```vbs

Sub CreateNewDDR()

    ' Define constants.
    Const ADDPROP_NONE  = &H0
    Const ADDPROP_GUID  = &H2
    Const ADDPROP_KEY   = &H8
    Const ADDPROP_ARRAY = &H10

    ' Define variables.
    Dim newDDR
    Dim siteCode
    Dim computerName
    Dim siteName
    Dim newIPAddress(2), newIPSubnet(2), newMACAddress(2)

    ' Load variables with values.
    siteCode = "ABC"
    computerName="ComputerName"
    siteName="Active Directory Site Name"
    newIPAddress(0)="123.234.12.23"
    newIPAddress(1)="123.234.12.32"
    newIPSubnet(0)="123.234.12.0"
    newIPSubnet(1)="123.234.12.0"
    newMACAddress(0)="00:02:A5:B1:11:68"
    newMACAddress(1)="00:02:A5:B1:11:69"

    ' Load an instance of the SMSResGen.dll.
    Set newDDR=CreateObject("SMSResGen.SMSResGen.1")

    ' Create a new DDR using the DDRNew method.
    newDDR.DDRNew "System", "CustomAgent", siteCode

    ' Add properties to the new DDR using the DDRAddString method and the previously defined variables.
    newDDR.DDRAddString "NetBIOS Name", computerName, 64, ADDPROP_KEY
    newDDR.DDRAddString "AD Site Name", siteName, 64, ADDPROP_NONE

    ' Add properties to the new DDR using the DDRAddStringArray method and the previously defined variables.
    newDDR.DDRAddStringArray "IP Addresses", Array(newIPAddress(0),newIPAddress(1)), 64, ADDPROP_ARRAY
    newDDR.DDRAddStringArray "MAC Addresses", Array(newMACAddress(0),newMACAddress(1)), 64, ADDPROP_ARRAY OR ADDPROP_KEY
    newDDR.DDRAddStringArray "IP Subnets", Array(newIPSubnet(0),newIPSubnet(1)), 64, ADDPROP_ARRAY

    ' Write new DDR to file.
    newDDR.DDRWrite "NewDDR.DDR"
    wscript.echo "Created new DDR."

End Sub

```

```c

public void CreateNewDDR()
{
    try
    {
        // Define and set the required variables.
        string Computer = "ComputerName";
        string SiteName = "Active Directory Site Name";
        string[] IPAddress  = new string[] { "123.234.12.23", "123.234.12.32" };
        string[] IPSubnet   = new string[] { "123.234.12.0", "123.234.12.0" };
        string[] MACAddress = new string[] { "00:02:A5:B1:11:68", "00:02:A5:B1:11:68" };
        string siteCode = "TQ1";

        // Create the SMSResGenClass instance.
        SMSRSGENCTLLib.SMSResGen newDDR = new SMSRSGENCTLLib.SMSResGen();

        // Create a new DDR using the DDRNew method.
        newDDR.DDRNew("System", "CustomAgent", siteCode);

        // Add properties to the new DDR using the DDRAddString method and the previously defined variables.
        newDDR.DDRAddString("NetBIOS Name", Computer, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_KEY);
        newDDR.DDRAddString("AD Site Name", SiteName, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_NONE);

        // Add properties to the new DDR using the DDRAddStringArray method and the previously defined variables.
        newDDR.DDRAddStringArray("IP Subnets", IPAddress, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_ARRAY);
        newDDR.DDRAddStringArray("MAC Addresses", MACAddress, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_ARRAY | SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_KEY);
        newDDR.DDRAddStringArray("IP Subnets", IPSubnet, 64, SMSRSGENCTLLib.DDRPropertyFlagsEnum.ADDPROP_ARRAY);

        // Write new DDR to file.
        newDDR.DDRWrite("NewDDR.DDR");
        Console.WriteLine("Created new DDR.");
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create DDR. Error: " + ex.Message);
        throw;
    }
}

```

## Compiling the Code

Important

This VBScript and C# examples require **smsrsgen.dll** and **smsrsgenctl.dll**, respectively. Both files are included as a part of the downloadable Configuration Manager SDK (in the "Redistributables" folder).

The file smsrsgenctl.dll is a 32-bit dll and must be registered on the system that will run the application. In addition, the application using smsrsgenctl.dll should be compiled as an x86 application.

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](role-based-administration).