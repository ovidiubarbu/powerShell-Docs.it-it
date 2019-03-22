---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.topic: conceptual
title: modello di esempio di writeup di problemi noti o di una limitazione
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794494"
---
 ><span data-ttu-id="06bf5-103">Nota: specificare una proposta di titolo descrittivo e una breve descrizione</span><span class="sxs-lookup"><span data-stu-id="06bf5-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="06bf5-104">Esempio: Errori di tipo ExecutionPolicy errati</span><span class="sxs-lookup"><span data-stu-id="06bf5-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="06bf5-105">In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="06bf5-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="06bf5-106">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="06bf5-106">Resolution</span></span>

<span data-ttu-id="06bf5-107">Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="06bf5-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
