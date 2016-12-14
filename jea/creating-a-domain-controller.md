---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: creazione di un controller di dominio
ms.technology: powershell
ms.openlocfilehash: 80b957ed666ca626c6083041cf99c263e2e0dc27
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="creating-a-domain-controller"></a>Creazione di un controller di dominio

In questo documento si presuppone che il computer faccia parte di un dominio.
Se non esiste un dominio a cui aggiungere il computer, questa sezione spiega come configurare rapidamente un controller di dominio con DSC.

#### <a name="prerequisites"></a>Prerequisiti

1.  Il computer fa parte di una rete interna
2.  Il computer non è associato a un dominio esistente
3.  Il computer esegue Windows Server 2016 o ha WMF 5.0 installato

#### <a name="install-xactivedirectory"></a>Installare xActiveDirectory
Se il computer ha una connessione attiva a Internet, eseguire il comando seguente in una finestra di PowerShell con privilegi elevati:
```PowerShell
Install-Module xActiveDirectory -Force
```
Se non è presente una connessione a Internet, installare xActiveDirectory in un altro computer e quindi copiare la cartella xActiveDirectory nella cartella "C:\Programmi\WindowsPowerShell\Modules" nel computer in uso.

Per verificare se l'installazione ha avuto esito positivo, eseguire il comando seguente:
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a>Configurare un dominio con DSC
Copiare il seguente script di PowerShell per impostare il computer in uso come controller di dominio in un nuovo dominio.
**NOTA DELL'AUTORE: ESISTE UN PROBLEMA NOTO CON LE CREDENZIALI SPECIFICATE E NON UTILIZZATE.  PER SICUREZZA, NON DIMENTICARE LA PASSWORD DI AMMINISTRATORE LOCALE.**

```PowerShell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value $env:COMPUTERNAME -Force

# This "MetaConfiguration" sets the DSC Engine to automatically reboot if required
[DscLocalConfigurationManager()]
Configuration MetaConfiguration
{
    Node $env:Computername
    {
        Settings
        {
            RebootNodeIfNeeded = $true
        }
    }

}

MetaConfiguration
# Apply the MetaConfiguration
Set-DscLocalConfigurationManager .\MetaConfiguration

# Configure a domain controller of a new "Contoso" domain
configuration DomainController
{
    param
    (
        $node,
        $cred
    )
    Import-DscResource -ModuleName xActiveDirectory

    Node $node
    {
        WindowsFeature ADDS
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain Contoso
        {
            DomainName = 'contoso.com'
            DomainAdministratorCredential = $cred
            SafemodeAdministratorPassword = $cred
            DependsOn = '[WindowsFeature]ADDS'
        }

        file temp
        {
            DestinationPath = 'C:\temp.txt'
            Contents = 'Domain has been created'
            DependsOn = '[xADDomain]Contoso'
        }
    }
}

$ConfigData = @{
    AllNodes = @(
        @{
            NodeName = $env:Computername
            PSDscAllowPlainTextPassword = $true
        }
    )
}

# Enter your desired password for the domain administrator (note, this will be stored as plain text)
DomainController -cred (Get-Credential -Message "Enter desired credential for domain administrator") -node $env:Computername -configurationData $ConfigData

# Apply the configuration to create the domain controller
Start-DSCConfiguration -path .\DomainController -ComputerName $env:Computername -Wait -Force -Verbose
```
Il computer verrà riavviato più volte.
Il processo è completato quando viene visualizzato un file denominato "C:\temp.txt" che indica che il dominio è stato creato.

#### <a name="set-up-users-and-groups"></a>Configurare utenti e gruppi
I comandi seguenti consentono di configurare i gruppi Operator e Helpdesk nel dominio e un utente non amministratore corrispondente che è membro dei gruppi.
```PowerShell
# Make Groups
$NonAdminOperatorGroup = New-ADGroup -Name "JEA_NonAdmin_Operator" -GroupScope DomainLocal -PassThru
$NonAdminHelpDeskGroup = New-ADGroup -Name "JEA_NonAdmin_HelpDesk" -GroupScope DomainLocal -PassThru
$TestGroup = New-ADGroup -Name "Test_Group" -GroupScope DomainLocal -PassThru

# Make Users
$OperatorUser = New-ADUser -Name "OperatorUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $OperatorUser

$HelpDeskUser = New-ADUser -name "HelpDeskUser" -AccountPassword (ConvertTo-SecureString 'pa$$w0rd' -AsPlainText -Force) -PassThru
Enable-ADAccount -Identity $HelpDeskUser

# Add Users to Groups
Add-ADGroupMember -Identity $NonAdminOperatorGroup -Members $OperatorUser
Add-ADGroupMember -Identity $NonAdminHelpDeskGroup -Members $HelpDeskUser
```

