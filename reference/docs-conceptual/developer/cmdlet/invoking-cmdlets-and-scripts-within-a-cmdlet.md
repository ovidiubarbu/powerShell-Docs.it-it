---
title: Richiamo di cmdlet e script all'interno di un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364290"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="f817a-102">Richiamo di cmdlet e script all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="f817a-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="f817a-103">Un cmdlet può richiamare altri cmdlet e script dall'interno del metodo di elaborazione dell'input del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f817a-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="f817a-104">In questo modo è possibile aggiungere al cmdlet la funzionalità di cmdlet e script esistenti senza dover riscrivere il codice.</span><span class="sxs-lookup"><span data-stu-id="f817a-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="f817a-105">Metodo Invoke</span><span class="sxs-lookup"><span data-stu-id="f817a-105">The Invoke Method</span></span>

<span data-ttu-id="f817a-106">Tutti i cmdlet possono richiamare un cmdlet esistente chiamando il metodo [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) dall'interno di un metodo di elaborazione dell'input, ad esempio [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), sottoposto a override da cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f817a-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="f817a-107">Tuttavia, è possibile richiamare solo i cmdlet che derivano direttamente dalla classe [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="f817a-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="f817a-108">Non è possibile richiamare un cmdlet che deriva dalla classe [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="f817a-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="f817a-109">Il metodo [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) presenta le varianti seguenti.</span><span class="sxs-lookup"><span data-stu-id="f817a-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="f817a-110">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto cmdlet e restituisce una raccolta di oggetti di tipo "T".</span><span class="sxs-lookup"><span data-stu-id="f817a-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="f817a-111">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto cmdlet e restituisce un emumerator fortemente tipizzato.</span><span class="sxs-lookup"><span data-stu-id="f817a-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="f817a-112">Questa variante consente all'utente di usare gli oggetti nella raccolta per eseguire operazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="f817a-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="f817a-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="f817a-113">Examples</span></span>

|<span data-ttu-id="f817a-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="f817a-114">Example</span></span>|<span data-ttu-id="f817a-115">Description</span><span class="sxs-lookup"><span data-stu-id="f817a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f817a-116">Richiamo di cmdlet all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="f817a-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="f817a-117">In questo esempio viene illustrato come richiamare un cmdlet da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f817a-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="f817a-118">Richiamo di script all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="f817a-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="f817a-119">In questo esempio viene illustrato come richiamare uno script fornito al cmdlet da un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f817a-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f817a-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f817a-120">See Also</span></span>

[<span data-ttu-id="f817a-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f817a-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)