---
title: Come aggiungere il nome di Cmdlet e il riepilogo per un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083338"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Come aggiungere il nome dei cmdlet e il riepilogo a un argomento della Guida sui cmdlet

Questa sezione descrive come aggiungere contenuto che viene visualizzato nelle sezioni nome e il riepilogo della Guida del cmdlet. Nel file della Guida, questo contenuto viene aggiunto al nodo del comando per ciascun cmdlet.

> [!NOTE]
> Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell. Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Per aggiungere il nome del Cmdlet e un riepilogo

- La Guida dei cmdlet è possibile visualizzare due descrizioni del cmdlet. La descrizione prima è una breve descrizione che viene definita il riepilogo. La seconda descrizione è una descrizione più dettagliata che verrà discusso [aggiunta la descrizione dettagliata per un argomento della Guida Cmdlet](./how-to-add-a-cmdlet-description.md). Entrambe queste descrizioni devono essere scritti come un paragrafo unico.

- Il riepilogo non si ripetono il nome del cmdlet. Per informare l'utente che il cmdlet Get-Server Ottiene un server è breve, ma non informativi. Al contrario, uso dei sinonimi e aggiungere i dettagli per la descrizione.

  Esempio: "Ottiene un oggetto che rappresenta un computer locale o remoto."

- Usare verbi semplici, ad esempio "get", "Crea" e "Modifica" il riepilogo. Evitare di usare "set" perché è vaga e fantasiosi parole come "la modifica."

  Esempio: "Ottiene informazioni sulla firma Authenticode in un file".

- Scrivere in forma attiva. Ad esempio, "Usa l'oggetto TimeSpan..." è molto più chiaro rispetto a "l'oggetto TimeSpan utilizzabile per..."

- Evitare il verbo "display" quando si descrivono i cmdlet che ottiene gli oggetti. Anche se Windows PowerShell consente di visualizzare i dati di cmdlet, è importante per introdurre gli utenti per il concetto che il cmdlet restituisce gli oggetti di .NET Framework i cui dati potrebbero non essere visualizzati. Se si evidenziazione la visualizzazione, l'utente potrebbe non essere consapevoli che il cmdlet potrebbe avere restituito molte altre proprietà e metodi utili che non vengono visualizzati.

## <a name="see-also"></a>Vedere anche

 [Windows PowerShell SDK](../windows-powershell-reference.md)