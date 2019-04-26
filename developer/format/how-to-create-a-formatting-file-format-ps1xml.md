---
title: Come creare un File di formattazione (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065502"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Come creare un file di formattazione (con estensione format.ps1xml)

In questo argomento viene descritto come creare un file di formattazione (. format.ps1xml).

> [!NOTE]
> È anche possibile creare un file di formattazione eseguendo una copia di uno dei file di Windows PowerShell. Se si esegue una copia di un file esistente, eliminare la firma digitale esistente e aggiungere la propria firma per il nuovo file.

### <a name="to-create-a-formatps1xml-file"></a>Per creare un. file format.ps1xml.

1. Creare un file di testo (txt) usando un testo dell'editor, ad esempio Blocco note.

2. Copiare le righe seguenti nel file di formattazione.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Il \<Configuration >\</Configuration > tag definiscono radice `Configuration` nodo. Tutti i tag XML aggiuntivi verranno racchiusi all'interno di questo nodo.

   - Il <ViewDefinitions> </ViewDefinitions> tag definiscono il `ViewDefinitions` nodo. Tutte le visualizzazioni vengono definite all'interno di questo nodo.

3. Salvare il file nella cartella di installazione di Windows PowerShell, alla cartella del modulo o in una sottocartella della cartella del modulo. Usare il formato nome seguente quando si salva il file: `MyFile.format.ps1xml`. File di formattazione devono usare il `.format.ps1xml` estensione.

   A questo punto si è pronti aggiungere le visualizzazioni per il file di formattazione. Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione. È possibile aggiungere una visualizzazione singola per ogni oggetto, più visualizzazioni per lo stesso oggetto o una singola visualizzazione che viene usata da più oggetti.

## <a name="see-also"></a>Vedere anche

[La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File](./writing-a-powershell-formatting-file.md)
