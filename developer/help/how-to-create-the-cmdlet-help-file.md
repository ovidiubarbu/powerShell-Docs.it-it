---
title: Come creare il File della Guida dei Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083247"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Come creare il file della Guida sui cmdlet

Questa sezione descrive come creare un file XML valido che include contenuto per gli argomenti della Guida di cmdlet di Windows PowerShell. In questa sezione viene illustrato come denominare il file della Guida, come aggiungere le intestazioni appropriate XML e come aggiungere nodi che conterranno le diverse sezioni del contenuto della Guida cmdlet.

> [!NOTE]
> Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell. Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Come creare un File della Guida dei Cmdlet

1. Creare un file di testo e salvarlo con codifica UTF8. Il nome del file deve essere nel formato seguente, in modo che Windows PowerShell può rilevare come un file della Guida.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Aggiungere le intestazioni XML seguente al file di testo. Tenere presente che il file verrà convalidato rispetto allo schema del linguaggio di modellazione multi-agente (MAML). Attualmente, Windows PowerShell non fornisce alcuno strumento per convalidare il file.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Aggiungere un nodo del comando per il file della Guida per ciascun cmdlet nell'assembly. Ogni nodo all'interno del nodo comando mette in relazione a varie sezioni dell'argomento della Guida del cmdlet.

   La tabella seguente elenca l'elemento XML per ogni nodo, seguita da una descrizione di ogni nodo.

   |Node|Description|
   |----------|-----------------|
   |`<details>`|Aggiunge contenuto per le sezioni di nome e il riepilogo dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere il nome di Cmdlet e il riepilogo](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Aggiunge contenuto per la sezione Descrizione dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere la descrizione dettagliata per un argomento della Guida Cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Aggiunge contenuto per la sezione relativa alla sintassi dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere la sintassi per un argomento della Guida Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Aggiunge contenuto per la sezione parametri dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere parametri a un argomento della Guida Cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Aggiunge il contenuto della sezione di input dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere i tipi di Input a un argomento della Guida Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Aggiunge il contenuto della sezione di output dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere valori restituiti per un argomento della Guida Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Aggiunge contenuto alla sezione Note dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere note per un argomento della Guida Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Aggiunge il contenuto della sezione di esempi dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come esempi di aggiungere un argomento della Guida per Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Aggiunge il contenuto della sezione collegamenti correlati dell'argomento della Guida del cmdlet. Per altre informazioni, vedere [come aggiungere collegamenti correlati a un argomento della Guida Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Esempio

 Di seguito è riportato un esempio di un nodo del comando che include i nodi per le diverse sezioni dell'argomento della Guida del cmdlet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Vedere anche

 [Come aggiungere il nome di Cmdlet e riepilogo](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Come aggiungere la descrizione dettagliata per un argomento della Guida del Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Come aggiungere la sintassi per un argomento della Guida del Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Come aggiungere parametri a un argomento della Guida del Cmdlet](./how-to-add-parameter-information.md)

 [Come aggiungere i tipi di Input a un argomento della Guida del Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Come aggiungere i valori restituiti per un argomento della Guida del Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Come aggiungere note per un argomento della Guida Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Come aggiungere esempi per un argomento della Guida del Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Come aggiungere collegamenti correlati a un argomento della Guida del Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)