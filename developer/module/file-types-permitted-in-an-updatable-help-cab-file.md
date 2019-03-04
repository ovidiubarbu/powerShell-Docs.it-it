---
title: Tipi di file consentiti in un aggiornabili consentono di File CAB | Microsoft Docs
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
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862837"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Tipi di file consentiti in un file CAB della Guida aggiornabile

Questo argomento elenca e descrive i requisiti di contenuto per i file CAB di Guida aggiornabile.

## <a name="updatable-help-cab-file-requirements"></a>Requisiti di File CAB di Guida aggiornabile

Contenuto del file CAB non compresso è limitato a 1 GB per impostazione predefinita. Per ignorare questo limite, gli utenti dovranno usare la **Force** parametro del [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.
Contenuto del file CAB non compresso è limitato a 1 GB per impostazione predefinita. Per ignorare questo limite, gli utenti dovranno usare la **Force** parametro del [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.

Per garantire la sicurezza dei file della Guida che vengono scaricati da Internet, un file CAB di Guida aggiornabile può includere solo i tipi di file elencati di seguito. Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet convalida tutti i file degli schemi argomento della Guida. Se il `Update-Help` cmdlet rileva un file che non è valido o non è un tipo consentito, ma non viene installato il file non valido e arresta l'installazione dei file dal CAB sul computer dell'utente.
Per garantire la sicurezza dei file della Guida che vengono scaricati da Internet, un file CAB di Guida aggiornabile può includere solo i tipi di file elencati di seguito. Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet convalida tutti i file degli schemi argomento della Guida. Se il `Update-Help` cmdlet rileva un file che non è valido o non è un tipo consentito, ma non viene installato il file non valido e arresta l'installazione dei file dal CAB sul computer dell'utente.

- Argomenti della Guida basati su XML per i cmdlet.

- Argomenti della Guida basati su XML per gli script e funzioni.

- Argomenti della Guida basati su XML per i provider di Windows PowerShell.

- Basata su testo argomenti della Guida, ad esempio sugli argomenti.

Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica il contenuto di file CAB quando si decompresso il file CAB. Se `Update-Help` individua i tipi di file non conformi in un file CAB di Guida aggiornabile, genera un errore irreversibile e arresta l'operazione. Non installa tutti i file della Guida dal CAB, anche quelli dei tipi di file conforme.
Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica il contenuto di file CAB quando si decompresso il file CAB. Se `Update-Help` individua i tipi di file non conformi in un file CAB di Guida aggiornabile, genera un errore irreversibile e arresta l'operazione. Non installa tutti i file della Guida dal CAB, anche quelli dei tipi di file conforme.