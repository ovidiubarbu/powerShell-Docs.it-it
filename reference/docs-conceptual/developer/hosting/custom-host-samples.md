---
title: Esempi di host personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367510"
---
# <a name="custom-host-samples"></a><span data-ttu-id="8370a-102">Esempi di host personalizzati</span><span class="sxs-lookup"><span data-stu-id="8370a-102">Custom Host Samples</span></span>

<span data-ttu-id="8370a-103">In questa sezione è incluso il codice di esempio per la scrittura di un host personalizzato.</span><span class="sxs-lookup"><span data-stu-id="8370a-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="8370a-104">È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="8370a-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8370a-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="8370a-105">In This Section</span></span>

 <span data-ttu-id="8370a-106">[Esempio host01](./host01-sample.md) Questo esempio illustra come implementare un'applicazione host che usa un host personalizzato di base.</span><span class="sxs-lookup"><span data-stu-id="8370a-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="8370a-107">[Esempio Host02](./host02-sample.md) Questo esempio illustra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata.</span><span class="sxs-lookup"><span data-stu-id="8370a-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="8370a-108">L'applicazione host imposta le impostazioni cultura dell'host su tedesco, esegue il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e Visualizza i risultati come verrebbero visualizzati utilizzando pwrsh. exe, quindi stampa i dati e l'ora correnti in tedesco.</span><span class="sxs-lookup"><span data-stu-id="8370a-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="8370a-109">[Esempio Host03](./host03-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="8370a-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="8370a-110">[Esempio Host04](./host04-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="8370a-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="8370a-111">L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.</span><span class="sxs-lookup"><span data-stu-id="8370a-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="8370a-112">[Esempio Host05](./host05-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="8370a-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="8370a-113">Questa applicazione host supporta anche le chiamate a computer remoti tramite i cmdlet [Enter-PSSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PSSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)</span><span class="sxs-lookup"><span data-stu-id="8370a-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="8370a-114">[Esempio Host06](./host06-sample.md) Questo esempio illustra come compilare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi Visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="8370a-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="8370a-115">Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.</span><span class="sxs-lookup"><span data-stu-id="8370a-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="8370a-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8370a-116">See Also</span></span>
