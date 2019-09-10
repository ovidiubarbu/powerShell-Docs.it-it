---
title: Informazioni su un modulo di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848057"
---
# <a name="understanding-a-windows-powershell-module"></a>Informazioni su un modulo di Windows PowerShell

Un *modulo* è un set di funzionalità correlate di Windows PowerShell, raggruppate come una comoda unità (in genere salvata in una singola directory). Definendo un set di file script correlati, assembly e risorse correlate come modulo, è possibile fare riferimento, caricare, rendere permanente e condividere il codice in modo molto più semplice rispetto a quanto altrimenti.

Lo scopo principale di un modulo è quello di consentire la modularità (IE, riuso e astrazione) del codice di Windows PowerShell. Ad esempio, il modo più semplice per creare un modulo consiste nel salvare semplicemente uno script di Windows PowerShell come file con estensione psm1. Questa operazione consente di controllare (ad esempio, rendere pubblica o privata) le funzioni e le variabili contenute nello script. Il salvataggio dello script come file con estensione psm1 consente inoltre di controllare l'ambito di determinate variabili. Infine, è anche possibile usare cmdlet come [install-module](/powershell/module/PowershellGet/Install-Module) per organizzare, installare e usare lo script come blocchi predefiniti per soluzioni di dimensioni maggiori.

## <a name="module-components-and-types"></a>Componenti e tipi del modulo

Un modulo è costituito da quattro componenti di base:

1. Un tipo di file di codice, in genere uno script di PowerShell o un assembly di cmdlet gestito.

2. Qualsiasi altra operazione che potrebbe essere necessaria per il file di codice precedente, ad esempio assembly aggiuntivi, file della guida o script.

3. Un file manifesto che descrive i file precedenti, oltre a archiviare i metadati, ad esempio informazioni sull'autore e sul controllo delle versioni.

4. Una directory che contiene tutto il contenuto precedente e che si trova nella posizione in cui PowerShell può ragionevolmente trovarlo.

   Si noti che nessuno di questi componenti è effettivamente necessario. Un modulo, ad esempio, può essere tecnicamente solo uno script archiviato in un file con estensione psm1. È anche possibile avere un modulo che non è altro che un file manifesto, usato principalmente per scopi organizzativi. È anche possibile scrivere uno script che crea dinamicamente un modulo e, di conseguenza, non necessita effettivamente di una directory in cui archiviare i dati. Le sezioni seguenti descrivono i tipi di moduli che è possibile ottenere combinando e associando le diverse parti possibili di un modulo insieme.

### <a name="script-modules"></a>Moduli di script

Come suggerisce il nome, un *modulo di script* è un file (con estensione psm1) che contiene qualsiasi codice di Windows PowerShell valido. Gli sviluppatori e gli amministratori di script possono utilizzare questo tipo di modulo per creare moduli i cui membri includono funzioni, variabili e altro ancora. A cuore, un modulo di script è semplicemente uno script di Windows PowerShell con un'estensione diversa, che consente agli amministratori di usare le funzioni di importazione, esportazione e gestione su di essa.

Inoltre, è possibile usare un file manifesto per includere altre risorse nel modulo, ad esempio file di dati, altri moduli dipendenti o script di Runtime. I file manifesto sono utili anche per tenere traccia dei metadati, ad esempio informazioni sulla creazione e sul controllo delle versioni.

