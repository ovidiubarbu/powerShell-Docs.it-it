---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954268"
---
><span data-ttu-id="25265-103">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="25265-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="25265-104">Chiave del Registro di sistema DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="25265-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="25265-105">DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** per abilitare la configurazione del computer in fase di avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="25265-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="25265-106">**DSCAutomationHostEnabled** supporta tre modalità:</span><span class="sxs-lookup"><span data-stu-id="25265-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="25265-107">Valore DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="25265-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="25265-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="25265-108">Description</span></span>   |
|---|---|
<span data-ttu-id="25265-109">0</span><span class="sxs-lookup"><span data-stu-id="25265-109">0</span></span> | <span data-ttu-id="25265-110">Disabilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="25265-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="25265-111">1</span><span class="sxs-lookup"><span data-stu-id="25265-111">1</span></span> | <span data-ttu-id="25265-112">Abilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="25265-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="25265-113">2</span><span class="sxs-lookup"><span data-stu-id="25265-113">2</span></span> | <span data-ttu-id="25265-114">Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente.</span><span class="sxs-lookup"><span data-stu-id="25265-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="25265-115">Si tratta del valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="25265-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="25265-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25265-116">See Also</span></span>

<span data-ttu-id="25265-117">Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="25265-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
