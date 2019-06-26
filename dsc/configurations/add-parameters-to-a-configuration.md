---
ms.date: 12/12/2018
keywords: dsc,powershell,risorsa,raccolta,configurazione
title: Aggiungere parametri a una configurazione
ms.openlocfilehash: 514bb4cf82b7adbe4cd3d3e34d5464f574cb2206
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301522"
---
# <a name="add-parameters-to-a-configuration"></a><span data-ttu-id="942d4-103">Aggiungere parametri a una configurazione</span><span class="sxs-lookup"><span data-stu-id="942d4-103">Add Parameters to a Configuration</span></span>

<span data-ttu-id="942d4-104">Così come le Funzioni, le [Configurazioni](configurations.md) possono essere parametrizzate per consentire configurazioni più dinamiche basate sull'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="942d4-104">Like Functions, [Configurations](configurations.md) can be parameterized to allow more dynamic configurations based on user input.</span></span> <span data-ttu-id="942d4-105">I passaggi sono simili a quelli descritti nelle [funzioni con parametri](/powershell/module/microsoft.powershell.core/about/about_functions).</span><span class="sxs-lookup"><span data-stu-id="942d4-105">The steps are similar to those described in [Functions with Parameters](/powershell/module/microsoft.powershell.core/about/about_functions).</span></span>

<span data-ttu-id="942d4-106">Questo esempio inizia con una configurazione di base che configura il servizio "Spooler" in "Esecuzione".</span><span class="sxs-lookup"><span data-stu-id="942d4-106">This example starts with a basic Configuration that configures the "Spooler" service to be "Running".</span></span>

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

## <a name="built-in-configuration-parameters"></a><span data-ttu-id="942d4-107">Parametri di configurazione predefiniti</span><span class="sxs-lookup"><span data-stu-id="942d4-107">Built-in Configuration parameters</span></span>

<span data-ttu-id="942d4-108">Diversamente da una funzione, tuttavia, l'attributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) non aggiunge alcuna funzionalità.</span><span class="sxs-lookup"><span data-stu-id="942d4-108">Unlike a Function though, the [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attribute adds no functionality.</span></span> <span data-ttu-id="942d4-109">Oltre ai [parametri comuni](/powershell/module/microsoft.powershell.core/about/about_commonparameters), le configurazioni possono anche usare i seguenti parametri predefiniti, senza che sia necessario definirli.</span><span class="sxs-lookup"><span data-stu-id="942d4-109">In addition to [Common Parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters), Configurations can also use the following built in parameters, without requiring you to define them.</span></span>

