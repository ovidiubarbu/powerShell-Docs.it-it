---
title: Concetti relativi alla segnalazione degli errori | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: 2f185e415e3effc2cf09a282ca1167e3bcfb7d6a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364620"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="4c794-102">Concetti relativi alla segnalazione di errori</span><span class="sxs-lookup"><span data-stu-id="4c794-102">Error Reporting Concepts</span></span>

<span data-ttu-id="4c794-103">Windows PowerShell fornisce due meccanismi per la segnalazione degli errori: un meccanismo per *terminare gli errori* e un altro meccanismo per gli *errori non fatali*.</span><span class="sxs-lookup"><span data-stu-id="4c794-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="4c794-104">È importante che il cmdlet segnali correttamente gli errori, in modo che l'applicazione host che esegue i cmdlet possa reagire in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="4c794-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="4c794-105">Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError \*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) quando si verifica un errore che non consente al cmdlet di continuare a elaborare gli oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="4c794-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="4c794-106">Il cmdlet deve chiamare il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) per segnalare errori non fatali quando il cmdlet può continuare a elaborare gli oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="4c794-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="4c794-107">Entrambi i metodi forniscono un record di errore che può essere utilizzato dall'applicazione host per analizzare la provocazione dell'errore.</span><span class="sxs-lookup"><span data-stu-id="4c794-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="4c794-108">Usare le linee guida seguenti per determinare se un errore è un errore di terminazione o non fatale.</span><span class="sxs-lookup"><span data-stu-id="4c794-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="4c794-109">Un errore è un errore di terminazione se impedisce al cmdlet di continuare a elaborare l'oggetto corrente o di elaborare correttamente eventuali altri oggetti di input, indipendentemente dal contenuto.</span><span class="sxs-lookup"><span data-stu-id="4c794-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="4c794-110">Se non si desidera che il cmdlet continui a elaborare l'oggetto corrente o altri oggetti di input, indipendentemente dal relativo contenuto, si verifica un errore di terminazione.</span><span class="sxs-lookup"><span data-stu-id="4c794-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="4c794-111">Un errore è un errore di terminazione se si verifica in un cmdlet che non accetta o restituisce un oggetto o se si trova in un cmdlet che accetta o restituisce un solo oggetto.</span><span class="sxs-lookup"><span data-stu-id="4c794-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="4c794-112">Un errore è un errore non fatale se si desidera che il cmdlet continui a elaborare l'oggetto corrente e altri oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="4c794-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="4c794-113">Un errore è un errore non fatale se è correlato a un oggetto di input specifico o a un subset di oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="4c794-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c794-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4c794-114">See Also</span></span>

[<span data-ttu-id="4c794-115">System. Management. Automation. cmdlet. ThrowTerminatingError \*</span><span class="sxs-lookup"><span data-stu-id="4c794-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="4c794-116">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="4c794-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="4c794-117">Record degli errori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c794-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="4c794-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c794-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
