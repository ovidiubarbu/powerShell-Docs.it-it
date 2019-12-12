---
title: Moduli e snap-in | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365370"
---
# <a name="modules-and-snap-ins"></a>Moduli e snap-in

I cmdlet possono essere aggiunti a una sessione usando i moduli (introdotti da Windows PowerShell 2,0) o gli snap-in. Una volta aggiunto il cmdlet alla sessione, può essere eseguito a livello di codice da un'applicazione host o in modo interattivo dalla riga di comando.

È consigliabile usare i moduli come metodo di recapito per aggiungere cmdlet a una sessione per i motivi seguenti:

- I moduli consentono di aggiungere cmdlet caricando l'assembly in cui è definito il cmdlet. Non è necessario implementare una classe snap-in.

- I moduli consentono di aggiungere altre risorse, ad esempio variabili, funzioni, script, tipi e file di formattazione e altro ancora.

- Gli snap-in possono essere utilizzati solo per aggiungere cmdlet e provider alla sessione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
