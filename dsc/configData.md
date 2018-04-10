---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Uso dei dati di configurazione
ms.openlocfilehash: 19544494a547a06d87701b38585844cb11d03e33
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="d5d31-103">Uso dei dati di configurazione in DSC</span><span class="sxs-lookup"><span data-stu-id="d5d31-103">Using configuration data in DSC</span></span>

><span data-ttu-id="d5d31-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d5d31-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d5d31-105">Con il parametro DSC predefinito **ConfigurationData** è possibile definire i dati che possono essere usati in una configurazione.</span><span class="sxs-lookup"><span data-stu-id="d5d31-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="d5d31-106">Ciò consente di creare una singola configurazione da usare per più nodi o ambienti diversi.</span><span class="sxs-lookup"><span data-stu-id="d5d31-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="d5d31-107">Ad esempio, se si sviluppa un'applicazione, è possibile usare una sola configurazione per l'ambiente di sviluppo e per quello di produzione e usare i dati di configurazione per specificare i dati per ogni ambiente.</span><span class="sxs-lookup"><span data-stu-id="d5d31-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="d5d31-108">Questo argomento descrive la struttura della tabella hash **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="d5d31-109">Per esempi di come usare i dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="d5d31-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="d5d31-110">Parametro comune ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="d5d31-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="d5d31-111">Una configurazione DSC accetta il parametro comune **ConfigurationData** specificato quando si compila la configurazione.</span><span class="sxs-lookup"><span data-stu-id="d5d31-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="d5d31-112">Per informazioni sulla compilazione delle configurazioni, vedere [Configurazioni DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="d5d31-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="d5d31-113">Il parametro **ConfigurationData** è una tabella hash che deve avere almeno una chiave denominata **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="d5d31-114">Può avere anche una o più chiavi aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="d5d31-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="d5d31-115">**Nota:** gli esempi di questo argomento usano una singola chiave aggiuntiva (diverso dalla chiave denominata **AllNodes**) denominata `NonNodeData`, ma è possibile includere qualsiasi numero di chiavi aggiuntive e assegnare loro un nome qualsiasi.</span><span class="sxs-lookup"><span data-stu-id="d5d31-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="d5d31-116">Il valore della chiave **AllNodes** è una matrice.</span><span class="sxs-lookup"><span data-stu-id="d5d31-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="d5d31-117">Ogni elemento della matrice è anche una tabella hash che deve avere almeno una chiave denominata **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="d5d31-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="d5d31-118">È anche possibile aggiungere altre chiavi a ogni tabella hash:</span><span class="sxs-lookup"><span data-stu-id="d5d31-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="d5d31-119">Per applicare una proprietà a tutti i nodi, è possibile creare un membro della matrice **AllNodes** ha come **NodeName** `*`.</span><span class="sxs-lookup"><span data-stu-id="d5d31-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="d5d31-120">Ad esempio, per assegnare a ogni nodo una proprietà `LogPath`, è possibile usare questo script:</span><span class="sxs-lookup"><span data-stu-id="d5d31-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="d5d31-121">Questo equivale ad aggiungere una proprietà con nome `LogPath` e valore `"C:\Logs"` a ciascuno degli altri blocchi (`VM-1`, `VM-2` e `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="d5d31-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="d5d31-122">Definizione della tabella hash ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="d5d31-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="d5d31-123">È possibile definire **ConfigurationData** come variabile all'interno dello stesso file di script di una configurazione, come negli esempi precedenti, o in un file `.psd1` separato.</span><span class="sxs-lookup"><span data-stu-id="d5d31-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="d5d31-124">Per definire **ConfigurationData** in un file `.psd1`, creare un file che contiene solo la tabella hash che rappresenta i dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="d5d31-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="d5d31-125">Ad esempio, è possibile creare un file denominato `MyData.psd1` con il seguente contenuto:</span><span class="sxs-lookup"><span data-stu-id="d5d31-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="d5d31-126">Compilazione di una configurazione con i dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="d5d31-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="d5d31-127">Per compilare una configurazione per la quale sono stati definiti i dati di configurazione, passare i dati della configurazione come valore del parametro **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="d5d31-128">Viene creato un file MOF per ogni voce della matrice **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="d5d31-129">Ogni file MOF è denominato con la proprietà `NodeName` della voce della matrice corrispondente.</span><span class="sxs-lookup"><span data-stu-id="d5d31-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="d5d31-130">Ad esempio, se si definiscono i dati di configurazione come nel file `MyData.psd1` precedente, la compilazione di una configurazione crea entrambi i file `VM-1.mof` e `VM-2.mof`.</span><span class="sxs-lookup"><span data-stu-id="d5d31-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="d5d31-131">Compilazione di una configurazione con i dati di configurazione usando una variabile</span><span class="sxs-lookup"><span data-stu-id="d5d31-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="d5d31-132">Per usare dati di configurazione definiti come variabile nello stesso file `.ps1`, passare il nome della variabile come valore del parametro **ConfigurationData** durante la compilazione della configurazione:</span><span class="sxs-lookup"><span data-stu-id="d5d31-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="d5d31-133">Compilazione di una configurazione con i dati di configurazione usando un file di dati</span><span class="sxs-lookup"><span data-stu-id="d5d31-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="d5d31-134">Per usare i dati di configurazione definiti in un file .psd1, passare il percorso e il nome del file come valore del parametro **ConfigurationData** durante la compilazione della configurazione:</span><span class="sxs-lookup"><span data-stu-id="d5d31-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="d5d31-135">Uso delle variabili ConfigurationData in una configurazione</span><span class="sxs-lookup"><span data-stu-id="d5d31-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="d5d31-136">DSC offre tre variabili speciali che possono essere usate in uno script di configurazione: **$AllNodes**, **$Node** e **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="d5d31-137">**$AllNodes** si riferisce all'intera raccolta di nodi definita in **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="d5d31-138">È possibile filtrare la raccolta **AllNodes** usando **.Where()** e **.Foreach()**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="d5d31-139">**Node** fa riferimento a una particolare voce della raccolta **AllNodes** dopo che viene filtrato usando **.Where()** o **.Foreach()**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="d5d31-140">**ConfigurationData** fa riferimento all'intera tabella hash che viene passata come parametro durante la compilazione di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="d5d31-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="d5d31-141">Uso di dati non specifici per un nodo</span><span class="sxs-lookup"><span data-stu-id="d5d31-141">Using non-node data</span></span>

<span data-ttu-id="d5d31-142">Come illustrato negli esempi precedenti, la tabella hash **ConfigurationData** può avere una o più chiavi oltre alla chiave obbligatoria **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="d5d31-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="d5d31-143">Negli esempi di questo argomento è stato usato un solo nodo aggiuntivo che è stato denominato `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="d5d31-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="d5d31-144">È comunque possibile definire qualsiasi numero di chiavi aggiuntive e assegnare alle chiavi qualsiasi nome.</span><span class="sxs-lookup"><span data-stu-id="d5d31-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="d5d31-145">Per un esempio d'uso di dati non nodo, vedere [Separazione dei dati di configurazione e dell'ambiente](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="d5d31-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5d31-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d5d31-146">See Also</span></span>
- [<span data-ttu-id="d5d31-147">Opzioni delle credenziali nei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="d5d31-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="d5d31-148">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="d5d31-148">DSC Configurations</span></span>](configurations.md)