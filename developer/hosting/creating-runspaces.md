---
title: Creazione di spazi di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857907"
---
# <a name="creating-runspaces"></a><span data-ttu-id="0575a-102">Creazione di spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="0575a-102">Creating Runspaces</span></span>

<span data-ttu-id="0575a-103">Uno spazio di esecuzione è l'ambiente operativo per i comandi che vengono richiamate da un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="0575a-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="0575a-104">Questo ambiente include i comandi e i dati che sono attualmente presenti ed eventuali restrizioni di linguaggio che attualmente si applicano.</span><span class="sxs-lookup"><span data-stu-id="0575a-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="0575a-105">Hosting di applicazioni può usare lo spazio di esecuzione predefinito fornito da Windows PowerShell, che include tutti i comandi di core disponibili, o creare uno spazio di esecuzione personalizzata che include solo un subset di comandi disponibili.</span><span class="sxs-lookup"><span data-stu-id="0575a-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="0575a-106">Per creare uno spazio di esecuzione personalizzata, è necessario creare un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) e assegnarlo a di spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0575a-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="0575a-107">Spazio di esecuzione attività</span><span class="sxs-lookup"><span data-stu-id="0575a-107">Runspace tasks</span></span>

1. [<span data-ttu-id="0575a-108">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="0575a-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="0575a-109">Creazione di uno spazio di esecuzione vincolata</span><span class="sxs-lookup"><span data-stu-id="0575a-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="0575a-110">Creazione di più spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="0575a-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="0575a-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0575a-111">See Also</span></span>
