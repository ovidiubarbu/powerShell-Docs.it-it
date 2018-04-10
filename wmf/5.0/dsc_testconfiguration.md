---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="082d3-102">Il cmdlet Test-DscConfiguration supporta configurazioni di riferimento</span><span class="sxs-lookup"><span data-stu-id="082d3-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="082d3-103">Il cmdlet Test-DscConfiguration è stato aggiornato per consentire il test dello stato di configurazione desiderato di uno o più nodi di destinazione, specificando un documento di configurazione di riferimento per il confronto.</span><span class="sxs-lookup"><span data-stu-id="082d3-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="082d3-104">I nuovi set di parametri seguenti usano le configurazioni DSC nel percorso specificato solo per eseguire test, senza mai applicare ogni configurazione ai nodi di destinazione specificati.</span><span class="sxs-lookup"><span data-stu-id="082d3-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="082d3-105">Come per il cmdlet Start-DscConfiguration e altri cmdlet DSC, il nome di ogni file MOF viene usato per determinare il nodo di destinazione su cui eseguire il test della configurazione.</span><span class="sxs-lookup"><span data-stu-id="082d3-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

<span data-ttu-id="082d3-106">I nuovi set di parametri seguenti usano una singola configurazione DSC solo per eseguire test, senza mai applicare la configurazione ai nodi di destinazione specificati.</span><span class="sxs-lookup"><span data-stu-id="082d3-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```