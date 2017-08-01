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
ms.translationtype: HT
ms.contentlocale: it-IT
---
### <a name="creating-a-domain-controller"></a><span data-ttu-id="8a9f9-103">Creazione di un controller di dominio</span><span class="sxs-lookup"><span data-stu-id="8a9f9-103">Creating a Domain Controller</span></span>

<span data-ttu-id="8a9f9-104">In questo documento si presuppone che il computer faccia parte di un dominio.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-104">This document assumes that your machine is domain joined.</span></span>
<span data-ttu-id="8a9f9-105">Se non esiste un dominio a cui aggiungere il computer, questa sezione spiega come configurare rapidamente un controller di dominio con DSC.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-105">If you currently don't have a domain to join, this section can help you quickly stand up a domain controller using DSC.</span></span>

#### <a name="prerequisites"></a><span data-ttu-id="8a9f9-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8a9f9-106">Prerequisites</span></span>

1.  <span data-ttu-id="8a9f9-107">Il computer fa parte di una rete interna</span><span class="sxs-lookup"><span data-stu-id="8a9f9-107">The machine is on an internal network</span></span>
2.  <span data-ttu-id="8a9f9-108">Il computer non è associato a un dominio esistente</span><span class="sxs-lookup"><span data-stu-id="8a9f9-108">The machine is not joined to an existing domain</span></span>
3.  <span data-ttu-id="8a9f9-109">Il computer esegue Windows Server 2016 o ha WMF 5.0 installato</span><span class="sxs-lookup"><span data-stu-id="8a9f9-109">The machine is running Windows Server 2016 or has WMF 5.0 installed</span></span>

#### <a name="install-xactivedirectory"></a><span data-ttu-id="8a9f9-110">Installare xActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="8a9f9-110">Install xActiveDirectory</span></span>
<span data-ttu-id="8a9f9-111">Se il computer ha una connessione attiva a Internet, eseguire il comando seguente in una finestra di PowerShell con privilegi elevati:</span><span class="sxs-lookup"><span data-stu-id="8a9f9-111">If your machine has an active internet connection, run the following command in an elevated PowerShell window:</span></span>
```PowerShell
Install-Module xActiveDirectory -Force
```
<span data-ttu-id="8a9f9-112">Se non è presente una connessione a Internet, installare xActiveDirectory in un altro computer e quindi copiare la cartella xActiveDirectory nella cartella "C:\Programmi\WindowsPowerShell\Modules" nel computer in uso.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-112">If you do not have an internet connection, install xActiveDirectory to another machine and then copy the xActiveDirectory folder to the "C:\Program Files\WindowsPowerShell\Modules" folder on your machine.</span></span>

<span data-ttu-id="8a9f9-113">Per verificare se l'installazione ha avuto esito positivo, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="8a9f9-113">To confirm the installation succeeded, run the following command:</span></span>
```PowerShell
Get-Module xActiveDirectory -ListAvailable
```

#### <a name="set-up-a-domain-with-dsc"></a><span data-ttu-id="8a9f9-114">Configurare un dominio con DSC</span><span class="sxs-lookup"><span data-stu-id="8a9f9-114">Set up a domain with DSC</span></span>
<span data-ttu-id="8a9f9-115">Copiare il seguente script di PowerShell per impostare il computer in uso come controller di dominio in un nuovo dominio.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-115">Copy the following script in PowerShell to make your machine a Domain Controller in a new domain.</span></span>
<span data-ttu-id="8a9f9-116">**NOTA DELL'AUTORE: ESISTE UN PROBLEMA NOTO CON LE CREDENZIALI SPECIFICATE E NON UTILIZZATE.  PER SICUREZZA, NON DIMENTICARE LA PASSWORD DI AMMINISTRATORE LOCALE.**</span><span class="sxs-lookup"><span data-stu-id="8a9f9-116">**AUTHOR'S NOTE: THERE IS A KNOWN ISSUE WITH THE CREDENTIALS PROVIDED NOT BEING USED.  TO BE SAFE, DON'T FORGET YOUR LOCAL ADMIN PASSWORD.**</span></span>

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
<span data-ttu-id="8a9f9-117">Il computer verrà riavviato più volte.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-117">Your machine will restart a few times.</span></span>
<span data-ttu-id="8a9f9-118">Il processo è completato quando viene visualizzato un file denominato "C:\temp.txt" che indica che il dominio è stato creato.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-118">You will know the process is complete once you see a file called "C:\temp.txt" containing "Domain has been created."</span></span>

#### <a name="set-up-users-and-groups"></a><span data-ttu-id="8a9f9-119">Configurare utenti e gruppi</span><span class="sxs-lookup"><span data-stu-id="8a9f9-119">Set up Users and Groups</span></span>
<span data-ttu-id="8a9f9-120">I comandi seguenti consentono di configurare i gruppi Operator e Helpdesk nel dominio e un utente non amministratore corrispondente che è membro dei gruppi.</span><span class="sxs-lookup"><span data-stu-id="8a9f9-120">The following commands will set up an Operator and Helpdesk group in your domain and a corresponding non-administrator user who is a member of that group.</span></span>
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

