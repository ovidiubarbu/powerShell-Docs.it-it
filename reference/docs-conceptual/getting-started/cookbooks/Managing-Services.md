---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Gestione dei servizi
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 9fd6c8bcfecc99756188409629ddf94b880aab91
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="managing-services"></a>Gestione dei servizi
Sono disponibili otto cmdlet Service principali, progettati per una vasta gamma di attività dei servizi. Verranno esaminati solo l'elenco e la modifica dello stato di esecuzione dei servizi, ma è possibile ottenere un elenco di cmdlet Service usando **Get-Help \&#42;-Service**, oltre a trovare informazioni sui diversi cmdlet Service con **Get-Help<Cmdlet-Name>**, ad esempio **Get-Help New-Service**.

## <a name="getting-services"></a>Ottenere servizi
È possibile ottenere servizi in un computer locale o remoto usando il cmdlet **Get-Service**. Come con **Get-Process**, l'uso del comando **Get-Service** senza parametri restituisce tutti i servizi. È possibile filtrare per nome, usando anche un asterisco come carattere jolly:

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Poiché non è sempre ovvio quale sia il nome effettivo di un servizio, potrebbe essere necessario individuare i servizi in base al nome visualizzato. È possibile farlo usando il nome specifico, caratteri jolly o un elenco di nomi visualizzati:

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

Il parametro ComputerName del cmdlet Get-Service può essere usato per ottenere servizi in computer remoti. Il parametro ComputerName accetta più valori e i caratteri jolly, pertanto è possibile recuperare i servizi di più computer con un unico comando. Il comando seguente ottiene ad esempio i servizi nel computer remoto Server01.

```
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Ottenere i servizi richiesti e dipendenti
Il cmdlet Get-Service include due parametri molto utili per l'amministrazione dei servizi. Il parametro DependentServices ottiene i servizi che dipendono dal servizio. Il parametro RequiredServices ottiene i servizi da cui dipende questo servizio.

Questi parametri visualizzano solo i valori delle proprietà DependentServices e ServicesDependedOn (alias=RequiredServices) dell'oggetto System.ServiceProcess.ServiceController restituito da Get-Service, ma semplificano i comandi e rendono più semplice ottenere queste informazioni.

Il comando seguente ottiene i servizi richiesti dal servizio LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Il comando seguente ottiene i servizi che richiedono il servizio LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

È anche possibile ottenere tutti i servizi che hanno dipendenze. Il comando seguente ha proprio questo scopo e usa il cmdlet Format-Table per visualizzare le proprietà Status, Name, RequiredServices e DependentServices dei servizi nel computer.

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Arresto, avvio, sospensione e riavvio di servizi
I cmdlet Service hanno tutti lo stesso formato generale. I servizi possono essere specificati in base al nome comune o al nome visualizzato e accettano elenchi e caratteri jolly come valori. Per arrestare lo spooler di stampa, usare:

```
Stop-Service -Name spooler
```

Per avviare lo spooler di stampa dopo che è stato arrestato, usare:

```
Start-Service -Name spooler
```

Per sospendere lo spooler di stampa, usare:

```
Suspend-Service -Name spooler
```

Il cmdlet **Restart-Service** funziona esattamente come gli altri cmdlet Service, ma di seguito sono disponibili alcuni esempi più complessi. Il suo uso più semplice prevede che venga specificato il nome del servizio:

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Si noterà che viene visualizzato un messaggio di avviso ripetuto sull'avvio dello spooler di stampa. Quando si esegue un'operazione di servizio che richiede un certo tempo, Windows PowerShell notificherà all'utente che sta ancora tentando di eseguire l'attività.

Per riavviare più servizi, è possibile ottenere un elenco di servizi, filtrarli e quindi eseguire il riavvio:

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Questi cmdlet Service non hanno un parametro ComputerName, ma è possibile eseguirli in un computer remoto usando il cmdlet Invoke-Command. Il comando seguente riavvia ad esempio il servizio Spooler nel computer remoto Server01.

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Impostazione delle proprietà dei servizi
Il cmdlet Set-Service consente di modificare le proprietà di un servizio in un computer locale o remoto. Poiché lo stato del servizio è una proprietà, è possibile usare questo cmdlet per avviare, arrestare e sospendere un servizio. Il cmdlet Set-Service ha anche un parametro StartupType che consente di modificare il tipo di avvio del servizio.

Per usare Set-Service in Windows Vista e versioni successive di Windows, aprire Windows PowerShell con l'opzione "Esegui come amministratore".

Per altre informazioni, vedere [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3).

## <a name="see-also"></a>Vedere anche
- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)

