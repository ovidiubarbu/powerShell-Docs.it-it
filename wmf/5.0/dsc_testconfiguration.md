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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Il cmdlet Test-DscConfiguration supporta configurazioni di riferimento

Il cmdlet Test-DscConfiguration è stato aggiornato per consentire il test dello stato di configurazione desiderato di uno o più nodi di destinazione, specificando un documento di configurazione di riferimento per il confronto.

I nuovi set di parametri seguenti usano le configurazioni DSC nel percorso specificato solo per eseguire test, senza mai applicare ogni configurazione ai nodi di destinazione specificati. Come per il cmdlet Start-DscConfiguration e altri cmdlet DSC, il nome di ogni file MOF viene usato per determinare il nodo di destinazione su cui eseguire il test della configurazione.

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

I nuovi set di parametri seguenti usano una singola configurazione DSC solo per eseguire test, senza mai applicare la configurazione ai nodi di destinazione specificati.

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