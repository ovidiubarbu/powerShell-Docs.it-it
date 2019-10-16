---
title: Parametri di data e ora | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 5b1f093de5db364ac806e58c4ed8dbf2948cb6c6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369790"
---
# <a name="date-and-time-parameters"></a>Parametri di data e ora

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri che gestiscono le informazioni di data e ora. I parametri di data e ora vengono in genere utilizzati per registrare quando si crea o si accede a un elemento.

|Parametro|Funzionalità|
|---|---|
|**Accedere**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che, quando viene specificato, il cmdlet funzionerà sulle risorse a cui è stato effettuato l'accesso in base alla data e all'ora specificate dai parametri **before** e **after** . Se questo parametro è specificato, non è necessario specificare i parametri **creati** e **modificati** .|
|**Dopo**<br>Tipo di dati: DateTime|Implementare questo parametro per specificare la data e l'ora in cui è stato utilizzato il cmdlet. Per il corretto funzionamento del parametro **after** , il cmdlet deve disporre anche di un parametro di **accesso**, **creato**o **modificato** . Il parametro deve essere impostato su **true** quando viene chiamato il cmdlet.|
|**Prima**<br>Tipo di dati: DateTime|Implementare questo parametro per specificare la data e l'ora in cui è stato utilizzato il cmdlet. Per il corretto funzionamento del parametro **before** , è necessario che il cmdlet disponga anche di un parametro di **accesso**, **creato**o **modificato** . Il parametro deve essere impostato su **true** quando viene chiamato il cmdlet.|
|**Creato**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che, quando viene specificato, il cmdlet funzionerà sulle risorse create in base alla data e all'ora specificate dai parametri **before** e **after** . Se questo parametro è specificato, non è necessario specificare i parametri a cui è stato **eseguito l'accesso** e **modificati** .|
|**Esatta**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che, quando viene specificato, il termine della risorsa debba corrispondere esattamente al nome della risorsa. Quando il parametro non viene specificato, il termine e il nome della risorsa non devono corrispondere esattamente.|
|**Modificato**<br>Tipo di dati: DateTime|Implementare questo parametro in modo che, quando viene specificato, il cmdlet opererà sulle risorse che sono state modificate in base alla data e all'ora specificate dai parametri **before** e **after** . Se questo parametro è specificato, non è necessario specificare i parametri di **accesso** e di **creazione** .|
## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
