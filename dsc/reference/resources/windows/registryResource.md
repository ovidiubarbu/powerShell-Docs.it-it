---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682259"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="6654f-103">Risorsa Registry DSC</span><span class="sxs-lookup"><span data-stu-id="6654f-103">DSC Registry Resource</span></span>

<span data-ttu-id="6654f-104">_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="6654f-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="6654f-105">La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="6654f-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6654f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6654f-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="6654f-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6654f-107">Properties</span></span>

| <span data-ttu-id="6654f-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="6654f-108">Property</span></span> | <span data-ttu-id="6654f-109">Description</span><span class="sxs-lookup"><span data-stu-id="6654f-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="6654f-110">Key</span><span class="sxs-lookup"><span data-stu-id="6654f-110">Key</span></span>| <span data-ttu-id="6654f-111">Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="6654f-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="6654f-112">Questo percorso deve includere l'hive.</span><span class="sxs-lookup"><span data-stu-id="6654f-112">This path must include the hive.</span></span>|
| <span data-ttu-id="6654f-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="6654f-113">ValueName</span></span>| <span data-ttu-id="6654f-114">Indica il nome del valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="6654f-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="6654f-115">Per aggiungere o rimuovere una chiave del Registro di sistema specificare questa proprietà come stringa vuota, senza specificare ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="6654f-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="6654f-116">Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema specificare questa proprietà come stringa vuota e specificare ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="6654f-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="6654f-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="6654f-117">Ensure</span></span>| <span data-ttu-id="6654f-118">Indica se la chiave e il valore esistono.</span><span class="sxs-lookup"><span data-stu-id="6654f-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="6654f-119">Impostare questa proprietà su "Present" per specificare che la chiave e il valore esistono.</span><span class="sxs-lookup"><span data-stu-id="6654f-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="6654f-120">Impostare questa proprietà su "Absent" per specificare che la chiave e il valore non esistono.</span><span class="sxs-lookup"><span data-stu-id="6654f-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="6654f-121">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="6654f-121">The default value is "Present".</span></span>|
| <span data-ttu-id="6654f-122">Force</span><span class="sxs-lookup"><span data-stu-id="6654f-122">Force</span></span>| <span data-ttu-id="6654f-123">Se la chiave del Registro di sistema è presente, **Force** la sovrascrive con il nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="6654f-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="6654f-124">Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere **$true**.</span><span class="sxs-lookup"><span data-stu-id="6654f-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="6654f-125">Hex</span><span class="sxs-lookup"><span data-stu-id="6654f-125">Hex</span></span>| <span data-ttu-id="6654f-126">Indica se i dati verranno espressi in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="6654f-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="6654f-127">Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="6654f-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="6654f-128">La proprietà non è valida per altri tipi.</span><span class="sxs-lookup"><span data-stu-id="6654f-128">Not valid for other types.</span></span> <span data-ttu-id="6654f-129">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="6654f-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="6654f-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6654f-130">DependsOn</span></span>| <span data-ttu-id="6654f-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="6654f-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6654f-132">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="6654f-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="6654f-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="6654f-133">ValueData</span></span>| <span data-ttu-id="6654f-134">Dati per il valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="6654f-134">The data for the registry value.</span></span>|
| <span data-ttu-id="6654f-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="6654f-135">ValueType</span></span>| <span data-ttu-id="6654f-136">Indica il tipo di valore.</span><span class="sxs-lookup"><span data-stu-id="6654f-136">Indicates the type of the value.</span></span> <span data-ttu-id="6654f-137">I tipi supportati sono: Stringa (REG_SZ), file binario (REG-BINARY), Dword 32 bit (REG_DWORD), Qword 64-bit (REG_QWORD), multistringa (REG_MULTI_SZ), stringa espandibile (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="6654f-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="6654f-138">Esempio</span><span class="sxs-lookup"><span data-stu-id="6654f-138">Example</span></span>

<span data-ttu-id="6654f-139">Questo esempio garantisce che sia presente una chiave denominata "ExampleKey" nell'hive **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="6654f-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="6654f-140">La modifica di un'impostazione del Registro di sistema nell'hive `HKEY\CURRENT\USER` richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema.</span><span class="sxs-lookup"><span data-stu-id="6654f-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="6654f-141">È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="6654f-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="6654f-142">Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="6654f-142">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
