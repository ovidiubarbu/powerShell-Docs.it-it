---
title: Come creare un file XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367320"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="d1c20-102">Come creare un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="d1c20-103">Negli argomenti di questa sezione viene illustrato come creare e popolare un file di informazioni della guida, comunemente noto come "file XML HelpInfo", per la funzionalità della Guida aggiornabile di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1c20-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="d1c20-104">Panoramica del file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="d1c20-105">Il file XML HelpInfo è la fonte principale di informazioni sulla guida aggiornabile per il modulo.</span><span class="sxs-lookup"><span data-stu-id="d1c20-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="d1c20-106">Include il percorso dei file della Guida per i moduli, le impostazioni cultura dell'interfaccia utente supportate e i numeri di versione utilizzati dalla guida aggiornabile per determinare se l'utente dispone dei file della guida più recenti.</span><span class="sxs-lookup"><span data-stu-id="d1c20-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="d1c20-107">Ogni modulo dispone di un solo file XML HelpInfo, anche se il modulo include più file della Guida per più impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d1c20-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="d1c20-108">L'autore del modulo Crea il file XML HelpInfo e lo inserisce nel percorso Internet specificato dalla chiave **HelpInfoUri** nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="d1c20-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="d1c20-109">Quando i file della guida del modulo vengono aggiornati e caricati, l'autore del modulo Aggiorna il file XML HelpInfo e sostituisce il file XML HelpInfo originale con la nuova versione.</span><span class="sxs-lookup"><span data-stu-id="d1c20-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="d1c20-110">È fondamentale che il file XML HelpInfo venga mantenuto con attenzione.</span><span class="sxs-lookup"><span data-stu-id="d1c20-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="d1c20-111">Se si caricano nuovi file, ma si dimentica di incrementare i numeri di versione, la guida aggiornabile non scaricherà i nuovi file nei computer degli utenti.</span><span class="sxs-lookup"><span data-stu-id="d1c20-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="d1c20-112">Se si aggiungono i file della Guida per una nuova lingua dell'interfaccia utente, ma non si aggiorna il file XML HelpInfo o lo si inserisce nella posizione corretta, la guida aggiornabile non scaricherà i nuovi file.</span><span class="sxs-lookup"><span data-stu-id="d1c20-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d1c20-113">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="d1c20-113">In this section</span></span>

<span data-ttu-id="d1c20-114">Questa sezione include gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="d1c20-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="d1c20-115">XML Schema HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="d1c20-116">File di esempio XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="d1c20-117">Come assegnare un nome a un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="d1c20-118">Come impostare i numeri di versione XML di HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d1c20-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="d1c20-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d1c20-119">See Also</span></span>

[<span data-ttu-id="d1c20-120">Supporto della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="d1c20-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)