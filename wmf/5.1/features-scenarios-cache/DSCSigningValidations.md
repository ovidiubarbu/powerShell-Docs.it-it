---
title: Convalide delle firme delle configurazioni e dei moduli DSC
author: jaimeo
contributor: berheabra
translationtype: Human Translation
ms.sourcegitcommit: 5c97ca6e93d31aaffc7e2207facc7658ee36dfb4
ms.openlocfilehash: 817fadb79716e41ce8cc8f4245dedc66347ac413

---

##Convalide delle firme delle configurazioni e dei moduli DSC
In DSC i moduli e i documenti di configurazione vengono distribuiti ai computer gestiti dal server o dal servizio di pull, nel caso del servizio di pull di Automazione di Azure. Se il server/servizio di pull è compromesso, un utente malintenzionato potrebbe modificare le configurazioni e i moduli nel server di pull e distribuirli a tutti i computer gestiti del cliente, danneggiandoli. 

 Questa minaccia è stata risolta in WMF 5.1. DSC supporta la convalida delle firme digitali nei moduli e nei file di configurazione (file MOF). Questa funzionalità impedisce che i nodi eseguano configurazioni o file di modulo non firmati da un'entità attendibile o che sono stati manomessi dopo essere stati firmati da un'entità attendibile. 



###Come firmare la configurazione e il modulo 
***
1. File di configurazione (file MOF): il cmdlet di PowerShell esistente [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) supporta ora la firma dei file MOF.  
2. Moduli: la firma dei moduli viene effettuata firmando il catalogo del modulo corrispondente eseguendo i passaggi seguenti: 
    * Creare un file di catalogo: un file di catalogo contiene una raccolta di hash di crittografia o identificazioni personali. Ogni identificazione personale corrisponde a un file incluso nel modulo.  Il nuovo cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) è stato aggiunto per consentire agli utenti di creare un file di catalogo per il modulo. Fare riferimento ai cmdlet di catalogo, [un collegamento](catalog-cmdlets.md) per creare i file di catalogo. 
    * Firmare il file di catalogo: usare [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) per firmare il file di catalogo.
    * Posizionare il file di catalogo all'interno della cartella del modulo.
Per convenzione, il file di catalogo del modulo deve trovarsi nella cartella del modulo con lo stesso nome del modulo.

###Impostazioni LocalConfigurationManager per l'abilitazione delle convalide delle firme

####PULL
La risorsa LocalConfigurationManager di un nodo esegue la convalida delle firme di moduli e configurazioni in base alle impostazioni correnti. Per impostazione predefinita, la convalida delle firme è disabilitata. La convalida delle firme può essere abilitata aggiungendo il blocco 'SignatureValidation' alla definizione della metaconfigurazione del nodo come illustrato di seguito:

```PowerShell
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
        # By default,LCM will use default Windows trusted publisher store to validate the certificate chain. If TrustedStorePath property is specified, LCM will use this custom store for retrieving the trusted publishers to validate the content.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'            
        SignedItemType =  'Configuration','Module'         # Those are list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.       
    }
 
}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose 
 ```

L'impostazione della metaconfigurazione precedente in un nodo abilita la convalida delle firme nelle configurazioni e nei moduli scaricati. La Gestione configurazione locale eseguirà i passaggi seguenti per verificare le firme digitali.
* Verifica che la firma in un file di configurazione (file MOF) sia valida. Usa il cmdlet di PowerShell [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) che è stato esteso nella versione 5.1 per il supporto della convalida delle firme dei file MOF.
* Verifica che l'autorità di certificazione che ha autorizzato il firmatario sia attendibile.
* Scarica le dipendenze del modulo/risorsa della configurazione in un percorso temporaneo.
* Verifica la firma del catalogo incluso all'interno del modulo.
    * Individua un file <moduleName>.cat e ne verifica la firma usando il cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).
    * Verifica che l'autorità di certificazione che ha autenticato il firmatario sia attendibile.
    * Usando il nuovo cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) verifica che il contenuto dei moduli non sia stato manomesso.
* Installa il modulo in $env:ProgramFiles\WindowsPowerShell\Modules\
* Configurazione del processo.

Nota: la convalida della firma nel catalogo del modulo e nella configurazione viene eseguita solo quando la configurazione viene applicata al sistema per la prima volta o quando il modulo viene scaricato e installato. I controlli di coerenza non convalidano la firma di Current.mof o le dipendenze del modulo.
Se la verifica non riesce in una qualsiasi fase, ad esempio se la configurazione di cui viene effettuato il pull dal server di pull non è firmata, l'elaborazione della configurazione verrà terminata con l'errore riportato di seguito e verranno eliminati tutti i file temporanei.

![Configurazione di output degli errori di esempio](../../images/PullUnsignedConfigFail.PNG)

Analogamente, il pull di un modulo il cui catalogo non è firmato causerà l'errore seguente:

![Modulo di output degli errori di esempio](../../images/PullUnisgnedCatalog.PNG)

####PUSH
Una configurazione inviata tramite push potrebbe essere alterata in origine prima di essere recapitata al nodo. La Gestione configurazione locale eseguirà passaggi di convalida della firma simili per le configurazioni di cui è stato effettuato il push o pubblicate.
Di seguito è riportato un esempio completo di convalida della firma per il push.

* Abilitazione della convalida delle firme nel nodo.

```Powershell
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
* Creazione di un file di configurazione di esempio.

```Powershell
# Sample configuration
Configuration Test{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

* Tentativo di push del file di configurazione non firmato nel nodo. 

```Powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
``` 
![ErrorUnsignedMofPushed](../../images/PushUnsignedMof.PNG)

* Firma del file di configurazione con il certificato di firma del codice.

![SignMofFile](../../images/SignMofFile.PNG)

* Tentativo di push del file MOF firmato.

![SignMofFile](../../images/PushSignedMof.PNG)




<!--HONumber=Aug16_HO3-->


