---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxEnvironment DSC per Linux
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="6999b-103">Risorsa nxEnvironment DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="6999b-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="6999b-104">La risorsa **nxEnvironment** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="6999b-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6999b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6999b-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="6999b-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6999b-106">Properties</span></span>

|  <span data-ttu-id="6999b-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6999b-107">Property</span></span> |  <span data-ttu-id="6999b-108">Description</span><span class="sxs-lookup"><span data-stu-id="6999b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="6999b-109">Name</span><span class="sxs-lookup"><span data-stu-id="6999b-109">Name</span></span>| <span data-ttu-id="6999b-110">Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="6999b-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="6999b-111">Value</span><span class="sxs-lookup"><span data-stu-id="6999b-111">Value</span></span>| <span data-ttu-id="6999b-112">Valore da assegnare alla variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="6999b-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="6999b-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="6999b-113">Ensure</span></span>| <span data-ttu-id="6999b-114">Determina se verificare l'esistenza della variabile.</span><span class="sxs-lookup"><span data-stu-id="6999b-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="6999b-115">Impostare questa proprietà su "Present" per specificare che la variabile esiste.</span><span class="sxs-lookup"><span data-stu-id="6999b-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="6999b-116">Impostarla su "Absent" per specificare che la variabile non esiste.</span><span class="sxs-lookup"><span data-stu-id="6999b-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="6999b-117">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="6999b-117">The default value is "Present".</span></span>|
| <span data-ttu-id="6999b-118">Path</span><span class="sxs-lookup"><span data-stu-id="6999b-118">Path</span></span>| <span data-ttu-id="6999b-119">Definisce la variabile di ambiente configurata.</span><span class="sxs-lookup"><span data-stu-id="6999b-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="6999b-120">Impostare questa proprietà su **$true** se la variabile è **Path**; in caso contrario, impostarla su **$false**.</span><span class="sxs-lookup"><span data-stu-id="6999b-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="6999b-121">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="6999b-121">The default is **$false**.</span></span> <span data-ttu-id="6999b-122">Se la variabile configurata è **Path**, il valore specificato tramite la proprietà **Value** viene aggiunto al valore esistente.</span><span class="sxs-lookup"><span data-stu-id="6999b-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="6999b-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6999b-123">DependsOn</span></span> | <span data-ttu-id="6999b-124">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6999b-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6999b-125">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6999b-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="6999b-126">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="6999b-126">Additional Information</span></span>

* <span data-ttu-id="6999b-127">Se la proprietà **Path** è assente o impostata su **$false**, le variabili di ambiente vengono gestite in `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="6999b-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="6999b-128">I programmi o gli script possono richiedere che la configurazione abbia come origine il file `/etc/environment` per accedere alle variabili di ambiente gestite.</span><span class="sxs-lookup"><span data-stu-id="6999b-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="6999b-129">Se la proprietà **Path** è impostata su **$true**, la variabile di ambiente viene gestita nel file `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="6999b-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="6999b-130">Se questo file non esiste, viene creato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6999b-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="6999b-131">Se la proprietà **Ensure** è impostata su "Absent" e la proprietà **Path** è impostata su **$true**, una variabile di ambiente esistente verrà rimossa solo da `/etc/profile.d/DSCenvironment.sh` e non da altri file.</span><span class="sxs-lookup"><span data-stu-id="6999b-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="6999b-132">Esempio</span><span class="sxs-lookup"><span data-stu-id="6999b-132">Example</span></span>

<span data-ttu-id="6999b-133">L'esempio seguente mostra come usare la risorsa **nxEnvironment** per specificare che **TestEnvironmentVariable** è presente e ha il valore "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="6999b-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="6999b-134">Se la variabile **TestEnvironmentVariable** non è presente, verrà creata.</span><span class="sxs-lookup"><span data-stu-id="6999b-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```