---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219532"
---
# <a name="register-a-powershell-repository"></a>Registrare un repository di PowerShell
È possibile configurare PowerShellGet per agire su repository interni. Ciò avviene tramite le seguenti aggiunte:
- Register-PSRepository: registra un repository per l'utente corrente.
- Unregister-PSRepository: rimuove un repository registrato per l'utente corrente.
- Set-PSRepository: imposta i valori per un repository registrato.
- Get-PSRepository: ottiene tutti i repository registrati per l'utente corrente.

Dopo aver registrato un repository, è possibile usare Find-Module e Install-Module per usarlo.

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
