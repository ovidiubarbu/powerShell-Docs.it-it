---
title:  Esecuzione di comandi remoti
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---

# Esecuzione di comandi remoti
È possibile eseguire comandi in uno o in centinaia di computer con un singolo comando di Windows PowerShell. Windows PowerShell supporta l'elaborazione remota grazie all'uso di varie tecnologie, tra cui WMI, RPC e WS\-Management.

## Comunicazione remota senza configurazione
Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e cambiare le impostazioni di uno o più computer remoti. Usano un'ampia varietà di tecnologie per le comunicazioni, molte delle quali funzionano in tutti i sistemi operativi Windows supportati da Windows PowerShell senza nessuna configurazione speciale.

Questi cmdlet sono i seguenti:

-   [Restart-Computer](https://technet.microsoft.com/en-us/library/dd315301.aspx)

-   [Test-Connection](https://technet.microsoft.com/en-us/library/dd315259.aspx)

-   [Clear-EventLog](https://technet.microsoft.com/en-us/library/dd347552.aspx)

-   [Get-EventLog](https://technet.microsoft.com/en-us/library/dd315250.aspx)

-   [Get-Hotfix](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process](https://technet.microsoft.com/en-us/library/dd347630.aspx)

-   [Get-Service](https://technet.microsoft.com/en-us/library/dd347591.aspx)

-   [Set-Service](https://technet.microsoft.com/en-us/library/dd315324.aspx)

-   [Get-WinEvent](https://technet.microsoft.com/en-us/library/dd315358.aspx)

-   [Get-WmiObject](https://technet.microsoft.com/en-us/library/dd315295.aspx)

In genere, i cmdlet che supportano la comunicazione remota senza configurazione speciale hanno un parametro ComputerName, mentre non hanno un parametro Session. Per trovare questi cmdlet nella sessione, digitare:

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Comunicazione remota di Windows PowerShell
La comunicazione remota di Windows PowerShell, basata sul protocollo WS\-Management, consente di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti. È possibile stabilire connessioni permanenti, avviare sessioni interattive 1:1 ed eseguire script in più computer.

Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota. Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).

Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla. Nella parte restante del documento ne verranno descritte alcune. Per altre informazioni, vedere [about_Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) e [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).

### Avviare una sessione interattiva
Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx). Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:

```
enter-pssession Server01
```

Il prompt dei comandi cambia per visualizzare il nome del computer con cui si è connessi. Da questo momento in poi, ogni comando digitato al prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.

Per terminare una sessione interattiva, digitare:

```
exit-pssession
```

Per altre informazioni sui cmdlet Enter\-PSSession e Exit\-PSSession, vedere [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) ed [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).

### Eseguire un comando remoto
Per eseguire qualsiasi comando in uno o più computer remoti, usare il cmdlet [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).
Ad esempio, per eseguire un comando [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) nei computer remoti Server01 e Server02, digitare:

```
invoke-command -computername Server01, Server02 {get-UICulture}
```

L'output viene restituito nel computer locale.

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

Per altre informazioni sul cmdlet Invoke\-Command, vedere [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).

### Eseguire uno script
Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet Invoke\-Command. Lo script deve essere attivo o accessibile sul computer locale. I risultati vengono restituiti al computer locale.

Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Per altre informazioni sul cmdlet Invoke\-Command, vedere [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).

### Stabilire una connessione permanente
Per eseguire una serie di comandi correlati che condividono dati, creare una sessione nel computer remoto e quindi usare il cmdlet Invoke\-Command per eseguire i comandi nella sessione creata. Per creare una sessione remota, usare il cmdlet New\-PSSession.

Ad esempio, il comando seguente crea una sessione remota nel computer Server01 e un'altra nel computer Server02. Gli oggetti sessione vengono salvati nella variabile $s.

```
$s = new-pssession -computername Server01, Server02
```

Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno. Inoltre, poiché le sessioni sono permanenti, è possibile raccogliere dati in un comando e usarli in un comando successivo.

Ad esempio, il comando seguente esegue un comando Get\-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h. La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.

```
invoke-command -session $s {$h = get-hotfix}
```

A questo punto è possibile usare i dati della variabile $h nei comandi successivi, ad esempio il seguente. I risultati vengono visualizzati nel computer locale.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"} }
```

### Comunicazione remota avanzata
La gestione remota di Windows PowerShell ha inizio in questo ambito. Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.

Per semplificare la configurazione remota, Windows PowerShell include un provider WSMan. L'unità WSMAN: creata dal provider consente di spostarsi in una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti.
Per altre informazioni sul provider di WS-Management, vedere [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) (Provider di WS-Management) e   [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) oppure digitare "get\-help wsman" nella console di Windows PowerShell.

Per altre informazioni, vedere:
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx). 

Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).

## Vedere anche
- [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [Import-PSSession](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [New-PSSession](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [Provider WSMan](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=May16_HO4-->


