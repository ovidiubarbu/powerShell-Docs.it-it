---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Istruzioni condizionali e cicli nelle configurazioni
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954078"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="cbe04-103">Istruzioni condizionali e cicli nelle configurazioni</span><span class="sxs-lookup"><span data-stu-id="cbe04-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="cbe04-104">È possibile rendere le [configurazioni](configurations.md) più dinamiche mediante le parole chiave di controllo del flusso di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cbe04-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="cbe04-105">Questo articolo illustrerà come è possibile usare le istruzioni condizionali e i cicli per rendere più dinamiche le configurazioni.</span><span class="sxs-lookup"><span data-stu-id="cbe04-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="cbe04-106">La combinazione di istruzioni condizionali e cicli con [parametri](add-parameters-to-a-configuration.md) e [dati di configurazione](configData.md) consente di ottenere maggiori flessibilità e controllo durante la compilazione delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="cbe04-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="cbe04-107">Proprio come una funzione o un blocco di script, è possibile usare qualsiasi elemento del linguaggio di PowerShell all'interno di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="cbe04-108">Le istruzioni usate verranno valutate solo quando si chiama la configurazione per compilare un file "MOF".</span><span class="sxs-lookup"><span data-stu-id="cbe04-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="cbe04-109">Gli esempi seguenti mostrano alcuni scenari semplici per una dimostrazione dei concetti.</span><span class="sxs-lookup"><span data-stu-id="cbe04-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="cbe04-110">Le istruzioni condizionali e i cicli vengono usati più spesso con i parametri e i dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="cbe04-111">In questo semplice esempio, il blocco di risorse **Service** recupera lo stato corrente di un servizio in fase di compilazione per generare un file "MOF" che mantiene lo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="cbe04-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="cbe04-112">L'uso di blocchi di risorse dinamici comprometterà l'efficacia di Intellisense.</span><span class="sxs-lookup"><span data-stu-id="cbe04-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="cbe04-113">Il parser di PowerShell non è in grado di determinare se i valori specificati sono accettabili fino a quando non viene compilata la configurazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="cbe04-114">Si potrebbe anche creare un blocco di risorse **Service** per ogni servizio nel computer corrente usando un ciclo `foreach`.</span><span class="sxs-lookup"><span data-stu-id="cbe04-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
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

<span data-ttu-id="cbe04-115">È anche possibile creare configurazioni solo per i computer online, usando una semplice istruzione `if`.</span><span class="sxs-lookup"><span data-stu-id="cbe04-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="cbe04-116">I blocchi di risorse dinamici negli esempi precedenti fanno riferimento al computer corrente.</span><span class="sxs-lookup"><span data-stu-id="cbe04-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="cbe04-117">In questa istanza, si tratterebbe del computer in cui viene creata la configurazione e non del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="cbe04-118">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="cbe04-118">Summary</span></span>

<span data-ttu-id="cbe04-119">In breve, è possibile usare qualsiasi elemento del linguaggio di PowerShell all'interno di una configurazione,</span><span class="sxs-lookup"><span data-stu-id="cbe04-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="cbe04-120">inclusi elementi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="cbe04-120">This includes things like:</span></span>

- <span data-ttu-id="cbe04-121">Oggetti personalizzati</span><span class="sxs-lookup"><span data-stu-id="cbe04-121">Custom Objects</span></span>
- <span data-ttu-id="cbe04-122">Tabelle hash</span><span class="sxs-lookup"><span data-stu-id="cbe04-122">Hashtables</span></span>
- <span data-ttu-id="cbe04-123">Modifica di stringhe</span><span class="sxs-lookup"><span data-stu-id="cbe04-123">String manipulation</span></span>
- <span data-ttu-id="cbe04-124">Comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="cbe04-124">Remoting</span></span>
- <span data-ttu-id="cbe04-125">WMI e CIM</span><span class="sxs-lookup"><span data-stu-id="cbe04-125">WMI and CIM</span></span>
- <span data-ttu-id="cbe04-126">Oggetti di Active Directory</span><span class="sxs-lookup"><span data-stu-id="cbe04-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="cbe04-127">altro...</span><span class="sxs-lookup"><span data-stu-id="cbe04-127">and more...</span></span>

<span data-ttu-id="cbe04-128">Qualsiasi codice di PowerShell definito in una configurazione verrà valutato in fase di compilazione, ma è anche possibile inserire codice nello script che contiene la configurazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="cbe04-129">Qualsiasi codice all'esterno del blocco di configurazione verrà eseguito quando si importa la configurazione.</span><span class="sxs-lookup"><span data-stu-id="cbe04-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbe04-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cbe04-130">See also</span></span>

- [<span data-ttu-id="cbe04-131">Aggiungere parametri a una configurazione</span><span class="sxs-lookup"><span data-stu-id="cbe04-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="cbe04-132">Separare i dati di configurazione dalle configurazioni</span><span class="sxs-lookup"><span data-stu-id="cbe04-132">Separate Configuration data from Configurations</span></span>](configData.md)