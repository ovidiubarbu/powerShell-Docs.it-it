---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.topic: conceptual
title: modello di esempio di writeup di problemi noti o di una limitazione
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055548"
---
 >Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## <a name="example-erroneous-executionpolicy-errors"></a>Esempio: Errori di tipo ExecutionPolicy errati
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

### <a name="resolution"></a>Risoluzione

Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```
