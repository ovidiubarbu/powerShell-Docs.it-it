---
title: Supporto della guida online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360660"
---
# <a name="supporting-online-help"></a>Supporto per la Guida in linea

A partire da Windows PowerShell 3,0, esistono due modi per supportare la funzionalità `Get-Help` online per i comandi di Windows PowerShell. In questo argomento viene illustrato come implementare questa funzionalità per diversi tipi di comando.

## <a name="about-online-help"></a>Informazioni sulla Guida in linea

La guida online è sempre stata una parte essenziale di Windows PowerShell. Anche se il cmdlet `Get-Help` Visualizza gli argomenti della Guida al prompt dei comandi, molti utenti preferiscono l'esperienza di lettura online, inclusi la codifica dei colori, i collegamenti ipertestuali e la condivisione di idee nel contenuto della community e nei documenti basati su wiki. Soprattutto, prima dell'avvento della Guida aggiornabile, la guida online forniva la versione più aggiornata dei file della guida.

Con l'avvento della Guida aggiornabile di Windows PowerShell 3,0, la guida online svolge ancora un ruolo fondamentale. Oltre all'esperienza utente flessibile, la Guida in linea consente agli utenti che non hanno o non possono utilizzare la guida aggiornabile di scaricare gli argomenti della guida.

## <a name="how-get-help--online-works"></a>Come funziona get-help-online

Per consentire agli utenti di trovare gli argomenti della guida online per i comandi, il comando `Get-Help` ha un parametro online che apre la versione online dell'argomento della Guida per un comando nel browser Internet predefinito dell'utente.

Ad esempio, il comando seguente consente di aprire l'argomento della Guida in linea per il cmdlet `Invoke-Command`.

```powershell
Get-Help Invoke-Command -Online
```

Per implementare `Get-Help`-online, il cmdlet `Get-Help` Cerca un Uniform Resource Identifier (URI) per l'argomento della guida della versione online nei percorsi seguenti.

- Il primo collegamento nella sezione collegamenti correlati dell'argomento della Guida per il comando. L'argomento della guida deve essere installato nel computer dell'utente. Questa funzionalità è stata introdotta in Windows PowerShell 2,0.

- Proprietà HelpUri di qualsiasi comando. La proprietà HelpUri è accessibile anche quando l'argomento della Guida per il comando non è installato nel computer dell'utente. Questa funzionalità è stata introdotta in Windows PowerShell 3,0.

  `Get-Help` cerca un URI nella prima voce della sezione collegamenti correlati prima di ottenere il valore della proprietà HelpUri. Se il valore della proprietà non è corretto o è stato modificato, è possibile eseguirne l'override immettendo un valore diverso nel primo collegamento correlato. Tuttavia, il primo collegamento correlato funziona solo quando gli argomenti della guida vengono installati nel computer dell'utente.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Aggiunta di un URI al primo collegamento correlato di un argomento della guida del comando

È possibile supportare `Get-Help`-online per qualsiasi comando aggiungendo un URI valido alla prima voce nella sezione collegamenti correlati dell'argomento della guida basato su XML per il comando. Questa opzione è valida solo negli argomenti della Guida basati su XML e funziona solo quando l'argomento della guida è installato nel computer dell'utente. Quando l'argomento della guida è installato e l'URI viene popolato, questo valore ha la precedenza sulla proprietà **HelpUri** del comando.

Per supportare questa funzionalità, l'URI deve essere visualizzato nell'elemento `maml:uri` sotto il primo elemento `maml:relatedLinks/maml:navigationLink` nell'elemento `maml:relatedLinks`.

Nel codice XML seguente viene illustrata la posizione corretta dell'URI. Il testo "versione online:" nell'elemento `maml:linkText` è una procedura consigliata, ma non è obbligatorio.

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

## <a name="adding-the-helpuri-property-to-a-command"></a>Aggiunta della proprietà HelpUri a un comando

In questa sezione viene illustrato come aggiungere la proprietà HelpUri ai comandi di tipi diversi.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Aggiunta di una proprietà HelpUri a un cmdlet

Per i cmdlet scritti in C#, aggiungere un attributo **HelpUri** alla classe cmdlet. Il valore dell'attributo deve essere un URI che inizia con "http" o "https".

Il codice seguente illustra l'attributo HelpUri della classe di cmdlet `Get-History`.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Aggiunta di una proprietà HelpUri a una funzione avanzata

Per le funzioni avanzate, aggiungere una proprietà **HelpUri** all'attributo di **cmdlet** . Il valore della proprietà deve essere un URI che inizia con "http" o "https".

Il codice seguente illustra l'attributo HelpUri della funzione New-Calendar

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Aggiunta di un attributo HelpUri a un comando CIM

Per i comandi CIM, aggiungere un attributo **HelpUri** all'elemento **CMDLETMETADATA** nel file CDXML. Il valore dell'attributo deve essere un URI che inizia con "http" o "https".

Il codice seguente illustra l'attributo HelpUri del comando Start-debug CIM

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Aggiunta di un attributo HelpUri a un flusso di lavoro

Per i flussi di lavoro scritti nel linguaggio di Windows PowerShell, aggiungere un **. Direttiva ExternalHelp** Comment nel codice del flusso di lavoro. Il valore della direttiva deve essere un URI che inizia con "http" o "https".

> [!NOTE]
> La proprietà HelpUri non è supportata per i flussi di lavoro basati su XAML in Windows PowerShell.

Nel codice seguente viene illustrato il. Direttiva ExternalHelp in un file del flusso di lavoro.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```