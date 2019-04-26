---
title: Visualizzazione di informazioni di errore | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068284"
---
# <a name="displaying-error-information"></a>Visualizzazione di informazioni sugli errori

In questo argomento illustra i modi in cui gli utenti possono visualizzare le informazioni sull'errore.

Quando il cmdlet rileva un errore, la presentazione di informazioni sull'errore ricorderà, per impostazione predefinita, l'output di errore seguente.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Tuttavia, gli utenti possono visualizzare gli errori per categoria, impostando il `$ErrorView` variabile `"CategoryView"`. Visualizzazione per categorie vengono visualizzate informazioni specifiche da record error piuttosto che da una descrizione di testo libero dell'errore. In questa vista può essere utile se si dispone di un lungo elenco di errori da analizzare. Nella visualizzazione categoria, il messaggio di errore precedente viene visualizzato come indicato di seguito.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Per altre informazioni sulle categorie di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Vedere anche

[Record degli errori di PowerShell di Windows](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
