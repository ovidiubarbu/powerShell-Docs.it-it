---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="7cd2c-103">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7cd2c-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="7cd2c-104">Chiave del Registro di sistema DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="7cd2c-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="7cd2c-105">DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** per abilitare la configurazione del computer all'avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="7cd2c-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="7cd2c-106">DSCAutomationHostEnabled supporta tre modalità:</span><span class="sxs-lookup"><span data-stu-id="7cd2c-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="7cd2c-107">Valore DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="7cd2c-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="7cd2c-108">Description</span><span class="sxs-lookup"><span data-stu-id="7cd2c-108">Description</span></span>   |
|---|---|
<span data-ttu-id="7cd2c-109">0</span><span class="sxs-lookup"><span data-stu-id="7cd2c-109">0</span></span> | <span data-ttu-id="7cd2c-110">Disabilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="7cd2c-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="7cd2c-111">1</span><span class="sxs-lookup"><span data-stu-id="7cd2c-111">1</span></span> | <span data-ttu-id="7cd2c-112">Abilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="7cd2c-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="7cd2c-113">2</span><span class="sxs-lookup"><span data-stu-id="7cd2c-113">2</span></span> | <span data-ttu-id="7cd2c-114">Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente.</span><span class="sxs-lookup"><span data-stu-id="7cd2c-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="7cd2c-115">Questo è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="7cd2c-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="7cd2c-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7cd2c-116">See Also</span></span>

<span data-ttu-id="7cd2c-117">Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="7cd2c-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>