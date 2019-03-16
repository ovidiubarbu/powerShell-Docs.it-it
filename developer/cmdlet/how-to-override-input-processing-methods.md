---
title: Come eseguire l'Override di metodi di elaborazione dell'Input | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056397"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="7fbeb-102">Come sostituire i metodi di elaborazione degli input</span><span class="sxs-lookup"><span data-stu-id="7fbeb-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="7fbeb-103">Questi esempi illustrano come sovrascrivere i metodi all'interno di un cmdlet di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="7fbeb-104">Questi metodi vengono usati per eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="7fbeb-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="7fbeb-105">Il [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metodo viene utilizzato per eseguire operazioni di avvio occasionale che sono valide per tutti gli oggetti elaborati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="7fbeb-106">Il runtime di Windows PowerShell chiama questo metodo solo una volta.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="7fbeb-107">Il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metodo viene utilizzato per elaborare gli oggetti passati al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="7fbeb-108">Il runtime di Windows PowerShell chiama questo metodo per ogni oggetto passato al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="7fbeb-109">Il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo viene utilizzato per eseguire le operazioni di elaborazione post monouso.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="7fbeb-110">Il runtime di Windows PowerShell chiama questo metodo solo una volta.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="7fbeb-111">Per eseguire l'override del metodo BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="7fbeb-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="7fbeb-112">Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="7fbeb-113">La classe seguente viene stampato un messaggio di esempio.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-113">The following class prints a sample message.</span></span> <span data-ttu-id="7fbeb-114">Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="7fbeb-115">Per eseguire l'override del metodo ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="7fbeb-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="7fbeb-116">Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="7fbeb-117">La classe seguente viene stampato un messaggio di esempio.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-117">The following class prints a sample message.</span></span> <span data-ttu-id="7fbeb-118">Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="7fbeb-119">L'override del metodo EndProcessing</span><span class="sxs-lookup"><span data-stu-id="7fbeb-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="7fbeb-120">Dichiarare un override di protetto il [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="7fbeb-121">La classe seguente visualizza un esempio.</span><span class="sxs-lookup"><span data-stu-id="7fbeb-121">The following class prints a sample.</span></span> <span data-ttu-id="7fbeb-122">Per usare questa classe, modificare il verbo e sostantivo nell'attributo Cmdlet, modificare il nome della classe in modo da riflettere il nuovo verbo e sostantivo e quindi aggiungere le funzionalità richieste per l'override del [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo).</span><span class="sxs-lookup"><span data-stu-id="7fbeb-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="7fbeb-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7fbeb-123">See Also</span></span>

[<span data-ttu-id="7fbeb-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="7fbeb-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="7fbeb-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="7fbeb-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="7fbeb-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="7fbeb-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="7fbeb-127">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7fbeb-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
