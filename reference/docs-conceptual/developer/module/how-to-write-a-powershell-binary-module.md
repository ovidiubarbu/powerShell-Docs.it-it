---
title: Come scrivere un modulo binario di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367120"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Come scrivere un modulo binario di PowerShell

Un modulo binario può essere qualsiasi assembly (. dll) che contiene le classi di cmdlet. Per impostazione predefinita, tutti i cmdlet nell'assembly vengono importati quando viene importato il modulo binario. Tuttavia, è possibile limitare i cmdlet importati creando un manifesto del modulo il cui modulo radice è l'assembly. (Ad esempio, la chiave CmdletsToExport del manifesto può essere usata per esportare solo i cmdlet necessari). Un modulo binario può inoltre contenere file aggiuntivi, una struttura di directory e altre informazioni di gestione utili che non possono essere utilizzate da un singolo cmdlet.

Nella procedura seguente viene descritto come creare e installare un modulo binario di PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Come creare e installare un modulo binario di PowerShell

1. Creare una soluzione PowerShell binaria, ad esempio un cmdlet scritto C#in, con le funzionalità necessarie e assicurarsi che venga eseguita correttamente.

   Dal punto di vista del codice, il nucleo di un modulo binario è semplicemente un assembly di cmdlet. In realtà, PowerShell tratterà un singolo assembly di cmdlet come modulo, in termini di caricamento e scaricamento, senza sforzi aggiuntivi da parte dello sviluppatore. Per ulteriori informazioni sulla scrittura di un cmdlet, vedere [scrittura di un cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Se necessario, creare il resto della soluzione, ovvero i cmdlet aggiuntivi, i file XML e così via, e descriverli con un manifesto del modulo.

   Oltre a descrivere gli assembly dei cmdlet nella soluzione, un manifesto del modulo può descrivere come si vuole che il modulo venga esportato e importato, quali cmdlet verranno esposti e quali file aggiuntivi verranno inseriti nel modulo.
   Come indicato in precedenza, tuttavia, PowerShell può considerare un cmdlet binario come un modulo senza ulteriori sforzi.
   Di conseguenza, un manifesto del modulo è particolarmente utile per combinare più file in un singolo pacchetto o per controllare in modo esplicito la pubblicazione per un determinato assembly.
   Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).

   Il codice seguente è un blocco di C# codice estremamente semplice che contiene tre cmdlet nello stesso file che possono essere usati come modulo.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Creare il pacchetto della soluzione e salvare il pacchetto in un punto qualsiasi nel percorso del modulo di PowerShell.

   La variabile di ambiente globale `PSModulePath` descrive i percorsi predefiniti che verranno usati da PowerShell per individuare il modulo. Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Se non si usano i percorsi predefiniti, sarà necessario indicare in modo esplicito il percorso del modulo durante l'installazione. Assicurarsi di creare una cartella in cui salvare il modulo, perché potrebbe essere necessaria la cartella per archiviare più assembly e file per la soluzione.

   Si noti che tecnicamente non è necessario installare il modulo in un punto qualsiasi dell'`PSModulePath`, che sono semplicemente i percorsi predefiniti che verrà ricercato da PowerShell per il modulo. Tuttavia, si tratta di una procedura consigliata, a meno che non si disponga di un buon motivo per archiviare il modulo altrove. Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica del percorso di installazione del modulo di PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importare il modulo in PowerShell con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   La chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) caricherà il modulo nella memoria attiva. Se si usa PowerShell 3,0 e versioni successive, verrà importato anche il nome del modulo nel codice. per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importazione di assembly snap-in come moduli

I cmdlet e i provider presenti negli assembly snap-in possono essere caricati come moduli binari. Quando gli assembly dello snap-in vengono caricati come moduli binari, i cmdlet e i provider nello snap-in sono disponibili per l'utente, ma la classe di snap-in nell'assembly viene ignorata e lo snap-in non è registrato. Di conseguenza, i cmdlet dello snap-in forniti da Windows PowerShell non sono in grado di rilevare lo snap-in anche se i cmdlet e i provider sono disponibili per la sessione.

Inoltre, tutti i file di formattazione o di tipi a cui fa riferimento lo snap-in non possono essere importati come parte di un modulo binario.
Per importare i file di formattazione e dei tipi, è necessario creare un manifesto del modulo.
Vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
