---
title: Richiamare i cmdlet e script all'interno di un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058879"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="f15fa-102">Richiamo di cmdlet e script all'interno di un cmdlet</span><span class="sxs-lookup"><span data-stu-id="f15fa-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="f15fa-103">Un cmdlet può richiamare altri cmdlet e script da entro il metodo del cmdlet di elaborazione dell'input.</span><span class="sxs-lookup"><span data-stu-id="f15fa-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="f15fa-104">In questo modo è possibile aggiungere la funzionalità di script e i cmdlet esistenti per il cmdlet senza dover riscrivere il codice.</span><span class="sxs-lookup"><span data-stu-id="f15fa-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="f15fa-105">Il metodo Invoke</span><span class="sxs-lookup"><span data-stu-id="f15fa-105">The Invoke Method</span></span>

<span data-ttu-id="f15fa-106">Tutti i cmdlet possono richiamare un cmdlet esistente chiamando il [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodo all'interno di un metodo di elaborazione, ad esempio dell'input [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), che viene viene sottoposto a override dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f15fa-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="f15fa-107">Tuttavia, è possibile richiamare solo i cmdlet che derivano direttamente dai [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="f15fa-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="f15fa-108">Non è possibile richiamare un cmdlet da cui deriva il [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) classe.</span><span class="sxs-lookup"><span data-stu-id="f15fa-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="f15fa-109">Il [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metodo presenta le seguenti varianti.</span><span class="sxs-lookup"><span data-stu-id="f15fa-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="f15fa-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto di cmdlet e restituisce una raccolta di oggetti di tipo "T".</span><span class="sxs-lookup"><span data-stu-id="f15fa-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="f15fa-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) questa variante richiama l'oggetto di cmdlet e restituisce un emumerator fortemente tipizzato.</span><span class="sxs-lookup"><span data-stu-id="f15fa-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="f15fa-112">Questa variante consente all'utente di usare gli oggetti nella raccolta per eseguire operazioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="f15fa-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="f15fa-113">Esempi</span><span class="sxs-lookup"><span data-stu-id="f15fa-113">Examples</span></span>

|<span data-ttu-id="f15fa-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="f15fa-114">Example</span></span>|<span data-ttu-id="f15fa-115">Description</span><span class="sxs-lookup"><span data-stu-id="f15fa-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f15fa-116">Richiamare i cmdlet all'interno di un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f15fa-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="f15fa-117">In questo esempio viene illustrato come richiamare un cmdlet all'interno di un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f15fa-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="f15fa-118">Richiamo degli script all'interno di un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f15fa-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="f15fa-119">In questo esempio viene illustrato come richiamare uno script che viene fornito per il cmdlet impedisce all'interno di un altro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f15fa-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f15fa-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f15fa-120">See Also</span></span>

[<span data-ttu-id="f15fa-121">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f15fa-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
