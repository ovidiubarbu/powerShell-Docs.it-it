---
title: Esempi di spazio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361000"
---
# <a name="runspace-samples"></a><span data-ttu-id="49dea-102">Esempi di spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="49dea-102">Runspace Samples</span></span>

<span data-ttu-id="49dea-103">Questa sezione include codice di esempio che illustra come usare tipi diversi di Runspaces per eseguire i comandi in modo sincrono e asincrono.</span><span class="sxs-lookup"><span data-stu-id="49dea-103">This section includes sample code that shows how to use different types of runspaces to run commands synchronously and asynchronously.</span></span> <span data-ttu-id="49dea-104">È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="49dea-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="49dea-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="49dea-105">In This Section</span></span>

> [!NOTE]
> <span data-ttu-id="49dea-106">Per esempi di applicazioni host che creano interfacce host personalizzate, vedere [esempi di host personalizzati](./custom-host-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49dea-106">For samples of host applications that create custom host interfaces, see [Custom Host Samples](./custom-host-samples.md).</span></span>

 <span data-ttu-id="49dea-107">[Esempio Runspace01](./runspace01-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono e visualizzarne l'output in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="49dea-107">[Runspace01 Sample](./runspace01-sample.md) This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously and display its output in a console window.</span></span>

 <span data-ttu-id="49dea-108">[Esempio Runspace02](./runspace02-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire in modo sincrono i cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) .</span><span class="sxs-lookup"><span data-stu-id="49dea-108">[Runspace02 Sample](./runspace02-sample.md) This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="49dea-109">I risultati di questi comandi vengono visualizzati usando un controllo [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) .</span><span class="sxs-lookup"><span data-stu-id="49dea-109">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

 <span data-ttu-id="49dea-110">[Esempio Runspace03](./runspace03-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script in modo sincrono e come gestire errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="49dea-110">[Runspace03 Sample](./runspace03-sample.md) This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="49dea-111">Lo script riceve un elenco di nomi di processo e quindi recupera tali processi.</span><span class="sxs-lookup"><span data-stu-id="49dea-111">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="49dea-112">I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="49dea-112">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

 <span data-ttu-id="49dea-113">[Esempio Runspace04](./runspace04-sample.md) Questo esempio illustra come usare la classe [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire i comandi e come intercettare gli errori di terminazione che vengono generati quando si eseguono i comandi.</span><span class="sxs-lookup"><span data-stu-id="49dea-113">[Runspace04 Sample](./runspace04-sample.md) This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="49dea-114">Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido.</span><span class="sxs-lookup"><span data-stu-id="49dea-114">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="49dea-115">Di conseguenza, non viene restituito alcun oggetto e viene generato un errore di terminazione.</span><span class="sxs-lookup"><span data-stu-id="49dea-115">As a result no objects are returned and a terminating error is thrown.</span></span>

 <span data-ttu-id="49dea-116">[Esempio Runspace05](./runspace05-sample.md) In questo esempio viene illustrato come aggiungere uno snap-in a un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) , in modo che il cmdlet dello snap-in sia disponibile quando viene aperto il spazio.</span><span class="sxs-lookup"><span data-stu-id="49dea-116">[Runspace05 Sample](./runspace05-sample.md) This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="49dea-117">Lo snap-in fornisce un cmdlet Get-proc (definito dall' [esempio GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) che viene eseguito in modo sincrono tramite un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="49dea-117">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

 <span data-ttu-id="49dea-118">[Esempio Runspace06](./runspace06-sample.md) Questo esempio illustra come aggiungere un modulo a un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) , in modo che il modulo venga caricato quando viene aperto il spazio.</span><span class="sxs-lookup"><span data-stu-id="49dea-118">[Runspace06 Sample](./runspace06-sample.md) This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="49dea-119">Il modulo fornisce un cmdlet Get-proc (definito dall' [esempio GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) che viene eseguito in modo sincrono usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="49dea-119">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

 <span data-ttu-id="49dea-120">[Esempio Runspace07](./runspace07-sample.md) Questo esempio illustra come creare un spazio e quindi usare tale spazio per eseguire due cmdlet in modo sincrono usando un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="49dea-120">[Runspace07 Sample](./runspace07-sample.md) This sample shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

 <span data-ttu-id="49dea-121">[Esempio Runspace08](./runspace08-sample.md) Questo esempio illustra come aggiungere comandi e argomenti alla pipeline di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire i comandi in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="49dea-121">[Runspace08 Sample](./runspace08-sample.md) This sample shows how to add commands and arguments to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

 <span data-ttu-id="49dea-122">[Esempio Runspace09](./runspace09-sample.md) Questo esempio illustra come aggiungere uno script alla pipeline di un oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire lo script in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="49dea-122">[Runspace09 Sample](./runspace09-sample.md) This sample shows how to add a script to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span> <span data-ttu-id="49dea-123">Gli eventi vengono usati per gestire l'output dello script.</span><span class="sxs-lookup"><span data-stu-id="49dea-123">Events are used to handle the output of the script.</span></span>

 <span data-ttu-id="49dea-124">[Esempio Runspace10](./runspace10-sample.md) Questo esempio illustra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), come creare un spazio che usa lo stato della sessione iniziale e come eseguire il comando usando Oggetto [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="49dea-124">[Runspace10 Sample](./runspace10-sample.md) This sample shows how to create a default initial session state, how to add a cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), how to create a runspace that uses the initial session state, and how to run the command by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

 <span data-ttu-id="49dea-125">[Esempio Runspace11](./runspace11-sample.md) Viene illustrato come usare la classe [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili.</span><span class="sxs-lookup"><span data-stu-id="49dea-125">[Runspace11 Sample](./runspace11-sample.md) This shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="49dea-126">Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato.</span><span class="sxs-lookup"><span data-stu-id="49dea-126">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="49dea-127">Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.</span><span class="sxs-lookup"><span data-stu-id="49dea-127">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="see-also"></a><span data-ttu-id="49dea-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="49dea-128">See Also</span></span>