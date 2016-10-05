---
title: Protezione del file MOF
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 0dc83a1b69f26a25874c819a2f3a027ed7966895
ms.openlocfilehash: f0aed5bb627825b74fe4df29cbe2f0bc53f90c23

---

# Protezione del file MOF

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC indica ai nodi di destinazione quale configurazione devono avere inviando un file MOF che contiene queste informazioni a ogni nodo, in cui Gestione configurazione locale implementa la configurazione desiderata. Poiché questo file contiene i dettagli della configurazione, è importante garantirne la sicurezza. A tale scopo, è possibile impostare Gestione configurazione locale per verificare le credenziali di un utente. Questo argomento descrive come trasmettere queste credenziali in modo sicuro al nodo di destinazione crittografandole con i certificati.

>**Nota:** questo argomento illustra i certificati usati per la crittografia. Per la crittografia è sufficiente un certificato autofirmato, dal momento che la chiave privata viene sempre mantenuta segreta e la crittografia non implica l'attendibilità del documento. I certificati autofirmati *non* vanno usati a scopo di autenticazione. È consigliabile usare un certificato proveniente da un'Autorità di certificazione attendibile a scopo di autenticazione.

## Prerequisiti

Per crittografare correttamente le credenziali usate per proteggere una configurazione DSC, assicurarsi di avere a disposizione quanto segue:

