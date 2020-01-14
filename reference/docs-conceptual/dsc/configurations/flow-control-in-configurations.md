---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Istruzioni condizionali e cicli nelle configurazioni
ms.openlocfilehash: 86f75be4a3d1c1760dd6269335431e8ab9fd8d09
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736897"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="bffba-103">Istruzioni condizionali e cicli in una configurazione</span><span class="sxs-lookup"><span data-stu-id="bffba-103">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="bffba-104">È possibile rendere la [configurazione](configurations.md) più dinamica usando le parole chiave di controllo del flusso di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bffba-104">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="bffba-105">Questo articolo illustra come è possibile usare le istruzioni condizionali e i cicli per rendere più dinamica `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-105">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="bffba-106">La combinazione di istruzioni condizionali e cicli con [parametri](add-parameters-to-a-configuration.md) e [dati di configurazione](configData.md) consente di ottenere maggiori flessibilità e controllo durante la compilazione di `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-106">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="bffba-107">Proprio come una funzione o un blocco di script, è possibile usare qualsiasi funzione del linguaggio di PowerShell in una `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-107">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span>
<span data-ttu-id="bffba-108">Le istruzioni usate verranno valutate solo quando si chiama la `Configuration` per compilare un file `.mof`.</span><span class="sxs-lookup"><span data-stu-id="bffba-108">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="bffba-109">Gli esempi seguenti illustrano alcuni scenari per una dimostrazione dei concetti.</span><span class="sxs-lookup"><span data-stu-id="bffba-109">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="bffba-110">Le istruzioni condizionali e i cicli vengono usati più spesso con i parametri e i dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="bffba-110">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="bffba-111">In questo esempio il blocco di risorse **Service** recupera lo stato corrente di un servizio in fase di compilazione per generare un file `.mof` che mantiene lo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="bffba-111">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="bffba-112">L'uso di blocchi di risorse dinamici comprometterà l'efficacia di Intellisense.</span><span class="sxs-lookup"><span data-stu-id="bffba-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="bffba-113">Il parser di PowerShell non è in grado di determinare se i valori specificati sono accettabili fino a quando non viene compilata la `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-113">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="bffba-114">Si potrebbe anche creare un blocco di risorse **Service** per ogni servizio nel computer corrente usando un ciclo `foreach`.</span><span class="sxs-lookup"><span data-stu-id="bffba-114">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="bffba-115">È anche possibile creare una `Configuration` solo per i computer online usando un'istruzione `if`.</span><span class="sxs-lookup"><span data-stu-id="bffba-115">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="bffba-116">I blocchi di risorse dinamici negli esempi precedenti fanno riferimento al computer corrente.</span><span class="sxs-lookup"><span data-stu-id="bffba-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="bffba-117">In questa istanza sarebbe il computer in cui viene creata la `Configuration` e non il nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="bffba-117">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="bffba-118">Summary</span><span class="sxs-lookup"><span data-stu-id="bffba-118">Summary</span></span>

<span data-ttu-id="bffba-119">In breve, è possibile usare qualsiasi funzione del linguaggio di PowerShell in una `Configuration`,</span><span class="sxs-lookup"><span data-stu-id="bffba-119">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="bffba-120">inclusi elementi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="bffba-120">This includes things like:</span></span>

- <span data-ttu-id="bffba-121">Oggetti personalizzati</span><span class="sxs-lookup"><span data-stu-id="bffba-121">Custom Objects</span></span>
- <span data-ttu-id="bffba-122">Tabelle hash</span><span class="sxs-lookup"><span data-stu-id="bffba-122">Hashtables</span></span>
- <span data-ttu-id="bffba-123">Modifica di stringhe</span><span class="sxs-lookup"><span data-stu-id="bffba-123">String manipulation</span></span>
- <span data-ttu-id="bffba-124">Comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="bffba-124">Remoting</span></span>
- <span data-ttu-id="bffba-125">WMI e CIM</span><span class="sxs-lookup"><span data-stu-id="bffba-125">WMI and CIM</span></span>
- <span data-ttu-id="bffba-126">Oggetti di Active Directory</span><span class="sxs-lookup"><span data-stu-id="bffba-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="bffba-127">altro...</span><span class="sxs-lookup"><span data-stu-id="bffba-127">and more...</span></span>

<span data-ttu-id="bffba-128">Qualsiasi codice di PowerShell definito in una `Configuration` viene valutato in fase di compilazione, ma è anche possibile inserire codice nello script che contiene la `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-128">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="bffba-129">Qualsiasi codice esterno al blocco `Configuration` viene eseguito quando si importa la `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="bffba-129">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="bffba-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bffba-130">See also</span></span>

- [<span data-ttu-id="bffba-131">Aggiungere parametri a una configurazione</span><span class="sxs-lookup"><span data-stu-id="bffba-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="bffba-132">Separare i dati di configurazione dalle configurazioni</span><span class="sxs-lookup"><span data-stu-id="bffba-132">Separate Configuration data from Configurations</span></span>](configData.md)
