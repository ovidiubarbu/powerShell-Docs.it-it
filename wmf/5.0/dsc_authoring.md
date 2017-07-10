---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="authoring-improvements-using-powershell-ise" class="xliff"></a>
# Miglioramenti per la creazione di configurazioni con PowerShell ISE

La creazione di configurazioni DSC in Windows PowerShell ISE è molto più semplice, grazie ai miglioramenti seguenti:

- È possibile elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.
- Completamento automatico per le proprietà della risorsa di tipo **enumeration**.
- Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.
- Completamento tramite TAB migliorato per i valori delle proprietà della risorsa.

**Nota:** è necessario disporre di una stringa vuota per i valori della proprietà della risorsa prima di poter usare CTRL+BARRA SPAZIATRICE per visualizzare l'elenco di opzioni. Premendo **TAB** è possibile scorrere le opzioni.

