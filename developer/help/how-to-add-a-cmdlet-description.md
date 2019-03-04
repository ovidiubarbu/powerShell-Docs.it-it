---
title: Come aggiungere una descrizione del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862597"
---
# <a name="how-to-add-a-cmdlet-description"></a>Come aggiungere una descrizione del cmdlet

Questa sezione descrive come aggiungere il contenuto visualizzato nella sezione Descrizione del cmdlet Help. Nel file della Guida, questo contenuto viene aggiunto al nodo del comando per ciascun cmdlet.

> [!NOTE]
> Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell. Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.

### <a name="to-add-a-description"></a>Per aggiungere una descrizione

- Inizia illustrando le funzionalità di base del cmdlet in modo più dettagliato. In molti casi, è possibile spiegare i termini utilizzati nel nome del cmdlet e illustrare i concetti di familiari con un esempio. Ad esempio, se il cmdlet aggiunge i dati in un file, illustrano che aggiunge i dati alla fine di un file esistente.

- Per trovare tutte le funzionalità del cmdlet, esaminare l'elenco di parametri. Descrivere la funzione principale del cmdlet e quindi includere altre funzioni e funzionalità. Ad esempio, se la funzione principale del cmdlet consiste nel modificare una proprietà, ma il cmdlet può modificare tutte le proprietà, ad esempio, nella descrizione dettagliata. Se i parametri del cmdlet consentono agli utenti di sollecitazione informazioni in modi diversi, trattazione.

- Includere informazioni sui metodi che gli utenti possono usare il cmdlet, oltre all'Usa ovvia. Ad esempio, è possibile usare l'oggetto che il `Get-Host` cmdlet recupera per modificare il colore del testo nella finestra di comando di Windows PowerShell.

  Esempio:  "Il `Get-Acl` cmdlet recupera gli oggetti che rappresentano il descrittore di sicurezza di un file o una risorsa. Il descrittore di sicurezza contiene gli elenchi di controllo di accesso della risorsa. L'elenco ACL consente di specificare le relative autorizzazioni utenti e gruppi di utenti per accedere alla risorsa."

- La descrizione dettagliata deve descrivere il cmdlet, ma non dovrebbe descrivere i concetti che usa il cmdlet. Posizionare le definizioni di concetto in note aggiuntive.

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
