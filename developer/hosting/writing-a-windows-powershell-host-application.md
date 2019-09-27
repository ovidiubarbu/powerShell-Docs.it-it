---
title: Scrittura di un'applicazione host di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: b44708b3bbcb974a6178323dff2302b7da121af6
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323503"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="36635-102">Scrittura di un'applicazione host di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36635-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="36635-103">È possibile ospitare Windows PowerShell nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="36635-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="36635-104">L'applicazione host può definire il spazio in cui vengono eseguiti i comandi, aprire sessioni in un computer locale o remoto e richiamare i comandi in modo sincrono o asincrono in base alle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="36635-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="36635-105">Negli argomenti seguenti viene illustrato come creare un'applicazione che ospita Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36635-105">The following topics explain how to create an application that hosts Windows PowerShell.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="36635-106">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="36635-106">In This Section</span></span>

<span data-ttu-id="36635-107">[Guida introduttiva all'host di Windows PowerShell](./windows-powershell-host-quickstart.md) Vengono fornite istruzioni ed esempi di codice per iniziare a creare applicazioni host.</span><span class="sxs-lookup"><span data-stu-id="36635-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="36635-108">[Creazione di Runspaces](./creating-runspaces.md) Set di argomenti in cui viene illustrato come creare Runspaces per eseguire il comando di Windows PowerShell in un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="36635-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="36635-109">[Aggiunta e richiamo di comandi](./adding-and-invoking-commands.md) Viene illustrato come creare ed eseguire una pipeline di comandi nell'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="36635-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="36635-110">[Creazione di Runspaces Remote](./creating-remote-runspaces.md) Viene illustrato come connettere un spazio a un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="36635-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="36635-111">[Creazione di un'interfaccia utente personalizzata](./creating-a-custom-user-interface.md) Introduce interfacce utente personalizzate e fornisce collegamenti ad esempi.</span><span class="sxs-lookup"><span data-stu-id="36635-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="36635-112">[Esempi di applicazioni host](./host-application-samples.md) Questa sezione include esempi di applicazioni host complete.</span><span class="sxs-lookup"><span data-stu-id="36635-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="36635-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="36635-113">See Also</span></span>

[<span data-ttu-id="36635-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="36635-114">Windows PowerShell</span></span>](https://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
