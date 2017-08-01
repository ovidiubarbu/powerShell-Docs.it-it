---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "distribuzione e manutenzione con più computer"
ms.technology: powershell
ms.openlocfilehash: 8117d0d12c062b460cb7117b54c138c8db5a1d0c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="multi-machine-deployment-and-maintenance"></a><span data-ttu-id="22564-103">Distribuzione e manutenzione con più computer</span><span class="sxs-lookup"><span data-stu-id="22564-103">Multi-machine Deployment and Maintenance</span></span>
<span data-ttu-id="22564-104">A questo punto, JEA è stato distribuito più volte ai sistemi locali.</span><span class="sxs-lookup"><span data-stu-id="22564-104">At this point, you have deployed JEA to local systems several times.</span></span>
<span data-ttu-id="22564-105">Poiché l'ambiente di produzione probabilmente è costituito da più di un computer, è importante esaminare i passaggi essenziali del processo di distribuzione che dovranno essere ripetuti in ogni computer.</span><span class="sxs-lookup"><span data-stu-id="22564-105">Because your production environment probably consists of more than one machine, it's important to walk through the critical steps in the deployment process that must be repeated on each machine.</span></span>

## <a name="high-level-steps"></a><span data-ttu-id="22564-106">Passaggi di alto livello:</span><span class="sxs-lookup"><span data-stu-id="22564-106">High Level Steps:</span></span>
1.  <span data-ttu-id="22564-107">Copiare i moduli (con capacità del ruolo) in ogni nodo.</span><span class="sxs-lookup"><span data-stu-id="22564-107">Copy your modules (with Role Capabilities) to each node.</span></span>
2.  <span data-ttu-id="22564-108">Copiare i file di configurazione di sessione in ogni nodo.</span><span class="sxs-lookup"><span data-stu-id="22564-108">Copy your session configuration files to each node.</span></span>
3.  <span data-ttu-id="22564-109">Eseguire `Register-PSSessionConfiguration` con la configurazione di sessione.</span><span class="sxs-lookup"><span data-stu-id="22564-109">Run `Register-PSSessionConfiguration` with your session configuration.</span></span>
4.  <span data-ttu-id="22564-110">Conservare una copia della configurazione di sessione e dei toolkit in un luogo sicuro.</span><span class="sxs-lookup"><span data-stu-id="22564-110">Keep a copy of your session configuration and toolkits in a secure location.</span></span>
<span data-ttu-id="22564-111">Quando si apportano modifiche, è opportuno usare un'unica "origine di dati reali".</span><span class="sxs-lookup"><span data-stu-id="22564-111">As you make modifications, it's good to have a "single source of truth."</span></span>

## <a name="example-script"></a><span data-ttu-id="22564-112">Script di esempio</span><span class="sxs-lookup"><span data-stu-id="22564-112">Example Script</span></span>
<span data-ttu-id="22564-113">Di seguito è riportato un esempio di script per la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="22564-113">Here's an example script for deployment.</span></span>
<span data-ttu-id="22564-114">Per usarlo nel proprio ambiente, è necessario usare i nomi o i percorsi dei moduli e delle condivisioni di file reali.</span><span class="sxs-lookup"><span data-stu-id="22564-114">To use it in your environment, you'll have to use the names/paths of real file shares and modules.</span></span>
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## <a name="modifying-capabilities"></a><span data-ttu-id="22564-115">Modifica delle capacità</span><span class="sxs-lookup"><span data-stu-id="22564-115">Modifying Capabilities</span></span>
<span data-ttu-id="22564-116">Quando si gestiscono molti computer, è importante che le modifiche vengano implementate in modo coerente.</span><span class="sxs-lookup"><span data-stu-id="22564-116">When dealing with many machines, it's important that modifications are rolled out in a consistent manner.</span></span>
<span data-ttu-id="22564-117">Se per JEA è già disponibile una risorsa DSC, l'ambiente è sincronizzato.</span><span class="sxs-lookup"><span data-stu-id="22564-117">Once JEA has a DSC Resource, this will help ensure your environment is in sync.</span></span>
<span data-ttu-id="22564-118">In caso contrario, è consigliabile conservare una copia master delle configurazioni di sessione e distribuirla di nuovo ogni volta che si apporta una modifica.</span><span class="sxs-lookup"><span data-stu-id="22564-118">Until that time, we highly recommend you keep a master copy of your session configurations and re-deploy each time you make a modification.</span></span>

## <a name="removing-capabilities"></a><span data-ttu-id="22564-119">Rimozione delle capacità</span><span class="sxs-lookup"><span data-stu-id="22564-119">Removing Capabilities</span></span>
<span data-ttu-id="22564-120">Per rimuovere la configurazione JEA dai sistemi, usare il comando seguente in ogni computer:</span><span class="sxs-lookup"><span data-stu-id="22564-120">To remove your JEA configuration from your systems, use the following command on each machine:</span></span>
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```

