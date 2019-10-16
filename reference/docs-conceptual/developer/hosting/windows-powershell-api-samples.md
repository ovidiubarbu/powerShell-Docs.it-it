---
title: Esempi di API di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82df2cde-ba12-46d2-b6ec-da5455fd9b57
caps.latest.revision: 8
ms.openlocfilehash: a472f07cb24b0de8e5dcdfcaddd2802575318d7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360840"
---
# <a name="windows-powershell-api-samples"></a><span data-ttu-id="1c9ce-102">Esempi di API di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c9ce-102">Windows PowerShell API Samples</span></span>

<span data-ttu-id="1c9ce-103">Questa sezione include codice di esempio che illustra come creare Runspaces che limitano le funzionalità e come eseguire i comandi in modo asincrono usando un pool spazio per fornire Runspaces.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-103">This section includes sample code that shows how to create runspaces that restrict functionality, and how to asynchronously run commands by using a runspace pool to supply the runspaces.</span></span> <span data-ttu-id="1c9ce-104">È possibile utilizzare Microsoft Visual Studio per creare un'applicazione console e quindi copiare il codice dagli argomenti in questa sezione nell'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1c9ce-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="1c9ce-105">In This Section</span></span>

<span data-ttu-id="1c9ce-106">[Esempio PowerShell01](./windows-powershell01-sample.md) Questo esempio illustra come usare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) per limitare la funzionalità di un spazio.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-106">[PowerShell01 Sample](./windows-powershell01-sample.md) This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="1c9ce-107">Nell'output di questo esempio viene illustrato come limitare la modalità del linguaggio di spazio, come contrassegnare un cmdlet come privato, come aggiungere e rimuovere cmdlet e provider, come aggiungere un comando proxy e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-107">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span>

<span data-ttu-id="1c9ce-108">[Esempio PowerShell02](./windows-powershell02-sample.md) Questo esempio illustra come eseguire i comandi in modo asincrono usando il Runspaces di un pool di spazio.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-108">[PowerShell02 Sample](./windows-powershell02-sample.md) This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="1c9ce-109">L'esempio genera un elenco di comandi, quindi esegue i comandi mentre il motore di Windows PowerShell apre un spazio dal pool quando necessario.</span><span class="sxs-lookup"><span data-stu-id="1c9ce-109">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>