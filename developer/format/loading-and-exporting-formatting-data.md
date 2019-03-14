---
title: Il caricamento e l'esportazione di dati di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 86a0e8b7e8967280daa57faf5c323efcd3b1368b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794196"
---
# <a name="loading-and-exporting-formatting-data"></a>Caricamento ed esportazione di dati di formattazione

Dopo aver creato il file di formattazione, è necessario aggiornare i dati di formato della sessione mediante il caricamento dei file nella sessione corrente. (I file di formattazione forniti da Windows PowerShell vengono caricati dagli snap-in registrati quando viene aperta la sessione corrente). Dopo aver aggiornati i dati in formato della sessione corrente, Windows PowerShell Usa tali dati per visualizzare gli oggetti .NET associati con le visualizzazioni definite nei file di formattazione caricati. Non sono previsti limiti al numero di file di formattazione che è possibile caricare nella sessione corrente. Oltre ad aggiornare i dati di formattazione, è possibile esportare i dati di formattazione nella sessione corrente in un file di formattazione.

## <a name="loading-format-data"></a>Il caricamento dei dati di formato

È possibile caricare i file di formattazione nella sessione corrente usando i metodi seguenti:

- È possibile importare il file di formattazione nella sessione corrente dalla riga di comando. Usare la [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, come descritto nella procedura seguente.

- È possibile creare un manifesto del modulo che fa riferimento a file di formattazione. I moduli consentono di formattare i file per la distribuzione del pacchetto. Usare la [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) per creare il manifesto e il [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet per caricare il modulo nella sessione corrente. Per altre informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- È possibile creare uno snap-in che fa riferimento a file di formattazione. Usare la [System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) fare riferimento ai file di formattazione. È consigliabile utilizzare i moduli per i cmdlet di pacchetto e qualsiasi formattazione associati e file di tipi per la distribuzione. Per altre informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Se si richiamano comandi a livello di codice, è possibile aggiungere una voce del file di formattazione per lo stato sessione iniziale di spazio di esecuzione in cui vengono eseguiti i comandi. Per altre informazioni sul tipo di .NET usata per aggiungere il file di formattazione, vedere il [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) classe.

Quando viene caricato un file di formattazione, viene aggiunto a un elenco interno che Windows PowerShell utilizza per determinare quale visualizzazione da utilizzare per la visualizzazione di oggetti dalla riga di comando. È possibile anteporre il file di formattazione all'inizio dell'elenco, oppure è possibile aggiungerlo alla fine dell'elenco. Conoscendo in cui i file di formattazione viene aggiunto a questo elenco è importante se si sta caricando file di formattazione che definisce una visualizzazione per un oggetto che dispone di una vista esistente definita, ad esempio quando si desidera modificare la modalità è un oggetto restituito da un cmdlet di Windows PowerShell core  visualizzato. Se si sta caricando un file di formattazione che definisce la vista sola per un oggetto, è possibile usare uno qualsiasi dei metodi descritti in precedenza.  Se si sta caricando un file di formattazione che definisce un'altra visualizzazione per un oggetto, è necessario usare il [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet e anteporre il file all'inizio dell'elenco.

## <a name="storing-your-formatting-file"></a>L'archiviazione File di formattazione

Non vi è alcun requisito per cui sono archiviati i file di formattazione su disco. Tuttavia, è consigliabile archiviarle nella cartella seguente: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Il caricamento di un file di formato tramite importazione-FormatData

1. Store il file di formattazione su disco.

2. Eseguire la [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet usando uno dei comandi seguenti.

   Per aggiungere la formattazione file all'inizio dell'elenco di utilizzare questo comando. Usare questo comando se si modifica la modalità di visualizzazione di un oggetto.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Per aggiungere la formattazione file alla fine dell'elenco di utilizzare questo comando.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Dopo aver aggiunto un file usando il [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, è possibile rimuovere il file dall'elenco mentre è aperta la sessione. È necessario chiudere la sessione per rimuovere il file di formattazione dall'elenco.

## <a name="exporting-format-data"></a>Esportazione dei dati di formato

Inserire il corpo della sezione qui.
