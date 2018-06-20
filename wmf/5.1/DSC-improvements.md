---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Miglioramenti di DSC in WMF 5.1
ms.openlocfilehash: 32bdde6d43d17cc76c454fe10b00097753a9eebe
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309543"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a>Miglioramenti di Desired State Configuration (DSC) in WMF 5.1

## <a name="dsc-class-resource-improvements"></a>Miglioramenti delle risorse di classe DSC

In WMF 5.1 sono stati corretti i problemi noti seguenti:

- Get-DscConfiguration può restituire valori vuoti (null) o errori se la funzione Get() di una risorsa DSC basata su classe restituisce un tipo complesso/Hashtable.
- Get-DscConfiguration restituisce un errore se nella configurazione DSC vengono usate le credenziali RunAs.
- La risorsa basata su classe non può essere usata in una configurazione composita.
- Start-DscConfiguration si blocca se la risorsa basata su classe ha una proprietà di tipo specifico.
- La risorsa basata su classe non può essere usata come risorsa esclusiva.

## <a name="dsc-resource-debugging-improvements"></a>Miglioramenti del debug delle risorse DSC

In WMF 5.0 il debugger di PowerShell non si arrestava in corrispondenza del metodo della risorsa basata su classe (Get/Set/Test).
In WMF 5.1 il debugger si arresta in corrispondenza del metodo della risorsa basata su classe nello stesso modo in cui si arresta per i metodi delle risorse basate su MOF.

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a>Il client di pull DSC supporta TLS 1.1 e TLS 1.2

In precedenza, il client di pull DSC supportava solo SSL3.0 e TLS1.0 su connessioni HTTPS.
Quando era necessario usare protocolli più sicuri, il client di pull smetteva di funzionare.
In WMF 5.1 il client di pull DSC non supporta più SSL 3.0 e aggiunge il supporto dei protocolli TLS 1.1 e TLS 1.2 più sicuri.

## <a name="improved-pull-server-registration"></a>Miglioramento della registrazione del server di pull

Nelle versioni precedenti di WMF le richieste di registrazione o reporting simultanee al server di pull DSC, con uso del database ESENT, facevano sì che la gestione della configurazione locale non riuscisse a eseguire la registrazione o il reporting.
In questi casi, nei log eventi del server di pull viene visualizzato il messaggio di errore "Nome istanza già in uso".
Ciò era dovuto a un modello errato che veniva usato per accedere al database ESENT in uno scenario multithread.
In WMF 5.1 questo problema è stato risolto.
Il reporting o le registrazioni simultanee, che comprendono l'uso del database ESENT, funzionano correttamente in WMF 5.1.
Tutto questo si applica solo al database ESENT, non al database OLE DB.

## <a name="enable-circular-log-on-esent-database-instance"></a>Abilitare il log circolare nell'istanza di database ESENT

Nella versione precedente di DSC-PullServer, i file di log del database ESENT riempiono lo spazio su disco del server di pull perché l'istanza del database viene creata senza registrazione circolare. In questa versione è possibile controllare il comportamento di registrazione circolare dell'istanza usando il file web.config del server di pull. Per impostazione predefinita, CircularLogging è impostato su TRUE.

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a>Convenzione di denominazione della configurazione parziale pull

Nella versione precedente la convenzione di denominazione di una configurazione parziale prevedeva che il nome del file MOF del servizio o del server pull corrispondesse al nome della configurazione parziale specificato nelle impostazioni di Gestione configurazione locale che doveva a sua volta corrispondere al nome di configurazione incorporato nel file MOF.

Vedere gli snapshot seguenti:

- Impostazioni della configurazione locale che definisce una configurazione parziale che un nodo è autorizzato a ricevere.

![Metaconfigurazione di esempio](../images/MetaConfigPartialOne.png)

- Definizione di configurazione parziale di esempio

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- 'ConfigurationName' incorporato nel file MOF generato.

![Esempio di file MOF generato](../images/PartialGeneratedMof.png)

- FileName nel repository di configurazione pull

![FileName nel repository di configurazione](../images/PartialInConfigRepository.png)

File MOF del nome del servizio di automazione di Azure generati come `<ConfigurationName>.<NodeName>.mof`.
La configurazione seguente viene compilata in PartialOne.localhost.mof.

Questo rendeva impossibile l'esecuzione del pull di una configurazione parziale dal servizio di automazione di Azure.

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

In WMF 5.1 una configurazione parziale nel server di pull/servizio può essere denominata `<ConfigurationName>.<NodeName>.mof`.
Inoltre, se un computer effettua il pull di una configurazione singola da un server di pull/servizio, il file di configurazione nel repository di configurazione del server pull potrà avere qualsiasi nome file.
Questa flessibilità di denominazione consente la gestione parziale dei nodi da parte del servizio di Automazione di Azure, dove parte della configurazione deriva da Automation DSC di Azure e una configurazione parziale viene gestita localmente.

La metaconfigurazione seguente imposta un nodo che viene gestito sia localmente che dal servizio di Automazione di Azure.

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a>Usare PsDscRunAsCredential con le risorse composite DSC

È stato aggiunto il supporto per l'uso di [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) con le risorse [composite](https://msdn.microsoft.com/en-us/powershell/dsc/authoringresourcecomposite) DSC.

