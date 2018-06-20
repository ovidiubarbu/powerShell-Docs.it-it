---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Uso di DSC in Nano Server
ms.openlocfilehash: 9e26c525b48e8656a3479db9c0a760eaeb8cf58a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190248"
---
# <a name="using-dsc-on-nano-server"></a>Uso di DSC in Nano Server

> Si applica a: Windows PowerShell 5.0

**DSC on Nano Server** (DSC su Nano Server) è un pacchetto opzionale contenuto nella cartella `NanoServer\Packages` del supporto Windows Server 2016. Il pacchetto può essere installato durante la creazione di un disco rigido virtuale per un Nano Server, specificando **Microsoft-NanoServer-DSC-Package** come valore del parametro **Packages** della funzione**New-NanoServerImage**. Se ad esempio si sta creando un disco rigido virtuale per una macchina virtuale, il comando potrebbe essere simile al seguente:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Per informazioni sull'installazione e l'uso di Nano Server e su come gestire Nano Server con la comunicazione remota di PowerShell, vedere [Getting Started with Nano Server](https://technet.microsoft.com/library/mt126167.aspx) (Guida introduttiva a Nano Server).


## <a name="dsc-features-available-on-nano-server"></a>Funzionalità DSC disponibili su Nano Server

 Poiché Nano Server supporta solo un set limitato di API rispetto a una versione completa di Windows Server, al momento DSC on Nano Server (DSC su Nano Server) non offre parità funzionale completa con DSC in esecuzione su SKU completi. DSC on Nano Server (DSC su Nano Server) è in fase di sviluppo attivo e non è ancora completo di tutte le funzionalità.

 Le funzionalità DSC seguenti sono attualmente disponibili in Nano Server:


* Modalità push e pull

* Tutti i cmdlet DSC presenti in una versione completa di Windows Server, inclusi i seguenti:
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn521621.aspx)
  * [Enable-DscDebug](https://technet.microsoft.com/en-us/library/mt517870.aspx)
  * [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx)
  * [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx)
  * [Stop-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143542.aspx)
  * [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx)
  * [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx)
  * [Publish-DscConfiguraiton](https://technet.microsoft.com/en-us/library/mt517875.aspx)
  * [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx)
  * [Restore-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407383.aspx)
  * [Remove-DscConfigurationDocument](https://technet.microsoft.com/en-us/library/mt143544.aspx)
  * [Get-DscConfigurationStatus](https://technet.microsoft.com/en-us/library/mt517868.aspx)
  * [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx)
  * [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
  * [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)
  * [New-DscChecksum](https://technet.microsoft.com/en-us/library/dn521622.aspx)

* Compilazione di configurazioni. Vedere [Configurazioni DSC](configurations.md)

  **Problema:** la crittografia delle password durante la compilazione della configurazione non funziona. Vedere [Protezione del file MOF](securemof.md)

* Compilazione di metaconfigurazioni. Vedere [Configurazione di Gestione configurazione locale](metaConfig.md)

* Esecuzione di una risorsa nel contesto utente. Vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)

* Risorse basate su classi. Vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)

* Debug di risorse DSC. Vedere [Debug di risorse DSC](debugresource.md)

  **Problema:** non funziona se una risorsa usa PsDscRunAsCredential. Vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)

* [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

* [Controllo delle versioni delle risorse](sxsResource.md)

* Client di pull, configurazione e risorse. Vedere [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md)

* [Configurazioni parziali (pull e push)](partialConfigs.md)

* [Segnalazione a un server di pull](reportServer.md)

* Crittografia MOF

* Registrazione degli eventi

* Creazione di report DSC di Automazione di Azure

* Risorse completamente funzionanti
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Log](logResource.md)
  * ProcessSet
  * [Registry](registryResource.md)
  * [Script](scriptResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)
  * WaitForAll. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)
  * WaitForAny. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)
  * WaitForSome. Vedere [Specifica delle dipendenze tra nodi](crossNodeDependencies.md)

* Risorse parzialmente funzionanti
  * [Gruppo](groupResource.md)
  * GroupSet

  **Problema:** le risorse indicate sopra non funzionano se l'istanza specifica viene chiamata due volte, vale a dire se la stessa configurazione viene eseguita due volte

  * [Service](serviceResource.md)
  * ServiceSet

  **Problema:** funziona solo per l'avvio/arresto del servizio (stato). Non funziona se si tenta di modificare altri attributi del servizi, come startuptype, credentials, description e così via. L'errore generato è simile al seguente:

  *Impossibile trovare il tipo [management.managementobject]: verificare che l'assembly contenente questo tipo sia caricato.*

* Risorse non funzionanti
  * [User](userResource.md)


## <a name="dsc-features-not-available-on-nano-server"></a>Funzionalità DSC non disponibili su Nano Server

Le funzionalità DSC seguenti sono attualmente non disponibili in Nano Server:

* Decrittografia del documento MOF con password crittografate
* Server di pull: attualmente non è possibile impostare un server di pull su Nano Server
* Tutte le funzioni non presenti nel relativo elenco sono disponibili

## <a name="using-custom-dsc-resources-on-nano-server"></a>Uso di risorse DSC personalizzate su Nano Server

A causa di un set limitato di API Windows e alle librerie CLR disponibili in Nano Server, le risorse DSC che funzionano sulla versione CLR completa di Windows non funzionano necessariamente anche su Nano server.
Eseguire un test completo prima di distribuire le risorse DSC personalizzate in un ambiente di produzione.

## <a name="see-also"></a>Vedere anche
- [Guida introduttiva a Nano Server](https://technet.microsoft.com/library/mt126167.aspx)