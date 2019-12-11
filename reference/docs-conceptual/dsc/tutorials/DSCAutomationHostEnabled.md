---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954268"
---
><span data-ttu-id="0088f-103">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0088f-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="0088f-104">Chiave del Registro di sistema DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="0088f-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="0088f-105">DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** per abilitare la configurazione del computer in fase di avvio iniziale.</span><span class="sxs-lookup"><span data-stu-id="0088f-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="0088f-106">**DSCAutomationHostEnabled** supporta tre modalità:</span><span class="sxs-lookup"><span data-stu-id="0088f-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="0088f-107">Valore DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="0088f-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="0088f-108">Description</span><span class="sxs-lookup"><span data-stu-id="0088f-108">Description</span></span>   |
|---|---|
<span data-ttu-id="0088f-109">0</span><span class="sxs-lookup"><span data-stu-id="0088f-109">0</span></span> | <span data-ttu-id="0088f-110">Disabilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="0088f-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0088f-111">1</span><span class="sxs-lookup"><span data-stu-id="0088f-111">1</span></span> | <span data-ttu-id="0088f-112">Abilitazione della configurazione della macchina al momento dell'avvio.</span><span class="sxs-lookup"><span data-stu-id="0088f-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="0088f-113">2</span><span class="sxs-lookup"><span data-stu-id="0088f-113">2</span></span> | <span data-ttu-id="0088f-114">Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente.</span><span class="sxs-lookup"><span data-stu-id="0088f-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="0088f-115">Questo è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="0088f-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0088f-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0088f-116">See Also</span></span>

<span data-ttu-id="0088f-117">Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="0088f-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
