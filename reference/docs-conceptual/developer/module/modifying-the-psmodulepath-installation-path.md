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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360670"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="6acb8-102">Modifica del percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="6acb8-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="6acb8-103">La variabile di ambiente `PSModulePath` archivia i percorsi delle posizioni dei moduli installati su disco.</span><span class="sxs-lookup"><span data-stu-id="6acb8-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="6acb8-104">Windows PowerShell usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo.</span><span class="sxs-lookup"><span data-stu-id="6acb8-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="6acb8-105">I percorsi in questa variabile vengono cercati nell'ordine in cui sono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="6acb8-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="6acb8-106">All'avvio di Windows PowerShell, `PSModulePath` viene creato come variabile di ambiente di sistema con il valore predefinito seguente: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="6acb8-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="6acb8-107">Per visualizzare la variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="6acb8-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="6acb8-108">Per visualizzare i percorsi specificati nella variabile `PSModulePath`, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="6acb8-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="6acb8-109">Per aggiungere percorsi alla variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="6acb8-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="6acb8-110">Per aggiungere percorsi a questa variabile, usare uno dei metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="6acb8-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="6acb8-111">Per aggiungere un valore temporaneo disponibile solo per la sessione corrente, eseguire il comando seguente dalla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="6acb8-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="6acb8-112">Per aggiungere un valore permanente disponibile ogni volta che viene aperta una sessione, aggiungere il comando seguente a un profilo di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6acb8-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="6acb8-113">Per ulteriori informazioni sui profili, vedere [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) nella libreria Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="6acb8-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="6acb8-114">Per aggiungere una variabile persistente al registro di sistema, creare una nuova variabile di ambiente utente denominata `PSModulePath` usando l'editor delle variabili di ambiente nella finestra di dialogo **proprietà del sistema** .</span><span class="sxs-lookup"><span data-stu-id="6acb8-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="6acb8-115">Per aggiungere una variabile persistente usando uno script, usare il metodo **nell'SetEnvironmentVariable** nella classe Environment.</span><span class="sxs-lookup"><span data-stu-id="6acb8-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="6acb8-116">Ad esempio, lo script seguente aggiunge il percorso "C:\Program Files\Fabrikam\Module al valore della variabile di ambiente PSModulePath per il computer.</span><span class="sxs-lookup"><span data-stu-id="6acb8-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="6acb8-117">Per aggiungere il percorso alla variabile di ambiente PSModulePath utente, impostare la destinazione su "User".</span><span class="sxs-lookup"><span data-stu-id="6acb8-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="6acb8-118">Per rimuovere i percorsi dal PSModulePath</span><span class="sxs-lookup"><span data-stu-id="6acb8-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="6acb8-119">È possibile rimuovere i percorsi dalla variabile utilizzando metodi simili. ad esempio, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` rimuoverà il percorso **c:\ModulePath** dalla sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="6acb8-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="6acb8-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6acb8-120">See Also</span></span>

[<span data-ttu-id="6acb8-121">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6acb8-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)