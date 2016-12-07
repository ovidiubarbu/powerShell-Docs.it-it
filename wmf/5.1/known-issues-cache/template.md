---
title: modello di esempio di writeup di problemi noti o di una limitazione
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## <a name="example-erroneous-executionpolicy-errors"></a>Esempio: Errori di tipo ExecutionPolicy errati ##
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

### <a name="resolution"></a>Risoluzione

Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```
