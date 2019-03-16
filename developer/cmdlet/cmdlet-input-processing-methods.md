---
title: I metodi di elaborazione dell'Input cmdlet | Microsoft Docs
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
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059372"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="39ac1-102">Metodi di elaborazione degli input dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="39ac1-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="39ac1-103">I cmdlet devono eseguire l'override di uno o più i metodi descritti in questo argomento per effettuare le operazioni di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="39ac1-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="39ac1-104">Questi metodi consentono al cmdlet di eseguire la pre-elaborazione operations, input operazioni di elaborazione e operazioni di post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="39ac1-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="39ac1-105">Questi metodi consentono anche di arrestare l'elaborazione di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="39ac1-106">Attività di pre-elaborazione</span><span class="sxs-lookup"><span data-stu-id="39ac1-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="39ac1-107">I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo per aggiungere eventuali operazioni di pre-elaborazione che sono valide per tutti i record che verranno elaborati in un secondo momento tramite il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="39ac1-108">Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="39ac1-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="39ac1-109">Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="39ac1-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="39ac1-110">Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) (metodo).</span><span class="sxs-lookup"><span data-stu-id="39ac1-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="39ac1-111">Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="39ac1-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="39ac1-112">In questa esercitazione, il **Select Str** cmdlet Usa il [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metodo per generare l'espressione regolare che viene usato per cercare il record di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="39ac1-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="39ac1-113">Attività di elaborazione di input</span><span class="sxs-lookup"><span data-stu-id="39ac1-113">Input Processing Tasks</span></span>

<span data-ttu-id="39ac1-114">I cmdlet possono eseguire l'override di [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo per elaborare l'input che viene inviato al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="39ac1-115">Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell chiama questo metodo per ogni record di input che viene elaborato dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="39ac1-116">Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="39ac1-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="39ac1-117">Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (metodo).</span><span class="sxs-lookup"><span data-stu-id="39ac1-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="39ac1-118">Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="39ac1-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="39ac1-119">Attività post-elaborazione</span><span class="sxs-lookup"><span data-stu-id="39ac1-119">Post-Processing Tasks</span></span>

<span data-ttu-id="39ac1-120">I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodo per aggiungere tutte le operazioni post-elaborazione sono valide per tutti i record che sono stati elaborati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="39ac1-121">Ad esempio, il cmdlet potrebbe essere necessario pulire le variabili oggetto dopo l'operazione è terminata l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="39ac1-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="39ac1-122">Quando Windows PowerShell elabora una pipeline di comandi, Windows PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="39ac1-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="39ac1-123">Tuttavia, è importante ricordare che il runtime di Windows PowerShell non chiamerà il [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metodo se il cmdlet viene annullato metà attraverso l'elaborazione di input o se una terminazione errore si verifica in qualsiasi parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39ac1-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="39ac1-124">Per questo motivo, un cmdlet che richiede la pulizia degli oggetti devono implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio, inclusi un finalizzatore, in modo che il runtime può chiamare entrambe le [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) e [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) metodi alla fine dell'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="39ac1-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="39ac1-125">Per altre informazioni sul modo in cui Windows PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="39ac1-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="39ac1-126">Il codice seguente viene illustrata un'implementazione del [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) (metodo).</span><span class="sxs-lookup"><span data-stu-id="39ac1-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="39ac1-127">Per un esempio più dettagliato di come usare il [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metodo, vedere [esercitazione SelectStr](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="39ac1-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39ac1-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39ac1-128">See Also</span></span>

[<span data-ttu-id="39ac1-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="39ac1-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="39ac1-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="39ac1-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="39ac1-131">System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname</span><span class="sxs-lookup"><span data-stu-id="39ac1-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="39ac1-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="39ac1-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="39ac1-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="39ac1-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