È ora possibile specificare un valore per PsDscRunAsCredential quando si usano risorse composite all'interno delle configurazioni.
Quando specificato, tutte le risorse vengono eseguite all'interno di una risorsa composita come utente RunAs.
Se una risorsa composita chiama un'altra risorsa composita, tutte le relative risorse vengono eseguite come utente RunAs.
Le credenziali RunAs vengono propagate a tutti i livelli della gerarchia di risorse composite.
Se una risorsa all'interno di una risorsa composita specifica un valore per PsDscRunAsCredential, durante la compilazione della configurazione si verifica un errore di merge.

Questo esempio mostra l'uso con la risorsa composita [WindowsFeatureSet](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_newresources) inclusa nel modulo PSDesiredStateConfiguration.

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a>Convalide delle firme delle configurazioni e dei moduli DSC

In DSC le configurazioni e i moduli vengono distribuiti dal server di pull a computer gestiti.
Se il server di pull è compromesso, un utente malintenzionato potrebbe modificare le configurazioni e i moduli nel server di pull e distribuirli a tutti i nodi gestiti danneggiandoli.

In WMF 5.1 DSC supporta la convalida delle firme digitali su file di catalogo e configurazione (file MOF).
Questa funzionalità impedisce che i nodi eseguano configurazioni o file di modulo non firmati da un'entità attendibile o manomessi dopo essere stati firmati da un'entità attendibile.

### <a name="how-to-sign-configuration-and-module"></a>Come firmare la configurazione e il modulo

***
* File di configurazione (.MOFs): il cmdlet di PowerShell esistente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) supporta ora la firma dei file MOF.
* Moduli: la firma dei moduli viene effettuata firmando il catalogo del modulo corrispondente eseguendo i passaggi seguenti:
    1. Creare un file di catalogo: un file di catalogo contiene una raccolta di hash di crittografia o identificazioni personali.
       Ogni identificazione personale corrisponde a un file incluso nel modulo.
       Il nuovo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) è stato aggiunto per consentire agli utenti di creare un file di catalogo per il modulo.
    2. Firmare il file di catalogo: usare [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) per firmare il file di catalogo.
    3. Posizionare il file di catalogo all'interno della cartella del modulo.
Per convenzione, il file di catalogo del modulo deve trovarsi nella cartella del modulo con lo stesso nome di quest'ultimo.

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a>Impostazioni LocalConfigurationManager per l'abilitazione delle convalide delle firme

#### <a name="pull"></a>Pull

La risorsa LocalConfigurationManager di un nodo esegue la convalida delle firme di moduli e configurazioni in base alle impostazioni correnti.
Per impostazione predefinita, la convalida delle firme è disabilitata.
La convalida delle firme può essere abilitata aggiungendo il blocco 'SignatureValidation' alla definizione della metaconfigurazione del nodo, come illustrato di seguito:

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

L'impostazione della metaconfigurazione precedente in un nodo abilita la convalida delle firme nelle configurazioni e nei moduli scaricati.
Gestione configurazione locale esegue i passaggi seguenti per verificare le firme digitali.

1. Verifica che la firma in un file di configurazione (file MOF) sia valida.
   Usa il cmdlet di PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) che è stato esteso nella versione 5.1 per il supporto della convalida delle firme dei file MOF.
2. Verifica che l'autorità di certificazione che ha autorizzato il firmatario sia attendibile.
3. Scarica le dipendenze del modulo/risorsa della configurazione in un percorso temporaneo.
4. Verifica la firma del catalogo incluso all'interno del modulo.
    * Individua un file `<moduleName>.cat` e ne verifica la firma usando il cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Verifica che l'autorità di certificazione che ha autenticato il firmatario sia attendibile.
    * Usando il nuovo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) verifica che il contenuto dei moduli non sia stato manomesso.
5. Installa il modulo in $env:ProgramFiles\WindowsPowerShell\Modules\
6. Configurazione del processo

> Nota: la convalida della firma nel catalogo del modulo e nella configurazione viene eseguita solo quando la configurazione viene applicata al sistema per la prima volta o quando il modulo viene scaricato e installato.
I controlli di coerenza non convalidano la firma di Current.mof o le dipendenze del modulo.
Se la verifica ha esito negativo in una fase, ad esempio se la configurazione di cui viene eseguito il pull dal server di pull non è firmata, l'elaborazione della configurazione viene terminata con l'errore riportato di seguito e vengono eliminati tutti i file temporanei.

![Configurazione di output degli errori di esempio](../images/PullUnsignedConfigFail.png)

Analogamente, il pull di un modulo il cui catalogo non è firmato causa l'errore seguente:

![Modulo di output degli errori di esempio](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a>Push

Una configurazione inviata mediante push potrebbe essere alterata in origine prima che venga recapitata al nodo.
Gestione configurazione locale esegue passaggi di convalida della firma simili per le configurazioni pubblicate o di cui è stato eseguito il push.
Di seguito è riportato un esempio completo di convalida della firma per il push.

- Abilitazione della convalida delle firme nel nodo.

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- Creazione di un file di configurazione di esempio.

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- Tentativo di push del file di configurazione non firmato nel nodo.

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- Firma del file di configurazione con il certificato di firma del codice.

![SignMofFile](../images/SignMofFile.png)

- Tentativo di push del file MOF firmato.

![SignMofFile](../images/PushSignedMof.png)
