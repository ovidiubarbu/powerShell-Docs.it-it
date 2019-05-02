---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Importare una versione specifica di una risorsa installata
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080001"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importare una versione specifica di una risorsa installata

> Si applica a: Windows PowerShell 5.0

In PowerShell 5.0, in un computer è possibile installare versioni separate di risorse DSC affiancate. Un modulo di risorse può archiviare versioni separate di una risorsa in cartelle denominate in base alla versione.

## <a name="installing-separate-resource-versions-side-by-side"></a>Installazione affiancata di versioni di risorse separate

È possibile usare i parametri **MinimumVersion**, **MaximumVersion** e **RequiredVersion** del cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per specificare la versione di un modulo da installare. La chiamata di **Install-Module** senza specificare una versione installa la versione più recente.

Ad esempio, sono disponibili più versioni del modulo **xFailOverCluster**, ognuna delle quali contiene una risorsa **xCluster**. La chiamata di **Install-Module** senza specificare il numero di versione installa la versione più recente del modulo.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Per installare una versione specifica di un modulo, specificare 1.1.0.0 per **RequiredVersion**. In questo modo la versione specificata viene installata affiancata alla versione installata.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

A questo punto vengono elencate entrambe le versioni del modulo quando si usa `Get-DSCResource`.

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

Se in un computer sono installate più versioni delle risorse, è necessario specificare la versione di tale risorsa quando viene usata in una configurazione. Eseguire questa operazione specificando il parametro **ModuleVersion** della parola chiave **Import-DscResource**. Se non viene specificata la versione di un modulo risorse di una risorsa di cui è installata più di una versione, la configurazione genera un errore.

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

>Nota: il parametro ModuleVersion di Import-DscResource non è disponibile in PowerShell 4.0. In PowerShell 4.0 è possibile specificare una versione del modulo passando un oggetto di specifica del modulo al parametro ModuleName di Import-DscResource. Un oggetto di specifica del modulo è una tabella hash che contiene le chiavi ModuleName e RequiredVersion. Ad esempio:

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
