---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Cmdlet di catalogo
ms.openlocfilehash: ec5fc866fe27a894b23b93d3ea46ad9c0cba288e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057638"
---
# <a name="catalog-cmdlets"></a><span data-ttu-id="b8c69-103">Cmdlet di catalogo</span><span class="sxs-lookup"><span data-stu-id="b8c69-103">Catalog Cmdlets</span></span>

<span data-ttu-id="b8c69-104">Sono stati aggiunti due nuovi cmdlet nel modulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) per generare e convalidare i file di catalogo di Windows.</span><span class="sxs-lookup"><span data-stu-id="b8c69-104">We have added two new cmdlets in [Microsoft.Powershell.Secuity](https://technet.microsoft.com/library/hh847877.aspx) module to generate and validate windows catalog files.</span></span>

## <a name="new-filecatalog"></a><span data-ttu-id="b8c69-105">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b8c69-105">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="b8c69-106">`New-FileCatalog` crea un file di catalogo Windows per set di cartelle e file.</span><span class="sxs-lookup"><span data-stu-id="b8c69-106">`New-FileCatalog` creates a windows catalog file for set of folders and files.</span></span> <span data-ttu-id="b8c69-107">Un file di catalogo contiene gli hash per tutti i file nei percorsi specificati.</span><span class="sxs-lookup"><span data-stu-id="b8c69-107">A catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="b8c69-108">Gli utenti possono distribuire il set di cartelle con il corrispondente file di catalogo che rappresenta le cartelle.</span><span class="sxs-lookup"><span data-stu-id="b8c69-108">Users can distribute the set of folders along with corresponding the catalog file that represents those folders.</span></span> <span data-ttu-id="b8c69-109">Un file di catalogo può essere usato dal destinatario del contenuto per convalidare le modifiche apportate alle cartelle dopo la creazione del catalogo.</span><span class="sxs-lookup"><span data-stu-id="b8c69-109">A catalog file can be used by the recipient of content to validate whether any changes were made to the folders after the catalog was created.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
<span data-ttu-id="b8c69-110">Il catalogo della creazione dei file viene supportato nella versione 1 e 2.</span><span class="sxs-lookup"><span data-stu-id="b8c69-110">We support creating catalog version 1 and 2.</span></span> <span data-ttu-id="b8c69-111">La versione 1 usa l'algoritmo di hash SHA1 per creare hash di file; la versione 2 usa SHA256.</span><span class="sxs-lookup"><span data-stu-id="b8c69-111">Version 1 uses SHA1 hashing algorithm to create file hashes and version 2 uses SHA256.</span></span> <span data-ttu-id="b8c69-112">La versione 2 del catalogo non è supportata in *Windows Server 2008 R2* e in *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="b8c69-112">Catalog version 2 is not supported on *Windows Server 2008 R2* and *Windows 7*.</span></span> <span data-ttu-id="b8c69-113">È consigliabile usare la versione 2 del catalogo se si usano le piattaforme *Windows 8*, *Windows Server 2012* e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b8c69-113">It is recommended to use catalog version 2 if using platforms *Windows 8*, *Windows Server 2012* and above.</span></span>

<span data-ttu-id="b8c69-114">Per usare questo comando in un modulo esistente, specificare le variabili CatalogFilePath e Path corrispondenti al percorso del manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="b8c69-114">To use this command on an existing module, specify the CatalogFilePath and Path variables to match the location of the module manifest.</span></span> <span data-ttu-id="b8c69-115">Nell'esempio seguente il manifesto del modulo è in C:\Programmi\Windows PowerShell\Moduli\Pester.</span><span class="sxs-lookup"><span data-stu-id="b8c69-115">In the example below, the module manifest is in C:\Program Files\Windows PowerShell\Modules\Pester.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="b8c69-116">Questa operazione crea il file di catalogo.</span><span class="sxs-lookup"><span data-stu-id="b8c69-116">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="b8c69-117">Per verificare l'integrità di un file di catalogo (Pester.cat nell'esempio precedente), è necessario che sia firmato con il cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).</span><span class="sxs-lookup"><span data-stu-id="b8c69-117">To verify the integrity of a catalog file (Pester.cat in above exmaple) it should be signed using the [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) cmdlet.</span></span>


## <a name="test-filecatalog"></a><span data-ttu-id="b8c69-118">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b8c69-118">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="b8c69-119">`Test-FileCatalog` convalida il catalogo che rappresenta un set di cartelle.</span><span class="sxs-lookup"><span data-stu-id="b8c69-119">`Test-FileCatalog` validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="b8c69-120">Questo cmdlet consente di confrontare gli hash di tutti i file e i relativi percorsi trovati nel file di catalogo con quelli salvati su disco.</span><span class="sxs-lookup"><span data-stu-id="b8c69-120">This cmdlet compares the hashes of all files and their relative paths found in the catalog file with ones saved to disk.</span></span> <span data-ttu-id="b8c69-121">Se rileva eventuali mancate corrispondenze tra i percorsi e gli hash di file restituisce lo stato `ValidationFailed`.</span><span class="sxs-lookup"><span data-stu-id="b8c69-121">If it detects any mismatch between file hashes and paths it returns a status of `ValidationFailed`.</span></span>
<span data-ttu-id="b8c69-122">L'utente può recuperare tutte queste informazioni usando il parametro `Detailed`.</span><span class="sxs-lookup"><span data-stu-id="b8c69-122">Users can retrieve all this information using the `Detailed` switch.</span></span> <span data-ttu-id="b8c69-123">Lo stato di firma del catalogo viene visualizzato come campo `Signature` e ciò equivale a chiamare il cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) sul file di catalogo.</span><span class="sxs-lookup"><span data-stu-id="b8c69-123">The signing status of the catalog is displayed as the `Signature` field, which is same as calling the [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet on the catalog file.</span></span>
<span data-ttu-id="b8c69-124">Gli utenti possono anche ignorare alcuni file durante la convalida usando il parametro `FilesToSkip`.</span><span class="sxs-lookup"><span data-stu-id="b8c69-124">Users can also skip any file during validation by using the `FilesToSkip` parameter.</span></span>
