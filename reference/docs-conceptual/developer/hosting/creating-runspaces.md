---
title: Creazione di Runspaces | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367580"
---
# <a name="creating-runspaces"></a>Creazione di spazi di esecuzione

Un spazio è l'ambiente operativo per i comandi richiamati da un'applicazione host. Questo ambiente include i comandi e i dati attualmente presenti e tutte le restrizioni relative alla lingua attualmente applicabili.

 Le applicazioni host possono usare il spazio predefinito fornito da Windows PowerShell, che include tutti i comandi di base disponibili, oppure creare un spazio personalizzato che includa solo un subset dei comandi disponibili. Per creare un spazio personalizzato, creare un oggetto [System. Management. Automation. Runspaces. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) e assegnarlo a spazio.

## <a name="runspace-tasks"></a>Attività spazio

1. [Creazione di un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Creazione di un spazio vincolato](./creating-a-constrained-runspace.md)

3. [Creazione di più Runspaces](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Vedere anche
