---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Miglioramenti della console in WMF 5.1
ms.openlocfilehash: fb689002caf42203d760f11acc64e52cfa681069
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189313"
---
# <a name="console-improvements-in-wmf-51"></a>Miglioramenti della console in WMF 5.1#

## <a name="powershell-console-improvements"></a>Miglioramenti apportati alla console di PowerShell

Per migliorare l'uso della console, sono state apportate a powershell.exe in WMF 5.1 le modifiche seguenti:

###<a name="vt100-support"></a>Supporto per VT100

Windows 10 ha aggiunto il supporto per le [sequenze di escape VT100](https://msdn.microsoft.com/en-us/library/windows/desktop/mt638032(v=vs.85).aspx).
Quando si calcola la larghezza delle tabelle, PowerShell ignorerà determinate sequenze di escape di formattazione VT100.

PowerShell ha inoltre aggiunto una nuova API che può essere usata per la formattazione di codice in modo da determinare se VT100 è supportato.
Ad esempio:

```
if ($host.UI.SupportsVirtualTerminal)
{
    $esc = [char]0x1b
    "A yellow ${esc}[93mhello${esc}[0m"
}
else
{
    "A default hello"
}
```
Ecco un [esempio](https://gist.github.com/lzybkr/dcb973dccd54900b67783c48083c28f7) completo che può essere usato per evidenziare le corrispondenze di Select-String.
Salvare l'esempio in un file denominato `MatchInfo.format.ps1xml` quindi per usarlo, nel profilo o altrove, eseguire `Update-FormatData -Prepend MatchInfo.format.ps1xml`.

Si noti che le sequenze di escape VT100 sono supportate solo a partire dall'aggiornamento Aniversary di Windows 10. Non sono supportate nei sistemi precedenti.

### <a name="vi-mode-support-in-psreadline"></a>Supporto della modalità vi in PSReadline

[PSReadline](https://github.com/lzybkr/PSReadLine) aggiunge il supporto per la modalità vi. Per usare la modalità vi, eseguire `Set-PSReadlineOption -EditMode Vi`.

### <a name="redirected-stdin-with-interactive-input"></a>Stdin reindirizzato con input interattivo

Nelle versioni precedenti, veniva richiesto l'avvio di PowerShell con `powershell -File -` quando stdin veniva reindirizzato e si volevano immettere i comandi in modo interattivo.

Con WMF 5.1, questa opzione di difficile individuazione non è più necessaria.
È possibile avviare PowerShell senza opzioni, ad esempio `powershell`.

Si noti che PSReadline al momento non supporta stdin reindirizzato e la funzionalità di modifica della riga di comando integrata con stdin reindirizzato è estremamente limitata, ad esempio non è possibile usare i tasti di direzione.
Questo problema verrà risolto nella versione successiva di PSReadline.
