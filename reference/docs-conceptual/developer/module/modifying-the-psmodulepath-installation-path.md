---
title: Modifica del percorso di installazione di PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: b176d8439025ac132962859f79e72ae6f9703e82
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405045"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="79774-102">Modifica del percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="79774-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="79774-103">La variabile di ambiente `PSModulePath` archivia i percorsi delle posizioni dei moduli installati su disco.</span><span class="sxs-lookup"><span data-stu-id="79774-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="79774-104">PowerShell usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo.</span><span class="sxs-lookup"><span data-stu-id="79774-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="79774-105">I percorsi in questa variabile vengono cercati nell'ordine in cui sono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="79774-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="79774-106">All'avvio di PowerShell, `PSModulePath` viene creato come variabile di ambiente di sistema con il valore predefinito seguente: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` in Windows e `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` su Linux o Mac e `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="79774-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="79774-107">Il percorso **CurrentUser** specifico dell'utente è la cartella `WindowsPowerShell\Modules` che si trova nel percorso dei **documenti** nel profilo utente.</span><span class="sxs-lookup"><span data-stu-id="79774-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="79774-108">Il percorso specifico di tale percorso varia in base alla versione di Windows e a seconda che si usi o meno il reindirizzamento cartelle.</span><span class="sxs-lookup"><span data-stu-id="79774-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="79774-109">Per impostazione predefinita, in Windows 10 il percorso è `$HOME\Documents\WindowsPowerShell\Modules`.</span><span class="sxs-lookup"><span data-stu-id="79774-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="79774-110">Per visualizzare la variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="79774-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="79774-111">Per visualizzare i percorsi specificati nella variabile `PSModulePath`, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="79774-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="79774-112">Per aggiungere percorsi alla variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="79774-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="79774-113">Per aggiungere percorsi a questa variabile, usare uno dei metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="79774-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="79774-114">Per aggiungere un valore temporaneo disponibile solo per la sessione corrente, eseguire il comando seguente dalla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="79774-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="79774-115">Per aggiungere un valore permanente disponibile ogni volta che viene aperta una sessione, aggiungere il comando precedente a un file di profilo di PowerShell (`$PROFILE`) ></span><span class="sxs-lookup"><span data-stu-id="79774-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="79774-116">Per altre informazioni sui profili, vedere [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="79774-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="79774-117">Per aggiungere una variabile persistente al registro di sistema, creare una nuova variabile di ambiente utente denominata `PSModulePath` usando l'editor delle variabili di ambiente nella finestra di dialogo **proprietà del sistema** .</span><span class="sxs-lookup"><span data-stu-id="79774-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="79774-118">Per aggiungere una variabile persistente usando uno script, usare il metodo .NET [nell'SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) sulla classe [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="79774-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="79774-119">Ad esempio, lo script seguente aggiunge il percorso `C:\Program Files\Fabrikam\Module` al valore della variabile di ambiente `PSModulePath` per il computer.</span><span class="sxs-lookup"><span data-stu-id="79774-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="79774-120">Per aggiungere il percorso alla variabile di ambiente `PSModulePath` utente, impostare la destinazione su "User".</span><span class="sxs-lookup"><span data-stu-id="79774-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="79774-121">Per rimuovere i percorsi dal PSModulePath</span><span class="sxs-lookup"><span data-stu-id="79774-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="79774-122">È possibile rimuovere i percorsi dalla variabile utilizzando metodi simili. ad esempio, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` eliminerà il percorso **c:\ModulePath** dalla sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="79774-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="79774-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="79774-123">See Also</span></span>

[<span data-ttu-id="79774-124">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="79774-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="79774-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="79774-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
