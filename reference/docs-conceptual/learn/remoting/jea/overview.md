---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Panoramica di Just Enough Administration (JEA)
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017702"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) è una tecnologia di protezione che consente l'amministrazione delegata per qualsiasi elemento che possa essere gestito da PowerShell. Con JEA, è possibile:

- **Ridurre il numero di amministratori dei computer** usando gli account virtuali o gli account dei servizi gestiti del gruppo per eseguire azioni con privilegi per conto degli utenti normali.
- **Limitare le operazioni consentite agli utenti** specificando quali cmdlet, funzioni e comandi esterni possono eseguire.
- **Capire meglio le azioni degli utenti** con trascrizioni e log che indicano esattamente i comandi eseguiti da un utente durante la sessione.

**Perché è importante JEA?**

Gli account con privilegi elevati usati per amministrare i server comporta un grave rischio nella sicurezza. Se un utente malintenzionato accede a uno di questi account, potrebbe avviare [attacchi laterali](https://aka.ms/pth) all'interno dell'organizzazione. Ogni account violato consente l'accesso ad altri account e risorse e permette agli utenti malintenzionati di raggiungere e sottrarre le informazioni più riservate della società, di lanciare attacchi Denial of Service e altro ancora.

Tuttavia, non è sempre semplice rimuovere i privilegi amministrativi. Si consideri lo scenario in cui il ruolo DNS è installato nello stesso computer del controller di dominio Active Directory. Gli amministratori DNS richiedono privilegi di amministratore locale per risolvere i problemi con il server DNS. A tale scopo, tuttavia, è necessario impostarli come membri del gruppo di sicurezza **Domain Admins** con privilegi elevati. Con questo approccio gli amministratori DNS saranno in grado di controllare l'intero dominio e di accedere a tutte le risorse del computer.

JEA consente di risolvere questo problema tramite il principio dei **privilegi minimi**. Con JEA è possibile configurare un endpoint di gestione per gli amministratori DNS che consenta l'accesso solo ai comandi PowerShell necessari per svolgere il lavoro. Ciò significa che è possibile definire accesso specifico per riparare una cache DNS danneggiata o riavviare il server DNS senza concedere inavvertitamente diritti per accedere ad Active Directory, sfogliare il file system o eseguire script potenzialmente pericolosi. Inoltre, quando la sessione JEA è configurata per l'uso di account virtuali con privilegi temporanei, gli amministratori DNS possono connettersi al server usando credenziali **senza privilegi di amministratore** e continuare a eseguire comandi che in genere richiedono privilegi di amministratore. JEA consente di rimuovere utenti dai ruoli di amministratore locale o di dominio con privilegi elevati e controllare attentamente le azioni che possono eseguire in ogni computer.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui requisiti per usare JEA, vedere l'articolo [Prerequisiti](prerequisites.md).

## <a name="samples-and-dsc-resource"></a>Esempi e risorsa DSC

Nel [repository GitHub JEA](https://github.com/PowerShell/JEA) sono disponibili configurazioni JEA di esempio e la risorsa DSC JEA.
