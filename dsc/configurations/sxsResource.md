---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Importare una versione specifica di una risorsa installata
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401170"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importare una versione specifica di una risorsa installata

> Si applica a: Windows PowerShell 5.0

In PowerShell 5.0, versioni distinte di risorse DSC possono essere installate in un computer fianco a fianco. Un modulo di risorse è possibile archiviare versioni distinte di una risorsa nella versione cartelle denominate.

## <a name="installing-separate-resource-versions-side-by-side"></a>Installazione di risorse separati versioni affiancate

È possibile usare i parametri **MinimumVersion**, **MaximumVersion** e **RequiredVersion** del cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per specificare la versione di un modulo da installare. La chiamata di **Install-Module** senza specificare una versione installa la versione più recente.

Ad esempio, sono disponibili più versioni del modulo **xFailOverCluster**, ognuna delle quali contiene una risorsa **xCluster**. La chiamata **Install-Module** senza specificare la versione numero consente di installare la versione più recente del modulo.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Per installare una versione specifica di un modulo, specificare una **RequiredVersion** di 1.1.0.0. Questo consente di installare la versione specificata side la versione installata.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Ora, noterete entrambi versione del modulo elencato quando si usa `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Specifica di una versione delle risorse in una configurazione

Se si dispone di versioni di risorse distinto installate in un computer, è necessario specificare la versione di tale risorsa quando viene utilizzata in una configurazione. Eseguire questa operazione specificando il parametro **ModuleVersion** della parola chiave **Import-DscResource**. Se non viene specificata la versione di un modulo risorse di una risorsa di cui è installata più di una versione, la configurazione genera un errore.

La configurazione seguente mostra come specificare la versione della risorsa da chiamare:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Nota: Il parametro ModuleVersion di Import-DscResource non è disponibile in PowerShell 4.0. In PowerShell 4.0 è possibile specificare una versione del modulo passando un oggetto di specifica del modulo al parametro ModuleName di Import-DscResource. Un oggetto di specifica del modulo è una tabella hash che contiene le chiavi ModuleName e RequiredVersion. Ad esempio:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

l'oggetto funziona anche in PowerShell 5.0, ma è consigliabile usare il parametro **ModuleVersion**.

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Risorse DSC](../resources/resources.md)
