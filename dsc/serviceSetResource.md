---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ServiceSet DSC
ms.openlocfilehash: a7516120f0c4bc1c91031adc8aabf6a59b845246
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="5c916-103">Risorsa ServiceSet DSC</span><span class="sxs-lookup"><span data-stu-id="5c916-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="5c916-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5c916-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="5c916-105">La risorsa **ServiceSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="5c916-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="5c916-106">Questa risorsa è una [risorsa composta](authoringResourceComposite.md) che chiama la [risorsa Service](serviceResource.md) per ogni servizio specificato nella proprietà `Name`.</span><span class="sxs-lookup"><span data-stu-id="5c916-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the `Name` property.</span></span>

<span data-ttu-id="5c916-107">Usare questa risorsa quando si vogliono configurare diversi servizi nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="5c916-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="5c916-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5c916-108">Syntax</span></span>

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="5c916-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="5c916-109">Properties</span></span>

|  <span data-ttu-id="5c916-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="5c916-110">Property</span></span>  |  <span data-ttu-id="5c916-111">Description</span><span class="sxs-lookup"><span data-stu-id="5c916-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5c916-112">Nome</span><span class="sxs-lookup"><span data-stu-id="5c916-112">Name</span></span>| <span data-ttu-id="5c916-113">Indica i nomi del servizio.</span><span class="sxs-lookup"><span data-stu-id="5c916-113">Indicates the service names.</span></span> <span data-ttu-id="5c916-114">A volte questo nome è diverso da quelli visualizzati.</span><span class="sxs-lookup"><span data-stu-id="5c916-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="5c916-115">È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx).</span><span class="sxs-lookup"><span data-stu-id="5c916-115">You can get a list of the services and their current state with the [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.</span></span>|
| <span data-ttu-id="5c916-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="5c916-116">StartupType</span></span>| <span data-ttu-id="5c916-117">Indica il tipo di avvio per il servizio.</span><span class="sxs-lookup"><span data-stu-id="5c916-117">Indicates the startup type for the service.</span></span> <span data-ttu-id="5c916-118">I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**</span><span class="sxs-lookup"><span data-stu-id="5c916-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**</span></span>|
| <span data-ttu-id="5c916-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="5c916-119">BuiltInAccount</span></span>| <span data-ttu-id="5c916-120">Indica l'account di accesso da usare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="5c916-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="5c916-121">I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="5c916-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span>|
| <span data-ttu-id="5c916-122">State</span><span class="sxs-lookup"><span data-stu-id="5c916-122">State</span></span>| <span data-ttu-id="5c916-123">Indica lo stato che si vuole specificare per i servizi: **Stopped** o **Running**.</span><span class="sxs-lookup"><span data-stu-id="5c916-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span>|
| <span data-ttu-id="5c916-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="5c916-124">Ensure</span></span>| <span data-ttu-id="5c916-125">Indica se i servizi sono presenti nel sistema.</span><span class="sxs-lookup"><span data-stu-id="5c916-125">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="5c916-126">Impostare questa proprietà su **Absent** per specificare che i servizi non esistono.</span><span class="sxs-lookup"><span data-stu-id="5c916-126">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="5c916-127">Se la proprietà è impostata su **Present** (valore predefinito), specifica che i servizio di destinazione esistono.</span><span class="sxs-lookup"><span data-stu-id="5c916-127">Setting it to **Present** (the default value) ensures that target services exist.</span></span>|
| <span data-ttu-id="5c916-128">Credential</span><span class="sxs-lookup"><span data-stu-id="5c916-128">Credential</span></span>| <span data-ttu-id="5c916-129">Indica le credenziali per l'account in cui verrà eseguita la risorsa del servizio.</span><span class="sxs-lookup"><span data-stu-id="5c916-129">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="5c916-130">Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme.</span><span class="sxs-lookup"><span data-stu-id="5c916-130">This property and the **BuiltinAccount** property cannot be used together.</span></span>|
| <span data-ttu-id="5c916-131">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5c916-131">DependsOn</span></span>| <span data-ttu-id="5c916-132">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="5c916-132">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5c916-133">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è *ResourceName* e il tipo è *ResourceType*, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5c916-133">For example, if the ID of the resource configuration script block that you want to run first is *ResourceName* and its type is *ResourceType*, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|



## <a name="example"></a><span data-ttu-id="5c916-134">Esempio</span><span class="sxs-lookup"><span data-stu-id="5c916-134">Example</span></span>

<span data-ttu-id="5c916-135">La configurazione seguente avvia i servizi "Servizi Desktop remoto" e "Audio di Windows".</span><span class="sxs-lookup"><span data-stu-id="5c916-135">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```