* **Uno strumento per l'emissione e la distribuzione dei certificati**. Questo argomento e gli esempi che contiene presuppongono l'uso di Autorità di certificazione Active Directory. Per altre informazioni generali su Servizi certificati Active Directory, vedere [Panoramica di Servizi certificati Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Servizi certificati Active Directory in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Accesso amministrativo al nodo o ai nodi di destinazione**.
* **Ogni nodo di destinazione ha un certificato che supporta la crittografia, salvato nel proprio archivio personale**. In Windows PowerShell il percorso di questo archivio è Cert:\LocalMachine\My. Gli esempi in questo argomento usano il modello "Autenticazione workstation", disponibile (insieme ad altri modelli di certificato) in [Modelli di certificato predefiniti](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Se si intende eseguire questa configurazione in un computer diverso dal nodo di destinazione, **esportare la chiave pubblica del certificato** e quindi importarla nel computer da cui verrà eseguita la configurazione. Assicurarsi di esportare solo la chiave **pubblica**, mantenendo protetta quella privata.

## Processo completo

 1. Configurare i certificati, le chiavi e le identificazioni personali, verificando che ogni nodo di destinazione abbia copie del certificato e che il computer di configurazione abbia la chiave pubblica e l'identificazione personale.
 2. Creare un blocco di dati di configurazione che contenga il percorso e l'identificazione personale della chiave pubblica.
 3. Creare uno script di configurazione che definisca la configurazione desiderata per il nodo di destinazione e che configuri la decrittografia nei nodi di destinazione indicando a Gestione configurazione locale di decrittografare i dati di configurazione usando il certificato e l'identificazione personale.
 4. Eseguire la configurazione, che specifica le impostazioni di Gestione configurazione locale e avvia la configurazione DSC.

![Diagram1](images/CredentialEncryptionDiagram1.png)

## Requisiti dei certificati

Per applicare la crittografia delle credenziali, è necessario che un certificato di chiave pubblica sia disponibile nel _nodo di destinazione_ considerato **attendibile** dal computer usato per creare la configurazione DSC.
Questo certificato di chiave pubblica presenta requisiti specifici ai fini dell'uso per la crittografia delle credenziali DSC:
 1. **Utilizzo chiavi**:
   - Deve contenere: 'KeyEncipherment' e 'DataEncipherment'.
   - _Non_ deve contenere: 'Firma digitale'.
 2. **Utilizzo chiavi avanzato**:
   - Deve contenere: Crittografia documento (1.3.6.1.4.1.311.80.1).
   - _Non_ deve contenere: Autenticazione client (1.3.6.1.5.5.7.3.2) e Autenticazione server (1.3.6.1.5.5.7.3.1).
 3. La chiave privata per il certificato è disponibile nel *nodo di destinazione_.
 4. Il **provider** per il certificato deve essere "Microsoft RSA SChannel Cryptographic Provider".
 
>**Procedura consigliata:** è possibile usare un certificato con l'uso di chiavi "Firma digitale" o uno degli EKU di autenticazione, ma in questo modo la chiave di crittografia sarà più esposta a usi non autorizzati o vulnerabile agli attacchi. È consigliabile usare un certificato creato in modo specifico per la protezione delle credenziali DSC che omette questi utilizzi chiave ed EKU.
  
Qualsiasi certificato esistente nel _nodo di destinazione_ che soddisfa questi criteri può essere usato per proteggere le credenziali DSC.

## Creazione di certificati

Esistono due approcci per creare e usare il certificato di crittografia richiesto (coppia di chiavi pubblica/privata).

1. Creare il certificato nel **Nodo di destinazione** ed esportare solo la chiave pubblica nel **Nodo di creazione**.
2. Creare il certificato sul **Nodo di creazione** ed esportare la coppia di chiavi nel **Nodo di destinazione**.

È consigliabile usare il metodo 1 poiché la chiave privata usata per decrittografare le credenziali nel MOF rimane sempre nel nodo di destinazione.


### Creazione del certificato sul nodo di destinazione

La chiave privata deve essere mantenuta segreta poiché viene usata per decrittare il MOF nel **nodo di destinazione**. Il modo più facile per fare ciò è creare il certificato della chiave privata nel **nodo di destinazione** e copiare il **certificato di chiave pubblica** sul computer usato per compilare la configurazione DSC in un file MOF.
L'esempio seguente consente di:
 1. creare un certificato nel **nodo di destinazione**.
 2. esportare il certificato di chiave pubblica nel **nodo di destinazione**.
 3. importare il certificato di chiave pubblica nell'archivio certificati **my** del **nodo di creazione**.

#### Sul nodo di destinazione: creare ed esportare il certificato
>Nodo di creazione: Windows Server 2016 e Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.

>Nodo di creazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti

Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.
In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.

In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
Dopo l'esportazione, ```DscPublicKey.cer``` deve essere copiato nel **nodo di creazione**.

#### Sul nodo di creazione: importare la chiave pubblica del certificato
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### Creazione del certificato sul nodo di creazione
In alternativa, è possibile creare il certificato di crittografia nel **nodo di creazione**, esportarlo con la **chiave privata** come file PFX e quindi importarlo nel **nodo di destinazione**.
Questo è il metodo corrente per l'implementazione della crittografia delle credenziali DSC in _Nano Server_.
Anche se il file PFX è protetto da password, è opportuno mantenere il file in sicurezza durante il trasferimento.
L'esempio seguente consente di:
 1. creare un certificato nel **nodo di creazione**.
 2. esportare il certificato con la chiave privata nel **nodo di creazione**.
 3. rimuove la chiave privata dal **nodo di creazione**, mantenendo il certificato della chiave pubblica nell'archivio **My**.
 4. importare il certificato di chiave privata nell'archivio certificati radice nel **nodo di destinazione**.
   - È necessario aggiungerlo all'archivio radice in modo che risulti attendibile per il **nodo di destinazione**.

#### Sul nodo di creazione: creare ed esportare il certificato
>Nodo di destinazione: Windows Server 2016 e Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```
Dopo l'esportazione, ```DscPrivateKey.cer``` deve essere copiato nel **nodo di destinazione**.

>Nodo di destinazione: Windows Server 2012 R2/Windows 8.1 e versioni precedenti

Poiché il cmdlet New-SelfSignedCertificate nei sistemi operativi Windows precedenti a Windows 10 e Windows Server 2016 non supportano il parametro **Type**, è richiesto un metodo alternativo per creare il certificato in questi sistemi operativi.
In questo caso è possibile usare ```makecert.exe``` o ```certutil.exe``` per creare il certificato.

In alternativa, è possibile [scaricare lo script New-SelfSignedCertificateEx.ps1 da Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) e usarlo per creare il certificato:
```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -StoreName 'My' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### Sul nodo di destinazione: importare la chiave privata del certificato come attendibile
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\Root -Password $mypwd > $null
```

## Dati di configurazione

Il blocco di dati di configurazione definisce i nodi di destinazione su cui operare, se crittografare o meno le credenziali, gli strumenti di crittografia e altre informazioni. Per altre informazioni sul blocco di dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](configData.md).

Gli elementi che possono essere configurati per ogni nodo correlati alla crittografia delle credenziali sono:
* **NodeName** - nome del nodo di destinazione per cui viene configurata la crittografia delle credenziali.
* **PsDscAllowPlainTextPassword** - indica se le credenziali non crittografate potranno essere passate a questo nodo. Si tratta di un'**operazione sconsigliata**.
* **Thumbprint** - identificazione personale del certificato che verrà usato per decrittografare le credenziali nella configurazione DSC nel _nodo di destinazione_. **Questo certificato deve essere presente nell'archivio certificati Computer locale nel nodo di destinazione.**
* **CertificateFile** - file di certificato (contenente solo la chiave pubblica) che deve essere usato per crittografare le credenziali per il _nodo di destinazione_. Deve trattarsi di un file di certificato in formato X.509 binario con codifica DER o X.509 con codifica Base-64.

Questo esempio mostra un blocco di dati di configurazione che specifica un nodo di destinazione su cui operare denominato targetNode, il percorso del file di certificato della chiave pubblica (denominato targetNode.cer) e l'identificazione personale per la chiave pubblica.

```powershell
$ConfigData= @{ 
    AllNodes = @(     
            @{  
                # The name of the node we are describing 
                NodeName = "targetNode" 

                # The path to the .cer file containing the 
                # public key of the Encryption Certificate 
                # used to encrypt credentials for this node 
                CertificateFile = "C:\publicKeys\targetNode.cer" 

         
                # The thumbprint of the Encryption Certificate 
                # used to decrypt the credentials on target node 
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8" 
            }; 
        );    
    }
```


## Script di configurazione

Nello script di configurazione stesso usare il parametro `PsCredential` per specificare che le credenziali devono essere archiviate per il periodo di tempo più breve possibile. Quando si esegue l'esempio fornito, DSC chiede le credenziali e quindi crittografa il file MOF usando la risorsa CertificateFile associata al nodo di destinazione nel blocco di dati di configurazione. Questo esempio di codice copia un file da una condivisione protetta a un utente.

```
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
    } 
}
```

## Configurazione della decrittografia

Prima che [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) funzioni correttamente, è necessario indicare a Gestione configurazione locale in ogni nodo di destinazione il certificato da usare per decrittografare le credenziali, usando la risorsa CertificateID per verificare l'identificazione personale del certificato. Questa funzione di esempio trova il certificato locale appropriato e potrebbe dover essere personalizzata perché trovi l'esatto certificato che si vuole usare:

```powershell
# Get the certificate that works for encryption 
function Get-LocalEncryptionCertificateThumbprint 
{ 
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid 
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify()) 
        { 
            return $_.Thumbprint 
        } 
    } 
}
```

Con il certificato indicato dall'identificazione personale, lo script di configurazione può essere aggiornato in modo da usare il valore:

```powershell
configuration CredentialEncryptionExample 
{ 
    param( 
        [Parameter(Mandatory=$true)] 
        [ValidateNotNullorEmpty()] 
        [PsCredential] $credential 
        ) 
    

    Node $AllNodes.NodeName 
    { 
        File exampleFile 
        { 
            SourcePath = "\\Server\share\path\file.ext" 
            DestinationPath = "C:\destinationPath" 
            Credential = $credential 
        } 
        
        LocalConfigurationManager 
        { 
             CertificateId = $node.Thumbprint 
        } 
    } 
}
```

## Esecuzione della configurazione

A questo punto, è possibile eseguire la configurazione, che genera due file:

 * Un file * .meta.mof che configura Gestione configurazione locale per decrittare le credenziali usando il certificato archiviato nell'archivio del computer locale e indicato dalla relativa identificazione personale. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applica il file *.meta.mof.
 * Un file MOF che applica effettivamente la configurazione. Start-DscConfiguration applica la configurazione.

I comandi seguenti eseguono questi passaggi:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Questo esempio eseguirebbe il push della configurazione DSC al nodo di destinazione.
La configurazione DSC può essere applicata anche tramite un server di pull DSC, se disponibile.

Vedere [Configurazione di un client di pull DSC](pullClient.md) per altre informazioni sull'applicazione delle configurazioni DSC tramite un server di pull DSC.

## Esempio di modulo di crittografia delle credenziali

Ecco un esempio completo che contiene tutti i passaggi, insieme a un cmdlet helper che esporta e copia le chiavi pubbliche:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )
    

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }
        
        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key 
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"         

    $ConfigData=    @{
        AllNodes = @(     
                        @{  
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );    
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration") 

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer") 

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```




<!--HONumber=Aug16_HO3-->


