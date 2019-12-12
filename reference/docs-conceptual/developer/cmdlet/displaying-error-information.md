---
title: Visualizzazione delle informazioni sull'errore | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369970"
---
# <a name="displaying-error-information"></a><span data-ttu-id="1d1a5-102">Visualizzazione di informazioni sugli errori</span><span class="sxs-lookup"><span data-stu-id="1d1a5-102">Displaying Error Information</span></span>

<span data-ttu-id="1d1a5-103">In questo argomento vengono illustrati i modi in cui gli utenti possono visualizzare le informazioni sugli errori.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="1d1a5-104">Quando il cmdlet rileva un errore, per impostazione predefinita la presentazione delle informazioni sull'errore sarà simile all'output degli errori seguente.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="1d1a5-105">Tuttavia, gli utenti possono visualizzare gli errori per categoria impostando la variabile di `$ErrorView` su `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="1d1a5-106">Visualizzazione categorie consente di visualizzare informazioni specifiche del record degli errori anziché una descrizione dell'errore in formato testo libero.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="1d1a5-107">Questa visualizzazione può essere utile se si dispone di un lungo elenco di errori da analizzare.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="1d1a5-108">Nella visualizzazione categoria il messaggio di errore precedente viene visualizzato come segue.</span><span class="sxs-lookup"><span data-stu-id="1d1a5-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="1d1a5-109">Per ulteriori informazioni sulle categorie di errore, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="1d1a5-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d1a5-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d1a5-110">See Also</span></span>

[<span data-ttu-id="1d1a5-111">Record degli errori di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d1a5-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="1d1a5-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1d1a5-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
