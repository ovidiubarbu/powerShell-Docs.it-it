---
title: Come creare un file di formattazione (format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363620"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Come creare un file di formattazione (con estensione format.ps1xml)

In questo argomento viene descritto come creare un file di formattazione (format. ps1xml).

> [!NOTE]
> È anche possibile creare un file di formattazione eseguendo una copia di uno dei file forniti da Windows PowerShell. Se si crea una copia di un file esistente, eliminare la firma digitale esistente e aggiungere la propria firma al nuovo file.

### <a name="to-create-a-formatps1xml-file"></a>Per creare un file con estensione format. ps1xml.

1. Creare un file di testo (con estensione txt) utilizzando un editor di testo, ad esempio Blocco note.

2. Copiare le righe seguenti nel file di formattazione.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - I tag \<Configuration > \</> di configurazione definiscono il nodo `Configuration` radice. Tutti i tag XML aggiuntivi verranno racchiusi in questo nodo.

   - I <ViewDefinitions></ViewDefinitions> Tag definiscono il nodo `ViewDefinitions`. Tutte le visualizzazioni vengono definite all'interno di questo nodo.

3. Salvare il file nella cartella di installazione di Windows PowerShell, nella cartella del modulo o in una sottocartella della cartella del modulo. Quando si salva il file, utilizzare il formato del nome seguente: `MyFile.format.ps1xml`. I file di formattazione devono usare l'estensione `.format.ps1xml`.

   A questo punto è possibile aggiungere visualizzazioni al file di formattazione. Non esiste alcun limite al numero di visualizzazioni che è possibile definire in un file di formattazione. È possibile aggiungere una singola visualizzazione per ogni oggetto, più visualizzazioni per lo stesso oggetto o una singola visualizzazione utilizzata da più oggetti.

## <a name="see-also"></a>Vedere anche

[Scrittura di un file di formattazione e di tipi di Windows PowerShell](./writing-a-powershell-formatting-file.md)
