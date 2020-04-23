---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxFileLine DSC per Linux
ms.openlocfilehash: 2e94bab318b5db65df88d268a88585079bab89bf
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953218"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="32f8c-103">Risorsa nxFileLine DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="32f8c-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="32f8c-104">La risorsa **nxFileLine** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le righe in un file di configurazione in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="32f8c-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="32f8c-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="32f8c-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="32f8c-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="32f8c-106">Properties</span></span>

|<span data-ttu-id="32f8c-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="32f8c-107">Property</span></span> |<span data-ttu-id="32f8c-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="32f8c-108">Description</span></span> |
|---|---|
|<span data-ttu-id="32f8c-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="32f8c-109">FilePath</span></span> |<span data-ttu-id="32f8c-110">Percorso completo del file in cui gestire le righe nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="32f8c-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="32f8c-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="32f8c-111">ContainsLine</span></span> |<span data-ttu-id="32f8c-112">Riga di cui specificare l'esistenza nel file.</span><span class="sxs-lookup"><span data-stu-id="32f8c-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="32f8c-113">Questa riga verrà aggiunta al file, se non è presente.</span><span class="sxs-lookup"><span data-stu-id="32f8c-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="32f8c-114">**ContainsLine** è una proprietà obbligatoria, ma può essere impostata su una stringa vuota (`ContainsLine = ""`) se non è necessaria.</span><span class="sxs-lookup"><span data-stu-id="32f8c-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="32f8c-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="32f8c-115">DoesNotContainPattern</span></span> |<span data-ttu-id="32f8c-116">Modello di espressione regolare per le righe che non devono essere presenti nel file.</span><span class="sxs-lookup"><span data-stu-id="32f8c-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="32f8c-117">Tutte le righe presenti nel file che corrispondono a questa espressione regolare verranno rimosse.</span><span class="sxs-lookup"><span data-stu-id="32f8c-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="32f8c-118">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="32f8c-118">Common properties</span></span>

|<span data-ttu-id="32f8c-119">Proprietà</span><span class="sxs-lookup"><span data-stu-id="32f8c-119">Property</span></span> |<span data-ttu-id="32f8c-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="32f8c-120">Description</span></span> |
|---|---|
|<span data-ttu-id="32f8c-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="32f8c-121">DependsOn</span></span> |<span data-ttu-id="32f8c-122">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="32f8c-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="32f8c-123">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="32f8c-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="32f8c-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="32f8c-124">Example</span></span>

<span data-ttu-id="32f8c-125">Questo esempio illustra l'uso della risorsa **nxFileLine** per configurare il file `/etc/sudoers`, specificando che l'utente: monuser è configurato per non richiedere TTY.</span><span class="sxs-lookup"><span data-stu-id="32f8c-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```