---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: concetti principali usati in questa guida
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="key-concepts-used-throughout-this-guide"></a>Concetti principali usati in questa guida
**Che cos'è esattamente JEA?**

JEA è un'estensione degli [endpoint vincolati](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) di PowerShell che aggiunge definizioni di ruoli, account virtuali e diversi altri miglioramenti per semplificare ulteriormente il blocco degli endpoint di gestione.
Un endpoint JEA è costituito da un file di configurazione di sessione di PowerShell e da uno o più file di capacità del ruolo.

**Che cosa sono i file di configurazione di sessione e i file di capacità del ruolo?**

I file di configurazione di sessione di PowerShell (estensione pssc) specificano *chi* può connettersi a un endpoint di PowerShell e *come* viene configurato l'endpoint.
Consentono di mappare utenti e gruppi di sicurezza a ruoli di gestione specifici e di configurare impostazioni globali come gli account virtuali e i criteri di trascrizione.
I file di configurazione di sessione sono specifici di ogni computer e questo consente di controllare l'accesso in base al computer, se necessario.

I file di capacità del ruolo di PowerShell (estensione psrc) definiscono *che cosa* sono in grado di eseguire nel sistema gli utenti appartenenti a un ruolo.
Consentono di limitare i cmdlet, le funzioni, i provider e i programmi esterni che un utente può usare nella sessione di JEA.
I file capacità del ruolo sono spesso generici per il ruolo servito (amministratore DNS, supporto tecnico di livello 1, controllo di sola lettura dell'inventario e così via) e appartengono ai moduli di PowerShell, rendendo più semplice la condivisione nel proprio ambiente e con altri utenti.

**In che modo JEA usa gli account virtuali?**

Nel file di configurazione di sessione di PowerShell è possibile configurare le sessioni JEA per usare gli account virtuali "RunAs".
Gli account virtuali sono account monouso con privilegi eseguiti per la connessione di un utente specifico in una sessione specifica nel cui contesto vengono eseguiti i comandi dell'utente.
Gli account virtuali appartengono al gruppo di sicurezza "Administrators" locale per impostazione predefinita, ma se necessario possono essere configurati in modo da appartenere solo a gruppi di sicurezza specificati.

**Comunicazione remota di PowerShell**: consente di eseguire i comandi di PowerShell nei computer remoti.
È possibile lavorare con uno o più computer e usare connessioni temporanee o permanenti.
In questa demo la comunicazione remota viene eseguita nel computer locale con una sessione interattiva.
JEA limita le funzionalità disponibili attraverso la comunicazione remota di PowerShell.
Per altre informazioni sulla comunicazione remota di PowerShell, eseguire `Get-Help about_Remote`.

**Utente "RunAs"**: quando si usa JEA, un utente non amministratore viene eseguito come "account virtuale" con privilegi.
L'account virtuale esiste solo durante la sessione remota.
Vale a dire, viene creato quando un utente si connette all'endpoint ed eliminato quando l'utente termina la sessione.
Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators locale.
In un controller di dominio è un membro del gruppo Domain Admins.
Gli account virtuali sono locali nel computer in cui vengono creati e non usufruiscono di autorizzazioni di fuori di tale computer.
Ciò significa che non vengono registrati in Active Directory e che non viene assegnato alcun RID.
Inoltre, se un comando o script consentito tenta di accedere alle risorse esterne al computer locale, accederà a tali risorse con l'identità del computer, non l'identità dell'account virtuale.

**Utente "connesso"**: l'utente non amministratore che si connette all'endpoint JEA e a cui vengono assegnati i ruoli.
I comandi eseguiti da questo utente vengono eseguiti nel contesto dell'utente RunAs o dell'account virtuale.

