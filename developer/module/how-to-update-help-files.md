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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082313"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="92311-102">Come aggiornare i file della Guida</span><span class="sxs-lookup"><span data-stu-id="92311-102">How to Update Help Files</span></span>

<span data-ttu-id="92311-103">In questo argomento viene illustrato come aggiornare i file della Guida per un modulo che supporta la Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="92311-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="92311-104">L'aggiornamento dei file della Guida</span><span class="sxs-lookup"><span data-stu-id="92311-104">Updating Help Files</span></span>

<span data-ttu-id="92311-105">Esistono molti motivi per aggiornare i file della Guida, ad esempio la correzione degli errori, per chiarire il concetto, rispondere alle domande frequenti, aggiungendo nuovi file o l'aggiunta di nuovi e migliori esempi.</span><span class="sxs-lookup"><span data-stu-id="92311-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="92311-106">Per aggiornare un file della Guida:</span><span class="sxs-lookup"><span data-stu-id="92311-106">To update a help file:</span></span>

1. <span data-ttu-id="92311-107">Modificare i file.</span><span class="sxs-lookup"><span data-stu-id="92311-107">Change the files.</span></span>

2. <span data-ttu-id="92311-108">Convertire i file in altre impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="92311-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="92311-109">Raccogliere tutti i file della Guida (nuove, modificati e invariati) per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="92311-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="92311-110">Convalidare i file rispetto allo schema XML.</span><span class="sxs-lookup"><span data-stu-id="92311-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="92311-111">Ricompilare i file CAB per ogni impostazione cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="92311-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="92311-112">Nel file XML HelpInfo, incrementare i numeri di versione del file CAB per ogni impostazione cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="92311-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="92311-113">Caricare i nuovi file CAB nel percorso specificato dal valore della **HelpContentUri** elemento nel file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="92311-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="92311-114">Sostituire i vecchi file CAB con i nuovi file CAB.</span><span class="sxs-lookup"><span data-stu-id="92311-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="92311-115">Caricare il file XML HelpInfo aggiornato nel percorso specificato per il **HelpInfoUri** chiave nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="92311-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="92311-116">Sostituire il file XML HelpInfo precedente con il nuovo file.</span><span class="sxs-lookup"><span data-stu-id="92311-116">Replace the older HelpInfo XML file with the new file.</span></span>