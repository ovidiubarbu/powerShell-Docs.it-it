---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401189"
---
><span data-ttu-id="0c2a3-103">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0c2a3-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="0c2a3-104">Chiave del Registro di sistema DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="0c2a3-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="0c2a3-105">DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** per abilitare la configurazione del computer all'avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="0c2a3-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="0c2a3-106">DSCAutomationHostEnabled supporta tre modalità:</span><span class="sxs-lookup"><span data-stu-id="0c2a3-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="0c2a3-107">Valore DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="0c2a3-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="0c2a3-108">Description</span><span class="sxs-lookup"><span data-stu-id="0c2a3-108">Description</span></span>   |
|---|---|
<span data-ttu-id="0c2a3-109">0</span><span class="sxs-lookup"><span data-stu-id="0c2a3-109">0</span></span> | <span data-ttu-id="0c2a3-110">Disabilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="0c2a3-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0c2a3-111">1</span><span class="sxs-lookup"><span data-stu-id="0c2a3-111">1</span></span> | <span data-ttu-id="0c2a3-112">Abilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="0c2a3-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0c2a3-113">2</span><span class="sxs-lookup"><span data-stu-id="0c2a3-113">2</span></span> | <span data-ttu-id="0c2a3-114">Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente.</span><span class="sxs-lookup"><span data-stu-id="0c2a3-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="0c2a3-115">Questo è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="0c2a3-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0c2a3-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0c2a3-116">See Also</span></span>

<span data-ttu-id="0c2a3-117">Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="0c2a3-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>