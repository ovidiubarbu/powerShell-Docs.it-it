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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369970"
---
# <a name="displaying-error-information"></a>Visualizzazione di informazioni sugli errori

In questo argomento vengono illustrati i modi in cui gli utenti possono visualizzare le informazioni sugli errori.

Quando il cmdlet rileva un errore, per impostazione predefinita la presentazione delle informazioni sull'errore sarà simile all'output degli errori seguente.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Tuttavia, gli utenti possono visualizzare gli errori per categoria impostando la variabile `$ErrorView` su `"CategoryView"`. Visualizzazione categorie consente di visualizzare informazioni specifiche del record degli errori anziché una descrizione dell'errore in formato testo libero. Questa visualizzazione può essere utile se si dispone di un lungo elenco di errori da analizzare. Nella visualizzazione categoria il messaggio di errore precedente viene visualizzato come segue.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Per ulteriori informazioni sulle categorie di errore, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Vedere anche

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
