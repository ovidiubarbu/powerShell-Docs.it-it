---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Informazioni sulle pipeline di PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002856"
---
# <a name="understanding-pipelines"></a>Informazioni sulle pipeline

Le pipeline si comportano come una serie di segmenti di pipe connessi. Gli elementi che si muovono nella pipeline passano tramite ogni segmento. Per creare una pipeline in PowerShell, è necessario collegare tra loro i comandi con l'operatore di pipe "|". L'output di ogni comando viene usato come input per il comando successivo.

La notazione usata per le pipeline è simile a quella usata in altre shell. A prima vista, può non essere evidente come si differenziano le pipeline in PowerShell. Anche se sullo schermo viene visualizzato testo, PowerShell invia tramite pipe oggetti, e non testo, tra i comandi.

## <a name="the-powershell-pipeline"></a>Pipeline di PowerShell

Le pipeline sono senza dubbio il concetto più importante usato nelle interfacce della riga di comando. Se usate correttamente, le pipeline riducono la necessità di usare comandi complessi e semplificano la visualizzazione del flusso di lavoro per i comandi. Ogni comando in una pipeline (denominato elemento della pipeline) passa il proprio output al comando successivo nella pipeline, elemento per elemento. I comandi non devono gestire più di un elemento per volta. Ne risultano un utilizzo inferiore delle risorse e la possibilità di iniziare a ottenere l'output immediatamente.

Ad esempio, se si usa il cmdlet `Out-Host` per forzare una visualizzazione pagina per pagina dell'output di un altro comando, l'output avrà lo stesso aspetto del normale testo visualizzato sullo schermo, suddiviso in pagine:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

La divisione in pagine riduce anche l'utilizzo della CPU perché i trasferimenti vengono elaborati nel cmdlet `Out-Host` quando è pronta per la visualizzazione una pagina completa. I cmdlet precedenti nella pipeline sospendono l'esecuzione finché non è disponibile la pagina di output successiva.

È possibile notare la differenza con Gestione attività Windows per monitorare l'uso della CPU e della memoria da parte di PowerShell. Eseguire questo comando: `Get-ChildItem C:\Windows -Recurse`. Confrontare l'utilizzo della CPU e della memoria con questo comando: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.

## <a name="objects-in-the-pipeline"></a>Oggetti nella pipeline

Quando si esegue un cmdlet in PowerShell, viene visualizzato output di testo perché è necessario rappresentare gli oggetti come testo in una finestra della console. L'output di testo può non visualizzare tutte le proprietà dell'oggetto restituito.

Ad esempio, si consideri il cmdlet `Get-Location`. Se si esegue `Get-Location` mentre il percorso corrente è la radice dell'unità C, verrà visualizzato l'output seguente:

```
PS> Get-Location

Path
----
C:\
```

L'output di testo è un riepilogo delle informazioni e non una rappresentazione completa dell'oggetto restituito da `Get-Location`. L'intestazione nell'output viene aggiunta dal processo che formatta i dati per la visualizzazione sullo schermo.

Quando l'output viene inviato tramite pipe al cmdlet `Get-Member`, si ottengono informazioni sull'oggetto restituito da `Get-Location`.

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` restituisce un oggetto **PathInfo** che contiene il percorso corrente e altre informazioni.
