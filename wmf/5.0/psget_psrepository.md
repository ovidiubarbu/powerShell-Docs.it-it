---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="b2ffe-102">Registrare un repository di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b2ffe-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="b2ffe-103">È possibile configurare PowerShellGet per agire su repository interni.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="b2ffe-104">Ciò avviene tramite le seguenti aggiunte:</span><span class="sxs-lookup"><span data-stu-id="b2ffe-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="b2ffe-105">Register-PSRepository: registra un repository per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="b2ffe-106">Unregister-PSRepository: rimuove un repository registrato per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="b2ffe-107">Set-PSRepository: imposta i valori per un repository registrato.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="b2ffe-108">Get-PSRepository: ottiene tutti i repository registrati per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="b2ffe-109">Dopo aver registrato un repository, è possibile usare Find-Module e Install-Module per usarlo.</span><span class="sxs-lookup"><span data-stu-id="b2ffe-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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