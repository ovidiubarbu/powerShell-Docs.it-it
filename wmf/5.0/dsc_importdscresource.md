---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219651"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="4d659-102">La parola chiave Import-DscResource supporta il parametro -ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="4d659-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="4d659-103">È stato aggiunto un nuovo parametro alla parola chiave dinamica `Import-DscResource`, disponibile durante la creazione di configurazioni DSC.</span><span class="sxs-lookup"><span data-stu-id="4d659-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="4d659-104">Gli autori di configurazioni possono ora specificare la versione del modulo esatta da cui caricare le risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="4d659-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="4d659-105">La nuova sintassi della parola chiave è:</span><span class="sxs-lookup"><span data-stu-id="4d659-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="4d659-106">**Name**: nomi di una o più risorse da importare.</span><span class="sxs-lookup"><span data-stu-id="4d659-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="4d659-107">**ModuleName**: nomi dei moduli o oggetti ModuleSpecification di uno o più moduli da importare.</span><span class="sxs-lookup"><span data-stu-id="4d659-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="4d659-108">**ModuleVersion**: versione del modulo da importare.</span><span class="sxs-lookup"><span data-stu-id="4d659-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="4d659-109">Se usato, ModuleName deve rappresentare un solo modulo in base al nome.</span><span class="sxs-lookup"><span data-stu-id="4d659-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="4d659-110">In Windows PowerShell ISE, viene visualizzato con IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="4d659-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="4d659-111">**Nota**: il parametro `–ModuleVersion` può essere usato solo in combinazione con il parametro `–ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="4d659-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="4d659-112">Non può essere usato con i nomi di risorse usando solo il parametro `–Name`.</span><span class="sxs-lookup"><span data-stu-id="4d659-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="4d659-113">In precedenza, l'unico modo per specificare la versione del modulo durante il caricamento delle risorse DSC era tramite l'oggetto di specifica del modulo, ad esempio: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="4d659-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