|<span data-ttu-id="942d4-110">Parametro</span><span class="sxs-lookup"><span data-stu-id="942d4-110">Parameter</span></span>  |<span data-ttu-id="942d4-111">Description</span><span class="sxs-lookup"><span data-stu-id="942d4-111">Description</span></span>  |
|---------|---------|
|`-InstanceName`|<span data-ttu-id="942d4-112">Usato nella definizione delle [configurazioni composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="942d4-112">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-DependsOn`|<span data-ttu-id="942d4-113">Usato nella definizione delle [configurazioni composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="942d4-113">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-PSDSCRunAsCredential`|<span data-ttu-id="942d4-114">Usato nella definizione delle [configurazioni composite](compositeconfigs.md)</span><span class="sxs-lookup"><span data-stu-id="942d4-114">Used in defining [Composite Configurations](compositeconfigs.md)</span></span>|
|`-ConfigurationData`|<span data-ttu-id="942d4-115">Usato per passare i [ dati di configurazione](configData.md) strutturati per l'uso nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="942d4-115">Used to pass in structured [Configuration Data](configData.md) for use in the Configuration.</span></span>|
|`-OutputPath`|<span data-ttu-id="942d4-116">Usato per specificare dove verrà compilato il file "\<computername\>.mof"</span><span class="sxs-lookup"><span data-stu-id="942d4-116">Used to specify where your "\<computername\>.mof" file will be compiled</span></span>|

## <a name="adding-your-own-parameters-to-configurations"></a><span data-ttu-id="942d4-117">Aggiungere parametri definiti dall'utente alle configurazioni</span><span class="sxs-lookup"><span data-stu-id="942d4-117">Adding your own parameters to Configurations</span></span>

<span data-ttu-id="942d4-118">Oltre ai parametri predefiniti, è anche possibile aggiungere alle configurazioni parametri definiti dall'utente.</span><span class="sxs-lookup"><span data-stu-id="942d4-118">In addition to the built-in parameters, you can also add your own parameters to your Configurations.</span></span> <span data-ttu-id="942d4-119">Il blocco dei parametri viene indirizzato direttamente alla dichiarazione di configurazione, proprio come una funzione.</span><span class="sxs-lookup"><span data-stu-id="942d4-119">The parameter block goes directly inside the Configuration declaration, just like a Function.</span></span> <span data-ttu-id="942d4-120">Un blocco di parametri di configurazione deve trovarsi all'esterno delle dichiarazioni di **nodo** e al di sopra delle istruzioni di *importazione*.</span><span class="sxs-lookup"><span data-stu-id="942d4-120">A Configuration parameter block should be outside any **Node** declarations, and above any *import* statements.</span></span> <span data-ttu-id="942d4-121">Aggiungendo i parametri, è possibile rendere le configurazioni maggiormente solide e dinamiche.</span><span class="sxs-lookup"><span data-stu-id="942d4-121">By adding parameters, you can make your Configurations more robust and dynamic.</span></span>

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a><span data-ttu-id="942d4-122">Aggiungere un parametro ComputerName</span><span class="sxs-lookup"><span data-stu-id="942d4-122">Add a ComputerName parameter</span></span>

<span data-ttu-id="942d4-123">Il primo parametro che è possibile aggiungere è un parametro `-Computername` per compilare dinamicamente un file "MOF" per qualsiasi parametro `-Computername` passato alla configurazione.</span><span class="sxs-lookup"><span data-stu-id="942d4-123">The first parameter you might add is a `-Computername` parameter so you can dynamically compile a ".mof" file for any `-Computername` you pass to your configuration.</span></span> <span data-ttu-id="942d4-124">Come per le funzioni, è anche possibile definire un valore predefinito, nel caso in cui l'utente non passi un valore per `-ComputerName`</span><span class="sxs-lookup"><span data-stu-id="942d4-124">Like Functions, you can also define a default value, in case the user does not pass in a value for `-ComputerName`</span></span>

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

<span data-ttu-id="942d4-125">All'interno della configurazione, è quindi possibile specificare il parametro `-ComputerName` quando si definisce il blocco Node.</span><span class="sxs-lookup"><span data-stu-id="942d4-125">Within your configuration, you can then specify your `-ComputerName` parameter when defining your Node block.</span></span>

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a><span data-ttu-id="942d4-126">Chiamare la configurazione con i parametri</span><span class="sxs-lookup"><span data-stu-id="942d4-126">Calling your Configuration with parameters</span></span>

<span data-ttu-id="942d4-127">Dopo aver aggiunto i parametri alla configurazione, è possibile usarli così come si farebbe con un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="942d4-127">After you have added parameters to your Configuration, you can use them just like you would with a cmdlet.</span></span>

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a><span data-ttu-id="942d4-128">Compilazione di più file MOF</span><span class="sxs-lookup"><span data-stu-id="942d4-128">Compiling multiple .mof files</span></span>

<span data-ttu-id="942d4-129">Il blocco Node può anche accettare un elenco delimitato da virgole di nomi computer e genererà file "MOF" per ciascuno di essi.</span><span class="sxs-lookup"><span data-stu-id="942d4-129">The Node block can also accept a comma-separated list of computer names and will generate ".mof" files for each.</span></span> <span data-ttu-id="942d4-130">È possibile eseguire l'esempio seguente per generare i file "MOF" per tutti i computer passati al parametro `-ComputerName`.</span><span class="sxs-lookup"><span data-stu-id="942d4-130">You can run the following example to generate ".mof" files for all of the computers passed to the `-ComputerName` parameter.</span></span>

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

## <a name="advanced-parameters-in-configurations"></a><span data-ttu-id="942d4-131">Parametri avanzati nelle configurazioni</span><span class="sxs-lookup"><span data-stu-id="942d4-131">Advanced parameters in Configurations</span></span>

<span data-ttu-id="942d4-132">Oltre a un parametro `-ComputerName`, è possibile aggiungere parametri per il nome e lo stato del servizio.</span><span class="sxs-lookup"><span data-stu-id="942d4-132">In addition to a `-ComputerName` parameter, we can add parameters for the service name and state.</span></span> <span data-ttu-id="942d4-133">L'esempio seguente aggiunge un blocco di parametri con un parametro `-ServiceName` e lo usa per definire in modo dinamico il blocco di risorse **Service**.</span><span class="sxs-lookup"><span data-stu-id="942d4-133">The following example adds a parameter block with a `-ServiceName` parameter and uses it to dynamically define the **Service** resource block.</span></span> <span data-ttu-id="942d4-134">Aggiunge anche un parametro `-State` per definire in modo dinamico **State** nel blocco di risorse **Service**.</span><span class="sxs-lookup"><span data-stu-id="942d4-134">It also adds a `-State` parameter to dynamically define the **State** in the **Service** resource block.</span></span>

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
> <span data-ttu-id="942d4-135">In scenari più avanzati, potrebbe essere più utile spostare i dati dinamici in [dati di configurazione](configData.md) strutturati.</span><span class="sxs-lookup"><span data-stu-id="942d4-135">In more advacned scenarios, it might make more sense to move your dynamic data into a structured [Configuration Data](configData.md).</span></span>

<span data-ttu-id="942d4-136">La configurazione di esempio usa qui un valore dinamico `$ServiceName`, ma se non ne è specificato uno la compilazione genera un errore.</span><span class="sxs-lookup"><span data-stu-id="942d4-136">The example Configuration now takes a dynamic `$ServiceName`, but if one is not specified, compiling results in an error.</span></span> <span data-ttu-id="942d4-137">È possibile aggiungere un valore predefinito simile a questo esempio.</span><span class="sxs-lookup"><span data-stu-id="942d4-137">You could add a default value like this example.</span></span>

```powershell
[String]
$ServiceName="Spooler"
```

<span data-ttu-id="942d4-138">In questa istanza, tuttavia, è più opportuno forzare semplicemente l'utente a specificare un valore per il parametro `$ServiceName`.</span><span class="sxs-lookup"><span data-stu-id="942d4-138">In this instance though, it makes more sense to simply force the user to specify a value for the `$ServiceName` parameter.</span></span> <span data-ttu-id="942d4-139">L'attributo `parameter` consente di aggiungere ulteriore supporto di convalida e pipeline ai parametri di configurazione.</span><span class="sxs-lookup"><span data-stu-id="942d4-139">The `parameter` attribute allows you to add further validation and pipeline support to your Configuration's parameters.</span></span>

<span data-ttu-id="942d4-140">Di sopra di qualsiasi dichiarazione di parametro, aggiungere il blocco di attributi `parameter` come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="942d4-140">Above any parameter declaration, add the `parameter` attribute block as in the example below.</span></span>

```powershell
[parameter()]
[String]
$ServiceName
```

<span data-ttu-id="942d4-141">È possibile specificare argomenti per ogni attributo `parameter` per controllare gli aspetti del parametro definito.</span><span class="sxs-lookup"><span data-stu-id="942d4-141">You can specify arguments to each `parameter` attribute, to control aspects of the defined parameter.</span></span> <span data-ttu-id="942d4-142">L'esempio seguente rende `$ServiceName` un parametro **obbligatorio**.</span><span class="sxs-lookup"><span data-stu-id="942d4-142">The following example makes the `$ServiceName` a **Mandatory** parameter.</span></span>

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

<span data-ttu-id="942d4-143">Per il parametro `$State`, sarebbe opportuno impedire all'utente di specificare valori di fuori di un set predefinito (come Running, Stopped). L'attributo `ValidationSet*`impedisce all'utente di specificare valori di fuori di un set predefinito (come Running, Stopped).</span><span class="sxs-lookup"><span data-stu-id="942d4-143">For the `$State` parameter, we would like to prevent the user from specifying values outside of a predefined set (like Running, Stopped) the `ValidationSet*`attribute would prevent the user from specifying values outside of a predefined set (like Running, Stopped).</span></span> <span data-ttu-id="942d4-144">L'esempio seguente aggiunge l'attributo `ValidationSet` al parametro `$State`.</span><span class="sxs-lookup"><span data-stu-id="942d4-144">The following example adds the `ValidationSet` attribute to the `$State` parameter.</span></span> <span data-ttu-id="942d4-145">Poiché non si desidera rendere il parametro `$State` **obbligatorio**, è necessario aggiungere per esso un valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="942d4-145">Since we do not want to make the `$State` parameter **Mandatory**, we will need to add a default value for it.</span></span>

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> <span data-ttu-id="942d4-146">Non è necessario specificare un attributo `parameter` quando si usa un attributo `validation`.</span><span class="sxs-lookup"><span data-stu-id="942d4-146">You do not need to specify a `parameter` attribute when using a `validation` attribute.</span></span>

<span data-ttu-id="942d4-147">Sono disponibili altre informazioni su `parameter` e sugli attributi di convalida nelle [informazioni sui parametri delle funzioni avanzate](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span><span class="sxs-lookup"><span data-stu-id="942d4-147">You can read more about the `parameter` and validation attributes in [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).</span></span>

## <a name="fully-parameterized-configuration"></a><span data-ttu-id="942d4-148">Configurazione completa con parametri</span><span class="sxs-lookup"><span data-stu-id="942d4-148">Fully parameterized Configuration</span></span>

<span data-ttu-id="942d4-149">È ora disponibile una configurazione con parametri che forza l'utente a specificare `-InstanceName`, `-ServiceName` e che convalida il parametro `-State`.</span><span class="sxs-lookup"><span data-stu-id="942d4-149">We now have a parameterized Configuration that forces the user to specify an `-InstanceName`, `-ServiceName`, and validates the `-State` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="942d4-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="942d4-150">See also</span></span>

- [<span data-ttu-id="942d4-151">Scrivere informazioni della Guida per le configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="942d4-151">Write help for DSC configurations</span></span>](configHelp.md)
- [<span data-ttu-id="942d4-152">Istruzioni condizionali e cicli nelle configurazioni</span><span class="sxs-lookup"><span data-stu-id="942d4-152">Dynamic Configurations</span></span>](flow-control-in-configurations.md)
- [<span data-ttu-id="942d4-153">Uso dei dati di configurazione in DSC</span><span class="sxs-lookup"><span data-stu-id="942d4-153">Use Configuration Data in your Configurations</span></span>](configData.md)
- [<span data-ttu-id="942d4-154">Separazione dei dati di configurazione e dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="942d4-154">Separate configuration and environment data</span></span>](separatingEnvData.md)
