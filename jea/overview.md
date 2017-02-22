---
description: 
manager: dongill
ms.topic: article
author: rpsqrd
ms.author: ryanpu
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-12-05
title: Panoramica di Just Enough Administration (JEA)
ms.technology: powershell
ms.openlocfilehash: 742f88bd130a9bcb577914c842735e8c47ca53e6
ms.sourcegitcommit: cfe32f213819ae76de05da564c3e2c4b7ecfda2f
translationtype: HT
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) è una tecnologia di protezione che consente l'amministrazione delegata per qualsiasi elemento che possa essere gestito con PowerShell.
Con JEA, è possibile:

- **Ridurre il numero di amministratori dei computer** sfruttando gli account virtuali che eseguono azioni con privilegi per conto degli utenti normali.
- **Limitare le operazioni consentite agli utenti** specificando quali cmdlet, funzioni e comandi esterni possono eseguire.
- **Capire meglio le azioni degli utenti** con trascrizioni e log che indicano esattamente i comandi eseguiti da un utente durante la sessione.

**Perché tutto questo è importante?**

Gli account con privilegi elevati usati per amministrare i server comporta un grave rischio nella sicurezza.
Se un utente malintenzionato accede a uno di questi account, potrebbe avviare [attacchi laterali](http://aka.ms/pth) all'interno dell'organizzazione.
Ogni account violato può dare accesso ad altri account e risorse e consentire agli utenti malintenzionati di raggiungere e sottrarre le informazioni più riservate della società, di lanciare attacchi Denial of Service e altro ancora.

Non è sempre molto semplice rimuovere i privilegi amministrativi.
Si consideri lo scenario in cui il ruolo DNS è installato nello stesso computer del controller di dominio Active Directory.
Gli amministratori DNS richiedono privilegi di amministratore locale per risolvere problemi con il server DNS, e per fare ciò è necessario che siano membri del gruppo di sicurezza con privilegi elevati "Domain Admins".
Con questo approccio gli amministratori DNS saranno in grado di controllare l'intero dominio e di accedere a tutte le risorse del computer.

JEA consente di risolvere questo problema adottando il principio di *privilegio minimo*.
Con JEA è possibile configurare un endpoint di gestione per gli amministratori DNS che consenta l'accesso solo ai comandi PowerShell necessari per svolgere il loro lavoro.
Ciò significa che è possibile definire accesso specifico per riparare una cache DNS danneggiata o riavviare il server DNS senza concedere inavvertitamente diritti per accedere ad Active Directory, sfogliare il file system o eseguire script potenzialmente pericolosi.
In aggiunta, quando la sessione JEA è configurata per l'uso di account virtuali con privilegi temporanei, gli amministratori DNS possono connettersi al server usando credenziali *senza privilegi di amministratore* ed eseguire comandi che in genere richiedono tali privilegi.
Questa funzionalità consente di rimuovere utenti dai ruoli di amministratore locale o di dominio con privilegi elevati e controllare attentamente le azioni che possono eseguire in ogni computer.

## <a name="get-started-with-jea"></a>Introduzione a JEA

Oggi è possibile usare JEA in tutti i computer che eseguono Windows Server 2016 o Windows 10.
È anche possibile eseguire JEA su sistemi operativi precedenti con un aggiornamento di Windows Management Framework.
Per altre informazioni sui requisiti per usare JEA e su come creare, usare e controllare un endpoint JEA, vedere gli argomenti seguenti:

- [Prerequisiti](prerequisites.md): illustra come impostare l'ambiente per usare JEA.
- [Funzionalità del ruolo](role-capabilities.md): illustra come creare i ruoli che determinano le azioni che un utente può eseguire in una sessione JEA.
- [Configurazioni della sessione](session-configurations.md): illustra come configurare gli endpoint JEA che eseguono il mapping degli utenti ai ruoli e impostare l'identità JEA
- [Registrazione di JEA](register-jea.md): creare un endpoint JEA e renderlo disponibile per gli utenti.
- [Uso di JEA](using-jea.md): informazioni sui diversi modi in cui è possibile usare JEA.
- [Considerazioni sulla sicurezza](security-considerations.md): rivedere le procedure consigliate sulla sicurezza e le implicazioni delle opzioni di configurazione JEA.
- [Controllare e creare report in JEA](audit-and-report.md): informazioni su come controllare e creare report negli endpoint JEA.