---
title:   Uso di risorse con più versioni
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Uso di risorse con più versioni

> Si applica a: Windows PowerShell 5.0

In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side. Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.

## Installazione di più versioni delle risorse side-by-side

È possibile usare i parametri **MinimumVersion**, **MaximumVersion** e **RequiredVersion** del cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) per specificare la versione di un modulo da installare. La chiamata di **Install-Module** senza specificare una versione installa la versione più recente.

Ad esempio, sono disponibili più versioni del modulo **xFailOverCluster**, ognuno dei quali contiene una risorsa **xCluster**. Il risultato della chiamata di **Install-Module** senza specificare il numero della versione è il seguente:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Se si chiama nuovamente **Install-Module**, ma si specifica una **RequiredVersion** di 1.1.0.0, si verifica quanto segue:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## Specifica di una versione delle risorse in una configurazione

Se si dispone di più risorse installate su un computer, è necessario specificare la versione di tale risorsa quando viene usata in una configurazione. Eseguire questa operazione specificando il parametro **ModuleVersion** della parola chiave **Import-DscResource**. Se non viene specificata la versione di un modulo risorse di una risorsa di cui è installata più di una versione, la configurazione genera un errore.

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

## Vedere anche
* [Configurazioni DSC](configurations.md)
* [Risorse DSC](resources.md)



<!--HONumber=May16_HO3-->


