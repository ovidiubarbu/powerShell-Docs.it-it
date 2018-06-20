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
><span data-ttu-id="ace92-103">Nota: specificare una proposta di titolo descrittivo e una breve descrizione</span><span class="sxs-lookup"><span data-stu-id="ace92-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="ace92-104">Esempio: Errori di tipo ExecutionPolicy errati</span><span class="sxs-lookup"><span data-stu-id="ace92-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="ace92-105">In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="ace92-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="ace92-106">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="ace92-106">Resolution</span></span>

<span data-ttu-id="ace92-107">Per risolvere il problema, impostare **ExecutionPolicy** su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="ace92-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
