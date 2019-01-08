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
# <a name="import-a-specific-version-of-an-installed-resource"></a><span data-ttu-id="897a3-103">Importare una versione specifica di una risorsa installata</span><span class="sxs-lookup"><span data-stu-id="897a3-103">Import a specific version of an installed resource</span></span>

> <span data-ttu-id="897a3-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="897a3-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="897a3-105">In PowerShell 5.0, versioni distinte di risorse DSC possono essere installate in un computer fianco a fianco.</span><span class="sxs-lookup"><span data-stu-id="897a3-105">In PowerShell 5.0, separate versions of DSC resources can be installed on a computer side by side.</span></span> <span data-ttu-id="897a3-106">Un modulo di risorse è possibile archiviare versioni distinte di una risorsa nella versione cartelle denominate.</span><span class="sxs-lookup"><span data-stu-id="897a3-106">A resource module can store separate versions of a resource in version named folders.</span></span>

## <a name="installing-separate-resource-versions-side-by-side"></a><span data-ttu-id="897a3-107">Installazione di risorse separati versioni affiancate</span><span class="sxs-lookup"><span data-stu-id="897a3-107">Installing separate resource versions side by side</span></span>

<span data-ttu-id="897a3-108">È possibile usare i parametri **MinimumVersion**, **MaximumVersion** e **RequiredVersion** del cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per specificare la versione di un modulo da installare.</span><span class="sxs-lookup"><span data-stu-id="897a3-108">You can use the **MinimumVersion**, **MaximumVersion**, and **RequiredVersion** parameters of the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to specify which version of a module to install.</span></span> <span data-ttu-id="897a3-109">La chiamata di **Install-Module** senza specificare una versione installa la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="897a3-109">Calling **Install-Module** without specifying a version installs the most recent version.</span></span>

<span data-ttu-id="897a3-110">Ad esempio, sono disponibili più versioni del modulo **xFailOverCluster**, ognuna delle quali contiene una risorsa **xCluster**.</span><span class="sxs-lookup"><span data-stu-id="897a3-110">For example, there are multiple versions of the **xFailOverCluster** module, each of which contains an **xCluster** resource.</span></span> <span data-ttu-id="897a3-111">La chiamata **Install-Module** senza specificare la versione numero consente di installare la versione più recente del modulo.</span><span class="sxs-lookup"><span data-stu-id="897a3-111">Calling **Install-Module** without specifying the version number installs the most recent version of the module.</span></span>

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

<span data-ttu-id="897a3-112">Per installare una versione specifica di un modulo, specificare una **RequiredVersion** di 1.1.0.0.</span><span class="sxs-lookup"><span data-stu-id="897a3-112">To install a specific version of a module, specify a **RequiredVersion** of 1.1.0.0.</span></span> <span data-ttu-id="897a3-113">Questo consente di installare la versione specificata side la versione installata.</span><span class="sxs-lookup"><span data-stu-id="897a3-113">This installs the specified version side by side with the installed version.</span></span>

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

<span data-ttu-id="897a3-114">Ora, noterete entrambi versione del modulo elencato quando si usa `Get-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="897a3-114">Now, you see both version of the module listed when you use `Get-DSCResource`.</span></span>

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a><span data-ttu-id="897a3-115">Specifica di una versione delle risorse in una configurazione</span><span class="sxs-lookup"><span data-stu-id="897a3-115">Specifying a resource version in a configuration</span></span>

<span data-ttu-id="897a3-116">Se si dispone di versioni di risorse distinto installate in un computer, è necessario specificare la versione di tale risorsa quando viene utilizzata in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="897a3-116">If you have separate resource versions installed on a computer, you must specify the version of that resource when you use it in a configuration.</span></span> <span data-ttu-id="897a3-117">Eseguire questa operazione specificando il parametro **ModuleVersion** della parola chiave **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="897a3-117">You do this by specifying the **ModuleVersion** parameter of the **Import-DscResource** keyword.</span></span> <span data-ttu-id="897a3-118">Se non viene specificata la versione di un modulo risorse di una risorsa di cui è installata più di una versione, la configurazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="897a3-118">If you fail to specify the version of a resource module of a resource of which you have more than one version installed, the configuration generates an error.</span></span>

<span data-ttu-id="897a3-119">La configurazione seguente mostra come specificare la versione della risorsa da chiamare:</span><span class="sxs-lookup"><span data-stu-id="897a3-119">The following configuration shows how to specify the version of the resource to call:</span></span>

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

><span data-ttu-id="897a3-120">Nota: Il parametro ModuleVersion di Import-DscResource non è disponibile in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="897a3-120">Note: The ModuleVersion parameter of Import-DscResource is not available in PowerShell 4.0.</span></span> <span data-ttu-id="897a3-121">In PowerShell 4.0 è possibile specificare una versione del modulo passando un oggetto di specifica del modulo al parametro ModuleName di Import-DscResource.</span><span class="sxs-lookup"><span data-stu-id="897a3-121">In PowerShell 4.0, you can specify a module version by passing a module specification object to the ModuleName parameter of Import-DscResource.</span></span> <span data-ttu-id="897a3-122">Un oggetto di specifica del modulo è una tabella hash che contiene le chiavi ModuleName e RequiredVersion.</span><span class="sxs-lookup"><span data-stu-id="897a3-122">A module specification object is a hash table that contains ModuleName and RequiredVersion  keys.</span></span> <span data-ttu-id="897a3-123">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="897a3-123">For example:</span></span>

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

<span data-ttu-id="897a3-124">l'oggetto funziona anche in PowerShell 5.0, ma è consigliabile usare il parametro **ModuleVersion**.</span><span class="sxs-lookup"><span data-stu-id="897a3-124">This will also work in PowerShell 5.0, but it is recommended that you use the **ModuleVersion** parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="897a3-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="897a3-125">See also</span></span>

- [<span data-ttu-id="897a3-126">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="897a3-126">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="897a3-127">Risorse DSC</span><span class="sxs-lookup"><span data-stu-id="897a3-127">DSC Resources</span></span>](../resources/resources.md)
