---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: 98e9a6251cb4e55443498bd770b4c563c25c7509
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="37dd1-103">Risorsa Registry DSC</span><span class="sxs-lookup"><span data-stu-id="37dd1-103">DSC Registry Resource</span></span>

> <span data-ttu-id="37dd1-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="37dd1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="37dd1-105">La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="37dd1-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="37dd1-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="37dd1-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="37dd1-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="37dd1-107">Properties</span></span>
|  <span data-ttu-id="37dd1-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="37dd1-108">Property</span></span>  |  <span data-ttu-id="37dd1-109">Description</span><span class="sxs-lookup"><span data-stu-id="37dd1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="37dd1-110">Key</span><span class="sxs-lookup"><span data-stu-id="37dd1-110">Key</span></span>| <span data-ttu-id="37dd1-111">Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato.</span><span class="sxs-lookup"><span data-stu-id="37dd1-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="37dd1-112">Questo percorso deve includere l'hive.</span><span class="sxs-lookup"><span data-stu-id="37dd1-112">This path must include the hive.</span></span>|
| <span data-ttu-id="37dd1-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="37dd1-113">ValueName</span></span>| <span data-ttu-id="37dd1-114">Indica il nome del valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="37dd1-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="37dd1-115">Per aggiungere o rimuovere una chiave del Registro di sistema specificare questa proprietà come stringa vuota, senza specificare ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="37dd1-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="37dd1-116">Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema specificare questa proprietà come stringa vuota e specificare ValueType o ValueData.</span><span class="sxs-lookup"><span data-stu-id="37dd1-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="37dd1-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="37dd1-117">Ensure</span></span>| <span data-ttu-id="37dd1-118">Indica se la chiave e il valore esistono.</span><span class="sxs-lookup"><span data-stu-id="37dd1-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="37dd1-119">Impostare questa proprietà su "Present" per specificare che la chiave e il valore esistono.</span><span class="sxs-lookup"><span data-stu-id="37dd1-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="37dd1-120">Impostare questa proprietà su "Absent" per specificare che la chiave e il valore non esistono.</span><span class="sxs-lookup"><span data-stu-id="37dd1-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="37dd1-121">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="37dd1-121">The default value is "Present".</span></span>|
| <span data-ttu-id="37dd1-122">Force</span><span class="sxs-lookup"><span data-stu-id="37dd1-122">Force</span></span>| <span data-ttu-id="37dd1-123">Se la chiave del Registro di sistema è presente, __Force__ la sovrascrive con il nuovo valore.</span><span class="sxs-lookup"><span data-stu-id="37dd1-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="37dd1-124">Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere __$true__.</span><span class="sxs-lookup"><span data-stu-id="37dd1-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="37dd1-125">Hex</span><span class="sxs-lookup"><span data-stu-id="37dd1-125">Hex</span></span>| <span data-ttu-id="37dd1-126">Indica se i dati verranno espressi in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="37dd1-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="37dd1-127">Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale.</span><span class="sxs-lookup"><span data-stu-id="37dd1-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="37dd1-128">La proprietà non è valida per altri tipi.</span><span class="sxs-lookup"><span data-stu-id="37dd1-128">Not valid for other types.</span></span> <span data-ttu-id="37dd1-129">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="37dd1-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="37dd1-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="37dd1-130">DependsOn</span></span>| <span data-ttu-id="37dd1-131">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="37dd1-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="37dd1-132">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="37dd1-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="37dd1-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="37dd1-133">ValueData</span></span>| <span data-ttu-id="37dd1-134">Dati per il valore del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="37dd1-134">The data for the registry value.</span></span>|
| <span data-ttu-id="37dd1-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="37dd1-135">ValueType</span></span>| <span data-ttu-id="37dd1-136">Indica il tipo di valore.</span><span class="sxs-lookup"><span data-stu-id="37dd1-136">Indicates the type of the value.</span></span> <span data-ttu-id="37dd1-137">I tipi supportati sono:</span><span class="sxs-lookup"><span data-stu-id="37dd1-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="37dd1-138">Stringa (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="37dd1-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="37dd1-139">Binario (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="37dd1-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="37dd1-140">Dword a 32 bit (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="37dd1-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="37dd1-141">Qword a 64 bit (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="37dd1-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="37dd1-142">Multistringa (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="37dd1-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="37dd1-143">Stringa espandibile (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="37dd1-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="37dd1-144">Esempio</span><span class="sxs-lookup"><span data-stu-id="37dd1-144">Example</span></span>
<span data-ttu-id="37dd1-145">Questo esempio garantisce che sia presente una chiave denominata "ExampleKey" nell'hive **HKEY\_LOCAL\_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="37dd1-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="37dd1-146">**Nota:** la modifica di un'impostazione del Registro di sistema nell'hive **HKEY\_CURRENT\_USER** richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema.</span><span class="sxs-lookup"><span data-stu-id="37dd1-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="37dd1-147">È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="37dd1-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="37dd1-148">Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="37dd1-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>
