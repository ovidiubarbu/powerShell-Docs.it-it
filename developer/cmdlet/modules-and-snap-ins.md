---
title: I moduli e Snap-in | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067621"
---
# <a name="modules-and-snap-ins"></a>Moduli e snap-in

I cmdlet possono essere aggiunti tramite moduli (introdotti da Windows PowerShell 2.0) o gli snap-in a una sessione. Dopo aver aggiunto il cmdlet alla sessione che può essere eseguita a livello di codice da un'applicazione host o in modo interattivo dalla riga di comando.

È consigliabile usare i moduli come il metodo di recapito per l'aggiunta di cmdlet per una sessione per i motivi seguenti:

- I moduli consentono di aggiungere i cmdlet per il caricamento dell'assembly in cui è definito il cmdlet. Non è necessario implementare una classe di snap-in.

- I moduli consentono di aggiungere altre risorse, ad esempio variabili, funzioni, script, i tipi e formattazione file e altro ancora.

- Gli snap-in è utilizzabile solo per aggiungere i cmdlet e provider alla sessione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
