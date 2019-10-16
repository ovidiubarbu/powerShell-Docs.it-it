---
title: Come aggiornare i file della Guida | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367140"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="6bfb0-102">Come aggiornare i file della Guida</span><span class="sxs-lookup"><span data-stu-id="6bfb0-102">How to Update Help Files</span></span>

<span data-ttu-id="6bfb0-103">In questo argomento viene illustrato come aggiornare i file della Guida per un modulo che supporta la guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="6bfb0-104">Aggiornamento dei file della Guida</span><span class="sxs-lookup"><span data-stu-id="6bfb0-104">Updating Help Files</span></span>

<span data-ttu-id="6bfb0-105">Esistono diversi motivi per aggiornare i file della guida, ad esempio correggere gli errori, chiarire un concetto, rispondere a una domanda frequente, aggiungere nuovi file o aggiungere nuovi esempi nuovi e migliori.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="6bfb0-106">Per aggiornare un file della guida:</span><span class="sxs-lookup"><span data-stu-id="6bfb0-106">To update a help file:</span></span>

1. <span data-ttu-id="6bfb0-107">Modificare i file.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-107">Change the files.</span></span>

2. <span data-ttu-id="6bfb0-108">Tradurre i file in altre impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="6bfb0-109">Raccogliere tutti i file della guida (nuovi, modificati e non modificati) per il modulo in ogni impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="6bfb0-110">Convalidare i file rispetto al XML Schema.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="6bfb0-111">Ricompilare i file CAB per ogni lingua dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="6bfb0-112">Nel file XML HelpInfo, incrementare i numeri di versione del file CAB per ogni lingua dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="6bfb0-113">Caricare i nuovi file CAB nel percorso specificato dal valore dell'elemento **HelpContentUri** nel file XML HELPINFO.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="6bfb0-114">Sostituire i file CAB meno recenti con i nuovi file CAB.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="6bfb0-115">Caricare il file XML HelpInfo aggiornato nel percorso specificato dalla chiave **HelpInfoUri** nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="6bfb0-116">Sostituire il file XML HelpInfo precedente con il nuovo file.</span><span class="sxs-lookup"><span data-stu-id="6bfb0-116">Replace the older HelpInfo XML file with the new file.</span></span>