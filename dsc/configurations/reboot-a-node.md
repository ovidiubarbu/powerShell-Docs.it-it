---
ms.date: 1/17/2019
keywords: dsc,powershell,configurazione,installazione
title: Riavviare un nodo
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680742"
---
# <a name="reboot-a-node"></a>Riavviare un nodo

> [!NOTE]
> In questo argomento descrive come riavviare un nodo. Affinché il riavvio venga portato a termine il **ActionAfterReboot** e **RebootNodeIfNeeded** è necessario configurare correttamente le impostazioni di Gestione configurazione locale.
> Per altre informazioni sulle impostazioni di Gestione configurazione locale, vedere [configurare Gestione configurazione locale](../managing-nodes/metaConfig.md), o [configurare Gestione configurazione locale (v4)](../managing-nodes/metaConfig4.md).

I nodi possono essere riavviati all'interno di una risorsa, tramite il `$global:DSCMachineStatus` flag. Impostando questo flag su `1` nella `Set-TargetResource` forza la funzione LCM riavviare il nodo direttamente dopo il **impostare** metodo della risorsa corrente. Usare questo flag, il **xPendingReboot** risorse rileva se è in sospeso un riavvio all'esterno di DSC.

I [configurazioni](configurations.md) può eseguire i passaggi che richiedono il nodo da riavviare. Potrebbe trattarsi di operazioni, ad esempio:

- Windows: aggiornamenti
- Installazione del software
- Rinomina file
- Ridenominazione del computer

Il **xPendingReboot** risorsa controlli dei computer specifici per determinare se un riavvio in sospeso. Se il nodo richiede un riavvio all'esterno di DSC, il **xPendingReboot** set di risorse di `$global:DSCMachineStatus` flag `1` forzare un riavvio e risolvendo la condizione in sospeso.

> [!NOTE]
> Qualsiasi risorsa DSC può indicare a Gestione configurazione locale per riavviare il nodo impostando questo flag `Set-TargetResource` (funzione). Per altre informazioni, vedere [scrittura di una risorsa DSC personalizzata con MOF](../resources/authoringResourceMOF.md).

## <a name="syntax"></a>Sintassi

```
xPendingReboot [String] #ResourceName
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

| Proprietà | Description |
| --- | --- |
| Nome| Parametro obbligatorio che deve essere univoco per ogni istanza della risorsa all'interno di una configurazione.|
| SkipComponentBasedServicing | Riavvii Skip attivati dal componente di manutenzione pacchetti basato su componenti. |
| SkipWindowsUpdate | Riavvii Skip attivati da Windows Update.|
| SkipPendingFileRename | Ignorare i riavvii di ridenominazione di file in sospeso. |
| SkipCcmClientSDK | Riavvii Skip attivati dal client di Configuration Manager. |
| SkipComputerRename | Skip riavvia precedentemente per le operazioni di ridenominazione di Computer. |
| PSDSCRunAsCredential | Supportato in v5. Viene eseguita la risorsa con l'utente specificato. |
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. Per altre informazioni, vedere [usando DependsOn](resource-depends-on.md)|

## <a name="example"></a>Esempio

L'esempio seguente installa Microsoft Exchange tramite i [xExchange](https://github.com/PowerShell/xExchange) risorsa.
Durante l'installazione, il **xPendingReboot** risorsa viene usata per riavviare il nodo.

> [!NOTE]
> Questo esempio richiede le credenziali di un account che disponga dei diritti per aggiungere un server di Exchange della foresta. Per altre informazioni sull'uso delle credenziali in DSC, vedere [gestione delle credenziali in DSC](../configurations/configDataCredentials.md)

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> Questo esempio si presuppone di aver configurato la gestione configurazione locale per consentire i riavvii e continuare la configurazione dopo il riavvio.

## <a name="where-to-download"></a>Come scaricare

È possibile scaricare le risorse usate in questo argomento nei percorsi seguenti o usando PowerShell gallery.

- [xPendingReboot](https://github.com/PowerShell/xPendingReboot)
- [xExchange](https://github.com/PowerShell/xExchange)
