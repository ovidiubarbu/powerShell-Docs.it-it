---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7e87ed4bc9a86be52d4d06d3e87386a1111227c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681632"
---
# <a name="software-inventory-logging-sil"></a>Registrazione inventario software (SIL)

**IMPORTANTE:** *quando si installa WMF 5.0 in un computer Windows Server 2012 R2 Server che già esegue SIL, è necessario eseguire il cmdlet Start-SilLogging una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.*

Registrazione inventario software contribuisce a ridurre i costi operativi associati al recupero di informazioni accurate sul software Microsoft installato localmente in un server, ma soprattutto in più server in un ambiente IT (presupponendo che il software sia installato ed eseguito in tutto l'ambiente IT). A condizione che ce ne sia uno disponibile configurato, è possibile inoltrare questi dati a un server di aggregazione e raccogliere i dati di log in un'unica posizione tramite un processo automatico uniforme.

Pur essendo possibile registrare i dati di inventario software anche eseguendo query direttamente in ogni computer, avvalendosi di un'architettura di inoltro (sulla rete) avviata da ogni server, la funzionalità Registrazione inventario software consente di superare le difficoltà di individuazione dei server tipiche di molti scenari di gestione delle risorse e di inventario software. Registrazione inventario software usa SSL per proteggere i dati inoltrati tramite HTTPS a un server di aggregazione. L'archiviazione dei dati in un'unica posizione facilita l'analisi, la modifica e la condivisione dei dati all'occorrenza.

Nessuno di questi dati viene inviato a Microsoft con questa funzionalità. I dati e la funzionalità della registrazione dell'inventario software sono destinati unicamente agli amministratori e al proprietario della licenza del software del server.

Per altre informazioni e documentazione sui cmdlet di Registrazione inventario software, vedere le risorse online per Windows Server 2012 R2 all'indirizzo <http://technet.microsoft.com/library/dn383584.aspx>.
