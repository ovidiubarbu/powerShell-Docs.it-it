---
title: Understanding a PowerShell Module di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862737"
---
# <a name="understanding-a-windows-powershell-module"></a>Informazioni su un modulo di Windows PowerShell

Oggetto *modulo* è un set di funzionalità di Windows PowerShell correlate, raggruppati in un'unità pratica (in genere salvata in una singola directory). Definendo un set di file di script correlati, assembly e le risorse correlate come modulo, è possibile fare riferimento a, caricare, salvare in modo permanente e condividere il codice molto più semplice di quanto accadrebbe in caso contrario.

Lo scopo principale di un modulo è consentire la modularità di codice di Windows PowerShell (ad esempio, il riutilizzo e astrazione). Il modo più semplice della creazione di un modulo, ad esempio, è sufficiente salvare uno script di Windows PowerShell come file con estensione psm1. Consente di controllo (ad esempio, Rendi pubblica o privata) le funzioni e variabili contenute nello script. Salvataggio dello script come file con estensione psm1 consente anche di controllare l'ambito di determinate variabili. Infine, è possibile anche usare i cmdlet, ad esempio [Install-Module](/powershell/module/PowershellGet/Install-Module) per organizzare, installare e usare uno script come blocchi predefiniti per le soluzioni più grandi.

## <a name="module-components-and-types"></a>Tipi e i componenti di modulo

Un modulo è costituito da quattro componenti di base:

1. Alcuni l'ordinamento dei file di codice, in genere uno script di PowerShell o un assembly di cmdlet gestite.

2. Qualsiasi altro file di codice sopra riportato potrebbe necessario, ad esempio assembly aggiuntivi, file della Guida, o gli script.

3. Un file manifesto che descrive i file indicati sopra, come pure archivia i metadati, ad esempio author e controllo delle versioni delle informazioni...

4. Una directory che contiene tutto il contenuto precedente e si trova dove PowerShell ragionevolmente trovarlo.

   Si noti che nessuno di questi componenti, da soli, sono effettivamente necessari. Ad esempio, un modulo può essere tecnicamente solo uno script archiviato in un file con estensione psm1. È anche possibile avere un modulo che non è altro che un file manifesto, che viene usato principalmente per scopi organizzativi. È anche possibile scrivere uno script che crea dinamicamente un modulo e di conseguenza non deve effettivamente una directory per archiviare qualsiasi elemento. Le sezioni seguenti descrivono i tipi di moduli che è possibile ottenere dalla combinazione di entrambe le parti diverse possibili di un modulo tra loro.

### <a name="script-modules"></a>Moduli di script

Come suggerisce il nome, una *modulo di script* è un file (. psm1) che contiene qualsiasi codice di PowerShell di Windows valido. Gli amministratori e sviluppatori di script possono usare questo tipo di modulo per creare moduli i cui membri includono funzioni, variabili e altro ancora. In questo caso un modulo di script è semplicemente uno script di Windows PowerShell con un'estensione diversa, che consente agli amministratori di utilizzare le funzioni di importazione, esportazione e la gestione su di esso.

Inoltre, è possibile utilizzare un file manifesto da includere altre risorse del modulo, ad esempio i file di dati, gli altri moduli dipendenti o script di runtime. I file manifesto sono utili anche per i metadati, ad esempio informazioni sulla creazione e controllo delle versioni di rilevamento.

