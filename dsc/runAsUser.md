---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Esecuzione di DSC con le credenziali dell'utente
ms.openlocfilehash: 37e6ff64c9c6d3960653d417e22a6c93c653230c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="running-dsc-with-user-credentials"></a>Esecuzione di DSC con le credenziali dell'utente

> Si applica a: Windows PowerShell 5.0, Windows PowerShell 5.1

È possibile eseguire una risorsa DSC con un set di credenziali specificato usando la proprietà **PsDscRunAsCredential** nella configurazione.
Per impostazione predefinita, DSC esegue ogni risorsa come account di sistema.
In alcuni casi può essere necessario eseguirla con le credenziali di un utente, ad esempio quando si installano pacchetti MSI in un contesto utente specifico, si impostano le chiavi del Registro di sistema di un utente, si accede a una directory locale specifica dell'utente o si accede a una condivisione di rete.

Ogni risorsa DSC ha una proprietà **PsDscRunAsCredential** che può essere impostare su qualsiasi credenziale utente (oggetto [PSCredential](https://msdn.microsoft.com/library/ms572524(v=VS.85).aspx)).
Le credenziali possono essere hardcoded come il valore della proprietà nella configurazione oppure è possibile impostare il valore su [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx), che chiederà all'utente le credenziali in fase di compilazione della configurazione. Per informazioni sulla compilazione di configurazioni, vedere [Configurazioni DSC](configurations.md).

>**Nota:** In PowerShell 5.0 non è supportato l'uso della proprietà **PsDscRunAsCredential** nelle configurazioni che chiamano risorse composite.
>In PowerShell 5.1 la proprietà **PsDscRunAsCredential** è supportata nelle configurazioni che chiamano risorse composite.

>**Nota**: la proprietà **PsDscRunAsCredential** non è disponibile in PowerShell 4.0.

Nell'esempio seguente **Get-Credential** viene usato per richiedere le credenziali all'utente.
La risorsa [Registry](registryResource.md) viene usata per modificare la chiave del Registro di sistema che specifica il colore di sfondo della finestra del prompt dei comandi di Windows.

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```
>**Nota**: in questo esempio si presuppone che sia disponibile un certificato valido in `C:\publicKeys\targetNode.cer` e che l'identificazione personale del certificato sia il valore visualizzato.
>Per informazioni sulla crittografia delle credenziali nei file MOF della configurazione DSC, vedere [Protezione del file MOF](secureMOF.md).