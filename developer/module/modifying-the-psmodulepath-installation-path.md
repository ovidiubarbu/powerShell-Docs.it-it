---
title: Modifica il percorso di installazione di PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855567"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="ff53c-102">Modifica del percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ff53c-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="ff53c-103">Il `PSModulePath` variabile di ambiente vengono archiviati i percorsi per i percorsi dei moduli installati nel disco.</span><span class="sxs-lookup"><span data-stu-id="ff53c-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="ff53c-104">Windows PowerShell Usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo.</span><span class="sxs-lookup"><span data-stu-id="ff53c-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="ff53c-105">La ricerca vengono eseguiti nell'ordine in cui vengono visualizzati i percorsi nella variabile.</span><span class="sxs-lookup"><span data-stu-id="ff53c-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="ff53c-106">Quando si avvia Windows PowerShell, `PSModulePath` viene creata come una variabile di ambiente di sistema con il seguente valore predefinito: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="ff53c-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="ff53c-107">Per visualizzare la variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ff53c-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="ff53c-108">Per visualizzare i percorsi specificati nel `PSModulePath` variabile, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ff53c-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="ff53c-109">Aggiungere percorsi alla variabile PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ff53c-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="ff53c-110">Per aggiungere i percorsi a questa variabile, usare uno dei metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ff53c-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="ff53c-111">Per aggiungere un valore temporaneo che è disponibile solo per la sessione corrente, eseguire il comando seguente dalla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="ff53c-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="ff53c-112">Per aggiungere un valore persistente che è disponibile ogni volta che viene aperta una sessione, aggiungere il comando seguente a un profilo di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ff53c-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="ff53c-113">Per altre informazioni sui profili, vedere [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) nella libreria Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="ff53c-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="ff53c-114">Per aggiungere una variabile persistente nel Registro di sistema, creare una nuova variabile di ambiente utente denominata `PSModulePath` usando l'Editor delle variabili di ambiente nel **le proprietà di sistema** nella finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="ff53c-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="ff53c-115">Per aggiungere una variabile persistente usando uno script, usare il **SetEnvironmentVariable** metodo sulla classe di ambiente.</span><span class="sxs-lookup"><span data-stu-id="ff53c-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="ff53c-116">Ad esempio, lo script seguente aggiunge il "c:\Programmi\Microsoft Files\Fabrikam\Module percorso al valore della variabile di ambiente PSModulePath per il computer.</span><span class="sxs-lookup"><span data-stu-id="ff53c-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="ff53c-117">Per aggiungere il percorso alla variabile di ambiente PSModulePath utente, impostare la destinazione su "Utente".</span><span class="sxs-lookup"><span data-stu-id="ff53c-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="ff53c-118">Per rimuovere i percorsi da PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ff53c-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="ff53c-119">È possibile rimuovere i percorsi dalla variabile tramite metodi simili: ad esempio, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` rimuoverà il **c:\ModulePath** percorso dalla sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="ff53c-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff53c-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ff53c-120">See Also</span></span>

[<span data-ttu-id="ff53c-121">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff53c-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
