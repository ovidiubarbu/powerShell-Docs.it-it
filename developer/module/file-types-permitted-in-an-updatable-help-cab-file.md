---
title: Tipi di file consentiti in un aggiornabili consentono di File CAB | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794247"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="de0fd-102">Tipi di file consentiti in un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="de0fd-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="de0fd-103">Questo argomento elenca e descrive i requisiti di contenuto per i file CAB di Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="de0fd-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="de0fd-104">Requisiti di File CAB di Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="de0fd-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="de0fd-105">Contenuto del file CAB non compresso è limitato a 1 GB per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="de0fd-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="de0fd-106">Per ignorare questo limite, gli utenti dovranno usare la **Force** parametro del [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de0fd-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="de0fd-107">Per garantire la sicurezza dei file della Guida che vengono scaricati da Internet, un file CAB di Guida aggiornabile può includere solo i tipi di file elencati di seguito.</span><span class="sxs-lookup"><span data-stu-id="de0fd-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="de0fd-108">Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet convalida tutti i file degli schemi argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="de0fd-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="de0fd-109">Se il `Update-Help` cmdlet rileva un file che non è valido o non è un tipo consentito, ma non viene installato il file non valido e arresta l'installazione dei file dal CAB sul computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="de0fd-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="de0fd-110">Argomenti della Guida basati su XML per i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de0fd-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="de0fd-111">Argomenti della Guida basati su XML per gli script e funzioni.</span><span class="sxs-lookup"><span data-stu-id="de0fd-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="de0fd-112">Argomenti della Guida basati su XML per i provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de0fd-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="de0fd-113">Basata su testo argomenti della Guida, ad esempio sugli argomenti.</span><span class="sxs-lookup"><span data-stu-id="de0fd-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="de0fd-114">Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica il contenuto di file CAB quando si decompresso il file CAB.</span><span class="sxs-lookup"><span data-stu-id="de0fd-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="de0fd-115">Se `Update-Help` individua i tipi di file non conformi in un file CAB di Guida aggiornabile, genera un errore irreversibile e arresta l'operazione.</span><span class="sxs-lookup"><span data-stu-id="de0fd-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="de0fd-116">Non installa tutti i file della Guida dal CAB, anche quelli dei tipi di file conforme.</span><span class="sxs-lookup"><span data-stu-id="de0fd-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>