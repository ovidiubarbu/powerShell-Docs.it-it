---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Gestione dei proprietari di elementi
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222108"
---
# <a name="managing-item-owners"></a>Gestione dei proprietari di elementi

La proprietà di un elemento in PowerShell Gallery è definita dalla persona che ha pubblicato l'elemento in questione in PowerShell Gallery.
A volte questi metadati devono essere gestiti anche dopo la pubblicazione dell'elemento iniziale. Questo significa che i metadati del proprietario devono essere modificabili, mentre l'elemento stesso non lo è.

Tutti i proprietari di elementi hanno pari diritti.
Questo significa che qualsiasi proprietario di elemento può pubblicare una nuova versione dell'elemento stesso. Significa anche che qualsiasi proprietario di elemento può rimuovere un altro proprietario di elemento.
Nessun proprietario ha un'autorità maggiore di altri proprietari.

## <a name="setting-an-items-initial-owner"></a>Impostazione del proprietario iniziale di un elemento

Quando un elemento viene pubblicato in PowerShell Gallery, il proprietario iniziale viene definito dall'utente che ha pubblicato l'elemento in questione. Questo è determinato dal titolare della chiave API usata nel cmdlet Publish-Module.

## <a name="adding-owners"></a>Aggiunta di proprietari

Dopo che un elemento è stato pubblicato in PowerShell Gallery, la procedura per invitare altri utenti a diventare proprietari di tale elemento è semplice.

1. [Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario dell'elemento.
2. Passare a una pagina di tipo elemento usando la scheda 'Elementi', eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Gestisci elementi personali).
3. Dopo aver eseguito l'accesso come proprietario di un elemento, nel lato sinistro è disponibile il collegamento 'Manage Owners' (Gestisci proprietari) su cui fare clic.
4. Immettere il nome utente della persona da aggiungere come proprietario e fare clic su 'Aggiungi'.
5. Al nuovo comproprietario viene inviato un messaggio di posta elettronica, come invito a diventare proprietario di un elemento.
6. Dopo aver fatto clic sul collegamento, l'utente diventa a tutti gli effetti comproprietario dell'elemento e ne ha il pieno controllo, inclusa la possibilità di rimuovere altri utenti come proprietari.

**NOTA**: fino a quando non conferma la proprietà, l'utente *non* verrà elencato come proprietario di un elemento.
Nella pagina **Manage Owners** (Gestisci proprietari), nella sezione relativa ai proprietari correnti, verrà visualizzata un'"approvazione in sospeso".
Tale invito può essere rimosso, così come è possibile rimuovere altri proprietari.
Questo meccanismo di inviti impedisce che gli utenti aggiungano falsamente altri utenti come proprietari dei loro elementi.

Si tenga presente che i metadati di tipo "Autori" sono semplice testo in formato libero e che soltanto i metadati di tipo "Proprietari" sono controllati.


## <a name="removing-owners"></a>Rimozione di proprietari

Se un elemento ha più proprietari ed è necessario rimuoverne uno, seguire questa semplice procedura:

1. [Accedere](https://powershellgallery.com/users/account/LogOn) a PowerShell Gallery con l'account attualmente proprietario dell'elemento;
2. Passare a una pagina di tipo elemento usando la scheda Elementi, eseguendo una ricerca o facendo clic sul proprio nome utente e quindi su [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Gestisci elementi personali).
3. Dopo aver eseguito l'accesso come proprietario di un elemento, nel lato sinistro è disponibile il collegamento 'Manage Owners' (Gestisci proprietari) su cui fare clic;
4. Fare clic sul collegamento 'Rimuovi' accanto al proprietario da rimuovere.



## <a name="transferring-item-ownership"></a>Trasferimento della proprietà degli elementi

A volte Microsoft riceve richieste di supporto relative al trasferimento della proprietà di un elemento da un utente all'altro. Questa operazione, tuttavia, può essere quasi sempre eseguita dagli utenti in modo autonomo.
Il trasferimento della proprietà da un utente a un altro è semplicemente una combinazione delle due procedure descritte in precedenza.

1. Il proprietario corrente invita il nuovo utente a diventare comproprietario e il nuovo utente accetta l'invito;
2. Il nuovo utente rimuove il vecchio utente dall'elenco dei proprietari.

La richiesta di supporto può avere due motivi differenti, ma la procedura rimane la stessa.

- La proprietà dell'elemento cambia da uno sviluppatore a un altro
- L'elemento è stato pubblicato accidentalmente con un account non corretto


## <a name="orphaned-items"></a>Elenchi orfani

Anche se raramente, si è presentato anche lo scenario descritto di seguito.
Gli elementi sono diventati orfani e non è possibile usare soltanto l'account del proprietario degli elementi per aggiungere nuovi proprietari.
Di seguito sono riportati alcuni esempi relativi a questo scenario:

- L'account del proprietario è associato a un indirizzo di posta elettronica che non esiste più e l'utente ha dimenticato la password
- L'utente registrato ha lasciato l'azienda che produce l'elemento e non può essere raggiunto per aggiornarne la proprietà
- A causa di un bug che ha interessato solo pochi elementi, l'elemento risulta senza proprietario in PowerShell Gallery

Gli amministratori di PowerShell Gallery possono accedere al collegamento 'Manage Owners' (Gestisci proprietari) per qualsiasi elemento.
Se l'utente che ha inviato la richiesta è il legittimo proprietario di un elemento e non è in grado di raggiungere il proprietario corrente per ottenere le autorizzazioni di proprietà, può usare il collegamento 'Report Abuse' (Segnala abusi) per contattare gli amministratori di PowerShell Gallery.
Gli amministratori eseguiranno quindi un processo per verificare la proprietà dell'elemento.
Se stabiliscono che l'utente deve essere un proprietario dell'elemento, gli amministratori useranno il collegamento 'Manage Owners' (Gestisci proprietari) e invieranno all'utente un invito a diventare proprietario.
Gli amministratori agiranno in questo modo solo dopo aver verificato il diritto dell'utente a essere un proprietario. Questo tipo di processo varia a seconda delle circostanze.
Spesso gli amministratori useranno l'URL di progetto dell'elemento per contattare il proprietario del progetto stesso. In alternativa, per contattare il proprietario del progetto potranno essere usati Twitter, la posta elettronica o altri sistemi.