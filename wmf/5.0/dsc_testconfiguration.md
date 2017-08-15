---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2017
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

