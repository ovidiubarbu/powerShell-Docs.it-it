---
title: Miglioramento delle registrazioni del server di pull
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## Miglioramento della registrazione del server di pull ##

Nelle versioni precedenti di WMF le richieste di registrazione o reporting simultanee al server di pull DSC, con uso del database ESENT, facevano sì che la gestione della configurazione locale non riuscisse ad eseguire la registrazione o il reporting. In questi casi i registri eventi del server di pull visualizzano il messaggio di errore "Nome istanza già in uso".
Ciò era dovuto a un modello errato che veniva usato per accedere al database ESENT in uno scenario multithread. In WMF 5.1 questo problema è stato risolto. Le registrazioni o il reporting simultanei, che comprendono l'uso del database ESENT, funzionano correttamente in WMF 5.1. Tutto questo si applica solo al database ESENT, non al database OLE DB. 



<!--HONumber=Jul16_HO3-->


