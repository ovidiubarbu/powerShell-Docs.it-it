---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Correzioni di bug in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147851"
---
# <a name="bug-fixes-in-wmf-51"></a>Correzioni di bug in WMF 5.1

## <a name="bug-fixes"></a>Correzioni di bug

In WMF 5.1 sono stati corretti i bug importanti seguenti:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Rispetto completo del modulo auto-discovery PSModulePath

In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando). Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.

WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente. In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Il reindirizzamento di file non usa più -Encoding Unicode hardcoded

In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file.

A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Correzione di una regressione nell'accesso dei membri di System.Reflection.TypeInfo

Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`. Questo bug è stato corretto in WMF 5.1.

### <a name="fixed-some-issues-with-com-objects"></a>Risolti alcuni problemi con gli oggetti COM

In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM. Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Le conversioni di argomenti non venivano sempre eseguite correttamente

Nell'esempio seguente:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

Il metodo **SendKeys** prevede una stringa, ma PowerShell non converte il carattere in una stringa, rinviando la conversione a **IDispatch::Invoke** che usa **VariantChangeType** per eseguire la conversione. In questo esempio, il risultato è l'invio delle chiavi '1', '7' e '3' invece della chiave **Volume.Mute** prevista.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Gli oggetti COM enumerabili non venivano sempre gestiti correttamente

PowerShell in genere enumera la maggior parte degli oggetti enumerabili, ma una regressione introdotta in WMF 5.0 impediva l'enumerazione di oggetti COM che implementano IEnumerable. Ad esempio:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

Nell'esempio precedente, WMF 5.0 ha scritto in modo errato **Scripting.Dictionary** nella pipeline anziché enumerare le coppie chiave-valore.

### <a name="ordered-was-not-allowed-inside-classes"></a>[ordered] non è consentito all'interno delle classi

In WMF 5.0 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi. `[ordered]` è simile a un valore letterale di tipo, ma non è un tipo .NET. WMF 5.0 restituiva erroneamente un errore relativo a `[ordered]` in una classe:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Supporto non funzionante sugli argomenti della Guida con più versioni

Prima di WMF 5.1, se erano installate più versioni di un modulo e tutte condividevano un argomento della Guida, ad esempio about_PSReadline, `help about_PSReadline` restituiva più argomenti e non era possibile visualizzare la Guida vera e propria.

In WMF 5.1 il problema è stato risolto restituendo la Guida per la versione più recente dell'argomento.

`Get-Help` non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida. Per risolvere il problema, passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>La lettura di PowerShell.exe da STDIN non funziona più

I clienti usano `powershell -command -` da app native per eseguire PowerShell passandolo nello script tramite STDIN. Purtroppo questa funzionalità non è più disponibile a causa di altri modifiche nell'host della console.

Questo problema è stato risolto per la versione 5.1 in Windows 10 Anniversary Update.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe crea picchi di utilizzo della CPU all'avvio

PowerShell usa una query WMI per controllare se è stato avviato tramite Criteri di gruppo per evitare di causare ritardi nella fase di accesso. Ne risulta che la query WMI inserisce tzres.mui.dll in ogni processo nel sistema, perché la classe WMI **Win32_Process** tenta di recuperare informazioni sul fuso orario locale. Ciò comporta un notevole picco di utilizzo della CPU in **wmiprvse** (host del provider WMI). La soluzione consiste nell'usare chiamate all'API Win32 per ottenere le stesse informazioni invece di usare WMI.