Infine, un modulo di script, come qualsiasi altro modulo che non viene creato dinamicamente, deve essere salvato in una cartella che può essere ragionevolmente individuata da PowerShell. In genere, si tratta del percorso del modulo di PowerShell. Tuttavia, se necessario, è possibile descrivere in modo esplicito la posizione in cui è installato il modulo. Per altre informazioni, vedere [come scrivere un modulo di script di PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Moduli binari

Un *modulo binario* è un assembly .NET Framework (. dll) che contiene il codice compilato, ad C#esempio. Gli sviluppatori di cmdlet possono utilizzare questo tipo di modulo per condividere i cmdlet, i provider e altro ancora. Gli snap-in esistenti possono anche essere usati come moduli binari. Rispetto a un modulo di script, un modulo binario consente di creare cmdlet più veloci o di usare funzionalità, ad esempio il multithreading, che non sono semplici da codificare negli script di Windows PowerShell.

Come per i moduli di script, è possibile includere un file manifesto per descrivere le risorse aggiuntive utilizzate dal modulo e per tenere traccia dei metadati relativi al modulo. Analogamente, è probabile che si debba installare il modulo binario in una cartella in un punto qualsiasi del percorso del modulo PowerShell. Per altre informazioni, vedere How to [Write a PowerShell Binary Module](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Moduli manifesto

Un *modulo manifesto* è un modulo che usa un file manifesto per descrivere tutti i relativi componenti, ma non ha alcun tipo di assembly o script di base. (Formalmente, un modulo manifesto lascia vuoto `ModuleToProcess` l' `RootModule` elemento o del manifesto). Tuttavia, è comunque possibile usare le altre funzionalità di un modulo, ad esempio la possibilità di caricare gli assembly dipendenti o eseguire automaticamente determinati script di pre-elaborazione. È anche possibile usare un modulo manifesto come modo pratico per creare un pacchetto di risorse che altri moduli utilizzeranno, ad esempio moduli, assembly, tipi o formati annidati. Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Moduli dinamici

Un *modulo dinamico* è un modulo che non viene caricato o salvato in un file. Vengono invece creati in modo dinamico da uno script, usando il cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Questo tipo di modulo consente a uno script di creare un modulo su richiesta che non deve essere caricato o salvato nell'archivio permanente. Per sua natura, un modulo dinamico deve essere di breve durata e pertanto non è accessibile dal `Get-Module` cmdlet. Analogamente, non necessitano in genere di manifesti dei moduli, né probabilmente necessitano di cartelle permanenti per archiviare gli assembly correlati.

## <a name="module-manifests"></a>Manifesti dei moduli

Un *manifesto del modulo* è un file con estensione psd1 che contiene una tabella hash. Le chiavi e i valori nella tabella hash eseguono le operazioni seguenti:

- Descrivere il contenuto e gli attributi del modulo.

- Definire i prerequisiti.

- Determinare il modo in cui vengono elaborati i componenti.

  I manifesti non sono indispensabili per un modulo. I moduli possono fare riferimento ai file di script (con estensione ps1), ai file del modulo di script (con estensione psm1), ai file manifesto (con estensione psd1), alla formattazione e ai file di tipo (con estensione ps1xml), agli assembly di cmdlet e provider (con estensione dll), file di risorse, file della guida, file di localizzazione o qualsiasi altro tipo di file viene fornito come parte del modulo. Per uno script internazionalizzato, la cartella del modulo contiene anche un set di file di catalogo dei messaggi. Se si aggiunge un file manifesto alla cartella del modulo, è possibile fare riferimento a più file come singola unità facendo riferimento al manifesto.

  Il manifesto stesso descrive le seguenti categorie di informazioni:

- Metadati sul modulo, ad esempio il numero di versione del modulo, l'autore e la descrizione.

- Prerequisiti necessari per importare il modulo, ad esempio la versione di Windows PowerShell, la versione Common Language Runtime (CLR) e i moduli richiesti.

- Direttive di elaborazione, ad esempio gli script, i formati e i tipi da elaborare.

- Restrizioni sui membri del modulo da esportare, ad esempio gli alias, le funzioni, le variabili e i cmdlet da esportare.

  Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Archiviazione e installazione di un modulo

Dopo aver creato un modulo script, binario o manifesto, è possibile salvare il lavoro in un percorso accessibile ad altri utenti. Ad esempio, il modulo può essere archiviato nella cartella di sistema in cui è installato Windows PowerShell oppure può essere archiviato in una cartella utente.

In generale, è possibile determinare dove installare il modulo usando uno dei percorsi archiviati nella `$ENV:PSModulePath` variabile. L'uso di uno di questi percorsi indica che PowerShell può trovare e caricare automaticamente il modulo quando un utente effettua una chiamata al codice. Se si archivia il modulo in un altro punto, è possibile indicare in modo esplicito a PowerShell di passare il percorso del modulo come parametro quando si `Install-Module`chiama.

Indipendentemente dal fatto che il percorso della cartella venga definito *base* del modulo (ModuleBase) e il nome del file di modulo script, binario o manifesto deve essere uguale al nome della cartella del modulo, con le eccezioni seguenti:

- I moduli dinamici creati dal `New-Module` cmdlet possono essere denominati usando il `Name` parametro del cmdlet.

- I moduli importati dagli oggetti assembly tramite il `"dynamic_code_module_" + assembly.GetName()`  **`Import-Module` comando-assembly** vengono denominati in base alla sintassi seguente:.

  Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica del percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Cmdlet e variabili del modulo

I cmdlet e le variabili seguenti vengono forniti da Windows PowerShell per la creazione e la gestione dei moduli.

Cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) questo cmdlet crea un nuovo modulo dinamico che esiste solo in memoria. Il modulo viene creato da un blocco di script e i membri esportati, ad esempio le relative funzioni e variabili, sono immediatamente disponibili nella sessione e rimangono disponibili fino alla chiusura della sessione.

Cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) questo cmdlet crea un nuovo file manifesto del modulo (con estensione psd1), ne popola i valori e salva il file manifesto nel percorso specificato. Questo cmdlet può essere usato anche per creare un modello di manifesto del modulo che può essere compilato manualmente.

Cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) questo cmdlet aggiunge uno o più moduli alla sessione corrente.

Cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) questo cmdlet recupera le informazioni sui moduli che sono stati o che possono essere importati nella sessione corrente.

Cmdlet [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) questo cmdlet specifica i membri del modulo, ad esempio cmdlet, funzioni, variabili e alias, che vengono esportati da un file di modulo di script (con estensione psm1) o da un modulo dinamico creato `New-Module` con il cmdlet.

Cmdlet [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) questo cmdlet rimuove i moduli dalla sessione corrente.

Cmdlet [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) questo cmdlet verifica che un manifesto del modulo descriva accuratamente i componenti di un modulo verificando che i file elencati nel file manifesto del modulo (con estensione psd1) esistano effettivamente nei percorsi specificati.

$PSScriptRoot questa variabile contiene la directory da cui viene eseguito il modulo di script. Consente agli script di usare il percorso del modulo per accedere ad altre risorse.

$env:P SModulePath questa variabile di ambiente contiene un elenco delle directory in cui sono archiviati i moduli di Windows PowerShell. Windows PowerShell usa il valore di questa variabile quando si importano i moduli automaticamente e aggiorna gli argomenti della Guida per i moduli.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
