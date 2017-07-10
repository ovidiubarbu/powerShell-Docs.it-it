---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4e0c1638bf10e57580a463c46595ac9bc142a5b4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="just-enough-administration-jea" class="xliff"></a>
# JEA (Just Enough Administration)
JEA (Just Enough Administration) è una nuova funzionalità di WMF 5.0 che consente l'amministrazione basata su ruoli tramite la comunicazione remota di PowerShell.  Questa funzionalità estende l'infrastruttura esistente di endpoint vincolati, consentendo a utenti non amministratori di eseguire comandi, script e file eseguibili specifici come amministratore.  In questo modo è possibile ridurre il numero di amministratori con diritti completi nel proprio ambiente e migliorare la sicurezza.  JEA funziona per qualsiasi elemento gestito tramite PowerShell e consente di eseguire le attività di gestione con maggiore sicurezza.  Per informazioni più dettagliate su JEA (Just Enough Administration) consultare la [guida all'esperienza](http://aka.ms/JEA).

Diversamente dagli endpoint vincolati precedenti, JEA è sia potente che semplice da configurare.  Le capacità degli utenti in JEA possono essere sottoposte a un controllo granulare, fino a limitare i set di parametri e i valori che possono essere forniti a un comando specifico. Le azioni dell'utente vengono eseguite nel contesto di un account virtuale occasionale con i diritti per eseguire azioni di amministrazione.  I comandi richiamati dall'utente possono essere registrati per i controlli di sicurezza.

Il funzionamento di JEA è basato sulla possibilità di creare endpoint vincolati con configurazioni specifiche.  Questi endpoint hanno alcune caratteristiche importanti:

1. Gli utenti che si connettono a tali endpoint possono eseguire azioni con un account virtuale con privilegi elevati che esiste solo per la durata della sessione remota.  Per impostazione predefinita, questo account virtuale è un membro del gruppo Administrators predefinito e del gruppo Domain Administrators nei controller di dominio (nota: queste autorizzazioni sono configurabili). La possibilità di connettersi con un account utente e di eseguire operazioni con un account diverso con privilegi elevati, permette di consentire agli utenti senza privilegi elevati di eseguire specifiche attività amministrative senza concedere loro diritti amministrativi per i sistemi.
2. L'endpoint è bloccato.  Questo significa che PowerShell viene eseguito nella modalità linguaggio NoLanguage.  Per l'utente sono visibili solo comandi, script e file eseguibili specifici.
3. Ai diversi utenti che si connettono viene presentato un set diverso di capacità in base ai gruppi di appartenenza.  È possibile specificare capacità diverse per ruoli diversi sullo stesso endpoint.

