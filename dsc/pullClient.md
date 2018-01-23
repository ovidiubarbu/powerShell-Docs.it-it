---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull DSC
ms.openlocfilehash: 98a67b8d27eeb445bb70f75253ca31e12207d5bd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="c73ec-103">Configurazione di un client di pull DSC</span><span class="sxs-lookup"><span data-stu-id="c73ec-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="c73ec-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c73ec-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c73ec-105">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL o il percorso di file per contattare il server di pull da cui ottenere le configurazioni e le risorse, oltre alla posizione in cui inviare i dati di report.</span><span class="sxs-lookup"><span data-stu-id="c73ec-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="c73ec-106">Gli argomenti seguenti illustrano come configurare i client di pull:</span><span class="sxs-lookup"><span data-stu-id="c73ec-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="c73ec-107">Configurazione di un client di pull usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="c73ec-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="c73ec-108">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="c73ec-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="c73ec-109">**Nota**: questi argomenti si applicano a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="c73ec-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="c73ec-110">Per configurare un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="c73ec-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

