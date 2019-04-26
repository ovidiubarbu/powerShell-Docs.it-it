---
title: Creazione di spazi di esecuzione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17f323c3-e873-449e-8a28-477f1c6b5e12
caps.latest.revision: 6
ms.openlocfilehash: b4e61600f68521e4e7ab56ceae3349381e88a70a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082941"
---
# <a name="creating-runspaces"></a>Creazione di spazi di esecuzione

Uno spazio di esecuzione è l'ambiente operativo per i comandi che vengono richiamate da un'applicazione host. Questo ambiente include i comandi e i dati che sono attualmente presenti ed eventuali restrizioni di linguaggio che attualmente si applicano.

 Hosting di applicazioni può usare lo spazio di esecuzione predefinito fornito da Windows PowerShell, che include tutti i comandi di core disponibili, o creare uno spazio di esecuzione personalizzata che include solo un subset di comandi disponibili. Per creare uno spazio di esecuzione personalizzata, è necessario creare un [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) e assegnarlo a di spazio di esecuzione.

## <a name="runspace-tasks"></a>Spazio di esecuzione attività

1. [Creazione di un InitialSessionState](./creating-an-initialsessionstate.md)

2. [Creazione di uno spazio di esecuzione vincolata](./creating-a-constrained-runspace.md)

3. [Creazione di più spazi di esecuzione](./creating-multiple-runspaces.md)

## <a name="see-also"></a>Vedere anche
