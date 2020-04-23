---
ms.date: 04/11/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un server di pull SMB DSC
ms.openlocfilehash: be41f7a708f1a129919fae8300fc4307441097f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500694"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configurazione di un server di pull SMB DSC

Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità. È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).

Un server di pull [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) DSC è un computer che ospita condivisioni file SMB che rendono disponibili i file di configurazione DSC e le risorse DSC ai nodi di destinazione quando tali nodi li richiedono.

Per usare un server di pull SMB per DSC, è necessario:

- Configurare una condivisione file SMB in un server che esegue PowerShell 4.0 o versione successiva
- Configurare un client che esegue PowerShell 4.0 o versione successiva per effettuare il pull da tale condivisione SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Uso della la risorsa xSmbShare per creare una condivisione file SMB

Esistono diversi modi per configurare una condivisione file SMB, ma ecco come è possibile farlo tramite DSC.

### <a name="install-the-xsmbshare-resource"></a>Installare la risorsa xSmbShare

Chiamare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per installare il modulo **xSmbShare**.

> [!NOTE]
> Il cmdlet `Install-Module` è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0.
> **xSmbShare** contiene la risorsa DSC **xSmbShare**, che può essere usata per creare una condivisione file SMB.

### <a name="create-the-directory-and-file-share"></a>Creare la directory e la condivisione file

La configurazione seguente usa la risorsa **File** per creare la directory per la condivisione e la risorsa **xSmbShare** per configurare la condivisione SMB:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

La configurazione crea la directory `C:\DscSmbShare`, se non esiste già, e quindi usa tale directory come condivisione file SMB. È necessario concedere **FullAccess** a tutti gli account che devono scrivere nella condivisione file o eseguire eliminazioni da questa. È necessario concedere**ReadAccess** a tutti i nodi client che ricevono configurazioni e/o risorse DSC dalla condivisione.

> [!NOTE]
> DSC viene eseguito con l'account di sistema per impostazione predefinita, pertanto il computer stesso deve avere accesso alla condivisione.

### <a name="give-file-system-access-to-the-pull-client"></a>Consentire l'accesso al file system al client di pull

L'assegnazione di **ReadAccess** a un nodo client consente a tale nodo di accedere alla condivisione SMB, ma non a file o cartelle al suo interno. È quindi necessario concedere in modo esplicito ai nodi client l'accesso alla cartella e alle sottocartelle della condivisione SMB. DSC consente tale operazione usando la risorsa **cNtfsPermissionEntry**, contenuta nel modulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).
La configurazione seguente aggiunge un blocco **cNtfsPermissionEntry** che concede l'accesso ReadAndExecute al client di pull:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Inserimento di configurazioni e risorse

Salvare nella condivisione SMB tutti i file MOF di configurazione e/o le risorse DSC che si vuole siano disponibili per il pull dai nodi client.

Qualsiasi file MOF di configurazione deve essere denominato *ConfigurationID.mof*, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione. Per altre informazioni sulla configurazione di client di pull, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).

> [!NOTE]
> Se si usa un server di pull SMB, è necessario usare gli ID di configurazione. I nomi di configurazione non sono supportati per SMB.

Ogni modulo di risorse deve essere compresso e denominato in base alla convenzione seguente `{Module Name}_{Module Version}.zip`. Ad esempio, un modulo denominato xWebAdminstration con versione 3.1.2.0 verrebbe denominato 'xWebAdministration_3.2.1.0.zip'. Ogni versione di un modulo deve essere contenuta in un unico file ZIP. Non sono supportate versioni distinte di un modulo in un file ZIP.
Prima di creare un pacchetto per i moduli delle risorse DSC da usare con il server di pull è necessario apportare una piccola modifica alla struttura di directory.

Il formato predefinito dei moduli contenenti risorse DSC in WMF 5.0 è `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Prima creare il pacchetto per il server di pull, rimuovere semplicemente la cartella `{Module version}` in modo il percorso diventi `{Module Folder}\DscResources\{DSC Resource Folder}\`. Con questa modifica, comprimere la cartella come descritto in precedenza e collocare i file ZIP nella cartella di condivisione SMB.

## <a name="creating-the-mof-checksum"></a>Creazione del checksum per il file MOF

Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione. Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum). Il cmdlet accetta un parametro `Path` che specifica la cartella in cui si trova il file MOF di configurazione. Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione. Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.

Il file di checksum deve essere presente nella stessa directory del file MOF di configurazione (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` per impostazione predefinita) e avere lo stesso nome, con estensione `.checksum`.

> [!NOTE]
> Se si modifica il file MOF di configurazione in qualsiasi modo, è anche necessario ricreare il file di checksum.

## <a name="setting-up-a-pull-client-for-smb"></a>Impostazione di un client di pull per SMB

Per impostare un client che esegue il pull di configurazioni e/o di risorse da una condivisione SMB, configurare Gestione configurazione locale con i blocchi **ConfigurationRepositoryShare** e **ResourceRepositoryShare** che specificano la condivisione da cui eseguire il pull di configurazioni e risorse DSC.

Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).

> [!NOTE]
> Per semplicità, questo esempio usa **PSDscAllowPlainTextPassword** per consentire il passaggio di una password non crittografata al parametro **Credential**. Per informazioni sul passaggio di credenziali in modo più sicuro, vedere [Opzioni delle credenziali nei dati di configurazione](../configurations/configDataCredentials.md). È **necessario** specificare **ConfigurationID** nel blocco **Impostazioni** di una metaconfigurazione per un server di pull SMB, anche se si esegue solo il pull di risorse.

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Riconoscimenti

Un ringraziamento speciale per:

- Mike F. Robbins, i cui post sull'uso di SMB per DSC hanno aiutato a comporre il contenuto in questo argomento. Il suo blog è [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, che ha creato il modulo **cNtfsAccessControl**. L'origine per questo modulo è in [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Vedere anche

[Panoramica di PowerShell DSC](../overview/overview.md)

[Applicazione delle configurazioni](enactingConfigurations.md)

[Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md)
