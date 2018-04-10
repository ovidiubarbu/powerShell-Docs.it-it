---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Miglioramenti per la creazione di configurazioni con PowerShell ISE

La creazione di configurazioni DSC in Windows PowerShell ISE è molto più semplice, grazie ai miglioramenti seguenti:

- È possibile elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.
- Completamento automatico per le proprietà della risorsa di tipo **enumeration**.
- Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.
- Completamento tramite TAB migliorato per i valori delle proprietà della risorsa.

**Nota:** è necessario disporre di una stringa vuota per i valori della proprietà della risorsa prima di poter usare CTRL+BARRA SPAZIATRICE per visualizzare l'elenco di opzioni. Premendo **TAB** è possibile scorrere le opzioni.