---
title: Miglioramenti apportati al motore di PowerShell
author: jasonsh
translationtype: Human Translation
ms.sourcegitcommit: 47c963343c541d0f2ace194f365de5fcd809ccc5
ms.openlocfilehash: 1b35a25312b44d14ec8771be9e17aaa43e270b61

---

# Miglioramenti apportati al motore di PowerShell #

I miglioramenti seguenti apportati al motore di PowerShell principale sono stati implementati in PowerShell 5.1:


## Prestazioni ##

Le prestazioni sono migliorate in alcune aree importanti:

1. Avvio
2. Pipelining ai cmdlet quali ForEach-Object e Where-Object più veloce del 50% circa 

Alcuni miglioramenti di esempio (i risultati possono variare in base all'hardware): 

| Scenario | 5.0 - Tempo (ms) | 5.1 - Tempo (ms) |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | 900 | 250 |
| Prima esecuzione di PowerShell: `powershell -command "Unknown-Command"` | 30000 | 13000 |
| Cache di analisi del comando integrata: `powershell -command "Unknown-Command"` | 7000 | 520 |
| <code>1..1000000 &#124; % { }</code> | 1400 | 750 |
  
Una modifica correlata all'avvio può avere impatto su alcuni scenari non supportati. PowerShell non legge i file `$pshome\*.ps1xml`: questi file sono stati convertiti in C# per evitare il sovraccarico dell'elaborazione di file XML da parte di alcuni file e della CPU. I file supportano ancora V2 side-by-side, pertanto se si modifica il contenuto del file, la modifica non avrà alcun impatto su V5, ma solo su V2. Si noti che la modifica dei contenuti di questi file non ha mai costituito uno scenario supportato.

Un'altra modifica evidente riguarda la modalità di memorizzazione nella cache dei comandi esportati e di altre informazioni relative ai moduli installati in un sistema da parte di PowerShell. In precedenza, la cache veniva archiviata nella directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`. In WMF 5.1, la cache è un singolo file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
Per altre informazioni dettagliate, vedere [analysis_cache.md]().

A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.



## Correzioni di bug ##

Sono stati corretti i bug importanti seguenti:

### Rispetto completo del modulo auto-discovery `$env:PSModulePath` ###

In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando). Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.

WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente. In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.

### Reindirizzamento del file non più come hardcoded `-Encoding Unicode` ###

In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file, ad esempio `Get-ChildItem > out.txt`, perché PowerShell aveva aggiunto `-Encoding Unicode`.

A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`, ad esempio

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Correzione di una regressione nell'accesso dei membri di `System.Reflection.TypeInfo` ###

Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`.
Questo bug è stato corretto in WMF 5.1.


### Risolti alcuni problemi con gli oggetti COM ###

In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM.
Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.

#### Le conversioni di argomenti non venivano sempre eseguite correttamente ####

Nell'esempio seguente:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Il metodo SendKeys prevede una stringa, ma PowerShell non converte il carattere in una stringa, rinviando la conversione a IDispatch::Invoke che usa VariantChangeType per eseguire la conversione. In questo esempio, ciò ha comportato l'invio di chiavi '1', '7' e '3' anziché la chiave Volume.Mute prevista.

#### Gli oggetti COM enumerabili non venivano sempre gestiti correttamente ####

PowerShell in genere enumera la maggior parte degli oggetti enumerabili, ma una regressione introdotta in WMF 5.0 impediva l'enumerazione di oggetti COM che implementano IEnumerable.  Ad esempio:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Nell'esempio precedente, WMF 5.0 ha scritto in modo errato Scripting.Dictionary nella pipeline anziché enumerare le coppie chiave-valore.


### `[ordered]` non è consentito all'interno delle classi ###

In WMF 5 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi.  `[ordered]` è simile a un valore letterale di tipo, ma non è un tipo .NET.  WMF 5 restituiva erroneamente un errore relativo a `[ordered]` in una classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### Supporto non funzionante sugli argomenti della Guida con più versioni ###

Prima di WMF 5.1, se erano installate più versioni di un modulo e tutte condividevano un argomento della Guida, ad esempio about_PSReadline, `help about_PSReadline` restituiva più argomenti e non era possibile visualizzare la Guida vera e propria.

In WMF 5.1 il problema è stato risolto restituendo la Guida per la versione più recente dell'argomento.

Get-Help non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida. La soluzione alternativa consiste nel passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito. 



<!--HONumber=Sep16_HO3-->


