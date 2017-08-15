---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Informazioni sulla pipeline di Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a>Informazioni sulla pipeline di Windows PowerShell
Il piping è usato praticamente ovunque in Windows PowerShell. Anche se sullo schermo viene visualizzato del testo, Windows PowerShell non invia tramite pipe testo tra i comandi, bensì oggetti.

La notazione usata per le pipeline è simile a quella usata in altre shell, pertanto, a prima vista, potrebbe non essere evidente che Windows PowerShell stia introducendo qualcosa di nuovo. Se ad esempio si usa il cmdlet **Out-Host** per forzare una visualizzazione pagina per pagina dell'output di un altro comando, l'output avrà lo stesso aspetto del normale testo visualizzato sullo schermo, suddiviso in pagine:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

Il comando Out-Host -Paging è un elemento della pipeline utile in caso di output lungo da visualizzare lentamente. La sua utilità si rivela in particolare se l'operazione richiede un uso elevato della CPU. Dal momento che l'elaborazione viene trasferita al cmdlet Out-Host quando dispone di una pagina completa pronta per la visualizzazione, i cmdlet che lo precedono nella pipeline interrompono l'operazione finché non è disponibile la pagina successiva di output. È possibile vedere questo comportamento se si usa Gestione attività Windows per monitorare l'uso della CPU e della memoria da parte di Windows PowerShell.

Eseguire il comando seguente: **Get-ChildItem C:\\Windows -Recurse**. Confrontare l'uso della CPU e della memoria con questo comando: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**. Quello che si vede sullo schermo è testo, poiché è necessario rappresentare gli oggetti come testo in una finestra della console. Questa è solo una rappresentazione di quello che accade veramente in Windows PowerShell. Si consideri ad esempio il cmdlet Get-Location. Se si digita **Get-Location** mentre il percorso corrente è la radice dell'unità C, verrà visualizzato l'output seguente:

```
PS> Get-Location

Path
----
C:\
```

Se Windows PowerShell ha inviato il testo attraverso una pipe, emettendo un comando come **Get-Location | Out-Host**, passerà da **Get-Location** a **Out-Host** un set di caratteri nell'ordine in cui sono visualizzati sullo schermo. In altre parole, se le informazioni dell'intestazione venissero ignorate, **Out-Host** riceverebbe per prima cosa il carattere "**C"**, quindi il carattere "**:"** e infine il carattere "**\\"**. Il cmdlet **Out-Host** non è in grado di determinare quale significato associare all'output di caratteri del cmdlet **Get-Location**.

Invece di usare del testo per consentire ai comandi in una pipeline di comunicare, Windows PowerShell usa oggetti. Dal punto di vista di un utente, gli oggetti impacchettano le informazioni correlate in un modulo che rende più semplice manipolare le informazioni come unità ed estrarre gli specifici elementi richiesti.

Il comando **Get-Location** non restituisce testo contenente il percorso corrente, ma un pacchetto di informazioni denominato oggetto **PathInfo** che contiene il percorso corrente insieme ad altre informazioni. Il cmdlet **Out-Host** invia quindi questo oggetto **PathInfo** sullo schermo e Windows PowerShell decide quali informazioni visualizzare e come visualizzarle in base alle proprie regole di formattazione.

In realtà, l'output delle informazioni dell'intestazione del cmdlet **Get-Location** viene aggiunto solo alla fine del processo, durante la formattazione dei dati per la visualizzazione sullo schermo. Ciò che compare sullo schermo è un riepilogo delle informazioni e non una rappresentazione completa dell'oggetto di output.

Dato che possono esistere più output di informazioni da un comando di Windows PowerShell rispetto a quelli visualizzati nella finestra della console, in che modo è possibile recuperare gli elementi non visibili? Come si visualizzano i dati aggiuntivi? E cosa accade se si vogliono visualizzare i dati in un formato diverso da quello che Windows PowerShell usa normalmente?

Nel resto di questa sezione viene spiegato come individuare la struttura di oggetti specifici di Windows PowerShell, selezionando elementi specifici e formattandoli per una visualizzazione più semplice, e come inviare queste informazioni a percorsi di output alternativi, ad esempio file e stampanti.

