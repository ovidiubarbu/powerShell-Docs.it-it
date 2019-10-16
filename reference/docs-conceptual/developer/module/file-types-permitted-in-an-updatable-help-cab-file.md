---
title: Tipi di file consentiti in un file CAB della Guida aggiornabile | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367260"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a><span data-ttu-id="67267-102">Tipi di file consentiti in un file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="67267-102">File Types Permitted in an Updatable Help CAB File</span></span>

<span data-ttu-id="67267-103">In questo argomento vengono elencati e descritti i requisiti di contenuto per i file CAB della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="67267-103">This topics lists and describes the content requirements for Updatable Help CAB files.</span></span>

## <a name="updatable-help-cab-file-requirements"></a><span data-ttu-id="67267-104">Requisiti dei file CAB della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="67267-104">Updatable Help CAB File Requirements</span></span>

<span data-ttu-id="67267-105">Per impostazione predefinita, il contenuto del file CAB non compresso è limitato a 1 GB.</span><span class="sxs-lookup"><span data-stu-id="67267-105">Uncompressed CAB file content is limited to 1 GB by default.</span></span> <span data-ttu-id="67267-106">Per aggirare questo limite, gli utenti devono usare il parametro **Force** dei cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="67267-106">To bypass this limit, users have to use the **Force** parameter of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="67267-107">Per garantire la sicurezza dei file della Guida scaricati da Internet, un file CAB della Guida aggiornabile può includere solo i tipi di file elencati di seguito.</span><span class="sxs-lookup"><span data-stu-id="67267-107">To assure the security of help files that are downloaded from the Internet, an Updatable Help CAB file can include only the file types listed below.</span></span> <span data-ttu-id="67267-108">Il cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) convalida tutti i file rispetto agli schemi degli argomenti della guida.</span><span class="sxs-lookup"><span data-stu-id="67267-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet validates all files against the help topic schemas.</span></span> <span data-ttu-id="67267-109">Se il cmdlet `Update-Help` rileva un file che non è valido o non è un tipo consentito, non installa il file non valido e interrompe l'installazione dei file dal file CAB nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="67267-109">If the `Update-Help` cmdlet encounters a file that is invalid or is not a permitted type, it does not install the invalid file and stops installing files from the CAB on the user's computer.</span></span>

- <span data-ttu-id="67267-110">Argomenti della Guida basati su XML per i cmdlet di.</span><span class="sxs-lookup"><span data-stu-id="67267-110">XML-based help topics for cmdlets.</span></span>

- <span data-ttu-id="67267-111">Argomenti della Guida basati su XML per gli script e le funzioni.</span><span class="sxs-lookup"><span data-stu-id="67267-111">XML-based help topics for scripts and functions.</span></span>

- <span data-ttu-id="67267-112">Argomenti della Guida basati su XML per i provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67267-112">XML-based help topics for Windows PowerShell providers.</span></span>

- <span data-ttu-id="67267-113">Argomenti della Guida basati su testo, ad esempio informazioni sugli argomenti.</span><span class="sxs-lookup"><span data-stu-id="67267-113">Text-based help topics, such as About topics.</span></span>

<span data-ttu-id="67267-114">[Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifica il contenuto dei CAB quando DECOMPRIME il CAB.</span><span class="sxs-lookup"><span data-stu-id="67267-114">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) verifies the CAB contents when it unpacks the CAB.</span></span> <span data-ttu-id="67267-115">Se `Update-Help` individua tipi di file non conformi in un file CAB della Guida aggiornabile, viene generato un errore di terminazione e l'operazione viene arrestata.</span><span class="sxs-lookup"><span data-stu-id="67267-115">If `Update-Help` finds non-compliant file types in an Updatable Help CAB file, it generates a terminating error and stops the operation.</span></span> <span data-ttu-id="67267-116">Non installa i file della guida dal file CAB, neanche quelli dei tipi di file conformi.</span><span class="sxs-lookup"><span data-stu-id="67267-116">It does not install any help files from the CAB, even those of compliant file types.</span></span>