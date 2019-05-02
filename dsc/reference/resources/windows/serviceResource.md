---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Service DSC
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076895"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="6413f-103">Risorsa Service DSC</span><span class="sxs-lookup"><span data-stu-id="6413f-103">DSC Service Resource</span></span>

> <span data-ttu-id="6413f-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6413f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="6413f-105">La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6413f-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6413f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6413f-106">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="6413f-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6413f-107">Properties</span></span>

|  <span data-ttu-id="6413f-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6413f-108">Property</span></span>  |  <span data-ttu-id="6413f-109">Description</span><span class="sxs-lookup"><span data-stu-id="6413f-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="6413f-110">Nome</span><span class="sxs-lookup"><span data-stu-id="6413f-110">Name</span></span>| <span data-ttu-id="6413f-111">Indica il nome del servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-111">Indicates the service name.</span></span> <span data-ttu-id="6413f-112">A volte questo nome è diverso da quello visualizzato.</span><span class="sxs-lookup"><span data-stu-id="6413f-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="6413f-113">È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="6413f-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="6413f-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="6413f-114">BuiltInAccount</span></span>| <span data-ttu-id="6413f-115">Indica l'account di accesso da usare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="6413f-116">I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="6413f-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="6413f-117">Credential</span><span class="sxs-lookup"><span data-stu-id="6413f-117">Credential</span></span>| <span data-ttu-id="6413f-118">Indica le credenziali per l'account in cui verrà eseguito il servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="6413f-119">Questa proprietà e la proprietà __BuiltinAccount__ non possono essere usate insieme.</span><span class="sxs-lookup"><span data-stu-id="6413f-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="6413f-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6413f-120">DependsOn</span></span>| <span data-ttu-id="6413f-121">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6413f-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6413f-122">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6413f-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="6413f-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="6413f-123">StartupType</span></span>| <span data-ttu-id="6413f-124">Indica il tipo di avvio per il servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="6413f-125">I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**</span><span class="sxs-lookup"><span data-stu-id="6413f-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="6413f-126">State</span><span class="sxs-lookup"><span data-stu-id="6413f-126">State</span></span>| <span data-ttu-id="6413f-127">Indica lo stato che si vuole specificare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="6413f-128">Description</span><span class="sxs-lookup"><span data-stu-id="6413f-128">Description</span></span> | <span data-ttu-id="6413f-129">Specifica la descrizione del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6413f-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="6413f-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6413f-130">DisplayName</span></span> | <span data-ttu-id="6413f-131">Indica il nome visualizzato del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6413f-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="6413f-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="6413f-132">Ensure</span></span> | <span data-ttu-id="6413f-133">Indica se il servizio di destinazione è presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="6413f-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="6413f-134">Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste.</span><span class="sxs-lookup"><span data-stu-id="6413f-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="6413f-135">Se la proprietà è impostata su **Present** (valore predefinito), specifica che il servizio di destinazione esiste.</span><span class="sxs-lookup"><span data-stu-id="6413f-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="6413f-136">Path</span><span class="sxs-lookup"><span data-stu-id="6413f-136">Path</span></span> | <span data-ttu-id="6413f-137">Indica il percorso del file binario per un nuovo servizio.</span><span class="sxs-lookup"><span data-stu-id="6413f-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="6413f-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="6413f-138">Example</span></span>

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```