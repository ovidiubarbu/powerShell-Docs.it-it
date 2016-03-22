# Protezione del file MOF

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC indica ai nodi di destinazione quale configurazione devono avere inviando un file MOF che contiene queste informazioni a ogni nodo, in cui Gestione configurazione locale implementa la configurazione desiderata. Poiché questo file contiene i dettagli della configurazione, è importante garantirne la sicurezza. A questo scopo, è possibile impostare Gestione configurazione locale per il controllo delle credenziali di un utente. Questo argomento descrive come trasmettere queste credenziali in modo sicuro al nodo di destinazione crittografandole con i certificati.

## Prerequisiti

Per crittografare correttamente le credenziali usate per proteggere una configurazione DSC, assicurarsi di avere a disposizione quanto segue:

* **Uno strumento per l'emissione e la distribuzione dei certificati**. Questo argomento e gli esempi che contiene presuppongono l'uso di Autorità di certificazione Active Directory. Per altre informazioni generali su Servizi certificati Active Directory, vedere [Panoramica di Servizi certificati Active Directory](https://technet.microsoft.com/library/hh831740.aspx) e [Servizi certificati Active Directory in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Accesso amministrativo al nodo o ai nodi di destinazione**.
* **Ogni nodo di destinazione ha un certificato che supporta la crittografia, salvato nel proprio archivio personale**. In Windows PowerShell il percorso di questo archivio è Cert:\LocalMachine\My. Gli esempi in questo argomento usano il modello "Autenticazione workstation", disponibile (insieme ad altri modelli di certificato) in [Modelli di certificato predefiniti](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Se si intende eseguire questa configurazione in un computer diverso dal nodo di destinazione, **esportare la chiave pubblica del certificato** e quindi importarla nel computer da cui verrà eseguita la configurazione. Assicurarsi di esportare solo la chiave **pubblica**, mantenendo protetta quella privata.

## Processo completo

1. Configurare i certificati, le chiavi e le identificazioni personali, verificando che ogni nodo di destinazione abbia copie del certificato e che il computer di configurazione abbia la chiave pubblica e l'identificazione personale.
1. Creare un blocco di dati di configurazione che contenga il percorso e l'identificazione personale della chiave pubblica.
1. Creare uno script di configurazione che definisca la configurazione desiderata per il nodo di destinazione e che configuri la decrittografia nei nodi di destinazione indicando a Gestione configurazione locale di decrittografare i dati di configurazione usando il certificato e l'identificazione personale.
1. Eseguire la configurazione, che specifica le impostazioni di Gestione configurazione locale e avvia la configurazione DSC.

## Dati di configurazione

Il blocco di dati di configurazione definisce i nodi di destinazione su cui operare, se crittografare o meno le credenziali, gli strumenti di crittografia e altre informazioni. Per altre informazioni sul blocco di dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](configData.md).

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

Prima che `Start-DscConfiguration` funzioni correttamente, è necessario indicare a Gestione configurazione locale in ogni nodo di destinazione il certificato da usare per decrittografare le credenziali, usando la risorsa CertificateID per verificare l'identificazione personale del certificato. Questa funzione di esempio trova il certificato locale appropriato e potrebbe dover essere personalizzata perché trovi l'esatto certificato che si vuole usare:

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

* Un file *.meta.mof che configura Gestione configurazione locale per decrittografare le credenziali usando il certificato archiviato nell'archivio del computer locale e indicato dalla relativa identificazione personale. Set-DscLocalConfigurationManager applica il file *.meta.mof.
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
```<!--HONumber=Feb16_HO4-->
