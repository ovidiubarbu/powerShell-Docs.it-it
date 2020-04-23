---
ms.date: 01/17/2019
keywords: dsc,powershell,configurazione,installazione
title: Riavviare un nodo
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954028"
---
# <a name="reboot-a-node"></a>Riavviare un nodo

> [!NOTE]
> Questo argomento descrive come riavviare un nodo. Per eseguire correttamente il riavvio è necessario configurare correttamente le impostazioni di Gestione configurazione locale **ActionAfterReboot** e **RebootNodeIfNeeded**.
> Per informazioni sulle impostazioni di Gestione configurazione locale, vedere [Configurare Gestione configurazione locale](../managing-nodes/metaConfig.md) o [Configurare Gestione configurazione locale (v4)](../managing-nodes/metaConfig4.md).

I nodi possono essere riavviati all'interno di una risorsa tramite il flag `$global:DSCMachineStatus`. L'impostazione del flag su `1` nella funzione `Set-TargetResource` forza la Gestione configurazione locale a riavviare direttamente il nodo dopo il metodo **Set** della risorsa corrente. Con questo flag, la risorsa **PendingReboot** nel modulo di risorse DSC [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) rileva se un riavvio è in sospeso all'esterno di DSC.

Le [configurazioni](configurations.md) possono eseguire i passaggi che richiedono il riavvio del nodo, tra cui:

- Aggiornamenti di Windows
- Installazione di software
- Ridenominazione dei file
- Ridenominazione del computer

La risorsa **PendingReboot** esegue un controllo in percorsi specifici del computer per determinare se è presente un riavvio in sospeso. Se il nodo richiede un riavvio all'esterno di DSC, la risorsa **PendingReboot** imposta il flag `$global:DSCMachineStatus` su `1` forzando un riavvio e risolvendo la condizione in sospeso.

> [!NOTE]
> Tutte le risorse DSC possono indicare a Gestione configurazione locale di riavviare il nodo impostando questo flag nella funzione `Set-TargetResource`. Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sintassi

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a>Proprietà

| Proprietà | Descrizione |
| --- | --- |
| Nome| Parametro obbligatorio che deve essere univoco per ogni istanza della risorsa all'interno di una configurazione.|
| SkipComponentBasedServicing | Ignorare i riavvii attivati dal modulo di manutenzione pacchetti basato su componenti. |
| SkipWindowsUpdate | Ignorare i riavvii attivati da Windows Update.|
| SkipPendingFileRename | Ignorare i riavvii di ridenominazione file in sospeso. |
| SkipCcmClientSDK | Ignorare i riavvii attivati dal client di ConfigMgr. |
| SkipComputerRename | Ignorare i riavvii attivati dalla ridenominazione del computer. |
| PSDSCRunAsCredential | Supportata v5. Esegue la risorsa con l'utente specificato. |
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. Per altre informazioni, vedere [Uso di DependsOn](resource-depends-on.md)|

## <a name="example"></a>Esempio

L'esempio seguente installa Microsoft Exchange usando la risorsa [xExchange](https://github.com/PowerShell/xExchange).
Durante l'installazione, la risorsa **PendingReboot** viene usata per riavviare il nodo.

> [!NOTE]
> Questo esempio richiede le credenziali di un account che disponga dei diritti per aggiungere un server di Exchange alla foresta. Per altre informazioni sull'uso delle credenziali in DSC, vedere [Gestione delle credenziali in DSC](../configurations/configDataCredentials.md)

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Questo esempio presuppone che Gestione configurazione locale sia configurata per consentire i riavvii e continuare la configurazione dopo il riavvio.

## <a name="where-to-download"></a>Download

È possibile scaricare le risorse usate in questo argomento nei percorsi seguenti o usando PowerShell Gallery.

- [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc)
- [xExchange](https://github.com/PowerShell/xExchange)
