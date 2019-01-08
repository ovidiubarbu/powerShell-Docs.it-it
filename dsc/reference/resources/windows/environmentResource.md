---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Environment DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047607"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="17841-103">Risorsa Environment DSC</span><span class="sxs-lookup"><span data-stu-id="17841-103">DSC Environment Resource</span></span>

> <span data-ttu-id="17841-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="17841-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="17841-105">La risorsa __Environment__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema.</span><span class="sxs-lookup"><span data-stu-id="17841-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="17841-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="17841-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="17841-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="17841-107">Properties</span></span>

|  <span data-ttu-id="17841-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="17841-108">Property</span></span>  |  <span data-ttu-id="17841-109">Description</span><span class="sxs-lookup"><span data-stu-id="17841-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="17841-110">Nome</span><span class="sxs-lookup"><span data-stu-id="17841-110">Name</span></span>| <span data-ttu-id="17841-111">Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="17841-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="17841-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="17841-112">Ensure</span></span>| <span data-ttu-id="17841-113">Indica se una variabile esiste.</span><span class="sxs-lookup"><span data-stu-id="17841-113">Indicates if a variable exists.</span></span> <span data-ttu-id="17841-114">Impostare questa proprietà su __Present__ per creare una variabile di ambiente se non esiste o per specificare che il suo valore corrisponde a quello fornito tramite la proprietà __Value__ se la variabile esiste già.</span><span class="sxs-lookup"><span data-stu-id="17841-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="17841-115">Impostarla su __Absent__ per eliminare la variabile, se esiste.</span><span class="sxs-lookup"><span data-stu-id="17841-115">Set it to __Absent__ to delete the variable if it exists.</span></span>|
| <span data-ttu-id="17841-116">Path</span><span class="sxs-lookup"><span data-stu-id="17841-116">Path</span></span>| <span data-ttu-id="17841-117">Definisce la variabile di ambiente configurata.</span><span class="sxs-lookup"><span data-stu-id="17841-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="17841-118">Impostare questa proprietà su __$true__ se la variabile è __Path__; in caso contrario, impostarla su __$false__.</span><span class="sxs-lookup"><span data-stu-id="17841-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="17841-119">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="17841-119">The default is __$false__.</span></span> <span data-ttu-id="17841-120">Se la variabile configurata è __Path__, il valore specificato tramite la proprietà __Value__ viene aggiunto al valore esistente.</span><span class="sxs-lookup"><span data-stu-id="17841-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>|
| <span data-ttu-id="17841-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="17841-121">DependsOn</span></span> | <span data-ttu-id="17841-122">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="17841-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="17841-123">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="17841-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="17841-124">Value</span><span class="sxs-lookup"><span data-stu-id="17841-124">Value</span></span>| <span data-ttu-id="17841-125">Valore da assegnare alla variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="17841-125">The value to assign to the environment variable.</span></span>|

## <a name="example"></a><span data-ttu-id="17841-126">Esempio</span><span class="sxs-lookup"><span data-stu-id="17841-126">Example</span></span>

<span data-ttu-id="17841-127">L'esempio seguente specifica che __TestEnvironmentVariable__ è presente e ha il valore __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="17841-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="17841-128">Se la variabile non è presente, viene creata.</span><span class="sxs-lookup"><span data-stu-id="17841-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```