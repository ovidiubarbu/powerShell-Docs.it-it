---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: modello di esempio di writeup di problemi noti o di una limitazione
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## <a name="example-erroneous-executionpolicy-errors"></a>Esempio: Errori di tipo ExecutionPolicy errati ##
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

### <a name="resolution"></a>Risoluzione

Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```