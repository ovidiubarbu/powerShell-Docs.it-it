---
title: Come testare la guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367150"
---
# <a name="how-to-test-updatable-help"></a>Come testare una Guida aggiornabile

Questo argomento descrive gli approcci per testare la guida aggiornabile per un modulo.

## <a name="using-verbose-to-detect-errors"></a>Uso di Verbose per rilevare gli errori

Dopo aver caricato il file XML HelpInfo e i file CAB per il modulo, testare i file eseguendo un comando [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con il parametro **verbose** . Il parametro **verbose** indica `Update-Help` per segnalare i passaggi critici nelle azioni, leggendo la chiave **HelpInfoUri** nel manifesto del modulo per convalidare i tipi di file nel file CAB decompresso e inserendo i file nella directory del modulo specifica della lingua.

Quando tutti i messaggi dettagliati vengono risolti, eseguire un comando `Update-Help` con il parametro **debug** . Questo parametro deve rilevare eventuali problemi rimanenti con i file della Guida aggiornabili.