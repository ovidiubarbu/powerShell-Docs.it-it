---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Uso di risorse con più versioni
ms.openlocfilehash: 9e5b989be3f33fb9151f76cecb6d5f700b1e36c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="using-resources-with-multiple-versions"></a><span data-ttu-id="61c78-103">Uso di risorse con più versioni</span><span class="sxs-lookup"><span data-stu-id="61c78-103">Using resources with multiple versions</span></span>

> <span data-ttu-id="61c78-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="61c78-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="61c78-105">In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side.</span><span class="sxs-lookup"><span data-stu-id="61c78-105">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="61c78-106">Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.</span><span class="sxs-lookup"><span data-stu-id="61c78-106">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>

## <a name="installing-multiple-resource-versions-side-by-side"></a><span data-ttu-id="61c78-107">Installazione di più versioni delle risorse side-by-side</span><span class="sxs-lookup"><span data-stu-id="61c78-107">Installing multiple resource versions side-by-side</span></span>

<span data-ttu-id="61c78-108">È possibile usare i parametri **MinimumVersion**, **MaximumVersion** e **RequiredVersion** del cmdlet [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) per specificare la versione di un modulo da installare.</span><span class="sxs-lookup"><span data-stu-id="61c78-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="61c78-109">La chiamata di **Install-Module** senza specificare una versione installa la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="61c78-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="61c78-110">Ad esempio, sono disponibili più versioni del modulo **xFailOverCluster**, ognuno dei quali contiene una risorsa **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="61c78-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resouce.</span></span> <span data-ttu-id="61c78-111">Il risultato della chiamata di **Install-Module** senza specificare il numero della versione è il seguente:</span><span class="sxs-lookup"><span data-stu-id="61c78-111">The result of calling **Install-Module** without specifying the version number is as follows:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="61c78-112">Se si chiama nuovamente **Install-Module**, ma si specifica una **RequiredVersion** di 1.1.0.0, si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="61c78-112">Now, if you call **Install-Module** again, but specify a **RequiredVersion** of 1.1.0.0, it results in the following:</span></span>

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="61c78-113">Specifica di una versione delle risorse in una configurazione</span><span class="sxs-lookup"><span data-stu-id="61c78-113">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="61c78-114">Se si dispone di più risorse installate su un computer, è necessario specificare la versione di tale risorsa quando viene usata in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="61c78-114">If you have multiple resources installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="61c78-115">Eseguire questa operazione specificando il parametro **ModuleVersion** della parola chiave **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="61c78-115">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="61c78-116">Se non viene specificata la versione di un modulo risorse di una risorsa di cui è installata più di una versione, la configurazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="61c78-116">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="61c78-117">La configurazione seguente mostra come specificare la versione della risorsa da chiamare:</span><span class="sxs-lookup"><span data-stu-id="61c78-117">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="61c78-118">Nota: il parametro ModuleVersion di Import-DscResource non è disponibile in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="61c78-118">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="61c78-119">In PowerShell 4.0 è possibile specificare una versione del modulo passando un oggetto di specifica del modulo al parametro ModuleName di Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="61c78-119">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="61c78-120">Un oggetto di specifica del modulo è una tabella hash che contiene le chiavi ModuleName e RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="61c78-120">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="61c78-121">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="61c78-121">For example:</span></span>

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

<span data-ttu-id="61c78-122">l'oggetto funziona anche in PowerShell 5.0, ma è consigliabile usare il parametro **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="61c78-122">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="61c78-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="61c78-123">See also</span></span>
* [<span data-ttu-id="61c78-124">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="61c78-124">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="61c78-125">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="61c78-125">DSC Resources</span></span>](resources.md)