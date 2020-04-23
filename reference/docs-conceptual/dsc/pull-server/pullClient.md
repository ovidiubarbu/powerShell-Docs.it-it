---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un client di pull DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955168"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="8a6d2-103">Configurazione di un client di pull DSC</span><span class="sxs-lookup"><span data-stu-id="8a6d2-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="8a6d2-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8a6d2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a6d2-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="8a6d2-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="8a6d2-107">Per ogni nodo di destinazione è necessario specificare che venga usata la modalità pull e fornire l'URL o il percorso di file per contattare il server di pull da cui ottenere le configurazioni e le risorse, oltre alla posizione in cui inviare i dati di report.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="8a6d2-108">Gli argomenti seguenti illustrano come configurare i client di pull:</span><span class="sxs-lookup"><span data-stu-id="8a6d2-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="8a6d2-109">Configurazione di un client di pull usando nomi di configurazione</span><span class="sxs-lookup"><span data-stu-id="8a6d2-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="8a6d2-110">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="8a6d2-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="8a6d2-111">Questi argomenti si applicano a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="8a6d2-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="8a6d2-112">Per configurare un client di pull in PowerShell 4.0, vedere [Configurazione di un client di pull usando un ID configurazione in PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="8a6d2-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>