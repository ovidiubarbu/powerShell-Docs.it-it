---
title: Bug risolti in WMF 5.1 (anteprima)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 90d57af0c8b90e709769525455ae39557b9c7176

---

# Bug risolti in WMF 5.1 (anteprima)#

## Correzioni di bug ##

In WMF 5.1 sono stati corretti i bug importanti seguenti:

### Rispetto completo del modulo auto-discovery `$env:PSModulePath` ###

In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando). Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.

WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente. In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.

### Reindirizzamento del file non più come hardcoded `-Encoding Unicode` ###

In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file, ad esempio `get-childitem > out.txt` perché PowerShell aveva aggiunto `-Encoding Unicode`.

A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`, ad esempio

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### Correzione di una regressione nell'accesso dei membri di `System.Reflection.TypeInfo` ###

Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`.
Questo bug è stato risolto in WMF 5.1.


### Risolti alcuni problemi con gli oggetti COM ###

In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM.
Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.

#### Le conversioni di argomenti non venivano sempre eseguite correttamente ####

Nell'esempio seguente:

```
$obj = new-object -com wscript.shell
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

Questa modifica concerne anche i [problemi 1752224 su Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### `[ordered]` non è consentito all'interno delle classi ###

In WMF 5 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi.  `[ordered]` è simile a un valore letterale di tipo ma non è un tipo .Net.  WMF 5 restituiva erroneamente un errore relativo a `[ordered]` in una classe:

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

Get-Help non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida. Per risolvere il problema, passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito. 



<!--HONumber=Jul16_HO3-->


