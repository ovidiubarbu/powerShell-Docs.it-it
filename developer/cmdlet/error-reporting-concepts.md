---
title: Concetti di segnalazione degli errori | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054408"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="8d7e2-102">Concetti relativi alla segnalazione di errori</span><span class="sxs-lookup"><span data-stu-id="8d7e2-102">Error Reporting Concepts</span></span>

<span data-ttu-id="8d7e2-103">Windows PowerShell fornisce due meccanismi per la segnalazione degli errori: un meccanismo per la *irreversibili* e un altro meccanismo per *errori non fatali*.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="8d7e2-104">È importante per i cmdlet per segnalare gli errori correttamente in modo che l'applicazione host che esegue il cmdlet può rispondere in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="8d7e2-105">Il cmdlet deve chiamare il [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodo quando si verifica un errore che non esiste o non deve consentire al cmdlet di continuare a elaborare gli oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="8d7e2-106">Il cmdlet deve chiamare il [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo per segnalare errori non fatali quando il cmdlet può continuare a elaborare gli oggetti di input.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="8d7e2-107">Entrambi i metodi forniscono un record di errore che l'applicazione host può utilizzare per ricercare la causa dell'errore.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="8d7e2-108">Usare le linee guida seguenti per determinare se un errore è un tipo di terminazione o errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="8d7e2-109">Un errore è un errore irreversibile se evita che i cmdlet di continuare a elaborare l'oggetto corrente o dall'elaborazione degli oggetti di un'ulteriore input, indipendentemente dal loro contenuto.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="8d7e2-110">Un errore è un errore se non vuoi cmdlet continuare l'elaborazione degli oggetti di un'ulteriore input, indipendentemente dal loro contenuto o l'oggetto corrente.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="8d7e2-111">Un errore è un errore se si verifica in un cmdlet che non accettano o restituiscono un oggetto o se si verifica in un cmdlet che accetta o restituisce un solo oggetto.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="8d7e2-112">Se si desidera che i cmdlet per continuare a elaborare l'oggetto corrente e degli oggetti di un'ulteriore input, un errore è un errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="8d7e2-113">Se è collegato a un oggetto di input specifico o un subset di oggetti di input, un errore è un errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="8d7e2-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d7e2-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8d7e2-114">See Also</span></span>

[<span data-ttu-id="8d7e2-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="8d7e2-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="8d7e2-116">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="8d7e2-116">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="8d7e2-117">Record degli errori di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="8d7e2-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="8d7e2-118">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8d7e2-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
