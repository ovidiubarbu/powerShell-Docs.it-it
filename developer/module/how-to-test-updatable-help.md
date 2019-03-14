---
title: Come testare una Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794264"
---
# <a name="how-to-test-updatable-help"></a>Come testare una Guida aggiornabile

Questo argomento descrive gli approcci all'esecuzione di test per la Guida aggiornabile per un modulo.

## <a name="using-verbose-to-detect-errors"></a>Uso dettagliato per rilevare gli errori

Dopo aver caricato il file XML HelpInfo e un file CAB per un modulo, i file di test tramite l'esecuzione di un' [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con il **Verbose** parametro. Il **Verbose** parametro indica `Update-Help` per segnalare i passaggi essenziali relative azioni, di leggere il **HelpInfoUri** chiave nel manifesto del modulo per la convalida i tipi di file nel file CAB decompresso e il posizionamento dei file nella directory del modulo specifico della lingua.

Quando vengono risolti tutti i messaggi dettagliati, eseguire un' `Update-Help` comando con il **Debug** parametro. Questo parametro deve rilevare eventuali problemi rimanenti con i file della Guida aggiornabile.