---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: Esecuzione di comandi remoti
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401951"
---
# <a name="running-remote-commands"></a>Esecuzione di comandi remoti

È possibile eseguire comandi in uno o centinaia di computer con un unico comando di PowerShell. Windows PowerShell supporta l'elaborazione remota tramite varie tecnologie, tra cui WMI, RPC e WS-Management.

PowerShell Core supporta WMI, WS-Management e la comunicazione remota SSH. RPC non è più supportato.

Per altre informazioni sulla comunicazione remota in PowerShell Core, vedere gli articoli seguenti:

- [SSH Remoting in PowerShell Core][ssh-remoting] (Comunicazione remota SSH in PowerShell Core)
- [WSMan Remoting in PowerShell Core][wsman-remoting] (Comunicazione remota WS-Management in PowerShell Core)

## <a name="windows-powershell-remoting-without-configuration"></a>Comunicazione remota di Windows PowerShell senza configurazione

Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e modificare le impostazioni di uno o più computer remoti. Questi cmdlet usano diversi protocolli di comunicazione e sono supportati in tutti i sistemi operativi senza alcuna configurazione speciale.

Questi cmdlet sono i seguenti:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

In genere, i cmdlet che supportano la comunicazione remota senza configurazioni speciali includono il parametro ComputerName e non includono invece il parametro Session. Per trovare questi cmdlet nella sessione, digitare:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicazione remota di Windows PowerShell

Usando il protocollo WS-Management, la comunicazione remota di Windows PowerShell permette di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti. È possibile stabilire connessioni permanenti, avviare sessioni interattive ed eseguire script in computer remoti.

Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.
Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla.
Questo articolo ne indica solo alcune. Per altre informazioni, vedere [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

### <a name="start-an-interactive-session"></a>Avviare una sessione interattiva

Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).
Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:

```powershell
Enter-PSSession Server01
```

Il prompt dei comandi cambia per visualizzare il nome del computer remoto. Qualsiasi comando digitato nel prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.

Per terminare una sessione interattiva, digitare:

```powershell
Exit-PSSession
```

Per altre informazioni sui cmdlet Enter-PSSession ed Exit-PSSession, vedere:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Eseguire un comando remoto

Per eseguire un comando in uno o più computer, usare il cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command). Ad esempio, per eseguire un comando [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) nei computer remoti Server01 e Server02, digitare:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

L'output viene restituito nel computer locale.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Eseguire uno script

Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet `Invoke-Command`. Lo script deve essere attivo o accessibile sul computer locale. I risultati vengono restituiti al computer locale.

Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Stabilire una connessione permanente

Usare il cmdlet `New-PSSession` per creare una sessione permanente in un computer remoto. L'esempio seguente crea sessioni remote in Server01 e Server02. Gli oggetti sessione vengono archiviati nella variabile `$s`.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno. Poiché le sessioni sono permanenti, è possibile raccogliere dati da un comando e usarli in un altro comando.

Ad esempio, il comando seguente esegue un comando Get-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h. La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

È ora possibile usare i dati nella variabile `$h` con altri comandi nella stessa sessione. I risultati vengono visualizzati nel computer locale. Ad esempio:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicazione remota avanzata

La gestione remota di Windows PowerShell ha inizio in questo ambito. Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.

Windows PowerShell include un provider WSMan. Il provider crea un'unità `WSMAN:` che permette di spostarsi all'interno di una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti.

Per altre informazioni sul provider WSMan, vedere [Provider WSMan](https://technet.microsoft.com/library/dd819476.aspx) e [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets) (Informazioni sui cmdlet WS-Management) oppure digitare `Get-Help wsman` nella console di Windows PowerShell.

Per altre informazioni, vedere:

- [about_Remote_FAQ](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Vedere anche

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Provider WSMan](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md