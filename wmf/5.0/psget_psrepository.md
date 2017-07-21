---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,impostazione
ms.openlocfilehash: 81ce13a082ad1d7a13ba5fd76a7595b55708f54e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="bb56a-102">Registrare un repository di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb56a-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="bb56a-103">È possibile configurare PowerShellGet per agire su repository interni.</span><span class="sxs-lookup"><span data-stu-id="bb56a-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="bb56a-104">Ciò avviene tramite le seguenti aggiunte:</span><span class="sxs-lookup"><span data-stu-id="bb56a-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="bb56a-105">Register-PSRepository: registra un repository per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="bb56a-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="bb56a-106">Unregister-PSRepository: rimuove un repository registrato per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="bb56a-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="bb56a-107">Set-PSRepository: imposta i valori per un repository registrato.</span><span class="sxs-lookup"><span data-stu-id="bb56a-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="bb56a-108">Get-PSRepository: ottiene tutti i repository registrati per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="bb56a-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="bb56a-109">Dopo aver registrato un repository, è possibile usare Find-Module e Install-Module per usarlo.</span><span class="sxs-lookup"><span data-stu-id="bb56a-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```

