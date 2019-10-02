---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Gestione delle chiavi API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328292"
---
# <a name="managing-api-keys"></a>Gestione delle chiavi API

PowerShell Gallery supporta la creazione di più chiavi API per supportare una gamma di requisiti per la pubblicazione. Una chiave API può essere valida per uno o più pacchetti, concede privilegi specifici e ha una data di scadenza.

> [!IMPORTANT]
> Gli utenti che hanno pubblicato in PowerShell Gallery prima dell'introduzione delle chiavi API con ambito avranno una "chiave API con accesso completo". Le chiavi con accesso completo non presentano i miglioramenti apportati alla sicurezza nelle chiavi API con ambito. Le chiavi con accesso completo non scadono mai e si applicano a tutti gli elementi appartenenti all'utente. Se si elimina una chiave di questo tipo, non può essere ricreata.

L'immagine seguente illustra le opzioni disponibili quando si crea una chiave API con ambito.

![Creazione di chiavi API](../../Images/PSGallery_KeyScoped.png)

In questo esempio viene creata una chiave API denominata **AzureRMDataFactory**. Il valore di questa chiave può essere usato per eseguire il push dei pacchetti i cui nomi iniziano con "AzureRM.DataFactory" ed è valido per 365 giorni. Questo è uno scenario tipico quando diversi team all'interno della stessa organizzazione lavorano su pacchetti diversi. I membri del team hanno una chiave che concede loro privilegi per il pacchetto specifico su cui lavorano.
Il valore di scadenza impedisce l'uso di chiavi non aggiornate o dimenticate.

## <a name="using-glob-patterns"></a>Uso dei criteri GLOB

Se si lavora su più pacchetti, è possibile usare i criteri di GLOB per abbinare più pacchetti come gruppo. Le autorizzazioni della chiave API si applicano a tutti i nuovi pacchetti che corrispondono al criterio GLOB. L'esempio precedente usa il valore di **criterio GLOB** "AzureRM.DataFactory*". È possibile eseguire il push di un pacchetto denominato "AzureRm.DataFactoryV2.Netcore" usando questa chiave, poiché il pacchetto corrisponde al criterio GLOB.

## <a name="create-api-keys-securely"></a>Creare chiavi API in modo sicuro

Per sicurezza, un valore di chiave appena creato non viene mai visualizzato sullo schermo ed è disponibile solo con il pulsante Copia, come illustrato di seguito.

![Creazione di un nuovo valore della chiave API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> È possibile copiare il valore della chiave API solo immediatamente dopo averlo creato o aggiornato. Non verrà visualizzato e non sarà possibile accedervi nuovamente dopo che la pagina è stata aggiornata. Se si perde il valore della chiave, è necessario rigenerare la chiave e copiarla dopo che è stata rigenerata.

## <a name="key-permissions-and-expiration"></a>Autorizzazioni e scadenza delle chiavi

Le chiavi API con ambito possono assegnare le autorizzazioni seguenti:

- Push dei nuovi pacchetti
- Push dei pacchetti nuovi o di aggiornamento
- Eliminazione di pacchetti dall'elenco

Ogni nuova chiave ha una scadenza. Il valore di scadenza viene misurato in giorni. I valori possibili per la scadenza sono:

- 1 giorno
- 90 giorni
- 180 giorni
- 270 giorni
- 365 giorni (impostazione predefinita)

Queste impostazioni non possono essere modificate dopo la creazione della chiave. Non è possibile creare una nuova chiave che non scade mai.

## <a name="editing-and-deleting-existing-api-keys"></a>Modifica ed eliminazione di chiavi API esistenti

È possibile modificare alcune impostazioni di una chiave esistente. Come indicato in precedenza, non è possibile modificare l'ambito di protezione per una chiave API esistente o modificare la scadenza. Le opzioni modificabili sono visualizzate nella schermata seguente:

![Creazione di un nuovo valore della chiave API](../../Images/PSGallery_EditAPIKey.png)

Per modificare i pacchetti controllati da una chiave, è possibile scegliere singoli pacchetti dall'elenco o modificare il criterio GLOB.

Facendo clic su **Rigenera** si crea un nuovo valore di chiave. Proprio come per la creazione iniziale della chiave, è necessario **copiare** il valore della chiave immediatamente dopo averla aggiornata. L'opzione **Copia** non è disponibile dopo che si è usciti da questa pagina.

Se si fa clic su **Elimina** viene visualizzato un messaggio di conferma. Dopo essere stata eliminata, la chiave è inutilizzabile.

## <a name="key-expiration"></a>Scadenza della chiave

Dieci giorni prima della scadenza, PowerShell Gallery invia un avviso via posta elettronica al titolare dell'account della chiave API. Dopo la scadenza, la chiave è inutilizzabile. Nella parte superiore della pagina di gestione delle chiavi API viene visualizzato un messaggio di avviso che indica quali chiavi non sono più valide. È possibile generare un nuovo valore di chiave.
