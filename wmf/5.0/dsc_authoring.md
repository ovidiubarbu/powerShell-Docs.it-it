---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 1595a3e817fd711c35128f06927fd57df7a63fb8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218247"
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="b470d-102">Miglioramenti per la creazione di configurazioni con PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b470d-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="b470d-103">La creazione di configurazioni DSC in Windows PowerShell ISE è molto più semplice, grazie ai miglioramenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="b470d-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="b470d-104">È possibile elencare tutte le risorse DSC all'interno di un blocco **configuration** o **node** premendo **CTRL+BARRA SPAZIATRICE** in una riga vuota all'interno del blocco.</span><span class="sxs-lookup"><span data-stu-id="b470d-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="b470d-105">Completamento automatico per le proprietà della risorsa di tipo **enumeration**.</span><span class="sxs-lookup"><span data-stu-id="b470d-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="b470d-106">Completamento automatico per la proprietà **DependsOn** della risorsa DSC, in base alle altre istanze della risorsa nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="b470d-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="b470d-107">Completamento tramite TAB migliorato per i valori delle proprietà della risorsa.</span><span class="sxs-lookup"><span data-stu-id="b470d-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="b470d-108">**Nota:** è necessario disporre di una stringa vuota per i valori della proprietà della risorsa prima di poter usare CTRL+BARRA SPAZIATRICE per visualizzare l'elenco di opzioni.</span><span class="sxs-lookup"><span data-stu-id="b470d-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="b470d-109">Premendo **TAB** è possibile scorrere le opzioni.</span><span class="sxs-lookup"><span data-stu-id="b470d-109">Pressing **Tab** cycles through options.</span></span>
