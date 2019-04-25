---
ms.date: 08/24/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Script DSC
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076991"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="59055-103">Risorsa Script DSC</span><span class="sxs-lookup"><span data-stu-id="59055-103">DSC Script Resource</span></span>

> <span data-ttu-id="59055-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="59055-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="59055-105">La risorsa **Script** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire blocchi script di Windows PowerShell nei nodi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="59055-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="59055-106">La risorsa **Script** usa le proprietà `GetScript`, `SetScript` e `TestScript` che contengono blocchi di script definiti per eseguire le operazioni per lo stato DSC corrispondente.</span><span class="sxs-lookup"><span data-stu-id="59055-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="59055-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="59055-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="59055-108">I blocchi `GetScript`, `TestScript` e `SetScript` vengono archiviati come stringhe.</span><span class="sxs-lookup"><span data-stu-id="59055-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="59055-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="59055-109">Properties</span></span>

|<span data-ttu-id="59055-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="59055-110">Property</span></span>|<span data-ttu-id="59055-111">Description</span><span class="sxs-lookup"><span data-stu-id="59055-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="59055-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="59055-112">GetScript</span></span>|<span data-ttu-id="59055-113">Blocco di script che restituisce lo stato corrente del nodo.</span><span class="sxs-lookup"><span data-stu-id="59055-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="59055-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="59055-114">SetScript</span></span>|<span data-ttu-id="59055-115">Blocco di script usato da DSC per garantire la conformità quando il nodo non è nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="59055-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="59055-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="59055-116">TestScript</span></span>|<span data-ttu-id="59055-117">Blocco di script che determina se il nodo è nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="59055-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="59055-118">Credential</span><span class="sxs-lookup"><span data-stu-id="59055-118">Credential</span></span>| <span data-ttu-id="59055-119">Indica le credenziali da usare per l'esecuzione dello script, se sono necessarie credenziali.</span><span class="sxs-lookup"><span data-stu-id="59055-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="59055-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="59055-120">DependsOn</span></span>| <span data-ttu-id="59055-121">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="59055-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="59055-122">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="59055-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="59055-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="59055-123">GetScript</span></span>

<span data-ttu-id="59055-124">DSC non usa l'output generato da `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="59055-125">Il cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) esegue `GetScript` per recuperare lo stato corrente di un nodo.</span><span class="sxs-lookup"><span data-stu-id="59055-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="59055-126">Non è necessario che venga restituito un valore da `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="59055-127">Se si specifica un valore restituito, deve essere un valore `hashtable` contenente una chiave **Result** con valore `String`.</span><span class="sxs-lookup"><span data-stu-id="59055-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="59055-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="59055-128">TestScript</span></span>

<span data-ttu-id="59055-129">Il blocco di script `TestScript` viene eseguito da DSC per determinare se eseguire `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="59055-130">Se `TestScript` restituisce `$false`, DSC esegue `SetScript` per riportare il nodo allo stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="59055-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="59055-131">Deve restituire un valore `boolean`.</span><span class="sxs-lookup"><span data-stu-id="59055-131">It must return a `boolean` value.</span></span> <span data-ttu-id="59055-132">Se il risultato è `$true`, il nodo è conforme e non è necessario eseguire `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="59055-133">Il cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) esegue `TestScript` per recuperare la conformità dei nodi alle risorse **Script**.</span><span class="sxs-lookup"><span data-stu-id="59055-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="59055-134">Tuttavia, in questo caso il blocco `SetScript` non viene eseguito, indipendentemente dall'output restituito dal blocco `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="59055-135">Tutto l'output restituito da `TestScript` fa parte del valore restituito.</span><span class="sxs-lookup"><span data-stu-id="59055-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="59055-136">PowerShell interpreta l'output non eliminato come diverso da zero e questo significa che `TestScript` restituisce `$true` indipendentemente dallo stato del nodo.</span><span class="sxs-lookup"><span data-stu-id="59055-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="59055-137">Questo comportamento provoca risultati imprevedibili, falsi positivi e difficoltà durante la risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="59055-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="59055-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="59055-138">SetScript</span></span>

<span data-ttu-id="59055-139">`SetScript` modifica il nodo per applicare lo stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="59055-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="59055-140">Il blocco viene chiamato da DSC se il blocco di script `TestScript` restituisce `$false`.</span><span class="sxs-lookup"><span data-stu-id="59055-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="59055-141">`SetScript` non deve avere alcun valore restituito.</span><span class="sxs-lookup"><span data-stu-id="59055-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="59055-142">Esempi</span><span class="sxs-lookup"><span data-stu-id="59055-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="59055-143">Esempio 1: Scrivere testo di esempio tramite una risorsa Script</span><span class="sxs-lookup"><span data-stu-id="59055-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="59055-144">Questo esempio testa la presenza di `C:\TempFolder\TestFile.txt` in ogni nodo.</span><span class="sxs-lookup"><span data-stu-id="59055-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="59055-145">Se il file non esiste, viene creato tramite `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="59055-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="59055-146">`GetScript` restituisce il contenuto del file, senza usare il valore restituito.</span><span class="sxs-lookup"><span data-stu-id="59055-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="59055-147">Esempio 2: Confrontare le informazioni sulla versione tramite una risorsa Script</span><span class="sxs-lookup"><span data-stu-id="59055-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="59055-148">Questo esempio recupera informazioni sulla versione *conforme* da un file di testo nel computer di creazione e le archivia nella variabile `$version`.</span><span class="sxs-lookup"><span data-stu-id="59055-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="59055-149">Durante la generazione del file MOF del nodo, DSC sostituisce le variabili `$using:version` in ogni blocco di script con il valore della variabile `$version`.</span><span class="sxs-lookup"><span data-stu-id="59055-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="59055-150">Durante l'esecuzione, la versione *conforme* viene archiviata in un file di testo in ogni nodo e confrontata e aggiornata nelle esecuzioni successive.</span><span class="sxs-lookup"><span data-stu-id="59055-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```
