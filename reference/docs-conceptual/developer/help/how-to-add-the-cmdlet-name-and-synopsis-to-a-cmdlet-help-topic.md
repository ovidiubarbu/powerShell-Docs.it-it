---
title: Come aggiungere il nome del cmdlet e la sinossia a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361190"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Come aggiungere il nome dei cmdlet e il riepilogo a un argomento della Guida sui cmdlet

In questa sezione viene descritto come aggiungere contenuti che vengono visualizzati nelle sezioni nome e riepilogo della guida del cmdlet. Nel file della guida, questo contenuto viene aggiunto al nodo del comando per ogni cmdlet.

> [!NOTE]
> Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell. Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Per aggiungere il nome del cmdlet e un riepilogo

- La guida del cmdlet può visualizzare due descrizioni per il cmdlet. La prima descrizione è una breve descrizione indicata come sinossia. La seconda descrizione è una descrizione più dettagliata descritta in [aggiunta della descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md). Entrambe queste descrizioni devono essere scritte come un solo paragrafo.

- In sinossia non ripetere il nome del cmdlet. Informare l'utente che il cmdlet Get-server ottiene un server è Brief, ma non informativo. Usare invece i sinonimi e aggiungere i dettagli alla descrizione.

  Esempio: "ottiene un oggetto che rappresenta un computer locale o remoto".

- Usare verbi semplici come "Get", "create" e "Change" nella sintassi. Evitare di usare "set" perché è vago e parole fantasiose come "modifica".

  Esempio: "ottiene informazioni sulla firma Authenticode in un file".

- Scrivi nella voce attiva. Ad esempio, "usare l'oggetto TimeSpan..." è molto più chiaro di "l'oggetto TimeSpan può essere usato per..."

- Evitare il verbo "display" quando si descrivono i cmdlet che ottengono oggetti. Anche se Windows PowerShell Visualizza i dati dei cmdlet, è importante introdurre gli utenti al concetto che il cmdlet restituisce .NET Framework oggetti i cui dati potrebbero non essere visualizzati. Se si enfatizza la visualizzazione, è possibile che l'utente non renda conto che il cmdlet potrebbe avere restituito molte altre proprietà e metodi utili che non vengono visualizzati.

## <a name="see-also"></a>Vedere anche

 [Windows PowerShell SDK](../windows-powershell-reference.md)