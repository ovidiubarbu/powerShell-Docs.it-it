---
title: Caricamento ed esportazione dei dati di formattazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365120"
---
# <a name="loading-and-exporting-formatting-data"></a>Caricamento ed esportazione di dati di formattazione

Dopo aver creato il file di formattazione, è necessario aggiornare i dati del formato della sessione caricando i file nella sessione corrente. I file di formattazione forniti da Windows PowerShell vengono caricati dagli snap-in che vengono registrati al momento dell'apertura della sessione corrente. Una volta aggiornati i dati del formato della sessione corrente, Windows PowerShell usa tali dati per visualizzare gli oggetti .NET associati alle visualizzazioni definite nei file di formattazione caricati. Non esiste alcun limite al numero di file di formattazione che è possibile caricare nella sessione corrente. Oltre ad aggiornare i dati di formattazione, è possibile esportare di nuovo i dati del formato nella sessione corrente in un file di formattazione.

## <a name="loading-format-data"></a>Caricamento dei dati del formato

I file di formattazione possono essere caricati nella sessione corrente usando i metodi seguenti:

- È possibile importare il file di formattazione nella sessione corrente dalla riga di comando. Usare il cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) come descritto nella procedura seguente.

- È possibile creare un manifesto del modulo che fa riferimento al file di formattazione. I moduli consentono di comprimere i file di formattazione per la distribuzione. Usare il cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) per creare il manifesto e il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) per caricare il modulo nella sessione corrente. Per ulteriori informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- È possibile creare uno snap-in che fa riferimento al file di formattazione. Usare [System. Management. Automation. PSSnapin. formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) per fare riferimento ai file di formattazione. Si consiglia vivamente di utilizzare i moduli per creare pacchetti per i cmdlet e i file di formattazione e di tipi associati per la distribuzione. Per ulteriori informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Se si richiamano i comandi a livello di codice, è possibile aggiungere una voce del file di formattazione allo stato della sessione iniziale del spazio in cui vengono eseguiti i comandi. Per altre informazioni sul tipo .NET usato per aggiungere il file di formattazione, vedere [System. Management. Automation. Runspaces. Sessionstateformatentry? DisplayProperty = classe FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) .

Quando viene caricato un file di formattazione, questo viene aggiunto a un elenco interno usato da Windows PowerShell per determinare la visualizzazione da usare per la visualizzazione degli oggetti dalla riga di comando. È possibile anteporre il file di formattazione all'inizio dell'elenco oppure è possibile aggiungerlo alla fine dell'elenco. Sapere dove è stato aggiunto il file di formattazione a questo elenco è importante se si sta caricando un file di formattazione che definisce una vista per un oggetto con una vista esistente definita, ad esempio quando si desidera modificare il modo in cui un oggetto restituito da un cmdlet di Windows PowerShell core è  visualizzato. Se si sta caricando un file di formattazione che definisce l'unica visualizzazione per un oggetto, è possibile usare uno dei metodi descritti in precedenza.  Se si sta caricando un file di formattazione che definisce un'altra visualizzazione per un oggetto, è necessario usare il cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) e anteporre il file all'inizio dell'elenco.

## <a name="storing-your-formatting-file"></a>Archiviazione del file di formattazione

Non è necessario che i file di formattazione siano archiviati su disco. Tuttavia, è consigliabile archiviarli nella cartella seguente: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Caricamento di un file di formato con Import-FormatData

1. Archiviare il file di formattazione su disco.

2. Eseguire il cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) usando uno dei comandi seguenti.

   Per aggiungere il file di formattazione all'inizio dell'elenco, usare questo comando. Utilizzare questo comando se si modifica la modalità di visualizzazione di un oggetto.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Per aggiungere il file di formattazione alla fine dell'elenco, usare questo comando.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Una volta aggiunto un file usando il cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) , non è possibile rimuovere il file dall'elenco mentre la sessione è aperta. Per rimuovere il file di formattazione dall'elenco, è necessario chiudere la sessione.

## <a name="exporting-format-data"></a>Esportazione dei dati del formato

Inserire il corpo della sezione qui.
