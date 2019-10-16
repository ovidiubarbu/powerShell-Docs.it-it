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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367140"
---
# <a name="how-to-update-help-files"></a>Come aggiornare i file della Guida

In questo argomento viene illustrato come aggiornare i file della Guida per un modulo che supporta la guida aggiornabile.

## <a name="updating-help-files"></a>Aggiornamento dei file della Guida

Esistono diversi motivi per aggiornare i file della guida, ad esempio correggere gli errori, chiarire un concetto, rispondere a una domanda frequente, aggiungere nuovi file o aggiungere nuovi esempi nuovi e migliori.

Per aggiornare un file della guida:

1. Modificare i file.

2. Tradurre i file in altre impostazioni cultura dell'interfaccia utente.

3. Raccogliere tutti i file della guida (nuovi, modificati e non modificati) per il modulo in ogni impostazioni cultura dell'interfaccia utente.

4. Convalidare i file rispetto al XML Schema.

5. Ricompilare i file CAB per ogni lingua dell'interfaccia utente.

6. Nel file XML HelpInfo, incrementare i numeri di versione del file CAB per ogni lingua dell'interfaccia utente.

7. Caricare i nuovi file CAB nel percorso specificato dal valore dell'elemento **HelpContentUri** nel file XML HELPINFO. Sostituire i file CAB meno recenti con i nuovi file CAB.

8. Caricare il file XML HelpInfo aggiornato nel percorso specificato dalla chiave **HelpInfoUri** nel manifesto del modulo. Sostituire il file XML HelpInfo precedente con il nuovo file.