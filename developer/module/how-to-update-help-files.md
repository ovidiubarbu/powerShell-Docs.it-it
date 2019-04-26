---
title: Come aggiornare i file della Guida | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082313"
---
# <a name="how-to-update-help-files"></a>Come aggiornare i file della Guida

In questo argomento viene illustrato come aggiornare i file della Guida per un modulo che supporta la Guida aggiornabile.

## <a name="updating-help-files"></a>L'aggiornamento dei file della Guida

Esistono molti motivi per aggiornare i file della Guida, ad esempio la correzione degli errori, per chiarire il concetto, rispondere alle domande frequenti, aggiungendo nuovi file o l'aggiunta di nuovi e migliori esempi.

Per aggiornare un file della Guida:

1. Modificare i file.

2. Convertire i file in altre impostazioni cultura dell'interfaccia utente.

3. Raccogliere tutti i file della Guida (nuove, modificati e invariati) per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente.

4. Convalidare i file rispetto allo schema XML.

5. Ricompilare i file CAB per ogni impostazione cultura dell'interfaccia utente.

6. Nel file XML HelpInfo, incrementare i numeri di versione del file CAB per ogni impostazione cultura dell'interfaccia utente.

7. Caricare i nuovi file CAB nel percorso specificato dal valore della **HelpContentUri** elemento nel file XML HelpInfo. Sostituire i vecchi file CAB con i nuovi file CAB.

8. Caricare il file XML HelpInfo aggiornato nel percorso specificato per il **HelpInfoUri** chiave nel manifesto del modulo. Sostituire il file XML HelpInfo precedente con il nuovo file.