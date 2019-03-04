---
title: 'Creazione della Guida aggiornabile: Step-by-Step | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860317"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="d0f91-102">Creazione della Guida aggiornabile: istruzioni dettagliate</span><span class="sxs-lookup"><span data-stu-id="d0f91-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="d0f91-103">Questo documento Elenca i passaggi del processo di creazione della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="d0f91-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="d0f91-104">Creazione di una Guida aggiornabile: istruzioni dettagliate</span><span class="sxs-lookup"><span data-stu-id="d0f91-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="d0f91-105">La Guida aggiornabile è progettata per gli utenti finali, ma fornisce inoltre una serie di vantaggi significativi per gli autori di moduli e gli autori della Guida in linea, inclusa la possibilità di aggiungere contenuto, correggere gli errori, offrono più impostazioni cultura dell'interfaccia utente e rispondono ai commenti degli utenti e le richieste, tempo dopo il modulo è stato spedito.</span><span class="sxs-lookup"><span data-stu-id="d0f91-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="d0f91-106">Questo argomento viene illustrato come è creare un pacchetto e Guida di caricamento file in modo che gli utenti possono scaricarli e installarli usando il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d0f91-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="d0f91-107">I passaggi seguenti offrono una panoramica del processo di supporto della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="d0f91-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="d0f91-108">Passaggio 1: Trovare un sito Internet per i file della Guida</span><span class="sxs-lookup"><span data-stu-id="d0f91-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="d0f91-109">Il primo passaggio nella creazione di una Guida aggiornabile è trovare un percorso Internet per i file della Guida del modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="d0f91-110">In realtà, è possibile usare due posizioni diverse.</span><span class="sxs-lookup"><span data-stu-id="d0f91-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="d0f91-111">È possibile mantenere i file di informazioni del modulo della Guida (HelpInfo XML - descritto di seguito) in una posizione di Internet e i file CAB del contenuto della Guida in un altro percorso Internet.</span><span class="sxs-lookup"><span data-stu-id="d0f91-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="d0f91-112">Tutti i file della Guida contenuti CAB un modulo devono essere nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="d0f91-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="d0f91-113">È possibile inserire i file CAB del contenuto della Guida per moduli diversi nello stesso percorso.</span><span class="sxs-lookup"><span data-stu-id="d0f91-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="d0f91-114">Passaggio 2: Aggiungere una chiave HelpInfoURI per il manifesto del modulo</span><span class="sxs-lookup"><span data-stu-id="d0f91-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="d0f91-115">Aggiungere un **HelpInfoURI** chiave per il manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="d0f91-116">Il valore della chiave è l'identificatore URI (Uniform Resource) della posizione del file di informazioni XML HelpInfo per il modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="d0f91-117">Per la sicurezza, l'indirizzo deve iniziare con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="d0f91-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="d0f91-118">L'URI deve specificare un percorso Internet, ma non deve includere il nome del file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="d0f91-119">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d0f91-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="d0f91-120">Passaggio 3: Creare un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="d0f91-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="d0f91-121">Il file di informazioni XML HelpInfo contiene l'URI del percorso Internet i file della Guida e i numeri di versione dei file della Guida più recenti per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente supportato.</span><span class="sxs-lookup"><span data-stu-id="d0f91-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="d0f91-122">Ogni modulo Windows PowerShell ha un unico file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="d0f91-123">Quando si aggiornano i file della Guida, si modifica o sostituire il file XML HelpInfo; non si aggiunge un altro.</span><span class="sxs-lookup"><span data-stu-id="d0f91-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="d0f91-124">Per altre informazioni, vedere [come creare un File XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="d0f91-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="d0f91-125">Passaggio 4: Firmare i file della Guida</span><span class="sxs-lookup"><span data-stu-id="d0f91-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="d0f91-126">Non sono necessarie le firme digitali, ma ogni volta che si stanno condividendo file sono una raccomandazione di procedure consigliate.</span><span class="sxs-lookup"><span data-stu-id="d0f91-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="d0f91-127">Passaggio 5: Creare i file CAB</span><span class="sxs-lookup"><span data-stu-id="d0f91-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="d0f91-128">Usare uno strumento che consente di creare file cabinet (CAB), ad esempio MakeCab.exe, per creare una. File CAB che contiene i file della Guida per il modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="d0f91-129">Creare un file CAB per i file della Guida in ognuna delle impostazioni cultura dell'interfaccia utente supportato.</span><span class="sxs-lookup"><span data-stu-id="d0f91-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="d0f91-130">Per altre informazioni, vedere [come preparare aggiornabile aiutare i file CAB](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="d0f91-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="d0f91-131">Passaggio 6: Caricamento dei file</span><span class="sxs-lookup"><span data-stu-id="d0f91-131">Step 6: Upload your files</span></span>

<span data-ttu-id="d0f91-132">Per pubblicare i file della Guida nuovi o aggiornati, caricare i file CAB al percorso specificato da Internet i **HelpContentUri** elemento nel file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="d0f91-133">Quindi, caricare il file XML HelpInfo per il percorso Internet specificato dal valore della **HelpInfoUri** chiave nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="d0f91-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
