---
title: Scrittura di un'applicazione Host di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 1aaf936aa22af5c4a4b8c2fa4e6b3bbd2cff6d20
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855092"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="41925-102">Scrittura di un'applicazione host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41925-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="41925-103">È possibile ospitare Windows PowerShell nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="41925-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="41925-104">L'applicazione host può definire lo spazio di esecuzione in cui i comandi vengono eseguiti, aprire le sessioni in un computer locale o remoto e richiamare i comandi di che uno in modo sincrono o asincrono in base alle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="41925-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="41925-105">Gli argomenti seguenti illustrano come creare un'applicazione che ospita Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41925-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="41925-106">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="41925-106">In This Section</span></span>

<span data-ttu-id="41925-107">[Avvio rapido di Host di Windows PowerShell](./windows-powershell-host-quickstart.md) fornisce istruzioni ed esempi di codice per iniziare a creare applicazioni host.</span><span class="sxs-lookup"><span data-stu-id="41925-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="41925-108">[Creazione di spazi di esecuzione](./creating-runspaces.md) un insieme di argomenti che illustrano come creare spazi di esecuzione per eseguire il comando di Windows PowerShell in un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="41925-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="41925-109">[Aggiunta e la chiamata di comandi](./adding-and-invoking-commands.md) viene illustrato come creare ed eseguire una pipeline di comandi nell'applicazione host...</span><span class="sxs-lookup"><span data-stu-id="41925-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="41925-110">[Creazione di spazi di esecuzione remota](./creating-remote-runspaces.md) spiega come connettersi a uno spazio di esecuzione a un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="41925-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="41925-111">[Creazione di un'interfaccia utente personalizzata](./creating-a-custom-user-interface.md) vengono forniti collegamenti a esempi e interfacce utente personalizzate presenta.</span><span class="sxs-lookup"><span data-stu-id="41925-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="41925-112">[Esempi di applicazione per host](./host-application-samples.md) in questa sezione include esempi di applicazioni host completo.</span><span class="sxs-lookup"><span data-stu-id="41925-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="41925-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="41925-113">See Also</span></span>

[<span data-ttu-id="41925-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41925-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
