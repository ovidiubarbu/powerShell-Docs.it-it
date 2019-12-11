---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Service DSC
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953048"
---
# <a name="dsc-service-resource"></a><span data-ttu-id="60c6d-103">Risorsa Service DSC</span><span class="sxs-lookup"><span data-stu-id="60c6d-103">DSC Service Resource</span></span>

> <span data-ttu-id="60c6d-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="60c6d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="60c6d-105">La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="60c6d-105">The **Service** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="60c6d-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="60c6d-106">Syntax</span></span>

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="60c6d-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="60c6d-107">Properties</span></span>

|<span data-ttu-id="60c6d-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="60c6d-108">Property</span></span> |<span data-ttu-id="60c6d-109">Description</span><span class="sxs-lookup"><span data-stu-id="60c6d-109">Description</span></span> |
|---|---|
|<span data-ttu-id="60c6d-110">Nome</span><span class="sxs-lookup"><span data-stu-id="60c6d-110">Name</span></span> |<span data-ttu-id="60c6d-111">Indica il nome del servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-111">Indicates the service name.</span></span> <span data-ttu-id="60c6d-112">A volte questo nome è diverso da quello visualizzato.</span><span class="sxs-lookup"><span data-stu-id="60c6d-112">Note that sometimes this is different from the display name.</span></span> <span data-ttu-id="60c6d-113">È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="60c6d-113">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="60c6d-114">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="60c6d-114">BuiltInAccount</span></span> |<span data-ttu-id="60c6d-115">Indica l'account di accesso da usare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-115">Indicates the sign-in account to use for the service.</span></span> <span data-ttu-id="60c6d-116">I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.</span><span class="sxs-lookup"><span data-stu-id="60c6d-116">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="60c6d-117">Credential</span><span class="sxs-lookup"><span data-stu-id="60c6d-117">Credential</span></span> |<span data-ttu-id="60c6d-118">Indica le credenziali per l'account in cui verrà eseguito il servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-118">Indicates credentials for the account that the service will run under.</span></span> <span data-ttu-id="60c6d-119">Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme.</span><span class="sxs-lookup"><span data-stu-id="60c6d-119">This property and the **BuiltinAccount** property cannot be used together.</span></span> |
|<span data-ttu-id="60c6d-120">StartupType</span><span class="sxs-lookup"><span data-stu-id="60c6d-120">StartupType</span></span> |<span data-ttu-id="60c6d-121">Indica il tipo di avvio per il servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-121">Indicates the startup type for the service.</span></span> <span data-ttu-id="60c6d-122">I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**.</span><span class="sxs-lookup"><span data-stu-id="60c6d-122">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="60c6d-123">State</span><span class="sxs-lookup"><span data-stu-id="60c6d-123">State</span></span> |<span data-ttu-id="60c6d-124">Indica lo stato che si vuole specificare per il servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-124">Indicates the state you want to ensure for the service.</span></span> <span data-ttu-id="60c6d-125">I valori sono: **Running** o **Stopped**.</span><span class="sxs-lookup"><span data-stu-id="60c6d-125">The values are: **Running** or **Stopped**.</span></span> |
|<span data-ttu-id="60c6d-126">Description</span><span class="sxs-lookup"><span data-stu-id="60c6d-126">Description</span></span> |<span data-ttu-id="60c6d-127">Specifica la descrizione del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="60c6d-127">Indicates the description of the target service.</span></span> |
|<span data-ttu-id="60c6d-128">DisplayName</span><span class="sxs-lookup"><span data-stu-id="60c6d-128">DisplayName</span></span> |<span data-ttu-id="60c6d-129">Indica il nome visualizzato del servizio di destinazione.</span><span class="sxs-lookup"><span data-stu-id="60c6d-129">Indicates the display name of the target service.</span></span> |
|<span data-ttu-id="60c6d-130">Path</span><span class="sxs-lookup"><span data-stu-id="60c6d-130">Path</span></span> |<span data-ttu-id="60c6d-131">Indica il percorso del file binario per un nuovo servizio.</span><span class="sxs-lookup"><span data-stu-id="60c6d-131">Indicates the path to the binary file for a new service.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="60c6d-132">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="60c6d-132">Common properties</span></span>

|<span data-ttu-id="60c6d-133">Proprietà</span><span class="sxs-lookup"><span data-stu-id="60c6d-133">Property</span></span> |<span data-ttu-id="60c6d-134">Description</span><span class="sxs-lookup"><span data-stu-id="60c6d-134">Description</span></span> |
|---|---|
|<span data-ttu-id="60c6d-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="60c6d-135">DependsOn</span></span> |<span data-ttu-id="60c6d-136">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="60c6d-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="60c6d-137">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="60c6d-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="60c6d-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="60c6d-138">Ensure</span></span> |<span data-ttu-id="60c6d-139">Indica se il servizio di destinazione è presente nel sistema.</span><span class="sxs-lookup"><span data-stu-id="60c6d-139">Indicates whether the target service exists on the system.</span></span> <span data-ttu-id="60c6d-140">Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste.</span><span class="sxs-lookup"><span data-stu-id="60c6d-140">Set this property to **Absent** to ensure that the target service does not exist.</span></span> <span data-ttu-id="60c6d-141">Impostando il valore su **Present** ci si assicura che il servizio di destinazione esista.</span><span class="sxs-lookup"><span data-stu-id="60c6d-141">Setting it to **Present** ensures that target service exists.</span></span> <span data-ttu-id="60c6d-142">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="60c6d-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="60c6d-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="60c6d-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="60c6d-144">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="60c6d-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="60c6d-145">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="60c6d-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="60c6d-146">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="60c6d-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="60c6d-147">Esempio</span><span class="sxs-lookup"><span data-stu-id="60c6d-147">Example</span></span>

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