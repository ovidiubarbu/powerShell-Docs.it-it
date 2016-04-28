# Esecuzione di DSC con le credenziali dell'utente 

> Si applica a: Windows PowerShell 5.0

È possibile eseguire una configurazione DSC con un set di credenziali specificato usando la proprietà **PsDscRunAsCredential** nella configurazione. Per impostazione predefinita, DSC viene eseguito
con le credenziali dell'account di sistema. In alcuni casi può essere necessario eseguirlo con le credenziali di un utente, ad esempio per l'installazione di pacchetti MSI in un contesto utente specifico, l'impostazione delle chiavi del Registro di sistema di un utente,
l'accesso a una directory locale specifica di un utente o l'accesso a una condivisione di rete.

Per ogni risorsa DSC esiste una proprietà **PsDscRunAsCredential** che è possibile impostare su qualsiasi credenziale utente (oggetto [PSCredential](https://msdn.microsoft.com/en-us/library/ms572524(v=VS.85).aspx)).
Le credenziali possono essere hardcoded come valore della proprietà nella configurazione oppure è possibile impostare il valore su [Get-Credential](https://technet.microsoft.com/en-us/library/hh849815.aspx),
in modo da richiedere le credenziali all'utente al momento della compilazione della configurazione. Per informazioni sulla compilazione delle configurazioni, vedere [Configurazioni](configurations.md).

>**Nota:** la proprietà **PsDscRunAsCredential** non è disponibile in PowerShell 4.0.

Nell'esempio seguente **Get-Credential** viene usato per richiedere le credenziali all'utente. La risorsa [Registry](registryResource.md) viene usata per modificare la chiave del Registro di sistema che specifica il colore di sfondo
per la finestra del prompt dei comandi di Windows.

```powershell
Configuration ChangeCmdBackGroundColor    

{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName

    {
        Registry CmdPath

        {

            Key = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = Get-Credential
        }
    }                   
}

$configData = @{

    AllNodes = @(

    @{

        NodeName="localhost";
        PSDscAllowDomainUser = $true
        CertificateFile = "C:\publicKeys\targetNode.cer"
        Thumbprint = "7ee7f09d-4be0-41aa-a47f-96b9e3bdec25"

    })

}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Nota:** in questo esempio si presuppone che sia disponibile un certificato valido in `C:\publicKeys\targetNode.cer` e che l'identificazione personale del certificato sia il valore visualizzato.
>Per informazioni sulla crittografia delle credenziali nei file MOF di configurazione DSC, vedere [Protezione del file MOF](secureMOF.md). 



<!--HONumber=Mar16_HO2-->


