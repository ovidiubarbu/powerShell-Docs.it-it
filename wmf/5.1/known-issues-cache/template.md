---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: modello di esempio di writeup di problemi noti o di una limitazione
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

<a id="example-erroneous-executionpolicy-errors" class="xliff"></a>
## Esempio: Errori di tipo ExecutionPolicy errati ##
In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.

<a id="resolution" class="xliff"></a>
### Risoluzione

Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):

```powershell
Set-ExecutionPolicy RemoteSigned
```

