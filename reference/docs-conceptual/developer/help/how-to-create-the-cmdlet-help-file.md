---
title: Come creare il file della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996040"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Come creare il file della Guida sui cmdlet

In questa sezione viene descritto come creare un file XML valido che contiene contenuto per gli argomenti della guida sui cmdlet di Windows PowerShell. In questa sezione viene illustrato come assegnare un nome al file della guida, come aggiungere le intestazioni XML appropriate e come aggiungere nodi che conterranno le diverse sezioni del contenuto della guida del cmdlet.

> [!NOTE]
> Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell. Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Come creare un file della Guida per i cmdlet

1. Creare un file di testo e salvarlo utilizzando la codifica UTF8. Il nome del file deve avere il formato seguente, in modo che Windows PowerShell possa rilevarlo come file della guida del cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Aggiungere le intestazioni XML seguenti al file di testo. Tenere presente che il file verrà convalidato in base allo schema MAML (multiagent Modeling Language). Attualmente, Windows PowerShell non fornisce strumenti per convalidare il file.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Aggiungere un nodo del comando al file della guida del cmdlet per ogni cmdlet nell'assembly. Ogni nodo all'interno del nodo Command si riferisce alle diverse sezioni dell'argomento della guida del cmdlet.

   La tabella seguente elenca l'elemento XML per ogni nodo, seguito da una descrizione di ogni nodo.

   |Nodo|Description|
   |----------|-----------------|
   |`<details>`|Aggiunge contenuto per le sezioni nome e riepilogo dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere il nome del cmdlet e il riepilogo](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Aggiunge contenuto per la sezione Descrizione dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Aggiunge contenuto per la sezione della sintassi dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere la sintassi a un argomento della guida del cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Aggiunge contenuto per la sezione PARAMETERS dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere parametri a un argomento della guida del cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Aggiunge contenuto per la sezione INPUTs dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere tipi di input a un argomento della guida del cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Aggiunge contenuto per la sezione OUTPUTs dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere valori restituiti a un argomento della guida del cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Aggiunge contenuto alla sezione Note dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere note a un argomento della guida del cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Aggiunge contenuto per la sezione degli esempi dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere esempi a un argomento della guida del cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Aggiunge contenuto per la sezione collegamenti correlati dell'argomento della guida del cmdlet. Per ulteriori informazioni, vedere [come aggiungere collegamenti correlati a un argomento della guida del cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Esempio

 Di seguito è riportato un esempio di un nodo di comando che include i nodi per le varie sezioni dell'argomento della guida del cmdlet.

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
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

 [Come aggiungere il nome e la sintassi del cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Come aggiungere la descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md)

 [Come aggiungere la sintassi a un argomento della guida del cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Come aggiungere parametri a un argomento della guida del cmdlet](./how-to-add-parameter-information.md)

 [Come aggiungere tipi di input a un argomento della guida del cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Come aggiungere valori restituiti a un argomento della guida del cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Come aggiungere note a un argomento della guida del cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Come aggiungere esempi a un argomento della guida del cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Come aggiungere collegamenti correlati a un argomento della guida del cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)