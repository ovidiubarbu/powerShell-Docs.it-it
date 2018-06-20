---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Scopo del modello a oggetti di scripting di Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951325"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Scopo del modello a oggetti di scripting di Windows PowerShell ISE

Gli oggetti sono associati al formato e alla funzione di Windows PowerShell Integrated Scripting Environment (ISE). Il riferimento del modello a oggetti fornisce dettagli sulle proprietà dei membri e sui metodi esposti da tali oggetti. Vengono forniti esempi per mostrare come usare gli script per accedere direttamente a tali metodi e proprietà. Il modello a oggetti di scripting semplifica la gamma di attività seguenti.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Personalizzazione dell'aspetto di Windows PowerShell ISE

È possibile usare il modello a oggetti per modificare le impostazioni e le opzioni dell'applicazione. Ad esempio, è possibile modificarle come segue:

- È possibile modificare il colore di errori, avvisi, output dettagliati e output di debug.
- È possibile ottenere o impostare i colori di sfondo per il riquadro dei comandi, il riquadro di output e il riquadro di script.
- È possibile impostare il colore di primo piano per il riquadro di output.
- È possibile impostare il nome del tipo di carattere e la dimensione del carattere per Windows PowerShell ISE.
- È possibile configurare gli avvisi. Questa impostazione include gli avvisi che vengono generati quando viene aperto un file in più schede di PowerShell o quando uno script nel file viene eseguito prima del salvataggio del file.
- È possibile passare da una vista in cui il riquadro di script e il riquadro di output sono affiancati a una vista in cui il riquadro di script si trova sopra il riquadro di output. È possibile ancorare il riquadro dei comandi nella parte inferiore o superiore del riquadro di output.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Miglioramento della funzionalità di Windows PowerShell ISE

È possibile usare il modello a oggetti per migliorare le funzionalità di Windows PowerShell ISE. Ad esempio, è possibile:

- Aggiungere e modificare l'istanza di Windows PowerShell ISE. Ad esempio, per modificare i menu è possibile aggiungere nuove voci di menu e associare nuove voci di menu agli script.
- Creare script che eseguono alcune operazioni che si possono eseguire con i comandi di menu e i pulsanti in Windows PowerShell ISE, ad esempio aggiungere, rimuovere o selezionare una scheda di PowerShell.
- Attività di complemento che possono essere eseguite con i comandi di menu e i pulsanti, ad esempio rinominare una scheda di PowerShell.
- Modificare i buffer di testo per il riquadro dei comandi, il riquadro di output e il riquadro di script associati a un file. Ad esempio, è possibile:
  - Ottenere o impostare tutto il testo.
  - Ottenere o impostare una selezione di testo.
  - Eseguire uno script o una parte specifica di uno script.
  - Scorrere di una riga nella visualizzazione.
  - Inserire il testo in una posizione di inserimento.
  - Selezionare un blocco di testo.
  - Ottenere l'ultimo numero di riga.
- Eseguire operazioni sui file. Ad esempio, è possibile:
  - Aprire un file, salvarlo o salvarlo con un altro nome.
  - Determinare se un file è stato modificato dopo l'ultimo salvataggio.
  - Ottenere il nome del file.
  - Selezionare un file.

## <a name="automating-tasks"></a>Automazione di attività

È possibile usare il modello a oggetti di scripting per creare scelte rapide da tastiera per le operazioni frequenti.

## <a name="see-also"></a>Vedere anche

- [Gerarchia del modello a oggetti ISE](The-ISE-Object-Model-Hierarchy.md)