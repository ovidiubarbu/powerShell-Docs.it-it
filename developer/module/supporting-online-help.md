---
title: Supporto per la Guida Online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857917"
---
# <a name="supporting-online-help"></a>Supporto per la Guida in linea

A partire da Windows PowerShell 3.0, esistono due modi per supportare il `Get-Help` funzionalità Online per i comandi di Windows PowerShell. In questo argomento viene illustrato come implementare questa funzionalità per i tipi di comandi diverso.

## <a name="about-online-help"></a>Informazioni sulla Guida Online

Guida in linea è sempre stata una parte essenziale di Windows PowerShell. Sebbene il `Get-Help` cmdlet consente di visualizzare gli argomenti della Guida al prompt dei comandi, molti utenti preferiscono l'esperienza di lettura online, tra cui codifica a colori, collegamenti ipertestuali e la condivisione delle idee in documenti basati su wiki e contenuti della Community. Ancora più importante, prima dell'avvento di Guida aggiornabile, la Guida in linea fornita la versione più aggiornata dei file della Guida.

Con l'avvento di Guida aggiornabile in Windows PowerShell 3.0, la Guida in linea ha ancora un ruolo fondamentale. Oltre all'esperienza dell'utente flessibile Guida in linea vengono fornite informazioni per gli utenti che non hanno o non è possibile usare la Guida aggiornabile per scaricare gli argomenti della Guida.

## <a name="how-get-help--online-works"></a>Come Get-Help-Online Works

Per consentire agli utenti di trovare gli argomenti della Guida in linea dei comandi, il `Get-Help` command include un parametro Online che consente di aprire la versione online dell'argomento della Guida per un comando nel browser Internet predefinito dell'utente.

Ad esempio, il comando seguente consente di aprire l'argomento della Guida in linea per il `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Per implementare `Get-Help` -Online, il `Get-Help` cmdlet è simile per un identificatore URI (Uniform Resource) per l'argomento della Guida in linea di versione nei percorsi seguenti.

- Il primo collegamento nella sezione collegamenti correlati dell'argomento della Guida per il comando. L'argomento della Guida deve essere installato nel computer dell'utente. Questa funzionalità è stata introdotta in Windows PowerShell 2.0.

- La proprietà HelpUri di qualsiasi comando. La proprietà helpuri venga applicato è accessibile anche quando l'argomento della Guida per il comando non è installato nel computer dell'utente. Questa funzionalità è stata introdotta in Windows PowerShell 3.0.

  `Get-Help` Cerca un URI nella prima voce nella sezione collegamenti correlati prima di ottenere il valore della proprietà helpuri venga applicato. Se il valore della proprietà non è corretto o è stato modificato, è possibile eseguirne l'override immettendo un valore diverso nel primo collegamento correlato. Tuttavia, il primo collegamento correlato funziona solo quando gli argomenti della Guida siano installati nel computer dell'utente.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Aggiunta di un URI per il primo collegamento correlato di un argomento della Guida in linea di comando

È possibile supportare `Get-Help` -Online per qualsiasi comando mediante l'aggiunta di un URI valido per la prima voce nella sezione collegamenti correlati dell'argomento della Guida basati su XML per il comando. Questa opzione è valida solo in argomenti della Guida basati su XML e funziona solo quando l'argomento della Guida è installato nel computer dell'utente. Quando viene installato l'argomento della Guida e l'URI viene popolato, questo valore ha la precedenza il **HelpUri** proprietà del comando. Per informazioni su argomenti della Guida basati su XML per i comandi, vedere [Writing XML-Based gli argomenti della Guida per i comandi](../help/writing-xml-based-help-topics-for-commands.md).

Per supportare questa funzionalità, l'URI deve essere specificata nel `maml:uri` elemento sotto il primo `maml:relatedLinks/maml:navigationLink` elemento il `maml:relatedLinks` elemento.

Il codice XML seguente viene illustrata la posizione corretta dell'URI. La "versione Online:" testo nel `maml:linkText` elemento è una procedura consigliata, ma non è obbligatorio.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Aggiunta della proprietà helpuri venga applicato a un comando

Questa sezione illustra come aggiungere la proprietà helpuri venga applicato ai comandi di tipi diversi.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Aggiunta di una proprietà helpuri venga applicato a un Cmdlet

Per i cmdlet scritti in C#, aggiungere un' **HelpUri** attributo alla classe del Cmdlet. Il valore dell'attributo deve essere un URI che inizia con "http" o "https".

Il codice seguente mostra l'attributo HelpUri del `Get-History` classe cmdlet.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Aggiunta di una proprietà helpuri venga applicato a una funzione avanzata

Per le funzioni avanzate, aggiungere un **HelpUri** proprietà per il **CmdletBinding** attributo. Il valore della proprietà deve essere un URI che inizia con "http" o "https".

Il codice seguente mostra l'attributo HelpUri della funzione New-calendario

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Aggiunta di un attributo HelpUri a un comando CIM

Per i comandi CIM, aggiungere un **HelpUri** attributo il **CmdletMetadata** elemento nel file CDXML. Il valore dell'attributo deve essere un URI che inizia con "http" o "https".

Il codice seguente mostra l'attributo HelpUri del comando Start-Debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Aggiunta di un attributo HelpUri a un flusso di lavoro

Per i flussi di lavoro che vengono scritti nel linguaggio di Windows PowerShell, aggiungere un **. ExternalHelp** comment (direttiva) al codice del flusso di lavoro. Il valore della direttiva deve essere un URI che inizia con "http" o "https".

> [!NOTE]
> La proprietà helpuri venga applicato non è supportata per flussi di lavoro basati su XAML in Windows PowerShell.

Il codice seguente illustra il. Direttiva ExternalHelp in un file del flusso di lavoro.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```