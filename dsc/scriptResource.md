---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Script DSC
ms.openlocfilehash: 3824cbf48d980069b923d91e1fa24739e5d4e617
ms.sourcegitcommit: 378c7ed4e8c8c1c5fe71417b9ba672a4c990630b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="dsc-script-resource"></a><span data-ttu-id="35d19-103">Risorsa Script DSC</span><span class="sxs-lookup"><span data-stu-id="35d19-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="35d19-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="35d19-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="35d19-105">La risorsa **Script** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire blocchi script di Windows PowerShell nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="35d19-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="35d19-106">La risorsa `Script` dispone delle proprietà `GetScript`, `SetScript` e `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="35d19-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="35d19-107">Queste proprietà devono essere impostate per i blocchi di script che verranno eseguiti in ogni nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="35d19-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="35d19-108">Il blocco di script `GetScript` deve restituire una tabella hash che rappresenta lo stato del nodo corrente.</span><span class="sxs-lookup"><span data-stu-id="35d19-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="35d19-109">La tabella hash deve contenere solo una chiave `Result` e il valore deve essere di tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="35d19-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="35d19-110">Non è necessario restituire alcun valore.</span><span class="sxs-lookup"><span data-stu-id="35d19-110">It is not required to return anything.</span></span> <span data-ttu-id="35d19-111">DSC non esegue alcuna operazione con l'output di questo blocco di script.</span><span class="sxs-lookup"><span data-stu-id="35d19-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="35d19-112">Il blocco di script `TestScript` dovrebbe indicare se il nodo corrente necessita di modifica.</span><span class="sxs-lookup"><span data-stu-id="35d19-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="35d19-113">Il blocco restituirà `$true` se il nodo è aggiornato.</span><span class="sxs-lookup"><span data-stu-id="35d19-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="35d19-114">Il blocco restituirà `$false` se la configurazione del nodo non è aggiornata e deve essere aggiornata per il blocco di script `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="35d19-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="35d19-115">Il blocco di script `TestScript` viene chiamato da DSC.</span><span class="sxs-lookup"><span data-stu-id="35d19-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="35d19-116">Il blocco di script `SetScript` deve modificare il nodo.</span><span class="sxs-lookup"><span data-stu-id="35d19-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="35d19-117">Se il blocco `TestScript` restituisce `$false`, viene chiamato da DSC.</span><span class="sxs-lookup"><span data-stu-id="35d19-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="35d19-118">Se è necessario usare le variabili dallo script di configurazione nei blocchi di script `GetScript`, `TestScript` o `SetScript`, usare l'ambito `$using:` (vedere l'esempio di seguito).</span><span class="sxs-lookup"><span data-stu-id="35d19-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="35d19-119">Sintassi</span><span class="sxs-lookup"><span data-stu-id="35d19-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="35d19-120">Proprietà</span><span class="sxs-lookup"><span data-stu-id="35d19-120">Properties</span></span>

|  <span data-ttu-id="35d19-121">Proprietà</span><span class="sxs-lookup"><span data-stu-id="35d19-121">Property</span></span>  |  <span data-ttu-id="35d19-122">Description</span><span class="sxs-lookup"><span data-stu-id="35d19-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="35d19-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="35d19-123">GetScript</span></span>| <span data-ttu-id="35d19-124">Fornisce un blocco script di Windows PowerShell eseguito quando si richiama il cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx).</span><span class="sxs-lookup"><span data-stu-id="35d19-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="35d19-125">Questo blocco deve restituire una tabella hash.</span><span class="sxs-lookup"><span data-stu-id="35d19-125">This block must return a hashtable.</span></span> <span data-ttu-id="35d19-126">La tabella hash deve contenere solo una chiave **Result** e il valore deve essere di tipo **String**.</span><span class="sxs-lookup"><span data-stu-id="35d19-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="35d19-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="35d19-127">SetScript</span></span>| <span data-ttu-id="35d19-128">Fornisce un blocco script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35d19-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="35d19-129">Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), il blocco **TestScript** viene eseguito per primo.</span><span class="sxs-lookup"><span data-stu-id="35d19-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="35d19-130">Se il blocco **TestScript** restituisce **$false**, il blocco **SetScript** viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="35d19-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="35d19-131">Se il blocco **TestScript** restituisce **$true**, il blocco **SetScript** non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="35d19-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="35d19-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="35d19-132">TestScript</span></span>| <span data-ttu-id="35d19-133">Fornisce un blocco script di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35d19-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="35d19-134">Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), questo blocco viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="35d19-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="35d19-135">Se restituisce **$false**, il blocco SetScript viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="35d19-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="35d19-136">Se restituisce **$true**, il blocco SetScript non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="35d19-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="35d19-137">Il blocco **TestScript** viene eseguito anche quando si richiama il cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="35d19-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="35d19-138">In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal valore restituito dal blocco TestScript.</span><span class="sxs-lookup"><span data-stu-id="35d19-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="35d19-139">Il blocco **TestScript** deve restituire True se l'effettiva configurazione corrisponde alla configurazione dello stato desiderato corrente e False in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="35d19-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="35d19-140">La configurazione dello stato desiderato corrente è l'ultima configurazione applicata nel nodo che usa DSC.</span><span class="sxs-lookup"><span data-stu-id="35d19-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="35d19-141">Credential</span><span class="sxs-lookup"><span data-stu-id="35d19-141">Credential</span></span>| <span data-ttu-id="35d19-142">Indica le credenziali da usare per l'esecuzione dello script, se sono necessarie credenziali.</span><span class="sxs-lookup"><span data-stu-id="35d19-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="35d19-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="35d19-143">DependsOn</span></span>| <span data-ttu-id="35d19-144">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="35d19-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="35d19-145">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="35d19-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="35d19-146">Esempio 1</span><span class="sxs-lookup"><span data-stu-id="35d19-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="35d19-147">Esempio 2</span><span class="sxs-lookup"><span data-stu-id="35d19-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="35d19-148">Questa risorsa scrive la versione della configurazione di un file di testo.</span><span class="sxs-lookup"><span data-stu-id="35d19-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="35d19-149">Questa versione è disponibile nel computer client, ma non su tutti i nodi, quindi deve essere passata su tutti i blocchi di script della risorsa `Script` con l'ambito `using` di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35d19-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="35d19-150">Durante la generazione del file MOF del nodo, il valore della variabile `$version` viene letto da un file di testo nel computer client.</span><span class="sxs-lookup"><span data-stu-id="35d19-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="35d19-151">DSC sostituisce le variabili `$using:version` in ogni blocco di script con il valore della variabile `$version`.</span><span class="sxs-lookup"><span data-stu-id="35d19-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

