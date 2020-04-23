---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Chiamata diretta dei metodi delle risorse DSC
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954388"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="f136d-103">Chiamata diretta dei metodi delle risorse DSC</span><span class="sxs-lookup"><span data-stu-id="f136d-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="f136d-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f136d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f136d-105">È possibile usare il cmdlet [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) per chiamare direttamente le funzioni o i metodi di una risorsa DSC (le funzioni **Get-TargetResource**, **Set-TargetResource**, e **Test-TargetResource** di una risorsa basata su MOF, o i metodi **Get**, **Set**, e **Test** di una risorsa basata su classi).</span><span class="sxs-lookup"><span data-stu-id="f136d-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="f136d-106">Il cmdlet può essere usato da terze parti che desiderano usare risorse DSC o come strumento utile d'aiuto durante lo sviluppo delle risorse.</span><span class="sxs-lookup"><span data-stu-id="f136d-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="f136d-107">Questo cmdlet viene in genere usato in combinazione con una proprietà di metaconfigurazione `refreshMode = 'Disabled'`, ma può essere usato indipendentemente dall'impostazione di **refreshMode**.</span><span class="sxs-lookup"><span data-stu-id="f136d-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="f136d-108">Quando si chiama il cmdlet **Invoke-DscResource**, specificare il metodo o la funzione da chiamare usando il parametro **Method**.</span><span class="sxs-lookup"><span data-stu-id="f136d-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="f136d-109">Specificare le proprietà della risorsa passando una tabella hash come valore del parametro **Property**.</span><span class="sxs-lookup"><span data-stu-id="f136d-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="f136d-110">Di seguito vengono riportati alcuni esempi di chiamate dirette ai metodi della risorsa:</span><span class="sxs-lookup"><span data-stu-id="f136d-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="f136d-111">Verificare che sia presente un file</span><span class="sxs-lookup"><span data-stu-id="f136d-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="f136d-112">Eseguire un test per verificare la presenza di un file</span><span class="sxs-lookup"><span data-stu-id="f136d-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="f136d-113">Ottenere il contenuto del file</span><span class="sxs-lookup"><span data-stu-id="f136d-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="f136d-114">**Nota:** la chiamata diretta di metodi di risorse composite non è supportata.</span><span class="sxs-lookup"><span data-stu-id="f136d-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="f136d-115">Chiamare invece i metodi delle risorse sottostanti che costituiscono la risorsa composita.</span><span class="sxs-lookup"><span data-stu-id="f136d-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="f136d-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f136d-116">See Also</span></span>
- [<span data-ttu-id="f136d-117">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="f136d-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="f136d-118">Scrittura di una risorsa DSC personalizzata con classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="f136d-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="f136d-119">Debug di risorse DSC</span><span class="sxs-lookup"><span data-stu-id="f136d-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)