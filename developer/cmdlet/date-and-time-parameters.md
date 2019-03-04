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
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251354"
---
# <a name="date-and-time-parameters"></a>Parametri di data e ora

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri che gestiscono le informazioni di data e ora. Parametri di data e ora vengono in genere utilizzati per registrare quando un elemento viene creato o si accede.

|Parametro|Funzionalità|
|---|---|
|**Accessed**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che quando viene specificato il cmdlet funzionerà per le risorse che hanno effettuate l'accesso basato su data e ora specificato per il **prima di** e **dopo** parametri. Se viene specificato questo parametro, il **Created** e **Modified** i parametri devono non essere è possibile specificare.|
|**Dopo aver**<br>Tipo di dati: DateTime|Implementare questo parametro per specificare la data e l'ora dopo il quale è stato usato il cmdlet. Per il **dopo aver** parametro funzioni correttamente, il cmdlet deve anche avere un **Accessed**, **Created**, o **Modified** parametro. E, tale parametro deve essere impostato su **true** quando viene chiamato il cmdlet.|
|**Prima di**<br>Tipo di dati: DateTime|Implementare questo parametro per specificare la data e ora prima delle quali è stato usato il cmdlet. Per il **prima** parametro funzioni correttamente, il cmdlet deve anche avere un **Accessed**, **Created**, o **Modified** parametro. E, tale parametro deve essere impostato su **true** quando viene chiamato il cmdlet.|
|**Creato**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che quando viene specificato il cmdlet funzionerà per le risorse che sono state create in base alla data e ora specificate dal **prima** e **dopo** parametri. Se viene specificato questo parametro, il **Accessed** e **Modified** parametri non devono essere specificati.|
|**Exact**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che quando viene specificato il termine di risorsa deve corrispondere al nome della risorsa esattamente. Quando il parametro non viene specificato il termine di risorse e il nome non è necessario in modo che corrispondano esattamente.|
|**Modificato**<br>Tipo di dati: DateTime|Implementare questo parametro in modo che quando viene specificato il cmdlet funzionerà su risorse che sono state modificate in base alla data e ora specificate dal **prima** e **dopo** parametri. Se viene specificato questo parametro, il **Accessed** e **Created** parametri non devono essere specificati.|
## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
