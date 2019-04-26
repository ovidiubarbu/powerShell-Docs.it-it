---
title: Scrittura della Guida per i moduli di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082033"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Scrittura della Guida per i moduli di Windows PowerShell

I moduli di Windows PowerShell possono includere gli argomenti della Guida sul modulo e sui membri del modulo, ad esempio cmdlet, provider, funzioni e script. Il `Get-Help` cmdlet consente di visualizzare gli argomenti della Guida modulo nello stesso formato quando visualizza la Guida per altri elementi di Windows PowerShell, e gli utenti utilizzano standard `Get-Help` comandi per ottenere gli argomenti della Guida.

Questo documento viene illustrato il formato e il posizionamento corretto di argomenti della Guida di modulo e suggerisce le linee guida per il contenuto della Guida di modulo.

## <a name="types-of-module-help"></a>Tipi di modulo della Guida in linea

Un modulo può includere i seguenti tipi di Guida in linea.

- **Guida dei cmdlet**. Gli argomenti della Guida che descrivono i cmdlet in un modulo sono file XML che utilizzano il comando Guida in linea dello schema

- **Guida del provider**. Gli argomenti della Guida che descrivono i provider in un modulo sono file XML che usano il provider consentono di schema.

- **Funzione Help**. Gli argomenti della Guida che descrivono le funzioni in un modulo può essere utile per i file XML che utilizzano il comando dello schema o gli argomenti della Guida basata sui commenti all'interno della funzione, o lo script o modulo di script

- **Lo script Help**. Gli argomenti della Guida che descrivono gli script in un modulo può essere utile per i file XML che utilizzano il comando dello schema o argomenti della Guida basati su commenti nello script o nel modulo di script.

- **Concettuale ("About") della Guida**. È possibile usare un concettuale ("about"), l'argomento della Guida per descrivere il modulo e i relativi membri e per illustrare come i membri possono essere usati insieme per eseguire attività. Argomenti della Guida concettuale sono file di testo con codifica Unicode (UTF-8). Il nome del file è necessario usare il `about_<name>.help.txt` formato, ad esempio about_MyModule.help.txt. Per impostazione predefinita, Windows PowerShell include oltre 100 di queste Guida informazioni su concetti di base e sono formattati come nell'esempio seguente.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Posizionamento della Guida dei moduli

Il `Get-Help` cmdlet cerca i file di argomento della Guida di modulo in sottodirectory specifiche del linguaggio della directory del modulo.

Ad esempio, il diagramma di struttura di directory seguente mostra la posizione degli argomenti della Guida per il modulo SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> Nell'esempio, il  *\<ModulePath >* segnaposto rappresenta uno dei percorsi nella `PSModulePath` variabile di ambiente, ad esempio home\Documents\Modules $, $pshome\Modules o un percorso personalizzato specificato dall'utente.

## <a name="getting-module-help"></a>Visualizzazione della Guida di modulo

Quando un utente importa un modulo in una sessione, gli argomenti della Guida per il dato modulo vengono importati nella sessione con il modulo. È possibile elencare i file di argomento della Guida nel valore della chiave FileList nel manifesto del modulo, ma gli argomenti della Guida non sono interessati dal `Export-ModuleMember` cmdlet.

È possibile fornire argomenti della Guida di modulo in lingue diverse. Il `Get-Help` cmdlet Visualizza automaticamente gli argomenti della Guida di modulo nel linguaggio specificato per l'utente corrente nell'elemento di Regional and Language Options nel Pannello di controllo. In Windows Vista e versioni successive di Windows, `Get-Help` Cerca argomenti della Guida nella sottodirectory specifica del linguaggio della directory del modulo in conformità con gli standard di fallback language stabilita per Windows.

A partire da Windows PowerShell 3.0, che esegue un `Get-Help` comando per un cmdlet o una funzione attiva l'importazione automatica del modulo. Il `Get-Help` cmdlet consente di visualizzare immediatamente il contenuto degli argomenti della Guida nel modulo.

Se il modulo non contiene gli argomenti della Guida e non sono disponibili argomenti della Guida per i comandi del modulo nel computer dell'utente, `Get-Help` consente di visualizzare la Guida generata automaticamente. La Guida generata automaticamente include la sintassi dei comandi, parametri e tipi di input e output, ma non include le eventuali descrizioni. La Guida generata automaticamente include testo che indirizza l'utente a provare a usare il `Update-Help` cmdlet per scaricare la Guida per il comando da Internet o da una condivisione file. Consiglia di utilizzare anche il **Online** parametro del `Get-Help` per ottenere la versione online dell'argomento della Guida.

## <a name="supporting-updatable-help"></a>Supporto per la Guida aggiornabile

Gli utenti di Windows PowerShell 3.0 e versioni successive di Windows PowerShell possono scaricare e installare file della Guida aggiornati per un modulo da Internet o da una condivisione file locale. Il `Update-Help` e `Save-Help` cmdlet nascondono i dettagli di gestione da parte dell'utente. Agli utenti di eseguire la `Update-Help` cmdlet e quindi usare il `Get-Help` cmdlet per leggere i file della Guida più recenti per il modulo al prompt dei comandi Windows PowerShell. Gli utenti non sono necessario riavviare Windows o Windows PowerShell.

Gli utenti protetti da firewall e quelli senza accesso a Internet possono usare la Guida aggiornabile, nonché. Gli amministratori con Internet accedere utilizzare le `Save-Help` cmdlet per scaricare e installare i file della Guida più recenti in una condivisione file. Usano quindi gli utenti il **tracciato** parametro del `Update-Help` per ottenere i file della Guida più recenti dalla condivisione file.

Gli autori di moduli possono includere i file della Guida nel modulo e usare la Guida aggiornabile per aggiornare i file della Guida, oppure omettere i file della Guida dal modulo e usare la Guida aggiornabile per installare e aggiornare.

Per altre informazioni sulla Guida aggiornabile, vedere [supporto della Guida aggiornabile](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Supporto per la Guida in linea

Gli utenti che non è possibile o non si installano aggiornato i file nei propri computer spesso si basano sulla versione online degli argomenti della Guida di modulo della Guida. Il **Online** parametro del `Get-Help` cmdlet apre la versione online di un cmdlet o un argomento della Guida funzione avanzata per l'utente nel browser Internet predefinito.

Il `Get-Help` cmdlet Usa il valore della **HelpUri** proprietà della funzione per trovare la versione online dell'argomento della Guida o cmdlet.

A partire da Windows PowerShell 3.0, si consente agli utenti di trovare la versione online degli argomenti della Guida cmdlet e funzioni che definisce l'attributo HelpUri nella classe del cmdlet o le **HelpUri** proprietà del **CmdletBinding** attributo. Il valore dell'attributo è il valore della **HelpUri** proprietà del cmdlet o funzione.

Per altre informazioni, vedere [supporto della Guida Online](./supporting-online-help.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)

[Supporto per la Guida aggiornabile](./supporting-updatable-help.md)

[Supporto per la Guida Online](./supporting-online-help.md)