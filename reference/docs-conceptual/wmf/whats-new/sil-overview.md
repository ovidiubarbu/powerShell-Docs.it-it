---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Registrazione inventario software (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71147781"
---
# <a name="software-inventory-logging-sil"></a>Registrazione inventario software (SIL)

> [!IMPORTANT]
> Quando si installa WMF 5 in un computer Windows Server 2012 R2 che già esegue SIL, è necessario eseguire il cmdlet Start-SilLogging una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.

Registrazione inventario software contribuisce a ridurre i costi operativi associati al recupero di informazioni accurate sul software Microsoft installato localmente in un server, ma soprattutto in più server in un ambiente IT (presupponendo che il software sia installato ed eseguito in tutto l'ambiente IT). A condizione che ce ne sia uno disponibile configurato, è possibile inoltrare questi dati a un server di aggregazione e raccogliere i dati di log in un'unica posizione tramite un processo automatico uniforme.

Pur essendo possibile registrare i dati di inventario software anche eseguendo query direttamente in ogni computer, avvalendosi di un'architettura di inoltro (sulla rete) avviata da ogni server, la funzionalità Registrazione inventario software consente di superare le difficoltà di individuazione dei server tipiche di molti scenari di gestione delle risorse e di inventario software. Registrazione inventario software usa SSL per proteggere i dati inoltrati tramite HTTPS a un server di aggregazione. L'archiviazione dei dati in un'unica posizione facilita l'analisi, la modifica e la condivisione dei dati all'occorrenza.

Nessuno di questi dati viene inviato a Microsoft con questa funzionalità. I dati e la funzionalità della registrazione dell'inventario software sono destinati unicamente agli amministratori e al proprietario della licenza del software del server.

Per altre informazioni e documentazione sui cmdlet di Registrazione inventario software, vedere [Gestire Registrazione inventario software in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).
