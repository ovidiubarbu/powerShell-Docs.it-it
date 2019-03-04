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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860507"
---
# <a name="cmdlet-aliases"></a>Alias dei cmdlet

È possibile usare gli alias di cmdlet per migliorare l'esperienza utente di cmdlet. È possibile aggiungere alias al cmdlet usati di frequente per ridurre la digitazione e consentono di semplificare per completare le attività rapidamente. È possibile includere gli alias incorporati in dei cmdlet o gli utenti possono definire i propri alias personalizzati.

Ad esempio, il [Get-Command](/powershell/module/microsoft.powershell.core/get-command) include un cmdlet `gcm` alias. È anche possibile usare gli alias per aggiungere i nomi dei comandi da altri linguaggi, in modo che gli utenti non sono necessario apprendere nuovi comandi.

## <a name="alias-guidelines"></a>Linee guida di alias

Seguire queste linee guida quando si crea l'alias predefiniti per i cmdlet:

- Prima di assegnare alias, avviare Windows PowerShell e quindi eseguire la [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet per visualizzare gli alias che sono già in uso.

- Includere un prefisso di alias che fa riferimento il verbo del nome del cmdlet e un suffisso di alias che fa riferimento il sostantivo del nome del cmdlet. Ad esempio, l'alias per il `Import-Module` cmdlet è "ipmo". Per un elenco di tutti i verbi e i relativi alias, vedere [verbi dei Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Per i cmdlet che contengono il verbo stesso, includere lo stesso prefisso di alias. Gli alias per tutti i cmdlet di Windows PowerShell che contengono il verbo "Get" nel loro nome, ad esempio, usano il prefisso "g".

- Per i cmdlet che contengono il sostantivo stesso, includere lo stesso suffisso di alias. Gli alias per tutti i cmdlet di Windows PowerShell che contengono il sostantivo "Sessione" nel nome, ad esempio, usano il suffisso "NS".

- Per i cmdlet che sono equivalenti ai comandi in altre lingue, usare il nome del comando.

- In generale, verificare gli alias più brevi possibile. Assicurarsi che l'alias di dispone di almeno un carattere distinto del verbo e un carattere distinto per il sostantivo. Aggiungere più caratteri in base alle esigenze per rendere l'alias univoco.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
