---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Service DSC
ms.openlocfilehash: 3e2db8999ab1db2964f88e1ee14c6ad6e641c5e3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-service-resource"></a><span data-ttu-id="b09ca-103">Risorsa Service DSC</span><span class="sxs-lookup"><span data-stu-id="b09ca-103">DSC Service Resource</span></span>

> <span data-ttu-id="b09ca-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b09ca-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="b09ca-105">La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b09ca-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b09ca-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b09ca-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b09ca-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b09ca-107">Properties</span></span>

|  <span data-ttu-id="b09ca-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="b09ca-108">Property</span></span>  |  <span data-ttu-id="b09ca-109">Description</span><span class="sxs-lookup"><span data-stu-id="b09ca-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="b09ca-110">Nome</span><span class="sxs-lookup"><span data-stu-id="b09ca-110">Name</span></span>| <span data-ttu-id="b09ca-111">Indica il nome del servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-111">Indicates the service name.</span></span> <span data-ttu-id="b09ca-112">A volte questo nome è diverso da quello visualizzato.</span><span class="sxs-lookup"><span data-stu-id="b09ca-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="b09ca-113">È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet Get-Service.</span><span class="sxs-lookup"><span data-stu-id="b09ca-113">You can get a list of the services and their current state with the Get-Service cmdlet.</span></span>|
| <span data-ttu-id="b09ca-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="b09ca-114">BuiltInAccount</span></span>| <span data-ttu-id="b09ca-115">Indica l'account di accesso da usare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="b09ca-116">I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="b09ca-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="b09ca-117">Credential</span><span class="sxs-lookup"><span data-stu-id="b09ca-117">Credential</span></span>| <span data-ttu-id="b09ca-118">Indica le credenziali per l'account in cui verrà eseguito il servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="b09ca-119">Questa proprietà e la proprietà __BuiltinAccount__ non possono essere usate insieme.</span><span class="sxs-lookup"><span data-stu-id="b09ca-119">This property and the __BuiltinAccount__ property cannot be used together.</span></span>|
| <span data-ttu-id="b09ca-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b09ca-120">DependsOn</span></span>| <span data-ttu-id="b09ca-121">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="b09ca-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b09ca-122">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b09ca-122">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b09ca-123">StartupType</span><span class="sxs-lookup"><span data-stu-id="b09ca-123">StartupType</span></span>| <span data-ttu-id="b09ca-124">Indica il tipo di avvio per il servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-124">Indicates the startup type for the service.</span></span> <span data-ttu-id="b09ca-125">I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**</span><span class="sxs-lookup"><span data-stu-id="b09ca-125">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="b09ca-126">State</span><span class="sxs-lookup"><span data-stu-id="b09ca-126">State</span></span>| <span data-ttu-id="b09ca-127">Indica lo stato che si vuole specificare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-127">Indicates the state you want to ensure for the service.</span></span>|
| <span data-ttu-id="b09ca-128">Description</span><span class="sxs-lookup"><span data-stu-id="b09ca-128">Description</span></span> | <span data-ttu-id="b09ca-129">Specifica la descrizione del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b09ca-129">Indicates the description of the target service.</span></span>|
| <span data-ttu-id="b09ca-130">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b09ca-130">DisplayName</span></span> | <span data-ttu-id="b09ca-131">Indica il nome visualizzato del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b09ca-131">Indicates the display name of the target service.</span></span>|
| <span data-ttu-id="b09ca-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="b09ca-132">Ensure</span></span> | <span data-ttu-id="b09ca-133">Indica se il servizio di destinazione è presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="b09ca-133">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="b09ca-134">Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste.</span><span class="sxs-lookup"><span data-stu-id="b09ca-134">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="b09ca-135">Se la proprietà è impostata su **Present** (valore predefinito), specifica che il servizio di destinazione esiste.</span><span class="sxs-lookup"><span data-stu-id="b09ca-135">Setting it to **Present** (the default value) ensures that target service exists.</span></span>|
| <span data-ttu-id="b09ca-136">Path</span><span class="sxs-lookup"><span data-stu-id="b09ca-136">Path</span></span> | <span data-ttu-id="b09ca-137">Indica il percorso del file binario per un nuovo servizio.</span><span class="sxs-lookup"><span data-stu-id="b09ca-137">Indicates the path to the binary file for a new service.</span></span>|

## <a name="example"></a><span data-ttu-id="b09ca-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="b09ca-138">Example</span></span>

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