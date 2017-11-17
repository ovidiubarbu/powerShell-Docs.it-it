---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Configurazione di un client di pull DSC
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="aae41-103">Configurazione di un client di pull DSC</span><span class="sxs-lookup"><span data-stu-id="aae41-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="aae41-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="aae41-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="aae41-105">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL o il percorso di file per contattare il server di pull da cui ottenere le configurazioni e le risorse, oltre alla posizione in cui inviare i dati di report.</span><span class="sxs-lookup"><span data-stu-id="aae41-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="aae41-106">Gli argomenti seguenti illustrano come configurare i client di pull:</span><span class="sxs-lookup"><span data-stu-id="aae41-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="aae41-107">Configurazione di un client di pull usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="aae41-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="aae41-108">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="aae41-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="aae41-109">**Nota**: questi argomenti si applicano a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="aae41-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="aae41-110">Per configurare un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="aae41-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

