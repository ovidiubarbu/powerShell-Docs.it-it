---
title: Come scrivere un modulo di file binari di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229327"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Come scrivere un modulo binario di PowerShell

Un modulo binario può essere qualsiasi assembly (DLL) che contiene le classi di cmdlet. Per impostazione predefinita, vengono importati tutti i cmdlet nell'assembly quando viene importato il modulo binario. Tuttavia, è possibile limitare i cmdlet che vengono importati mediante la creazione di un manifesto del modulo il cui modulo radice è l'assembly. (Ad esempio, la chiave CmdletsToExport del manifesto è utilizzabile per esportare solo i cmdlet necessari.) Inoltre, un modulo binario può contenere altre parti di tali informazioni utili che non è un singolo cmdlet, una struttura di directory e file aggiuntivi.

La procedura seguente viene descritto come creare e installare un modulo binario di PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Come creare e installare un modulo binario di PowerShell

1. Creare una soluzione binaria di PowerShell (ad esempio un cmdlet scritto in C#), con le funzionalità necessarie e garantire che venga eseguito correttamente.

   Dalla prospettiva del codice, il nucleo di un modulo binario è semplicemente un assembly di cmdlet. In effetti, PowerShell considererà assembly un singolo cmdlet come un modulo, in termini di caricamento e scaricamento, senza ulteriori interventi da parte dello sviluppatore. Per altre informazioni sulla scrittura di un cmdlet, vedere [scrittura di un Cmdlet di Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Se necessario, creare il resto della soluzione: (altri cmdlet, i file XML e così via) e vengono descritte con un manifesto del modulo.

   Oltre a descrivere gli assembly di cmdlet nella soluzione, è possibile descrivere un manifesto del modulo come si desidera che il modulo esportati e importati, i cmdlet che verranno esposto e quali file aggiuntivi diventeranno il modulo.
   Come indicato in precedenza, tuttavia, un cmdlet binario, ad esempio un modulo con un impegno aggiuntivo può gestire con PowerShell.
   Di conseguenza, un manifesto del modulo è utile principalmente per la combinazione di più file in un singolo pacchetto o per il controllo in modo esplicito di pubblicazione per un determinato assembly.
   Per altre informazioni, vedere [come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md).

   Il codice seguente è un'operazione estremamente semplice C# blocco di codice che contiene tre cmdlet nello stesso file che può essere utilizzato come un modulo.

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

3. Creare un pacchetto della soluzione e salvare il pacchetto a una destinazione nel percorso del modulo di PowerShell.

   Il `PSModulePath` variabile di ambiente globali vengono descritti i percorsi predefiniti che PowerShell utilizzerà per individuare un modulo. Ad esempio, potrebbe essere un percorso comune per salvare un modulo in un sistema `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Se non si utilizza il percorso predefinito, è necessario dichiarare in modo esplicito il percorso del modulo durante l'installazione. Assicurarsi di creare una cartella in cui salvare il modulo, si potrebbe avere bisogno la cartella per archiviare più assembly e file per la soluzione.

   Si noti che tecnicamente non occorre installare un modulo in qualsiasi punto nel `PSModulePath` -sono semplicemente i percorsi predefiniti che eseguirà la ricerca per il modulo di PowerShell. Tuttavia, viene considerato ottimale per eseguire questa operazione, a meno che non si dispone di un buon motivo per l'archiviazione di un modulo in un'altra posizione. Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica il percorso di installazione del modulo PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importare un modulo in PowerShell con una chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   La chiamata a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) caricherà un modulo in memoria attiva. Se si usa PowerShell 3.0 e versioni successive, chiamare semplicemente il nome del modulo nel codice verrà anche importare i dati; per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importazione Snap-in assembly come moduli

Cmdlet e provider presenti negli assembly snap-in può essere caricato come moduli binari. Quando l'assembly snap-in vengono caricati come moduli binari, i cmdlet e provider nello snap-in sono disponibili all'utente, ma la classe di snap-nell'assembly viene ignorata e lo snap-in non è registrato. Di conseguenza, i cmdlet di snap-in di Windows PowerShell non è possibile rilevare lo snap-in anche con i cmdlet e provider disponibili nella sessione.

Inoltre, qualsiasi formattazione o tipi di file che fanno riferimento lo snap-in non è possibile importare come parte di un modulo binario.
Per importare i file di formattazione e tipi è necessario creare un manifesto del modulo.
Vedere [come scrivere un manifesto del modulo di PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
