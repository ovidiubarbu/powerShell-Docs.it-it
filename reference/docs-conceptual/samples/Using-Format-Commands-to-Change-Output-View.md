---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: Uso dei comandi Format per modificare la visualizzazione dell'output
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417600"
---
# <a name="using-format-commands-to-change-output-view"></a>Uso dei comandi Format per modificare la visualizzazione dell'output

PowerShell include un set di cmdlet che consentono di controllare la visualizzazione delle proprietà per oggetti specifici. I nomi di tutti i cmdlet iniziano con il verbo `Format`. Consentono di selezionare le proprietà da visualizzare.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

Questo articolo descrive i cmdlet `Format-Wide`, `Format-List` e `Format-Table`.

Tutti i tipi di oggetto in PowerShell includono proprietà predefinite che vengono usate quando non sono specificate le proprietà da visualizzare. Tutti i cmdlet usano anche lo stesso parametro **Property** per specificare le proprietà da visualizzare. Poiché `Format-Wide` visualizza solo una singola proprietà, il relativo parametro **Property** accetta un solo valore, ma i parametri della proprietà di `Format-List` e `Format-Table` accettano un elenco di nomi di proprietà.

In questo esempio l'output predefinito del cmdlet `Get-Process` indica che sono in esecuzione due istanze di Internet Explorer.

```powershell
Get-Process -Name iexplore
```

Il formato predefinito per gli oggetti **Process** visualizza le proprietà indicate di seguito:

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Uso di Format-Wide per output a elemento singolo

Per impostazione predefinita, il cmdlet `Format-Wide` visualizza solo la proprietà predefinita di un oggetto. Le informazioni associate a ogni oggetto sono visualizzate in una singola colonna:

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

È inoltre possibile specificare una proprietà non predefinita:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Controllo della visualizzazione di Format-Wide con il parametro Column

Con il cmdlet `Format-Wide` è possibile visualizzare unicamente una sola proprietà alla volta. È utile per la visualizzazione di elenchi di grandi dimensioni in più colonne.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Uso di Format-List per una visualizzazione elenco

Il cmdlet `Format-List` visualizza un oggetto sotto forma di elenco. Ogni proprietà ha un'etichetta ed è visualizzata in una riga distinta:

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

È possibile specificare il numero di proprietà che si vuole:

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Ottenere informazioni dettagliate usando Format-List con i caratteri jolly

Il cmdlet `Format-List` consente di usare un carattere jolly come valore del rispettivo parametro **Property**. In questo modo si possono visualizzare informazioni dettagliate. Gli oggetti includono spesso più informazioni di quelle necessarie, motivo per cui per impostazione predefinita PowerShell non visualizza tutti i valori della proprietà. Per visualizzare tutte le proprietà di un oggetto, usare il comando `Format-List -Property *`. Il comando seguente genera oltre 60 righe di output per un unico processo:

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Anche se il comando `Format-List` è utile per la visualizzazione dei dettagli, se si vuole una panoramica dell'output che includa molti elementi, è spesso più utile una visualizzazione semplificata in formato tabulare.

## <a name="using-format-table-for-tabular-output"></a>Uso di Format-Table per output in formato tabulare

Se si usa il cmdlet `Format-Table` senza nomi di proprietà specificati per formattare l'output del comando `Get-Process`, si ottiene esattamente lo stesso output di quando non si usa un cmdlet `Format`. Per impostazione predefinita, PowerShell visualizza gli oggetti **Process** in un formato tabulare.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Ottimizzazione dell'output di Format-Table (AutoSize)

Una visualizzazione tabulare è utile per visualizzare molte informazioni, ma potrebbe essere di difficile interpretazione se la schermata è troppo ristretta per contenere i dati. Nell'esempio precedente l'output è troncato. Se si specifica il parametro **AutoSize** quando si esegue il comando `Format-Table`, PowerShell calcola la larghezza delle colonne in base ai dati effettivi da visualizzare. In questo modo le colonne risultano leggibili.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

Il cmdlet `Format-Table` potrebbe comunque troncare i dati, ma solo alla fine della schermata. Per tutte le proprietà, fatta eccezione per l'ultima visualizzata, viene assegnato tutto lo spazio richiesto per la corretta visualizzazione degli elementi di dati più lunghi.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

Il comando `Format-Table` presuppone che le proprietà siano elencate in ordine di importanza. Per questo motivo, tenta di visualizzare interamente le proprietà in prossimità dell'inizio dell'elenco. Se il comando `Format-Table` non visualizza tutte le proprietà, rimuove alcune colonne dalla visualizzazione. Questo comportamento è illustrato nell'esempio precedente della proprietà **DependentServices**.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Ritorno a capo automatico dell'output di Format-Table nelle colonne (Wrap)

È possibile forzare il ritorno a capo automatico dei dati più lunghi di `Format-Table` nella rispettiva colonna visualizzata usando il parametro **Wrap**. È possibile che con il parametro**Wrap** non si ottengano i risultati previsti, dal momento che il parametro usa le impostazioni predefinite se non è specificato anche **AutoSize**:

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

L'uso del solo parametro **Wrap** non rallenta molto l'elaborazione. L'uso di **AutoSize** per formattare un elenco di file ricorsivi di una struttura di directory di grandi dimensioni potrebbe tuttavia richiedere molto tempo e usare una grande quantità di memoria prima di visualizzare i primi elementi dell'output.

Se non si teme il carico del sistema, **AutoSize** produce buoni risultati con il parametro **Wrap**.
Le colonne iniziali usano la larghezza necessaria per visualizzare gli elementi in una sola riga, ma se è necessario viene applicato il ritorno a capo automatico nell'ultima colonna.

> [!NOTE]
> Alcune colonne potrebbero non essere visualizzate quando si specificano per prime le colonne più larghe. Per ottenere risultati ottimali, specificare prima gli elementi di dati più piccoli.

Nell'esempio seguente vengono specificate prima le proprietà più larghe.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Nonostante il ritorno a capo automatico, l'ultima colonna **Id** viene omessa:

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Organizzazione dell'output di tabella (-GroupBy)

Un altro parametro utile per il controllo dell'output in formato tabulare è **GroupBy**. Specialmente gli elenchi in formato tabulare più lunghi possono essere difficili da confrontare. Il parametro **GroupBy** raggruppa l'output in base al valore di una proprietà. È ad esempio possibile raggruppare i servizi per **StartType** per un'analisi più semplice, omettendo il valore **StartType** nell'elenco delle proprietà:

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
