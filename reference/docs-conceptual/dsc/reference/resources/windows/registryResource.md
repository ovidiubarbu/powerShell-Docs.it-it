---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953078"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="51a55-103">Risorsa Registry DSC</span><span class="sxs-lookup"><span data-stu-id="51a55-103">DSC Registry Resource</span></span>

> <span data-ttu-id="51a55-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="51a55-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="51a55-105">La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="51a55-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="51a55-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="51a55-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="51a55-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="51a55-107">Properties</span></span>

|<span data-ttu-id="51a55-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="51a55-108">Property</span></span> |<span data-ttu-id="51a55-109">Descrizione</span><span class="sxs-lookup"><span data-stu-id="51a55-109">Description</span></span> |
|---|---|
|<span data-ttu-id="51a55-110">Chiave</span><span class="sxs-lookup"><span data-stu-id="51a55-110">Key</span></span> |<span data-ttu-id="51a55-111">Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="51a55-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="51a55-112">Questo percorso deve includere l'hive.</span><span class="sxs-lookup"><span data-stu-id="51a55-112">This path must include the hive.</span></span> |
|<span data-ttu-id="51a55-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="51a55-113">ValueName</span></span> |<span data-ttu-id="51a55-114">Indica il nome del valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="51a55-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="51a55-115">Per aggiungere o rimuovere una chiave del Registro di sistema, specificare questa proprietà come stringa vuota, senza specificare **ValueType** o **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="51a55-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="51a55-116">Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema, specificare questa proprietà come stringa vuota e specificare anche **ValueType** o **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="51a55-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="51a55-117">Force</span><span class="sxs-lookup"><span data-stu-id="51a55-117">Force</span></span> |<span data-ttu-id="51a55-118">Se la chiave del Registro di sistema è presente, **Force** la sovrascrive con il nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="51a55-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="51a55-119">Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere `$true`.</span><span class="sxs-lookup"><span data-stu-id="51a55-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="51a55-120">Hex</span><span class="sxs-lookup"><span data-stu-id="51a55-120">Hex</span></span> |<span data-ttu-id="51a55-121">Indica se i dati verranno espressi in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="51a55-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="51a55-122">Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="51a55-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="51a55-123">La proprietà non è valida per altri tipi.</span><span class="sxs-lookup"><span data-stu-id="51a55-123">Not valid for other types.</span></span> <span data-ttu-id="51a55-124">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="51a55-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="51a55-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="51a55-125">ValueData</span></span> |<span data-ttu-id="51a55-126">Dati per il valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="51a55-126">The data for the registry value.</span></span> |
|<span data-ttu-id="51a55-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="51a55-127">ValueType</span></span> |<span data-ttu-id="51a55-128">Indica il tipo di valore.</span><span class="sxs-lookup"><span data-stu-id="51a55-128">Indicates the type of the value.</span></span> <span data-ttu-id="51a55-129">I tipi supportati sono: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (REG_DWORD a 32 bit), **Qword** (REG_QWORD a 64 bit), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="51a55-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="51a55-130">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="51a55-130">Common properties</span></span>

|<span data-ttu-id="51a55-131">Proprietà</span><span class="sxs-lookup"><span data-stu-id="51a55-131">Property</span></span> |<span data-ttu-id="51a55-132">Descrizione</span><span class="sxs-lookup"><span data-stu-id="51a55-132">Description</span></span> |
|---|---|
|<span data-ttu-id="51a55-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51a55-133">DependsOn</span></span> |<span data-ttu-id="51a55-134">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="51a55-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51a55-135">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51a55-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="51a55-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="51a55-136">Ensure</span></span> |<span data-ttu-id="51a55-137">Indica se la chiave e il valore esistono.</span><span class="sxs-lookup"><span data-stu-id="51a55-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="51a55-138">Impostare questa proprietà su **Present** per assicurarsi che esistano.</span><span class="sxs-lookup"><span data-stu-id="51a55-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="51a55-139">Impostare questa proprietà su **Absent** per assicurarsi che non esistano.</span><span class="sxs-lookup"><span data-stu-id="51a55-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="51a55-140">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="51a55-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="51a55-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="51a55-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="51a55-142">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="51a55-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="51a55-143">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="51a55-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="51a55-144">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="51a55-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="51a55-145">Esempio</span><span class="sxs-lookup"><span data-stu-id="51a55-145">Example</span></span>

<span data-ttu-id="51a55-146">Questo esempio garantisce che sia presente una chiave denominata "ExampleKey" nell'hive **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="51a55-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="51a55-147">La modifica di un'impostazione del Registro di sistema nell'hive `HKEY_CURRENT_USER` richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema.</span><span class="sxs-lookup"><span data-stu-id="51a55-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="51a55-148">È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="51a55-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="51a55-149">Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="51a55-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>