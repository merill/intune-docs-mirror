---
layout: Conceptual
title: Connect to an SMS Provider by Using WMI - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi
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
description: Connect to the SMS Provider on a Configuration Manager site server by using the WMI SWbemLocator object or by using the Windows Script Host GetObject method.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 124ed410-ca52-5710-bb06-e959c5e9b08a
document_version_independent_id: c93873a4-b3ec-901a-0b91-98a8cbaac513
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b0191127-b1b5-d9dd-7264-13fbb3c2d8d9
---

# Connect to an SMS Provider by Using WMI - Configuration Manager | Microsoft Learn

Before connecting to the SMS Provider for a local or remote Configuration Manager site server, you first need to locate the SMS Provider for the site server. The SMS Provider can be either local or remote to the Configuration Manager site server you're using. The Windows Management Instrumentation (WMI) class `SMS_ProviderLocation` is present on all Configuration Manager site servers, and one instance will contain the location for the Configuration Manager site server you're using.

You can connect to the SMS Provider on a Configuration Manager site server by using the WMI [SWbemLocator](/en-us/windows/desktop/wmisdk/swbemlocator) object or by using the Windows Script Host `GetObject` method. Both approaches work equally well on local or remote connections, with the following limitations:

- You must use `SWbemLocator` if you need to pass user credentials to a remote computer.
- You can't use `SWbemLocator` to explicitly pass user credentials to a local computer.

    There are several different syntaxes that you can use to make the connection, depending on whether the connection is local or remote. After you're connected to the SMS Provider, you'll have an [SWbemServices](/en-us/windows/desktop/wmisdk/swbemservices) object that you use to access Configuration Manager objects.

Note

If you need to add context qualifiers for the connection, see [How to Add a Configuration Manager Context Qualifier by Using WMI](how-to-add-a-configuration-manager-context-qualifier-by-using-wmi).

### To connect to an SMS provider

1. Get a [WbemScripting.SWbemLocator](/en-us/windows/desktop/WmiSdk/swbemlocator) object.
2. Set the authentication level to packet privacy.
3. Set up a connection to the SMS Provider by using the [SWbemLocator](/en-us/windows/desktop/wmisdk/swbemlocator) object [ConnectServer](/en-us/windows/desktop/WmiSdk/swbemlocator-connectserver) method. Supply credentials only if it's a remote computer.
4. Using the [SMS_ProviderLocation](../../reference/misc/sms_providerlocation-server-wmi-class) object *ProviderForLocalSite* property, connect to the SMS Provider for the local computer and receive a [SWbemServices object](/en-us/windows/desktop/wmisdk/swbemservices).
5. Use the [SWbemServices](/en-us/windows/desktop/wmisdk/swbemservices) object to access provider objects. For more information, see [Objects overview](configuration-manager-objects-overview).

## Examples

The following example connects to the server. It then attempts to connect to the SMS Provider for that server. Typically this will be the same computer. If it isn't, [SMS_ProviderLocation](../../reference/misc/sms_providerlocation-server-wmi-class) provides the correct computer name.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```vbs
Function Connect(server, userName, userPassword)

    On Error Resume Next

    Dim net
    Dim localConnection
    Dim swbemLocator
    Dim swbemServices
    Dim providerLoc
    Dim location

    Set swbemLocator = CreateObject("WbemScripting.SWbemLocator")

    swbemLocator.Security_.AuthenticationLevel = 6 'Packet Privacy.

    ' If the server is local, do not supply credentials.
    Set net = CreateObject("WScript.NetWork")
    If UCase(net.ComputerName) = UCase(server) Then
        localConnection = true
        userName = ""
        userPassword = ""
        server = "."
    End If

    ' Connect to the server.
    Set swbemServices= swbemLocator.ConnectServer _
            (server, "root\sms",userName,userPassword)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't connect: " + Err.Description
        Connect = null
        Exit Function
    End If

    ' Determine where the provider is and connect.
    Set providerLoc = swbemServices.InstancesOf("SMS_ProviderLocation")

        For Each location In providerLoc
            If location.ProviderForLocalSite = True Then
                Set swbemServices = swbemLocator.ConnectServer _
                 (location.Machine, "root\sms\site_" + _
                    location.SiteCode,userName,userPassword)
                If Err.Number<>0 Then
                    Wscript.Echo "Couldn't connect:" + Err.Description
                    Connect = Null
                    Exit Function
                End If
                Set Connect = swbemServices
                Exit Function
            End If
        Next
    Set Connect = null ' Failed to connect.
End Function
```

The following sample connects to the remote server using PowerShell, and attempts an SMS connection.

```powerShell
$siteCode = ''
$siteServer = 'server.domain'

$credentials = Get-Credential
$username = $credentials.UserName

# The connector does not understand a PSCredential. The following command will pull your PSCredential password into a string.
$password = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto([System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($credentials.Password))

$NameSpace = "root\sms\site_$siteCode"
$SWbemLocator = New-Object -ComObject "WbemScripting.SWbemLocator"
$SWbemLocator.Security_.AuthenticationLevel = 6
$connection = $SWbemLocator.ConnectServer($siteServer,$Namespace,$username,$password)
```

## Compiling the Code

This C# example requires:

## Comments

The sample method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/desktop/wmisdk/swbemservices) |  |
| A valid connection to the SMS Provider. |  |  |
| `taskSequence` | - Managed: `IResultObject`- VBScript: `SWbemObject` | A valid task sequence ([SMS_TaskSequence](../../reference/osd/sms_tasksequence-server-wmi-class)). |
| `taskSequenceXML` | - Managed: `String`- VBScript: `String` | A valid task sequence XML. |

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).

## .NET Framework Security

Using script to pass the user name and password is a security risk and should be avoided where possible.

The preceding example sets the authentication to packet privacy. This is the same managed SMS Provider.

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../servers/configure/role-based-administration).