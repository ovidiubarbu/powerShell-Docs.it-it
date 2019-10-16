---
title: Scrittura della Guida per i moduli di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360560"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Scrittura della Guida per i moduli di Windows PowerShell

I moduli di Windows PowerShell possono includere argomenti della guida sul modulo e sui membri del modulo, ad esempio cmdlet, provider, funzioni e script. Il cmdlet `Get-Help` Visualizza gli argomenti della Guida relativi ai moduli nello stesso formato in cui viene visualizzata la guida per altri elementi di Windows PowerShell e gli utenti usano i comandi standard `Get-Help` per ottenere gli argomenti della guida.

Questo documento illustra il formato e la posizione corretta degli argomenti della guida sui moduli e suggerisce le linee guida per il contenuto della guida del modulo.

## <a name="types-of-module-help"></a>Tipi di guida del modulo

Un modulo può includere i seguenti tipi di guida.

- **Guida del cmdlet**. Gli argomenti della guida che descrivono i cmdlet in un modulo sono file XML che usano lo schema della guida del comando

- **Guida del provider**. Gli argomenti della guida che descrivono i provider in un modulo sono file XML che utilizzano lo schema della guida del provider.

- **Guida alla funzione**. Gli argomenti della guida che descrivono le funzioni in un modulo possono essere file XML che usano lo schema della guida del comando o gli argomenti della Guida basati su commenti all'interno della funzione oppure il modulo script o script

- **Guida dello script**. Gli argomenti della guida che descrivono gli script in un modulo possono essere file XML che usano gli argomenti della Guida relativi ai comandi o ai commenti del modulo script o script.

- **Guida concettuale ("about")** . È possibile utilizzare un argomento della Guida concettuale ("about") per descrivere il modulo e i relativi membri e spiegare in che modo i membri possono essere utilizzati insieme per eseguire le attività. Gli argomenti della Guida concettuale sono file di testo con codifica Unicode (UTF-8). Il nome file deve usare il formato `about_<name>.help.txt`, ad esempio about_MyModule. Help. txt. Per impostazione predefinita, Windows PowerShell include più di 100 di questi concetti concettuali sugli argomenti della guida e sono formattati come l'esempio seguente.

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

## <a name="placement-of-module-help"></a>Posizione della guida del modulo

Il cmdlet `Get-Help` cerca i file degli argomenti della guida del modulo in sottodirectory specifiche della lingua della directory del modulo.

Il diagramma della struttura di directory seguente, ad esempio, Mostra il percorso degli argomenti della Guida per il modulo SampleModule.

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
> Nell'esempio, il segnaposto *\<ModulePath >* rappresenta uno dei percorsi nella variabile di ambiente `PSModulePath`, ad esempio $Home \documents\modules, $PSHome \modules o un percorso personalizzato specificato dall'utente.

## <a name="getting-module-help"></a>Recupero della guida del modulo

Quando un utente importa un modulo in una sessione, gli argomenti della Guida per il modulo vengono importati nella sessione insieme al modulo. È possibile elencare i file di argomenti della guida nel valore della chiave FileList nel manifesto del modulo, ma gli argomenti della guida non sono interessati dal cmdlet `Export-ModuleMember`.

È possibile fornire argomenti della guida sui moduli in lingue diverse. Il cmdlet `Get-Help` Visualizza automaticamente gli argomenti della guida sui moduli nella lingua specificata per l'utente corrente nell'elemento Opzioni internazionali e della lingua nel pannello di controllo. In Windows Vista e nelle versioni successive di Windows, `Get-Help` cerca gli argomenti della Guida in sottodirectory specifiche della lingua della directory dei moduli in base agli standard di fallback della lingua stabiliti per Windows.

A partire da Windows PowerShell 3,0, l'esecuzione di un comando `Get-Help` per un cmdlet o una funzione attiva l'importazione automatica del modulo. Il cmdlet `Get-Help` Visualizza immediatamente il contenuto degli argomenti della guida nel modulo.

Se il modulo non contiene argomenti della guida e non sono disponibili argomenti della Guida per i comandi nel modulo sul computer dell'utente, `Get-Help` Visualizza la guida generata automaticamente. La guida generata automaticamente include la sintassi, i parametri e i tipi di input e output del comando, ma non include alcuna descrizione. La guida generata automaticamente include il testo che indirizza l'utente a provare a usare il cmdlet `Update-Help` per scaricare la guida per il comando da Internet o da una condivisione file. Si consiglia inoltre di utilizzare il parametro **online** del cmdlet `Get-Help` per ottenere la versione online dell'argomento della guida.

## <a name="supporting-updatable-help"></a>Supporto per la Guida aggiornabile

Gli utenti di Windows PowerShell 3,0 e versioni successive di Windows PowerShell possono scaricare e installare i file della Guida aggiornati per un modulo da Internet o da una condivisione file locale. I cmdlet `Update-Help` e `Save-Help` nascondono i dettagli di gestione dall'utente. Gli utenti eseguono il cmdlet `Update-Help` e quindi usano il cmdlet `Get-Help` per leggere i file della guida più recenti per il modulo al prompt dei comandi di Windows PowerShell. Gli utenti non devono riavviare Windows o Windows PowerShell.

Anche gli utenti protetti da firewall e quelli senza accesso a Internet possono utilizzare la guida aggiornabile. Gli amministratori con accesso a Internet usano il cmdlet `Save-Help` per scaricare e installare i file della guida più recenti in una condivisione file. Quindi, gli utenti usano il parametro **path** del cmdlet `Update-Help` per ottenere i file della guida più recenti dalla condivisione file.

Gli autori di moduli possono includere i file della guida nel modulo e usare la guida aggiornabile per aggiornare i file della Guida oppure omettere i file della guida dal modulo e usare la guida aggiornabile per installare e per aggiornarli.

Per ulteriori informazioni sulla guida aggiornabile, vedere Supporto per la [Guida aggiornabile](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Supporto per la Guida in linea

Gli utenti che non possono installare i file della Guida aggiornati nei propri computer spesso si basano sulla versione online degli argomenti della guida sui moduli. Il parametro **online** del cmdlet `Get-Help` apre la versione online di un cmdlet o di un argomento della Guida per le funzioni avanzate per l'utente nel browser Internet predefinito.

Il cmdlet `Get-Help` usa il valore della proprietà **HelpUri** del cmdlet o della funzione per trovare la versione online dell'argomento della guida.

A partire da Windows PowerShell 3,0, è possibile aiutare gli utenti a trovare la versione online degli argomenti della Guida relativi ai cmdlet e alle funzioni definendo l'attributo HelpUri nella classe cmdlet o la proprietà **HelpUri** dell'attributo di **cmdlet** . Il valore dell'attributo è il valore della proprietà **HelpUri** del cmdlet o della funzione.

Per ulteriori informazioni, vedere [supporto](./supporting-online-help.md)per la Guida in linea.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)

[Supporto della Guida aggiornabile](./supporting-updatable-help.md)

[Supporto della Guida in linea](./supporting-online-help.md)