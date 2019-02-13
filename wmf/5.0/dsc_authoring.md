---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682939"
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="a7df0-102">Miglioramenti per la creazione di configurazioni con PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a7df0-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="a7df0-103">La creazione di configurazioni DSC in Windows PowerShell ISE è molto più semplice, grazie ai miglioramenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="a7df0-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="a7df0-104">È possibile elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.</span><span class="sxs-lookup"><span data-stu-id="a7df0-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="a7df0-105">Completamento automatico per le proprietà della risorsa di tipo **enumeration**.</span><span class="sxs-lookup"><span data-stu-id="a7df0-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="a7df0-106">Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="a7df0-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="a7df0-107">Completamento tramite TAB migliorato per i valori delle proprietà della risorsa.</span><span class="sxs-lookup"><span data-stu-id="a7df0-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="a7df0-108">**Nota:** è necessario disporre di una stringa vuota per i valori della proprietà della risorsa prima di poter usare CTRL+BARRA SPAZIATRICE per visualizzare l'elenco di opzioni.</span><span class="sxs-lookup"><span data-stu-id="a7df0-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="a7df0-109">Premendo **TAB** è possibile scorrere le opzioni.</span><span class="sxs-lookup"><span data-stu-id="a7df0-109">Pressing **Tab** cycles through options.</span></span>
