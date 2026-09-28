---
layout: Conceptual
title: Calling Code Snippets - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets
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
description: How to set up the calling code for the code examples that are used throughout the Configuration Manager Software Development Kit (SDK).
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: d89789e7-1c41-3ae5-bdbe-dc4bdad984a0
document_version_independent_id: 0c07b825-27e8-f362-e109-d5f6bb033228
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/calling-code-snippets.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/calling-code-snippets
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/calling-code-snippets.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1b450678-22f5-316c-66fa-eb7efdc44b4c
---

# Calling Code Snippets - Configuration Manager | Microsoft Learn

The following code samples show how to set up the calling code for the code examples that are used throughout the Configuration Manager Software Development Kit (SDK).

Replace the SNIPPETMETHOD snippet with the snippet that you want to run. In most cases you will need to make changes, such as adding parameters, to make the code work.

For more information about remote Windows Management Instrumentation (WMI) connections, see [Connecting to WMI on a Remote Computer](/en-us/windows/win32/wmisdk/connecting-to-wmi-on-a-remote-computer).

## Example

```vbs
Dim connection
Dim computer
Dim userName
Dim userPassword
Dim password 'Password object

Wscript.StdOut.Write "Computer you want to connect to (Enter . for local): "
computer = WScript.StdIn.ReadLine

If computer = "." Then
    userName = ""
    userPassword = ""
Else
    Wscript.StdOut.Write "Please enter the user name: "
    userName = WScript.StdIn.ReadLine

    Set password = CreateObject("ScriptPW.Password")
    WScript.StdOut.Write "Please enter your password:"
    userPassword = password.GetPassword()
End If

Set connection = Connect(computer,userName,userPassword)

If Err.Number<>0 Then
    Wscript.Echo "Call to connect failed"
End If

Call SNIPPETMETHODNAME (connection)

Sub SNIPPETMETHODNAME(connection)
   ' Insert snippet code here.
End Sub

Function Connect(server, userName, userPassword)

    On Error Resume Next

    Dim net
    Dim localConnection
    Dim swbemLocator
    Dim swbemServices
    Dim providerLoc
    Dim location

    Set swbemLocator = CreateObject("WbemScripting.SWbemLocator")

    swbemLocator.Security_.AuthenticationLevel = 6 'Packet Privacy

    ' If  the server is local, don not supply credentials.
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

```c
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.ConfigurationManagement.ManagementProvider;
using Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine;

namespace ConfigurationManagerSnippets
{
    class Program
    {
        static void Main(string[] args)
        {
            // Setup snippet class.

            string computer = "";
            string userName = "";
            string password = "";

            SnippetClass snippets = new SnippetClass();

            Console.WriteLine("Computer you want to connect to (Enter . for local): ");
            computer = Console.ReadLine();
            Console.WriteLine();

            if (computer == ".")
            {
                computer = System.Net.Dns.GetHostName();
                userName = "";
                password = "";
            }
            else
            {
                Console.WriteLine("Please enter the user name: ");
                userName = Console.ReadLine();

                Console.WriteLine("Please enter your password:");
                password = snippets.ReturnPassword();
            }

            // Make connection to provider.
            WqlConnectionManager WMIConnection = snippets.Connect(computer, userName, password);

            // Call snippet function and pass the provider connection object.
            snippets.SNIPPETMETHODNAME(WMIConnection);
        }
    }

    class SnippetClass
    {
        public WqlConnectionManager Connect(string serverName, string userName, string userPassword)
        {
            try
            {
                SmsNamedValuesDictionary namedValues = new SmsNamedValuesDictionary();
                WqlConnectionManager connection = new WqlConnectionManager(namedValues);
                if (System.Net.Dns.GetHostName().ToUpper() == serverName.ToUpper())
                {
                    connection.Connect(serverName);
                }
                else
                {
                    connection.Connect(serverName, userName, userPassword);
                }
                return connection;
            }
            catch (SmsException ex)
            {
                Console.WriteLine("Failed to Connect. Error: " + ex.Message);
                return null;
            }
            catch (UnauthorizedAccessException ex)
            {
                Console.WriteLine("Failed to authenticate. Error:" + ex.Message);
                return null;
            }
        }

        public void SNIPPETMETHODNAME(WqlConnectionManager connection)
        {
            // Insert snippet code here.
        }

        public string ReturnPassword()
        {
            string password = "";
            ConsoleKeyInfo info = Console.ReadKey(true);
            while (info.Key != ConsoleKey.Enter)
            {
                if (info.Key != ConsoleKey.Backspace)
                {
                    password += info.KeyChar;
                    info = Console.ReadKey(true);
                }
                else if (info.Key == ConsoleKey.Backspace)
                {
                    if (!string.IsNullOrEmpty(password))
                    {
                        password = password.Substring
                        (0, password.Length - 1);
                    }
                    info = Console.ReadKey(true);
                }
            }
            for (int i = 0; i < password.Length; i++)
                Console.Write("*");
            return password;
        }
    }
}
```

## Compiling the Code

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

Note

The assemblies are in the &lt;Program Files&gt;\Microsoft Endpoint Manager\AdminConsole\bin folder.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../reqs/server-runtime-requirements).

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) and [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29). These can be caught together with [SmsException](/en-us/previous-versions/system-center/developer/cc147433%28v=msdn.10%29).