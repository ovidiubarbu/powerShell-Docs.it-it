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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670316"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="9f89e-102">Metodi di elaborazione degli input dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="9f89e-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="9f89e-103">I cmdlet devono eseguire l'override di uno o più i metodi descritti in questo argomento per effettuare le operazioni di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="9f89e-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="9f89e-104">Questi metodi consentono al cmdlet di eseguire le operazioni di pre-elaborazione, l'elaborazione dell'input e post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="9f89e-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="9f89e-105">Questi metodi consentono anche di arrestare l'elaborazione di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="9f89e-106">Per un esempio più dettagliato di come usare questi metodi, vedere [SelectStr esercitazione](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9f89e-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="9f89e-107">Operazioni di pre-elaborazione</span><span class="sxs-lookup"><span data-stu-id="9f89e-107">Pre-Processing Operations</span></span>

<span data-ttu-id="9f89e-108">I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo per aggiungere eventuali operazioni di pre-elaborazione che sono valide per tutti i record che verranno elaborati in un secondo momento tramite il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="9f89e-109">Quando PowerShell elabora una pipeline di comandi, PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="9f89e-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="9f89e-110">Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9f89e-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9f89e-111">Il codice seguente viene illustrata un'implementazione del metodo BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="9f89e-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="9f89e-112">Operazioni di elaborazione dell'input</span><span class="sxs-lookup"><span data-stu-id="9f89e-112">Input Processing Operations</span></span>

<span data-ttu-id="9f89e-113">I cmdlet possono eseguire l'override di [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo per elaborare l'input che viene inviato al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="9f89e-114">Quando PowerShell elabora una pipeline di comandi, PowerShell chiama questo metodo per ogni record di input che viene elaborato dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="9f89e-115">Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9f89e-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9f89e-116">Il codice seguente viene illustrata un'implementazione del metodo ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="9f89e-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="9f89e-117">Operazioni di post-elaborazione</span><span class="sxs-lookup"><span data-stu-id="9f89e-117">Post-Processing Operations</span></span>

<span data-ttu-id="9f89e-118">I cmdlet devono eseguire l'override di [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo per aggiungere tutte le operazioni post-elaborazione sono valide per tutti i record che sono stati elaborati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="9f89e-119">Ad esempio, il cmdlet potrebbe essere necessario pulire le variabili oggetto dopo l'operazione è terminata l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="9f89e-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="9f89e-120">Quando PowerShell elabora una pipeline di comandi, PowerShell viene chiamato questo metodo una volta per ogni istanza del cmdlet nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="9f89e-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="9f89e-121">Tuttavia, è importante ricordare che il runtime di PowerShell non chiamerà il metodo EndProcessing se il cmdlet viene annullato metà attraverso l'elaborazione di input o se si verifica un errore irreversibile in qualsiasi parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9f89e-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="9f89e-122">Per questo motivo, un cmdlet che richiede la pulizia degli oggetti devono implementare l'intero [System. IDisposable](/dotnet/api/System.IDisposable) criterio, inclusi un finalizzatore, in modo che il runtime può chiamare entrambe le EndProcessing e [ IDisposable](/dotnet/api/System.IDisposable.Dispose) metodi alla fine dell'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="9f89e-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="9f89e-123">Per altre informazioni sul modo in cui PowerShell richiama la pipeline dei comandi, vedere [ciclo di vita di elaborazione Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9f89e-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9f89e-124">Il codice seguente viene illustrata un'implementazione del metodo EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="9f89e-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="9f89e-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9f89e-125">See Also</span></span>

[<span data-ttu-id="9f89e-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="9f89e-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="9f89e-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="9f89e-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="9f89e-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="9f89e-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="9f89e-129">SelectStr Tutorial</span><span class="sxs-lookup"><span data-stu-id="9f89e-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="9f89e-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="9f89e-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="9f89e-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="9f89e-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
