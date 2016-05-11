# Uso di DSC in Nano Server

> Si applica a: Windows PowerShell 5.0

**DSC su Nano Server** è un pacchetto opzionale contenuto nella cartella `NanoServer\Packages` del supporto Windows Server 2016. Il pacchetto può essere installato quando si crea un disco rigido virtuale per un Nano Server
specificando **Microsoft-NanoServer-DSC-Package** come valore del parametro **Packages** della funzione**New-NanoServerImage**. Ad esempio, se si sta creando un disco rigido virtuale per una macchina
virtuale, il comando sarebbe simile al seguente:

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Per informazioni sull'installazione e l'uso di Nano Server, nonché su come gestire Nano Server con la comunicazione remota di PowerShell, vedere 
[Guida introduttiva a Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx).


## Funzionalità DSC disponibili su Nano Server

 Poiché Nano Server supporta solo un set limitato di API rispetto a una versione completa di Windows Server, al momento DSC in Nano server non dispone di parità funzionale completa con DSC in esecuzione 
 su SKU completi. DSC in Nano server è in fase di sviluppo attivo e non è ancora completo di tutte le funzionalità.
 
 Le funzionalità DSC seguenti sono attualmente disponibili in Nano Server: 


* Modalità push e pull
* Tutti i cmdlet DSC presenti in una versione completa di Windows Server, inclusi i seguenti: 
  * [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx)
  * [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)
        
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
    
* Configurazioni di compilazione (vedere [Configurazioni DSC](configurations.md))
* Metaconfigurazioni di compilazione (vedere [Configurazione di Gestione configurazione locale](metaConfig.md))
* [Esecuzione di DSC con le credenziali dell'utente (RunAs)](runAsUser.md)
* Risorse basate su classi (vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md))
* [Specifica delle dipendenze tra nodi](crossNodeDependencies.md) 
* [Controllo delle versioni delle risorse](sxsResource.md)
* Eventi
* Client di pull, configurazione e risorse (vedere [Configurazione di un client di pull usando nomi di configurazione](pullClientConfigNames.md))
* [Configurazioni parziali (pull e push)](partialConfigs.md)
* [Reporting to pull server (Segnalazione a un server di pull)](reportServer.md) 
* Crittografia MOF
* Registrazione degli eventi
* Creazione di report DSC di Automazione di Azure


* Risorse che funzionano
  * [Archive](archiveResource.md)
  * [Environment](environmentResource.md)
  * [File](fileResource.md)
  * [Gruppo](groupResource.md)
  * GroupSet
  * [Log](logResource.md)
  * ProcessSet
  * [Registro di sistema](registryResource.md)
  * [Servizio](serviceResource.md)
  * ServiceSet
  * [Script](scriptResource.md)
  * [Utente](userResource.md)
  * WindowsPackageCab
  * [WindowsProcess](windowsProcessResource.md)

  * WaitForAll (vedere [Specifying cross-node dependencies](crossNodeDependencies.md) Specifica delle dipendenze tra nodi))
  * WaitForAny (vedere [Specifying cross-node dependencies](crossNodeDependencies.md) Specifica delle dipendenze tra nodi))
  * WaitForSome (vedere [Specifying cross-node dependencies](crossNodeDependencies.md) Specifica delle dipendenze tra nodi))

## Funzionalità DSC non disponibili su Nano Server

Le funzionalità DSC seguenti sono attualmente non disponibili in Nano Server:

* Server di pull: attualmente non è possibile impostare un server di pull su Nano Server
* Tutte le funzioni non presenti nel relativo elenco sono disponibili

## Uso di risorse DSC personalizzate su Nano Server
 
A causa di un set limitato di API Windows e alle librerie CLR disponibili in Nano Server, le risorse DSC che funzionano sulla versione CLR completa di Windows non funzionano necessariamente anche su Nano server. 
Eseguire un test completo prima di distribuire le risorse DSC personalizzate in un ambiente di produzione.

## Vedere anche
- [Guida introduttiva a Nano Server](https://technet.microsoft.com/en-us/library/mt126167.aspx)

<!--HONumber=Apr16_HO4-->


