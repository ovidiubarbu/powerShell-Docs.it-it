---
title: Tipi di file consentiti in un file CAB della Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367260"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Tipi di file consentiti in un file CAB della Guida aggiornabile

In questo argomento vengono elencati e descritti i requisiti di contenuto per i file CAB della Guida aggiornabile.

## <a name="updatable-help-cab-file-requirements"></a>Requisiti dei file CAB della Guida aggiornabile

Per impostazione predefinita, il contenuto del file CAB non compresso è limitato a 1 GB. Per aggirare questo limite, gli utenti devono usare il parametro **Force** dei cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Per garantire la sicurezza dei file della Guida scaricati da Internet, un file CAB della Guida aggiornabile può includere solo i tipi di file elencati di seguito. Il cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) convalida tutti i file rispetto agli schemi degli argomenti della guida. Se il cmdlet `Update-Help` rileva un file che non è valido o non è un tipo consentito, non installa il file non valido e interrompe l'installazione dei file dal file CAB nel computer dell'utente.

- Argomenti della Guida basati su XML per i cmdlet di.

- Argomenti della Guida basati su XML per gli script e le funzioni.

- Argomenti della Guida basati su XML per i provider di Windows PowerShell.

- Argomenti della Guida basati su testo, ad esempio informazioni sugli argomenti.

[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica il contenuto dei CAB quando DECOMPRIME il CAB. Se `Update-Help` trova tipi di file non conformi in un file CAB della Guida aggiornabile, viene generato un errore di terminazione e l'operazione viene arrestata. Non installa i file della guida dal file CAB, neanche quelli dei tipi di file conformi.