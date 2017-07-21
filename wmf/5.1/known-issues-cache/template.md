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
><span data-ttu-id="f7387-103">Nota: specificare una proposta di titolo descrittivo e una breve descrizione</span><span class="sxs-lookup"><span data-stu-id="f7387-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="f7387-104">Esempio: Errori di tipo ExecutionPolicy errati</span><span class="sxs-lookup"><span data-stu-id="f7387-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="f7387-105">In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="f7387-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="f7387-106">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="f7387-106">Resolution</span></span>

<span data-ttu-id="f7387-107">Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="f7387-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

