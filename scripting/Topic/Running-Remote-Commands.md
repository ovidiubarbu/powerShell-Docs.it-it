---
title: Esecuzione di comandi remoti
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
---
# Esecuzione di comandi remoti
È possibile eseguire comandi in uno o in centinaia di computer con un singolo comando di Windows PowerShell. Windows PowerShell supporta l'elaborazione remota tramite varie tecnologie, tra cui WMI, RPC e WS-Management.

## Comunicazione remota senza configurazione
Molti cmdlet di Windows PowerShell hanno un parametro ComputerName che consente di raccogliere dati e cambiare le impostazioni di uno o più computer remoti. Usano un'ampia varietà di tecnologie per le comunicazioni, molte delle quali funzionano in tutti i sistemi operativi Windows supportati da Windows PowerShell senza nessuna configurazione speciale.

Questi cmdlet sono i seguenti:

-   [Restart-Computer](assetId:///bd52bcf6-80ee-4866-9320-04ee1d1dca4a)

-   [Test-Connection](assetId:///87d293e5-10e2-489b-b0a9-922d77c05f3f)

-   [Clear-EventLog](assetId:///05d0de31-3c9d-4cd6-8e1a-dac19835464c)

-   [Get-EventLog [m2]](assetId:///a4372a60-b7d9-4b1c-a268-aa5240300141)

-   [Get-Hotfix](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-Process [m2]](assetId:///27a05dbd-4b69-48a3-8d55-b295f6225f15)

-   [Get-Service [m2]](assetId:///0a09cb22-0a1c-4a79-9851-4e53075f9cf6)

-   [Set-Service [m2]](assetId:///b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

-   [Get-WinEvent](assetId:///e1ef636f-5170-4675-b564-199d9ef6f101)

-   [Get-WmiObject [m2]](assetId:///a4c499fa-deec-4c4b-b3fb-6e195d48a396)

In genere, i cmdlet che supportano la comunicazione remota senza configurazione speciale hanno un parametro ComputerName, mentre non hanno un parametro Session. Per trovare questi cmdlet nella sessione, digitare:

```
get-command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## Comunicazione remota di Windows PowerShell
La comunicazione remota di Windows PowerShell, basata sul protocollo WS-Management, consente di eseguire qualsiasi comando di Windows PowerShell in uno o più computer remoti. È possibile stabilire connessioni permanenti, avviare sessioni interattive 1:1 ed eseguire script in più computer.

Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota. Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd).

Una volta configurata la comunicazione remota di Windows PowerShell, sono disponibili diverse strategie per usarla. Nella parte restante del documento ne verranno descritte alcune. Per altre informazioni, vedere [about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970) e [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42).

### Avviare una sessione interattiva
Per avviare una sessione interattiva con un singolo computer remoto, usare il cmdlet [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c). Ad esempio, per avviare una sessione interattiva con il computer remoto Server01, digitare:

```
enter-pssession Server01
```

Il prompt dei comandi cambia per visualizzare il nome del computer con cui si è connessi. Da questo momento in poi, ogni comando digitato al prompt viene eseguito nel computer remoto e i risultati vengono visualizzati nel computer locale.

Per terminare una sessione interattiva, digitare:

```
exit-pssession
```

Per altre informazioni sui cmdlet Enter-PSSession ed Exit-PSSession, vedere [Enter-PSSession](assetId:///f4fd89b4-80e9-434e-bd46-952aa8d40d4c) ed [Exit-PSSession](assetId:///b6daa1ce-48a5-41a3-ac4b-b64dbe03465d).

### Eseguire un comando remoto
Per eseguire qualsiasi comando in uno o più computer remoti, usare il cmdlet [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462). Ad esempio, per eseguire un comando [Get-UICulture [m2]](assetId:///99175c2e-e856-4208-970e-3dd2f6bac5b8) nei computer remoti Server01 e Server02, digitare:

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

Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Eseguire uno script
Per eseguire uno script in uno o più computer remoti, usare il parametro FilePath del cmdlet Invoke-Command. Lo script deve essere attivo o accessibile sul computer locale. I risultati vengono restituiti al computer locale.

Ad esempio, il comando seguente esegue lo script DiskCollect.ps1 nei computer remoti Server01 e Server02.

```
invoke-command -computername Server01, Server02 -filepath c:\Scripts\DiskCollect.ps1
```

Per altre informazioni sul cmdlet Invoke-Command, vedere [Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462).

### Stabilire una connessione permanente
Per eseguire una serie di comandi correlati che condividono dati, creare una sessione nel computer remoto e quindi usare il cmdlet Invoke-Command per eseguire i comandi nella sessione creata. Per creare una sessione remota, usare il cmdlet New-PSSession.

Ad esempio, il comando seguente crea una sessione remota nel computer Server01 e un'altra nel computer Server02. Gli oggetti sessione vengono salvati nella variabile $s.

```
$s = new-pssession -computername Server01, Server02
```

Una volta stabilite le sessioni, è possibile eseguire qualsiasi comando al loro interno. Inoltre, poiché le sessioni sono permanenti, è possibile raccogliere dati in un comando e usarli in un comando successivo.

Ad esempio, il comando seguente esegue un comando Get-Hotfix nelle sessioni nella variabile $s e salva i risultati nella variabile $h. La variabile $h viene creata in ogni sessione in $s, ma non esiste nella sessione locale.

```
invoke-command -session $s {$h = get-hotfix}
```

A questo punto è possibile usare i dati della variabile $h nei comandi successivi, ad esempio il seguente. I risultati vengono visualizzati nel computer locale.

```
invoke-command -session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"
```

### Comunicazione remota avanzata
La gestione remota di Windows PowerShell ha inizio in questo ambito. Usando i cmdlet installati con Windows PowerShell, è possibile stabilire e configurare sessioni remote dalle estremità locali e remote, creare sessioni personalizzate e con restrizioni, consentire agli utenti di importare comandi da una sessione remota che vengono effettivamente eseguiti in modo implicito nella sessione remota, configurare la sicurezza di una sessione remota e altro ancora.

Per semplificare la configurazione remota, Windows PowerShell include un provider WSMan. L'unità WSMAN: creata dal provider consente di spostarsi in una gerarchia di impostazioni di configurazione nel computer locale e nei computer remoti. Per altre informazioni sul provider WSMan, vedere [WSMan Provider](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735) e [about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed) oppure, nella console di Windows PowerShell, digitare "get-help wsman".

Per altre informazioni, vedere [about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42), [Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25) e [Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d). Per informazioni sugli errori di comunicazione remota, vedere [about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317).

## Vedere anche
[about_Remote](assetId:///9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
[about_Remote_FAQ](assetId:///e23702fd-9415-4a98-9975-390a4d3adc42)
[about_Remote_Requirements](assetId:///da213949-134c-4741-b307-81f4492ba1bd)
[about_Remote_Troubleshooting](assetId:///2f890148-8578-49ed-85ea-79a489dd6317)
[about_PSSessions](assetId:///7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
[about_WS-Management_Cmdlets](assetId:///6ed3370a-ea10-45a5-9493-696aeace27ed)
[Invoke-Command](assetId:///22fd98ba-1874-492e-95a5-c069467b8462)
[Import-PSSession](assetId:///048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
[New-PSSession](assetId:///59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
[Register-PSSessionConfiguration](assetId:///af68867a-d201-4b19-a1de-594015ed8a25)
[Provider WSMan](assetId:///66fe1241-e08f-49ca-832f-a84c33ca8735)



<!--HONumber=Apr16_HO1-->


