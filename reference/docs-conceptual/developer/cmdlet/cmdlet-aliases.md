---
title: Alias di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369980"
---
# <a name="cmdlet-aliases"></a>Alias dei cmdlet

È possibile utilizzare gli alias dei cmdlet per migliorare l'esperienza utente del cmdlet. È possibile aggiungere alias ai cmdlet usati di frequente per ridurre la digitazione e semplificare il completamento rapido delle attività. È possibile includere alias predefiniti nei cmdlet oppure gli utenti possono definire i propri alias personalizzati.

Il cmdlet [Get-Command](/powershell/module/microsoft.powershell.core/get-command) dispone ad esempio di un alias `gcm` incorporato. È anche possibile usare alias per aggiungere nomi di comando da altri linguaggi, in modo che gli utenti non debbano apprendere nuovi comandi.

## <a name="alias-guidelines"></a>Linee guida per gli alias

Quando si creano alias predefiniti per i cmdlet, seguire queste linee guida:

- Prima di assegnare gli alias, avviare Windows PowerShell, quindi eseguire il cmdlet [get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) per visualizzare gli alias già usati.

- Includere un prefisso alias che fa riferimento al verbo del nome del cmdlet e un suffisso alias che fa riferimento al sostantivo nome del cmdlet. Ad esempio, l'alias per il cmdlet `Import-Module` è "IPMO". Per un elenco di tutti i verbi e dei rispettivi alias, vedere [verbi dei cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Per i cmdlet che hanno lo stesso verbo, includere lo stesso prefisso di alias. Ad esempio, gli alias per tutti i cmdlet di Windows PowerShell con il verbo "Get" nel nome usano il prefisso "g".

- Per i cmdlet che hanno lo stesso nome, includere lo stesso suffisso alias. Ad esempio, gli alias per tutti i cmdlet di Windows PowerShell che hanno il sostantivo "Session" nel nome usano il suffisso "sn".

- Per i cmdlet equivalenti ai comandi di altri linguaggi, usare il nome del comando.

- In generale, creare gli alias il più breve possibile. Verificare che l'alias includa almeno un carattere distinto per il verbo e un carattere distinto per il sostantivo. Aggiungere altri caratteri necessari per rendere univoco l'alias.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
