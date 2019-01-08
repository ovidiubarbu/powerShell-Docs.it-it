---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, raccolta, il programma di installazione
title: Aggiungere parametri a una configurazione
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401429"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="10028-103">Aggiungere parametri a una configurazione</span><span class="sxs-lookup"><span data-stu-id="10028-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="10028-104">Ad esempio le funzioni [configurazioni](configurations.md) può essere parametrizzata per consentire più dinamiche configurazioni basate sull'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="10028-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="10028-105">I passaggi sono simili a quelle descritte nel [le funzioni con parametri](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="10028-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="10028-106">In questo esempio inizia con una configurazione di base che consente di configurare il servizio "Spooler" in "Esecuzione".</span><span class="sxs-lookup"><span data-stu-id="10028-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="10028-107">Parametri di configurazione predefiniti</span><span class="sxs-lookup"><span data-stu-id="10028-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="10028-108">A differenza di una funzione, tuttavia, il [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attributo non aggiunge alcuna funzionalità.</span><span class="sxs-lookup"><span data-stu-id="10028-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="10028-109">Oltre a [parametri comuni](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configurazioni anche possono usare quanto segue compilata nei parametri, senza che sia necessario definirli.</span><span class="sxs-lookup"><span data-stu-id="10028-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="10028-110">Parametro</span><span class="sxs-lookup"><span data-stu-id="10028-110">Parameter</span></span>  |<span data-ttu-id="10028-111">Description</span><span class="sxs-lookup"><span data-stu-id="10028-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="10028-112">Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="10028-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="10028-113">Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="10028-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="10028-114">Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="10028-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="10028-115">Consente di passare in strutturato [i dati di configurazione](configData.md) per l'uso nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="10028-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="10028-116">Consente di specificare dove il "\<computername\>MOF" file verrà compilate</span><span class="sxs-lookup"><span data-stu-id="10028-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="10028-117">Aggiungere i propri parametri alle configurazioni</span><span class="sxs-lookup"><span data-stu-id="10028-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="10028-118">Oltre ai parametri predefiniti, è anche possibile aggiungere i propri parametri alle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="10028-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="10028-119">Il blocco dei parametri viene indirizzato direttamente all'interno della dichiarazione di configurazione, proprio come una funzione.</span><span class="sxs-lookup"><span data-stu-id="10028-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="10028-120">Un blocco del parametro di configurazione deve essere di fuori di qualsiasi **nodo** dichiarazioni e versioni successive qualsiasi *importare* istruzioni.</span><span class="sxs-lookup"><span data-stu-id="10028-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="10028-121">Quando si aggiungono parametri, è possibile apportare le configurazioni più affidabile e dinamica.</span><span class="sxs-lookup"><span data-stu-id="10028-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="10028-122">Aggiungere un parametro ComputerName</span><span class="sxs-lookup"><span data-stu-id="10028-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="10028-123">Il primo parametro è possibile aggiungere è un `-Computername` parametro affinché sia possibile compilare dinamicamente un file "con estensione MOF" per qualsiasi `-Computername` si passa alla propria configurazione.</span><span class="sxs-lookup"><span data-stu-id="10028-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="10028-124">Ad esempio funzioni, è inoltre possibile definire un valore predefinito, nel caso in cui l'utente non supera un valore per `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="10028-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="10028-125">All'interno della configurazione, è quindi possibile specificare il `-ComputerName` parametro quando si definisce il blocco del nodo.</span><span class="sxs-lookup"><span data-stu-id="10028-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="10028-126">Chiamare la configurazione con parametri</span><span class="sxs-lookup"><span data-stu-id="10028-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="10028-127">Dopo aver aggiunto i parametri per la configurazione, è possibile usarli come si farebbe con un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="10028-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="10028-128">La compilazione di più file con estensione MOF</span><span class="sxs-lookup"><span data-stu-id="10028-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="10028-129">Il blocco del nodo può anche accettare un elenco delimitato da virgole di nomi di computer e genererà file "MOF" per ciascuno.</span><span class="sxs-lookup"><span data-stu-id="10028-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="10028-130">È possibile eseguire l'esempio seguente per generare i file "MOF" per tutti i computer passati al `-ComputerName` parametro.</span><span class="sxs-lookup"><span data-stu-id="10028-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="10028-131">Parametri avanzati nelle configurazioni</span><span class="sxs-lookup"><span data-stu-id="10028-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="10028-132">Oltre a un `-ComputerName` parametro, è possibile aggiungere parametri per il nome del servizio e lo stato.</span><span class="sxs-lookup"><span data-stu-id="10028-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="10028-133">L'esempio seguente aggiunge un blocco di parametri con un `-ServiceName` parametro e lo usa per definire in modo dinamico il **servizio** blocco di risorse.</span><span class="sxs-lookup"><span data-stu-id="10028-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="10028-134">Aggiunge anche un `-State` parametro per definire in modo dinamico il **stato** nel **servizio** blocco di risorse.</span><span class="sxs-lookup"><span data-stu-id="10028-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="10028-135">In più scenari advacned, potrebbe essere più utile per spostare i dati dinamici in un structured [i dati di configurazione](configData.md).</span><span class="sxs-lookup"><span data-stu-id="10028-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="10028-136">Nell'esempio di configurazione ora accetta una dinamica `$ServiceName`, ma se non è specificato, la compilazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="10028-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="10028-137">È possibile aggiungere valore predefinito è simile all'esempio.</span><span class="sxs-lookup"><span data-stu-id="10028-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="10028-138">In questo caso, tuttavia, è più opportuno forzare semplicemente all'utente di specificare un valore per il `$ServiceName` parametro.</span><span class="sxs-lookup"><span data-stu-id="10028-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="10028-139">Il `parameter` attributo consente di aggiungere ulteriore convalida e la pipeline supportano ai parametri di configurazione.</span><span class="sxs-lookup"><span data-stu-id="10028-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="10028-140">Di sopra di qualsiasi dichiarazione di parametro, aggiungere il `parameter` blocco di attributi come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="10028-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="10028-141">È possibile specificare argomenti a ogni `parameter` attributo, per controllare gli aspetti del parametro definito.</span><span class="sxs-lookup"><span data-stu-id="10028-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="10028-142">Nell'esempio seguente viene eseguita la `$ServiceName` una **obbligatorio** parametro.</span><span class="sxs-lookup"><span data-stu-id="10028-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="10028-143">Per il `$State` parametro, siamo lieti di impedire all'utente di specificare i valori di fuori di un set predefinito (come in esecuzione, arrestato) il `ValidationSet*`attributo impedirebbe l'utente che specifica i valori di fuori di un set predefinito (ad esempio, in esecuzione, Arrestato).</span><span class="sxs-lookup"><span data-stu-id="10028-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="10028-144">L'esempio seguente aggiunge il `ValidationSet` dell'attributo di `$State` parametro.</span><span class="sxs-lookup"><span data-stu-id="10028-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="10028-145">Poiché non vogliamo rendere la `$State` parametro **obbligatorio**, è necessario aggiungere un valore predefinito per tale.</span><span class="sxs-lookup"><span data-stu-id="10028-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="10028-146">Non è necessario specificare una `parameter` attributo quando si usa un `validation` attributo.</span><span class="sxs-lookup"><span data-stu-id="10028-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="10028-147">Altre informazioni, vedere la `parameter` e gli attributi di convalida nel [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="10028-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="10028-148">Configurazione completa con parametri</span><span class="sxs-lookup"><span data-stu-id="10028-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="10028-149">È ora disponibile una configurazione con parametri che impone all'utente di specificare una `-InstanceName`, `-ServiceName`e convalida il `-State` parametro.</span><span class="sxs-lookup"><span data-stu-id="10028-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="10028-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="10028-150">See also</span></span>

- [<span data-ttu-id="10028-151">Scrivere informazioni della Guida per le configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="10028-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="10028-152">Configurazione dinamica</span><span class="sxs-lookup"><span data-stu-id="10028-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="10028-153">Usare i dati di configurazione nelle configurazioni</span><span class="sxs-lookup"><span data-stu-id="10028-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="10028-154">Dati di configurazione e dell'ambiente separato</span><span class="sxs-lookup"><span data-stu-id="10028-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
