---
title: Creazione di un'interfaccia utente personalizzata | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367630"
---
# <a name="creating-a-custom-user-interface"></a>Creazione di un'interfaccia utente personalizzata

Windows PowerShell fornisce le classi e le interfacce astratte che consentono di creare un'interfaccia utente interattiva personalizzata che ospita il motore di Windows PowerShell. Per creare un'interfaccia utente personalizzata, è necessario implementare la classe [System. Management. Automation. host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Facoltativamente, è anche possibile implementare le classi [System. Management. Automation. host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)e [System. Management. Automation. host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) e le interfacce System. Management. [Automation. host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) e [System. Management. Automation. host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) .
