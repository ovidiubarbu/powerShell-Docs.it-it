---
title: Creazione di Runspaces | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367580"
---
# <a name="creating-runspaces"></a><span data-ttu-id="2245c-102">Creazione di spazi di esecuzione</span><span class="sxs-lookup"><span data-stu-id="2245c-102">Creating Runspaces</span></span>

<span data-ttu-id="2245c-103">Un spazio è l'ambiente operativo per i comandi richiamati da un'applicazione host.</span><span class="sxs-lookup"><span data-stu-id="2245c-103">A runspace is the operating environment for the commands that are invoked by a host application.</span></span> <span data-ttu-id="2245c-104">Questo ambiente include i comandi e i dati attualmente presenti e tutte le restrizioni relative alla lingua attualmente applicabili.</span><span class="sxs-lookup"><span data-stu-id="2245c-104">This environment includes the commands and data that are currently present, and any language restrictions that currently apply.</span></span>

 <span data-ttu-id="2245c-105">Le applicazioni host possono usare il spazio predefinito fornito da Windows PowerShell, che include tutti i comandi di base disponibili, oppure creare un spazio personalizzato che includa solo un subset dei comandi disponibili.</span><span class="sxs-lookup"><span data-stu-id="2245c-105">Host applications can use the default runspace that is provided by Windows PowerShell, which includes all available core commands, or create a custom runspace that includes only a subset of the available commands.</span></span> <span data-ttu-id="2245c-106">Per creare un spazio personalizzato, creare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) e assegnarlo a spazio.</span><span class="sxs-lookup"><span data-stu-id="2245c-106">To create a customized runspace, you create an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and assign it to your runspace.</span></span>

## <a name="runspace-tasks"></a><span data-ttu-id="2245c-107">Attività spazio</span><span class="sxs-lookup"><span data-stu-id="2245c-107">Runspace tasks</span></span>

1. [<span data-ttu-id="2245c-108">Creazione di un InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="2245c-108">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)

2. [<span data-ttu-id="2245c-109">Creazione di un spazio vincolato</span><span class="sxs-lookup"><span data-stu-id="2245c-109">Creating a constrained runspace</span></span>](./creating-a-constrained-runspace.md)

3. [<span data-ttu-id="2245c-110">Creazione di più Runspaces</span><span class="sxs-lookup"><span data-stu-id="2245c-110">Creating multiple runspaces</span></span>](./creating-multiple-runspaces.md)

## <a name="see-also"></a><span data-ttu-id="2245c-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2245c-111">See Also</span></span>
