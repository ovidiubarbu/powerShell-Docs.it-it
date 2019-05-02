---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085644"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Miglioramenti per la creazione di configurazioni con PowerShell ISE

La creazione di configurazioni DSC in Windows PowerShell ISE è molto più semplice, grazie ai miglioramenti seguenti:

- È possibile elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.
- Completamento automatico per le proprietà della risorsa di tipo **enumeration**.
- Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.
- Completamento tramite TAB migliorato per i valori delle proprietà della risorsa.

**Nota:** è necessario disporre di una stringa vuota per i valori della proprietà della risorsa prima di poter usare CTRL+BARRA SPAZIATRICE per visualizzare l'elenco di opzioni. Premendo **TAB** è possibile scorrere le opzioni.
