---
title: Implementazione SessionConfiguration per un servizio web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b2a7ce2-3c33-469c-a4a4-b8fe3bd05324
caps.latest.revision: 5
ms.openlocfilehash: 93780ee8af80d78a5b97a32098384a148070b54a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080629"
---
# <a name="implementing-sessionconfiguration-for-a-management-odata-web-service"></a><span data-ttu-id="df3af-102">Implementazione di SessionConfiguration per un servizio Web OData di gestione</span><span class="sxs-lookup"><span data-stu-id="df3af-102">Implementing SessionConfiguration for a Management OData web service</span></span>

<span data-ttu-id="df3af-103">Usando il servizio Web di Windows PowerShell richiede una terza parte implementare il [pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaccia da esporre i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df3af-103">Using the Windows PowerShell Web Service requires a third party to implement the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface to expose Windows PowerShell cmdlets.</span></span> <span data-ttu-id="df3af-104">Questa interfaccia fornisce l'accesso alle informazioni relative alla sessione remota che utilizza il servizio web per eseguire i cmdlet nel server.</span><span class="sxs-lookup"><span data-stu-id="df3af-104">This interface provides access to information about the remote session that the web service uses to run the cmdlets on the server.</span></span> <span data-ttu-id="df3af-105">Dopo aver scritto il codice per implementare l'interfaccia, è necessario compilarlo in una DLL da utilizzare nell'applicazione web.</span><span class="sxs-lookup"><span data-stu-id="df3af-105">After writing the code to implement the interface, you must compile it into a DLL to be used in the web application.</span></span>

## <a name="implementation-of-pssessionconfiguration-interface"></a><span data-ttu-id="df3af-106">Implementazione dell'interfaccia PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="df3af-106">Implementation of PSSessionConfiguration interface</span></span>

<span data-ttu-id="df3af-107">Il codice seguente implementa il [pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="df3af-107">The following code implements the [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interface.</span></span>

```csharp
//-----------------------------------------------------------------------
// <copyright file="SessionConfiguration.cs" company="Microsoft Corporation">
//     Copyright (C) 2011 Microsoft Corporation
// </copyright>
//-----------------------------------------------------------------------

namespace Microsoft.Samples.Management.OData.RoleBasedPlugins
{
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Management.Automation;
    using System.Management.Automation.Remoting;
    using System.Management.Automation.Runspaces;

    /// <summary>
    /// Custom Session configuration implementation
    /// </summary>
    public class SessionConfiguration : PSSessionConfiguration
    {
        /// <summary>
        /// Gets application private data
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Always returns null</returns>
        public override PSPrimitiveDictionary GetApplicationPrivateData(PSSenderInfo senderInfo)
        {
            return null;
        }

        /// <summary>
        /// Gets custom initial session state
        /// It relies on the RBAC system to give list of commands allowed for a user
        /// and creates Initial Session state from that
        /// </summary>
        /// <param name="senderInfo">Sender information</param>
        /// <returns>Custom initial Session state</returns>
        public override InitialSessionState GetInitialSessionState(PSSenderInfo senderInfo)
        {
            if (senderInfo == null)
            {
                throw new ArgumentNullException("senderInfo");
            }

            if (senderInfo.UserInfo == null)
            {
                throw new ArgumentException("senderInfo.UserInfo is null");
            }

            InitialSessionState initialSessionState = InitialSessionState.CreateDefault();
            foreach (SessionStateCommandEntry command in initialSessionState.Commands)
            {
                command.Visibility = SessionStateEntryVisibility.Private;
            }

            List<string> scripts = RbacSystem.Current.GetScripts(senderInfo.UserInfo);
            foreach (string script in scripts)
            {
                initialSessionState.Commands.Add(new SessionStateScriptEntry(script));
            }

            List<string> modules = RbacSystem.Current.GetModules(senderInfo.UserInfo);
            if (modules.Count > 0)
            {
                initialSessionState.ImportPSModule(modules.ToArray());
            }

            // enable execution of scripts in this process
            System.Environment.SetEnvironmentVariable("PSExecutionPolicyPreference", "unrestricted");

            List<string> cmdletsFromRbac = RbacSystem.Current.GetCmdlets(senderInfo.UserInfo);

            // Add all commands from Rbac system to Initial Session State commands
            foreach (string cmdlet in cmdletsFromRbac)
            {
                SessionStateCommandEntry cmdletFromRbac = initialSessionState.Commands.FirstOrDefault(item => string.Equals(item.Name, cmdlet, StringComparison.OrdinalIgnoreCase));
                if (cmdletFromRbac == null)
                {
                    throw new ArgumentException("Command not found in InitialSessionState " + cmdlet);
                }

                cmdletFromRbac.Visibility = SessionStateEntryVisibility.Public;
            }

            return initialSessionState;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="df3af-108">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="df3af-108">See Also</span></span>

[<span data-ttu-id="df3af-109">Implementare l'autorizzazione personalizzata per un servizio web IIS OData gestione</span><span class="sxs-lookup"><span data-stu-id="df3af-109">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)