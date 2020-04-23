---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Environment DSC
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954718"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="6cbe8-103">Risorsa Environment DSC</span><span class="sxs-lookup"><span data-stu-id="6cbe8-103">DSC Environment Resource</span></span>

> <span data-ttu-id="6cbe8-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="6cbe8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="6cbe8-105">La risorsa **Environment** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="6cbe8-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6cbe8-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="6cbe8-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6cbe8-107">Properties</span></span>

|<span data-ttu-id="6cbe8-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6cbe8-108">Property</span></span> |<span data-ttu-id="6cbe8-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6cbe8-109">Description</span></span> |
|---|---|
|<span data-ttu-id="6cbe8-110">Nome</span><span class="sxs-lookup"><span data-stu-id="6cbe8-110">Name</span></span> |<span data-ttu-id="6cbe8-111">Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="6cbe8-112">Path</span><span class="sxs-lookup"><span data-stu-id="6cbe8-112">Path</span></span> |<span data-ttu-id="6cbe8-113">Definisce la variabile di ambiente configurata.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="6cbe8-114">Impostare questa proprietà su `$true` se la variabile è **Path**. In caso contrario, impostarla su `$false`.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="6cbe8-115">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-115">The default is `$false`.</span></span> <span data-ttu-id="6cbe8-116">Se la variabile configurata è **Path**, il valore specificato tramite la proprietà **Value** viene aggiunto al valore esistente.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="6cbe8-117">valore</span><span class="sxs-lookup"><span data-stu-id="6cbe8-117">Value</span></span> |<span data-ttu-id="6cbe8-118">Valore da assegnare alla variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="6cbe8-119">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="6cbe8-119">Common properties</span></span>

|<span data-ttu-id="6cbe8-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6cbe8-120">Property</span></span> |<span data-ttu-id="6cbe8-121">Descrizione</span><span class="sxs-lookup"><span data-stu-id="6cbe8-121">Description</span></span> |
|---|---|
|<span data-ttu-id="6cbe8-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6cbe8-122">DependsOn</span></span> |<span data-ttu-id="6cbe8-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6cbe8-124">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="6cbe8-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="6cbe8-125">Ensure</span></span> |<span data-ttu-id="6cbe8-126">Indica se una variabile esiste.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-126">Indicates if a variable exists.</span></span> <span data-ttu-id="6cbe8-127">Impostare questa proprietà su **Present** per creare una variabile di ambiente se non esiste o per specificare che il suo valore corrisponde a quello fornito tramite la proprietà **Value** se la variabile esiste già.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="6cbe8-128">Impostarla su **Absent** per eliminare la variabile, se esiste.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="6cbe8-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6cbe8-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="6cbe8-130">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="6cbe8-131">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="6cbe8-132">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="6cbe8-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="6cbe8-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="6cbe8-133">Example</span></span>

<span data-ttu-id="6cbe8-134">L'esempio seguente illustra come assicurarsi che TestEnvironmentVariable sia presente che abbia il valore _TestValue_.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="6cbe8-135">Se la variabile non è presente, viene creata.</span><span class="sxs-lookup"><span data-stu-id="6cbe8-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```