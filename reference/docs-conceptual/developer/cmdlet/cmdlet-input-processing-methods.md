---
title: Metodi di elaborazione degli input dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369870"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="5ad76-102">Metodi di elaborazione degli input dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ad76-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="5ad76-103">I cmdlet devono eseguire l'override di uno o più metodi di elaborazione dell'input descritti in questo argomento per eseguire il lavoro.</span><span class="sxs-lookup"><span data-stu-id="5ad76-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="5ad76-104">Questi metodi consentono al cmdlet di eseguire operazioni di pre-elaborazione, elaborazione dell'input e post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="5ad76-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="5ad76-105">Questi metodi consentono inoltre di arrestare l'elaborazione dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="5ad76-106">Per un esempio più dettagliato di come usare questi metodi, vedere [esercitazione su SelectStr](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5ad76-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="5ad76-107">Operazioni di pre-elaborazione</span><span class="sxs-lookup"><span data-stu-id="5ad76-107">Pre-Processing Operations</span></span>

<span data-ttu-id="5ad76-108">I cmdlet devono eseguire l'override del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) per aggiungere tutte le operazioni di pre-elaborazione valide per tutti i record che verranno elaborati successivamente dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="5ad76-109">Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="5ad76-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="5ad76-110">Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5ad76-111">Nel codice seguente viene illustrata un'implementazione del metodo BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="5ad76-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="5ad76-112">Operazioni di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="5ad76-112">Input Processing Operations</span></span>

<span data-ttu-id="5ad76-113">I cmdlet possono eseguire l'override del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) per elaborare l'input inviato al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="5ad76-114">Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo per ogni record di input elaborato dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="5ad76-115">Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5ad76-116">Nel codice seguente viene illustrata un'implementazione del metodo ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="5ad76-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="5ad76-117">Operazioni di post-elaborazione</span><span class="sxs-lookup"><span data-stu-id="5ad76-117">Post-Processing Operations</span></span>

<span data-ttu-id="5ad76-118">I cmdlet devono eseguire l'override del metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) per aggiungere eventuali operazioni di post-elaborazione valide per tutti i record elaborati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="5ad76-119">Ad esempio, il cmdlet potrebbe dover pulire le variabili oggetto dopo che è stata completata l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="5ad76-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="5ad76-120">Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="5ad76-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="5ad76-121">Tuttavia, è importante ricordare che il runtime di PowerShell non chiamerà il metodo EndProcessing se il cmdlet viene annullato a metà durante l'elaborazione dell'input o se si verifica un errore di terminazione in qualsiasi parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="5ad76-122">Per questo motivo, un cmdlet che richiede la pulizia degli oggetti deve implementare il modello [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluso un finalizzatore, in modo che il runtime possa chiamare i metodi EndProcessing e [System. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) alla fine di elaborazione.</span><span class="sxs-lookup"><span data-stu-id="5ad76-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="5ad76-123">Per altre informazioni su come PowerShell richiama la pipeline di comandi, vedere [ciclo](/previous-versions/ms714429(v=vs.85))di vita dell'elaborazione dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ad76-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="5ad76-124">Nel codice seguente viene illustrata un'implementazione del metodo EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="5ad76-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="5ad76-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5ad76-125">See Also</span></span>

[<span data-ttu-id="5ad76-126">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="5ad76-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="5ad76-127">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="5ad76-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="5ad76-128">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="5ad76-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="5ad76-129">Esercitazione su SelectStr</span><span class="sxs-lookup"><span data-stu-id="5ad76-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="5ad76-130">System. IDisposable</span><span class="sxs-lookup"><span data-stu-id="5ad76-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="5ad76-131">SDK della shell di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ad76-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
