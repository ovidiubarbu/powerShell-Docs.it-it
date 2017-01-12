---
title: Correzioni di bug in WMF 5.1
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 09316fef0594697a60a1bd4acabf39588f75edc2
ms.sourcegitcommit: f75fc25411ce6a768596d3438e385c43c4f0bf71
translationtype: HT
---
# <a name="bug-fixes-in-wmf-51"></a>Correzioni di bug in WMF 5.1#

## <a name="bug-fixes"></a>Correzioni di bug ##

In WMF 5.1 sono stati corretti i bug importanti seguenti:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Rispetto completo del modulo auto-discovery `$env:PSModulePath` ###

In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando). Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.

WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente. In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Reindirizzamento del file non più come hardcoded `-Encoding Unicode` ###

In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file, ad esempio `Get-ChildItem > out.txt`, perché PowerShell aveva aggiunto `-Encoding Unicode`.

A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Correzione di una regressione nell'accesso dei membri di `System.Reflection.TypeInfo` ###

Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`.
Questo bug è stato corretto in WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Risolti alcuni problemi con gli oggetti COM ###

In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM. Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Le conversioni di argomenti non venivano sempre eseguite correttamente ####

Nell'esempio seguente:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Il metodo SendKeys prevede una stringa, ma PowerShell non converte il carattere in una stringa, rinviando la conversione a IDispatch::Invoke che usa VariantChangeType per eseguire la conversione. In questo esempio, ciò ha comportato l'invio di chiavi '1', '7' e '3' anziché la chiave Volume.Mute prevista.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Gli oggetti COM enumerabili non venivano sempre gestiti correttamente ####

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

Questa modifica riguarda anche i [problemi 1752224 su Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` non è consentito all'interno delle classi ###

In WMF 5.0 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi.  
`[ordered]` è simile a un valore letterale di tipo, ma non è un tipo .NET. WMF 5.0 restituiva erroneamente un errore relativo a `[ordered]` in una classe:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Supporto non funzionante sugli argomenti della Guida con più versioni ###

Prima di WMF 5.1, se erano installate più versioni di un modulo e tutte condividevano un argomento della Guida, ad esempio about_PSReadline, `help about_PSReadline` restituiva più argomenti e non era possibile visualizzare la Guida vera e propria.

In WMF 5.1 il problema è stato risolto restituendo la Guida per la versione più recente dell'argomento.

`Get-Help` non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida. Per risolvere il problema, passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito. 
