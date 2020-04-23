---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Reindirizzamento dei dati con i cmdlet Out
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030071"
---
# <a name="redirecting-data-with-out--cmdlets"></a>Reindirizzamento dei dati con i cmdlet Out-*

In Windows PowerShell sono disponibili diversi cmdlet che consentono di controllare direttamente l'output dei dati. Questi cmdlet hanno in comune due importanti caratteristiche.

Per prima cosa, in genere trasformano i dati in una forma di testo, dal momento che convertono i dati in output per i componenti di sistema che richiedono input di testo. Ciò significa che devono rappresentare gli oggetti come testo. Il testo viene pertanto formattato così com'è visualizzato nella finestra della console di Windows PowerShell.

In secondo luogo, questi cmdlet usano il verbo **Out** di Windows PowerShell poiché inviano informazioni altrove all'esterno di Windows PowerShell. Il cmdlet **Out-Host** non costituisce un'eccezione: la visualizzazione della finestra host è all'esterno di Windows PowerShell. Questo aspetto è importante perché quando i dati vengono inviati all'esterno di Windows PowerShell, vengono effettivamente rimossi. È possibile verificare quanto affermato se si prova a creare una pipeline per il paging dei dati alla finestra host e si tenta di formattarla come elenco, come illustrato di seguito:

```powershell
Get-Process | Out-Host -Paging | Format-List
```

Si potrebbe pensare che il comando visualizzerà pagine di informazioni sui processi in formato elenco. Al contrario, viene visualizzato l'elenco tabulare predefinito:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Il cmdlet **Out-Host** invia i dati direttamente alla console, pertanto il comando **Format-List** non riceve mai niente da formattare.

Il modo corretto per definire la struttura di questo comando consiste nell'inserire il cmdlet **Out-Host** alla fine della pipeline come mostrato di seguito. In questo modo, i dati dei processi vengono formattati in un elenco prima dell'esecuzione del paging e della visualizzazione.

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

Ciò si applica a tutti i cmdlet **Out**. Un cmdlet **Out** deve essere sempre visualizzato alla fine della pipeline.

> [!NOTE]
> Tutti i cmdlet **Out** eseguono il rendering dell'output come testo, usando la formattazione esistente per la finestra della console, inclusi i limiti di lunghezza delle righe.

## <a name="paging-console-output-out-host"></a>Paging dell'output della console (Out-Host)

Per impostazione predefinita, Windows PowerShell invia dati alla finestra host, che è esattamente quello che fa il cmdlet Out-Host. L'uso principale del cmdlet Out-Host è il paging dei dati come descritto in precedenza. Il comando seguente usa ad esempio Out-Host per il paging dell'output del cmdlet Get-Command:

```powershell
Get-Command | Out-Host -Paging
```

È anche possibile usare la funzione **more** per il paging dei dati. In Windows PowerShell **more** è una funzione che chiama **Out-Host -Paging**. Il comando seguente dimostra l'uso della funzione **more** per il paging dell'output di Get-Command:

```powershell
Get-Command | more
```

Se si include uno o più nomi di file come argomenti della funzione more, la funzione leggerà i file specificati ed eseguirà il paging del contenuto all'host:

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a>Eliminazione dell'output (Out-Null)

Il cmdlet **Out-Null** è progettato per eliminare immediatamente qualsiasi input ricevuto. Questa funzionalità è utile per l'eliminazione dei dati non necessari ottenuti come effetto collaterale dell'esecuzione di un comando. Quando si digita il comando seguente, non verrà restituito niente dal comando:

```powershell
Get-Command | Out-Null
```

Il cmdlet **Out-Null** non elimina l'output di errore. Se ad esempio si immette il comando seguente, viene visualizzato un messaggio che informa che Windows PowerShell non riconosce "Is-NotACommand":

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a>Stampa dei dati (Out-Printer)

È possibile stampare dati usando il cmdlet **Out-Printer**. Il cmdlet **Out-Printer** userà la stampante predefinita se non si specifica il nome della stampante. È possibile usare qualsiasi stampante basata su Windows specificandone il nome visualizzato. Non è necessario alcun tipo di mapping delle porte della stampante, né una stampante fisica reale. Se ad esempio sono installati gli strumenti di acquisizione immagini per i documenti di Microsoft Office, è possibile inviare i dati in un file di immagine digitando:

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a>Salvataggio dei dati (Out-File)

È possibile inviare l'output in un file anziché nella finestra della console usando il cmdlet **Out-File**. La seguente riga di comando invia un elenco di processi al file **C:\\temp\\processlist.txt**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

I risultati dell'uso del cmdlet **Out-File** potrebbero non essere quelli previsti se si è abituati al reindirizzamento dell'output tradizionale. Per comprendere questo comportamento, è necessario considerare il contesto in cui viene eseguito il cmdlet **Out-File**.

Per impostazione predefinita, il cmdlet **Out-File** crea un file Unicode. Questo è il valore predefinito migliore a lungo termine, ma significa che gli strumenti che prevedono file ASCII non funzioneranno correttamente con il formato di output predefinito. È possibile cambiare il formato di output predefinito in ASCII usando il parametro **Encoding**:

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

**Out-file** formatta il contenuto del file come output della console. In questo modo l'output risulta troncato proprio come accade nella maggior parte dei casi in una finestra della console. Se ad esempio si esegue il comando seguente:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

L'output dettagliato sarà simile al seguente:

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

Per ottenere un output che non forzi il ritorno a capo automatico in base alla larghezza dello schermo, è possibile usare il parametro **Width** per specificare la lunghezza delle righe. Dal momento che **Width** è un parametro intero a 32 bit, il valore massimo che può avere è 2147483647. Digitare quanto segue per impostare la lunghezza delle righe su questo valore massimo:

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

Il cmdlet **Out-File** è particolarmente utile quando si vuole salvare l'output come sarebbe stato visualizzato nella console. Per un controllo più preciso del formato dell'output, sono necessari strumenti più avanzati, che saranno presi in esame nel capitolo successivo, insieme ad alcuni dettagli sulla manipolazione degli oggetti.