Infine, un modulo di script, come qualsiasi altro modulo che non viene creato dinamicamente, deve essere salvata in una cartella che PowerShell ragionevolmente possibile individuare. Si tratta in genere nel percorso di modulo di PowerShell. Tuttavia, se necessario è possibile descrivere in modo esplicito in cui è installato il modulo. Per altre informazioni, vedere [come scrivere un modulo di Script di PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Moduli binari

Oggetto *modulo binario* è un assembly di .NET Framework (con estensione dll) che contiene codice compilato, ad esempio C#. Gli sviluppatori di cmdlet è possono usare questo tipo di modulo per condividere i cmdlet, provider e altro ancora. (Gli snap-in esistente può essere utilizzato anche come moduli binari.) Rispetto a un modulo di script, un modulo binario consente di creare i cmdlet che sono più veloci o usano le funzionalità (ad esempio il multithreading) che non sono invece altrettanto facili da codice negli script di Windows PowerShell.

Come con i moduli di script, è possibile includere un file manifesto per descrivere le risorse aggiuntive che usa un modulo e per rilevare i metadati relativi a un modulo. Analogamente, è probabilmente necessario installare il modulo binario in una cartella in un punto lungo il percorso del modulo PowerShell. Per altre informazioni, vedere come [come scrivere un modulo binario PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Moduli del manifesto

Oggetto *modulo del manifesto* è un modulo che usa un file manifesto per descrivere tutti i suoi componenti, ma non ha alcun tipo di assembly principale o lo script. (Formalmente, un modulo del manifesto lascia il `ModuleToProcess` o `RootModule` elemento del manifesto vuoto.) Tuttavia, è possibile usare comunque le altre funzionalità di un modulo, ad esempio la possibilità di caricare gli assembly dipendenti o eseguono automaticamente alcuni script di pre-elaborazione. È anche possibile usare un modulo manifesto come un modo pratico per creare un pacchetto di risorse che utilizzano altri moduli, ad esempio i moduli annidati, gli assembly, tipi o formati. Per altre informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Moduli dinamici

Oggetto *modulo dinamico* è un modulo non è stato caricato da o salvato in un file. Al contrario, vengono creati in modo dinamico da uno script, usando il [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Questo tipo di modulo consente uno script creare un modulo su richiesta che non devono essere caricati o salvati in un archivio permanente. Per sua natura, un modulo dinamico deve essere di breve durata e pertanto non è possibile accedervi tramite il `Get-Module` cmdlet. Analogamente, in genere non richiedono manifesti dei moduli, né si è probabilmente necessario permanente cartelle per archiviare i relativi assembly correlato.

## <a name="module-manifests"></a>Manifesti dei moduli

Oggetto *manifesto del modulo* è un file con estensione psd1 che contiene una tabella hash. Le chiavi e valori nella tabella hash per le operazioni seguenti:

- Viene descritto il contenuto e gli attributi del modulo.

- Definiscono i prerequisiti.

- Determinare come vengono elaborati i componenti.

  I manifesti non sono indispensabili per un modulo. I moduli possono fare riferimento ai file di script (con estensione ps1), i file di modulo (con estensione psm1), i file manifesto (psd1), la formattazione di script e digitare i file (con estensione PS1XML), cmdlet e provider di assembly (DLL), i file di risorse, i file della Guida, i file di localizzazione o qualsiasi altro tipo di file o una risorsa che viene incluso come parte del modulo. Per uno script mercati internazionale, la cartella del modulo contiene anche un set di file di catalogo di messaggi. Se si aggiunge un file manifesto per la cartella del modulo, è possibile fare riferimento più file come singola unità facendo riferimento il manifesto.

  Il manifesto di se stesso descrive le categorie di informazioni seguenti:

- Metadati sul modulo, ad esempio il numero di versione del modulo, l'autore e la descrizione.

- Prerequisiti necessari per importare il modulo, ad esempio la versione di Windows PowerShell, la versione di common language runtime (CLR) e i moduli necessari.

- L'elaborazione istruzioni, ad esempio di script, i formati e tipi per l'elaborazione.

- Restrizioni su membri di modulo di esportare, ad esempio l'alias, funzioni, variabili e i cmdlet da esportare.

  Per altre informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>L'archiviazione e installare un modulo

Dopo aver creato un script, un modulo binario o manifesto, è possibile salvare il lavoro in una posizione che altri utenti possano accedervi. Ad esempio, un modulo può essere archiviato nella cartella di sistema in cui è installato Windows PowerShell, o possono essere archiviato in una cartella utente.

In generale, è possibile determinare dove è necessario installare un modulo tramite uno dei percorsi archiviati nel `$ENV:PSModulePath` variabile. Usando uno di questi percorsi significa che PowerShell può automaticamente individuare e caricare il modulo quando un utente effettua una chiamata a esso nel proprio codice. Se si archivia un modulo in un'altra posizione, è possibile in modo esplicito informare PowerShell passando il percorso del modulo come parametro quando si chiama `Install-Module`.

Indipendentemente da ciò, il percorso della cartella è detto il *base* del modulo (ModuleBase) e il nome dello script, file di modulo binario o manifesto deve essere lo stesso come il nome di cartella del modulo, con le eccezioni seguenti:

- I moduli dinamici creati dal `New-Module` cmdlet possono essere denominate usando il `Name` parametro del cmdlet.

- I moduli importati da oggetti assembly per il  **`Import-Module` -Assembly** comando sono denominate secondo la sintassi seguente: `"dynamic_code_module_" + assembly.GetName()`.

  Per altre informazioni, vedere [installazione di un modulo di PowerShell](./installing-a-powershell-module.md) e [modifica il percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Le variabili e i cmdlet del modulo

I cmdlet e le variabili seguenti vengono fornite da Windows PowerShell per la creazione e gestione dei moduli.

[Nuovo modulo](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet questo cmdlet crea un nuovo modulo dinamico che esiste solo in memoria. Il modulo viene creato da un blocco di script e i relativi membri esportati, ad esempio le relative funzioni e variabili, sono immediatamente disponibili nella sessione e rimangono disponibili finché non viene chiusa la sessione.

[Nuovo-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet questo cmdlet crea un nuovo file manifesto (psd1) del modulo, consente di popolare i relativi valori e Salva il file manifesto nel percorso specificato. Questo cmdlet è anche utilizzabile per creare un modello di manifesto di modulo che è possibile compilare manualmente.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet questo cmdlet aggiunge uno o più moduli alla sessione corrente.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet questo cmdlet recupera le informazioni sui moduli che sono già stati o che possono essere importati nella sessione corrente.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet questo cmdlet consente di specificare i membri del modulo (ad esempio cmdlet, funzioni, variabili e alias) che vengono esportati da un file di modulo (. psm1) di script o da un modulo dinamico creato con il `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet questo cmdlet rimuove i moduli dalla sessione corrente.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet questo cmdlet verifica che un manifesto del modulo descriva accuratamente i componenti di un modulo verificando che i file elencati nel file manifesto del modulo (con estensione psd1) esistano effettivamente nei percorsi specificati.

$PSScriptRoot questa variabile contiene la directory da cui è in esecuzione il modulo di script. In questo modo gli script possono usare il percorso del modulo per accedere ad altre risorse.

$env: PSModulePath questa variabile di ambiente contiene un elenco delle directory in cui PowerShell di Windows vengono archiviati i moduli. Windows PowerShell Usa il valore di questa variabile durante l'importazione di moduli automaticamente e l'aggiornamento di argomenti della Guida per i moduli.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
