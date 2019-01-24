---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Nano Server
ms.openlocfilehash: fd81fe56d16100f45d9ee2dfd8fdc303c2a6c17a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401435"
---
# <a name="using-dsc-on-nano-server"></a>Uso di DSC in Nano Server

> Si applica a: Windows PowerShell 5.0

**DSC on Nano Server** (DSC su Nano Server) è un pacchetto opzionale contenuto nella cartella `NanoServer\Packages` del supporto Windows Server 2016. Il pacchetto può essere installato durante la creazione di un disco rigido virtuale per un Nano Server, specificando **Microsoft-NanoServer-DSC-Package** come valore del parametro **Packages** della funzione**New-NanoServerImage**. Se ad esempio si sta creando un disco rigido virtuale per una macchina virtuale, il comando potrebbe essere simile al seguente:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Per informazioni sull'installazione e l'uso di Nano Server e su come gestire Nano Server con la comunicazione remota di PowerShell, vedere [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server) (Guida introduttiva a Nano Server).

## <a name="dsc-features-available-on-nano-server"></a>Funzionalità DSC disponibili su Nano Server

Poiché Nano Server supporta solo un set limitato di API rispetto a una versione completa di Windows Server, al momento DSC on Nano Server (DSC su Nano Server) non offre parità funzionale completa con DSC in esecuzione su SKU completi. DSC on Nano Server (DSC su Nano Server) è in fase di sviluppo attivo e non è ancora completo di tutte le funzionalità.

Le funzionalità DSC seguenti sono attualmente disponibili in Nano Server:

Modalità push e pull

- Tutti i cmdlet DSC presenti in una versione completa di Windows Server, inclusi i seguenti:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguraiton](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- Compilazione di configurazioni. Vedere [Configurazioni DSC](../configurations/configurations.md)

  **Problema #1629** La crittografia delle password (vedere [protezione del File MOF](../pull-server/secureMOF.md)) durante la configurazione di compilazione non funziona.

- Compilazione di metaconfigurazioni. Vedere [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)

- Esecuzione di una risorsa nel contesto utente. Vedere [Esecuzione di DSC con le credenziali dell'utente](../configurations/runAsUser.md)

- Risorse basate su classi. Vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](../resources/authoringResourceClass.md)

- Debug di risorse DSC. Vedere [Debug di risorse DSC](../troubleshooting/debugResource.md)

  **Problema #1629** Non funziona se una risorsa Usa PsDscRunAsCredential (vedere [esecuzione di DSC con le credenziali utente](../configurations/runAsUser.md))

- [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)

- [Controllo delle versioni delle risorse](../configurations/sxsResource.md)

- Client di pull, configurazione e risorse. Vedere [Configurazione di un client di pull usando nomi di configurazione](../pull-server/pullClientConfigNames.md)

- [Configurazioni parziali (pull e push)](../pull-server/partialConfigs.md)

- [Segnalazione a un server di pull](../pull-server/reportServer.md)

- Crittografia MOF

- Registrazione degli eventi

- Creazione di report DSC di Automazione di Azure

- Risorse completamente funzionanti

- **Archive**
- **Environment**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)
- **WaitForAny**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)
- **WaitForSome**. Vedere [Specifica delle dipendenze tra nodi](../configurations/crossNodeDependencies.md)

- Risorse parzialmente funzionanti
- **Gruppo**
- **GroupSet**

  **Problema #1629** Le risorse indicate sopra non riuscire se l'istanza specifica viene chiamato due volte (in esecuzione la stessa configurazione di due volte)

- **Service**
- **ServiceSet**

  **Problema #1629** Funziona solo per avvio/arresto del servizio (stato). Non funziona se si tenta di modificare altri attributi del servizi, come startuptype, credentials, description e così via. L'errore generato è simile al seguente:

  *Impossibile trovare il tipo [management.managementobject]: verificare che l'assembly contenente questo tipo sia caricato.*

- Risorse non funzionanti
- **User**

## <a name="dsc-features-not-available-on-nano-server"></a>Funzionalità DSC non disponibili su Nano Server

Le funzionalità DSC seguenti sono attualmente non disponibili in Nano Server:

- Decrittografia del documento MOF con password crittografate
- Server di pull: attualmente non è possibile impostare un server di pull su Nano Server
- Tutte le funzioni non presenti nel relativo elenco sono disponibili

## <a name="using-custom-dsc-resources-on-nano-server"></a>Uso di risorse DSC personalizzate su Nano Server

A causa di un set limitato di API Windows e alle librerie CLR disponibili in Nano Server, le risorse DSC che funzionano sulla versione CLR completa di Windows non funzionano necessariamente anche su Nano server.
Eseguire un test completo prima di distribuire le risorse DSC personalizzate in un ambiente di produzione.

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva a Nano Server](/windows-server/get-started/getting-started-with-nano-server)