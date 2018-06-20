---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.topic: conceptual
title: modello di esempio di writeup di problemi noti o di una limitazione
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221936"
---
>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## <a name="example-erroneous-executionpolicy-errors"></a>Esempio: Errori di tipo ExecutionPolicy errati ##
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

### <a name="resolution"></a>Risoluzione

Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```
