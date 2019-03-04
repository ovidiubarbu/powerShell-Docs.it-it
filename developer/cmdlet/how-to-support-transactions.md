---
title: Come supportare le transazioni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857117"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="a4529-102">Come supportare le transazioni</span><span class="sxs-lookup"><span data-stu-id="a4529-102">How to Support Transactions</span></span>

<span data-ttu-id="a4529-103">Questo esempio illustra gli elementi di base del codice che aggiunge il supporto per le transazioni a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a4529-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a4529-104">Per altre informazioni su come Windows PowerShell gestisce le transazioni, vedere [sulle transazioni][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="a4529-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="a4529-105">Il supporto delle transazioni</span><span class="sxs-lookup"><span data-stu-id="a4529-105">To support transactions</span></span>

1. <span data-ttu-id="a4529-106">Quando si dichiara l'attributo Cmdlet, specificare che il cmdlet supporta le transazioni.</span><span class="sxs-lookup"><span data-stu-id="a4529-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="a4529-107">Quando il cmdlet supporta le transazioni, Windows PowerShell aggiunge il `UseTransaction` parametro al cmdlet quando viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="a4529-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="a4529-108">All'interno di uno dei metodi di elaborazione dell'input, aggiungere un `if` blocco per determinare se una transazione è disponibile.</span><span class="sxs-lookup"><span data-stu-id="a4529-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="a4529-109">Se il `if` istruzione si risolve in `true`, le azioni all'interno di questa istruzione possono essere eseguite nel contesto della transazione corrente.</span><span class="sxs-lookup"><span data-stu-id="a4529-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="a4529-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4529-110">See Also</span></span>

[<span data-ttu-id="a4529-111">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4529-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
