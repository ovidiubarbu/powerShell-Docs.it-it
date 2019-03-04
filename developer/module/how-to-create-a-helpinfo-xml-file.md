---
title: Come creare un File XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853267"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="d0f27-102">Come creare un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="d0f27-103">Gli argomenti in questa sezione illustra come creare e popolare un file di informazioni della Guida, comunemente noto come un "file XML HelpInfo," per la funzionalità Guida aggiornabile di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0f27-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="d0f27-104">Panoramica del File XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="d0f27-105">Il file XML HelpInfo è la fonte principale di informazioni sulla Guida aggiornabile per il modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f27-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="d0f27-106">Include il percorso dei file della Guida per i moduli, le impostazioni cultura dell'interfaccia utente supportate e i numeri di versione utilizzato per determinare se l'utente ha i file della Guida più recente della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="d0f27-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="d0f27-107">Ogni modulo ha solo un file XML HelpInfo, anche se il modulo include più file della Guida per più impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d0f27-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="d0f27-108">Autore del modulo Crea il file XML HelpInfo e lo inserisce nel percorso specificato da Internet i **HelpInfoUri** chiave nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f27-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="d0f27-109">Quando i file della Guida dei moduli sono aggiornati e caricati, l'autore del modulo Aggiorna il file XML HelpInfo e sostituisce il file XML HelpInfo originale con la nuova versione.</span><span class="sxs-lookup"><span data-stu-id="d0f27-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="d0f27-110">È fondamentale che il file XML HelpInfo venga mantenuto con attenzione.</span><span class="sxs-lookup"><span data-stu-id="d0f27-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="d0f27-111">Se si carica nuovo file, ma dimentica di incrementare i numeri di versione, la Guida aggiornabile non verranno scaricati i nuovi file sui computer degli utenti.</span><span class="sxs-lookup"><span data-stu-id="d0f27-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="d0f27-112">Se si aggiungono i file della Guida per impostazioni cultura dell'interfaccia utente nuova, ma non aggiornare il file XML HelpInfo o inserirlo nella posizione corretta, la Guida aggiornabile è possibile che non verranno scaricati i nuovi file.</span><span class="sxs-lookup"><span data-stu-id="d0f27-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d0f27-113">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="d0f27-113">In this section</span></span>

<span data-ttu-id="d0f27-114">Questa sezione include gli argomenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="d0f27-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="d0f27-115">Schema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="d0f27-116">File di esempio XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="d0f27-117">Come assegnare un nome di un File XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="d0f27-118">Come impostare i numeri di versione XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f27-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="d0f27-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d0f27-119">See Also</span></span>

[<span data-ttu-id="d0f27-120">Supporto per la Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="d0f27-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)