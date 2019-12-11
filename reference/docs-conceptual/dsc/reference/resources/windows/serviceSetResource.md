---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ServiceSet DSC
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953028"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="ef7bc-103">Risorsa ServiceSet DSC</span><span class="sxs-lookup"><span data-stu-id="ef7bc-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="ef7bc-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ef7bc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="ef7bc-105">La risorsa **ServiceSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="ef7bc-106">Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Service](serviceResource.md) per ogni servizio specificato nella proprietà **Name**.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="ef7bc-107">Usare questa risorsa quando si vogliono configurare diversi servizi nello stesso stato.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef7bc-108">Sintassi</span><span class="sxs-lookup"><span data-stu-id="ef7bc-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ef7bc-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ef7bc-109">Properties</span></span>

|<span data-ttu-id="ef7bc-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ef7bc-110">Property</span></span> |<span data-ttu-id="ef7bc-111">Description</span><span class="sxs-lookup"><span data-stu-id="ef7bc-111">Description</span></span> |
|---|---|
|<span data-ttu-id="ef7bc-112">Nome</span><span class="sxs-lookup"><span data-stu-id="ef7bc-112">Name</span></span> |<span data-ttu-id="ef7bc-113">Indica i nomi del servizio.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-113">Indicates the service names.</span></span> <span data-ttu-id="ef7bc-114">A volte questo nome è diverso da quelli visualizzati.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="ef7bc-115">È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="ef7bc-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="ef7bc-116">StartupType</span></span> |<span data-ttu-id="ef7bc-117">Indica il tipo di avvio per i servizi.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="ef7bc-118">I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="ef7bc-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="ef7bc-119">BuiltInAccount</span></span> |<span data-ttu-id="ef7bc-120">Indica l'account di accesso da usare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="ef7bc-121">I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="ef7bc-122">State</span><span class="sxs-lookup"><span data-stu-id="ef7bc-122">State</span></span> |<span data-ttu-id="ef7bc-123">Indica lo stato che si vuole specificare per i servizi: **Stopped** o **Running**.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="ef7bc-124">Credential</span><span class="sxs-lookup"><span data-stu-id="ef7bc-124">Credential</span></span> |<span data-ttu-id="ef7bc-125">Indica le credenziali per l'account in cui verrà eseguita la risorsa del servizio.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="ef7bc-126">Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ef7bc-127">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="ef7bc-127">Common properties</span></span>

|<span data-ttu-id="ef7bc-128">Proprietà</span><span class="sxs-lookup"><span data-stu-id="ef7bc-128">Property</span></span> |<span data-ttu-id="ef7bc-129">Description</span><span class="sxs-lookup"><span data-stu-id="ef7bc-129">Description</span></span> |
|---|---|
|<span data-ttu-id="ef7bc-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ef7bc-130">DependsOn</span></span> |<span data-ttu-id="ef7bc-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ef7bc-132">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ef7bc-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="ef7bc-133">Ensure</span></span> |<span data-ttu-id="ef7bc-134">Indica se i servizi sono presenti nel sistema.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="ef7bc-135">Impostare questa proprietà su **Absent** per specificare che i servizi non esistono.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="ef7bc-136">Impostando il valore su **Present** ci si assicura che i servizi di destinazione esistano.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="ef7bc-137">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="ef7bc-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ef7bc-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="ef7bc-139">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ef7bc-140">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="ef7bc-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ef7bc-141">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ef7bc-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef7bc-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="ef7bc-142">Example</span></span>

<span data-ttu-id="ef7bc-143">La configurazione seguente avvia i servizi "Servizi Desktop remoto" e "Audio di Windows".</span><span class="sxs-lookup"><span data-stu-id="ef7bc-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

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