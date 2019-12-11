---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxEnvironment DSC per Linux
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953228"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="eead5-103">Risorsa nxEnvironment DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="eead5-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="eead5-104">La risorsa **nxEnvironment** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="eead5-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="eead5-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="eead5-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="eead5-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="eead5-106">Properties</span></span>

|<span data-ttu-id="eead5-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="eead5-107">Property</span></span> |<span data-ttu-id="eead5-108">Description</span><span class="sxs-lookup"><span data-stu-id="eead5-108">Description</span></span> |
|---|---|
|<span data-ttu-id="eead5-109">Nome</span><span class="sxs-lookup"><span data-stu-id="eead5-109">Name</span></span> |<span data-ttu-id="eead5-110">Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="eead5-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="eead5-111">Value</span><span class="sxs-lookup"><span data-stu-id="eead5-111">Value</span></span> |<span data-ttu-id="eead5-112">Valore da assegnare alla variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="eead5-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="eead5-113">Path</span><span class="sxs-lookup"><span data-stu-id="eead5-113">Path</span></span> |<span data-ttu-id="eead5-114">Definisce la variabile di ambiente configurata.</span><span class="sxs-lookup"><span data-stu-id="eead5-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="eead5-115">Impostare questa proprietà su `$true` se la variabile è **Path**. In caso contrario, impostarla su `$false`.</span><span class="sxs-lookup"><span data-stu-id="eead5-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="eead5-116">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="eead5-116">The default is `$false`.</span></span> <span data-ttu-id="eead5-117">Se la variabile configurata è **Path**, il valore specificato tramite la proprietà **Value** viene aggiunto al valore esistente.</span><span class="sxs-lookup"><span data-stu-id="eead5-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="eead5-118">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="eead5-118">Common properties</span></span>

|<span data-ttu-id="eead5-119">Proprietà</span><span class="sxs-lookup"><span data-stu-id="eead5-119">Property</span></span> |<span data-ttu-id="eead5-120">Description</span><span class="sxs-lookup"><span data-stu-id="eead5-120">Description</span></span> |
|---|---|
|<span data-ttu-id="eead5-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eead5-121">DependsOn</span></span> |<span data-ttu-id="eead5-122">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="eead5-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eead5-123">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="eead5-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="eead5-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="eead5-124">Ensure</span></span> |<span data-ttu-id="eead5-125">Determina se verificare l'esistenza della variabile.</span><span class="sxs-lookup"><span data-stu-id="eead5-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="eead5-126">Impostare questa proprietà su **Present** per assicurarsi che la variabile esista.</span><span class="sxs-lookup"><span data-stu-id="eead5-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="eead5-127">Impostarla su **Absent** per assicurarsi che la variabile non esista.</span><span class="sxs-lookup"><span data-stu-id="eead5-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="eead5-128">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="eead5-128">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="eead5-129">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="eead5-129">Additional Information</span></span>

- <span data-ttu-id="eead5-130">Se la proprietà **Path** è assente o impostata su `$false`, le variabili di ambiente vengono gestite in `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="eead5-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="eead5-131">I programmi o gli script possono richiedere che la configurazione abbia come origine il file `/etc/environment` per accedere alle variabili di ambiente gestite.</span><span class="sxs-lookup"><span data-stu-id="eead5-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="eead5-132">Se la proprietà **Path** è impostata su `$true`, la variabile di ambiente viene gestita nel file `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="eead5-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="eead5-133">Se questo file non esiste, viene creato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="eead5-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="eead5-134">Se la proprietà **Ensure** è impostata su **Absent** e la proprietà **Path** è impostata su `$true`, una variabile di ambiente esistente verrà rimossa solo da `/etc/profile.d/DSCenvironment.sh` e non da altri file.</span><span class="sxs-lookup"><span data-stu-id="eead5-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="eead5-135">Esempio</span><span class="sxs-lookup"><span data-stu-id="eead5-135">Example</span></span>

<span data-ttu-id="eead5-136">L'esempio seguente mostra come usare la risorsa **nxEnvironment** per specificare che **TestEnvironmentVariable** è presente e ha il valore "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="eead5-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="eead5-137">Se la variabile **TestEnvironmentVariable** non è presente, verrà creata.</span><span class="sxs-lookup"><span data-stu-id="eead5-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```