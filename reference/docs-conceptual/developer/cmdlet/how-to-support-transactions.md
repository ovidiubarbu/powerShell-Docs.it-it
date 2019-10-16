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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365540"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="26697-102">Come supportare le transazioni</span><span class="sxs-lookup"><span data-stu-id="26697-102">How to Support Transactions</span></span>

<span data-ttu-id="26697-103">Questo esempio Mostra gli elementi di codice di base che aggiungono il supporto per le transazioni a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="26697-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26697-104">Per ulteriori informazioni sul modo in cui Windows PowerShell gestisce le transazioni, vedere [informazioni sulle transazioni][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="26697-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="26697-105">Per supportare le transazioni</span><span class="sxs-lookup"><span data-stu-id="26697-105">To support transactions</span></span>

1. <span data-ttu-id="26697-106">Quando si dichiara l'attributo del cmdlet, specificare che il cmdlet supporta le transazioni.</span><span class="sxs-lookup"><span data-stu-id="26697-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="26697-107">Quando il cmdlet supporta le transazioni, Windows PowerShell aggiunge il parametro `UseTransaction` al cmdlet quando viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="26697-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="26697-108">All'interno di uno dei metodi di elaborazione dell'input, aggiungere un blocco `if` per determinare se una transazione è disponibile.</span><span class="sxs-lookup"><span data-stu-id="26697-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="26697-109">Se l'istruzione `if` viene risolta in `true`, le azioni all'interno di questa istruzione possono essere eseguite nel contesto della transazione corrente.</span><span class="sxs-lookup"><span data-stu-id="26697-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="26697-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="26697-110">See Also</span></span>

[<span data-ttu-id="26697-111">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26697-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
