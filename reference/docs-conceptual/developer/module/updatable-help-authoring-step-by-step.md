---
title: 'Creazione di una guida aggiornabile: procedura dettagliata | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366990"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="b8242-102">Creazione della Guida aggiornabile: istruzioni dettagliate</span><span class="sxs-lookup"><span data-stu-id="b8242-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="b8242-103">In questo documento sono elencati i passaggi del processo di creazione della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="b8242-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="b8242-104">Creazione della Guida aggiornabile: procedura dettagliata</span><span class="sxs-lookup"><span data-stu-id="b8242-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="b8242-105">La guida aggiornabile è progettata per gli utenti finali, ma offre anche vantaggi significativi agli autori dei moduli e ai writer di supporto, inclusa la possibilità di aggiungere contenuto, correggere errori, distribuire più impostazioni cultura dell'interfaccia utente e rispondere a richieste e commenti degli utenti, molto dopo il il modulo è stato spedito.</span><span class="sxs-lookup"><span data-stu-id="b8242-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="b8242-106">In questo argomento viene illustrato come creare un pacchetto e caricare i file della Guida in modo che gli utenti possano scaricarli e installarli usando i cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="b8242-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="b8242-107">Nei passaggi seguenti viene fornita una panoramica del processo di supporto della Guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="b8242-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="b8242-108">Passaggio 1: trovare un sito Internet per i file della Guida</span><span class="sxs-lookup"><span data-stu-id="b8242-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="b8242-109">Il primo passaggio nella creazione della Guida aggiornabile è trovare un percorso Internet per i file della guida del modulo.</span><span class="sxs-lookup"><span data-stu-id="b8242-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="b8242-110">In realtà, è possibile usare due posizioni diverse.</span><span class="sxs-lookup"><span data-stu-id="b8242-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="b8242-111">È possibile salvare il file di informazioni della guida del modulo (HelpInfo XML, descritto di seguito) in un percorso Internet e i file CAB del contenuto della Guida in un altro percorso Internet.</span><span class="sxs-lookup"><span data-stu-id="b8242-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="b8242-112">Tutti i file CAB del contenuto della Guida per un modulo devono trovarsi nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="b8242-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="b8242-113">È possibile inserire i file CAB del contenuto della Guida per moduli diversi nello stesso percorso.</span><span class="sxs-lookup"><span data-stu-id="b8242-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="b8242-114">Passaggio 2: aggiungere una chiave HelpInfoURI al manifesto del modulo</span><span class="sxs-lookup"><span data-stu-id="b8242-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="b8242-115">Aggiungere una chiave **HelpInfoURI** al manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="b8242-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="b8242-116">Il valore della chiave è il Uniform Resource Identifier (URI) del percorso del file di informazioni XML HelpInfo per il modulo.</span><span class="sxs-lookup"><span data-stu-id="b8242-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="b8242-117">Per la sicurezza, l'indirizzo deve iniziare con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="b8242-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="b8242-118">L'URI deve specificare un percorso Internet, ma non deve includere il nome del file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="b8242-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="b8242-119">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b8242-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="b8242-120">Passaggio 3: creare un file XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="b8242-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="b8242-121">Il file di informazioni XML HelpInfo contiene l'URI del percorso Internet dei file della guida e i numeri di versione dei file della guida più recenti per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente supportate.</span><span class="sxs-lookup"><span data-stu-id="b8242-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="b8242-122">Ogni modulo di Windows PowerShell include un file XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="b8242-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="b8242-123">Quando si aggiornano i file della guida, si modifica o si sostituisce il file XML HelpInfo. non è possibile aggiungerne un altro.</span><span class="sxs-lookup"><span data-stu-id="b8242-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="b8242-124">Per ulteriori informazioni, vedere [come creare un file XML HELPINFO](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="b8242-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="b8242-125">Passaggio 4: firmare i file della Guida</span><span class="sxs-lookup"><span data-stu-id="b8242-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="b8242-126">Le firme digitali non sono necessarie, ma sono consigliate per le procedure consigliate ogni volta che si condividono i file.</span><span class="sxs-lookup"><span data-stu-id="b8242-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="b8242-127">Passaggio 5: creare file CAB</span><span class="sxs-lookup"><span data-stu-id="b8242-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="b8242-128">Usare uno strumento che crea file CAB (con estensione cab), ad esempio MakeCab. exe, per creare un. File CAB contenente i file della Guida per il modulo.</span><span class="sxs-lookup"><span data-stu-id="b8242-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="b8242-129">Creare un file CAB separato per i file della Guida in ognuna delle impostazioni cultura dell'interfaccia utente supportate.</span><span class="sxs-lookup"><span data-stu-id="b8242-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="b8242-130">Per ulteriori informazioni, vedere [come preparare i file CAB della Guida aggiornabile](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="b8242-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="b8242-131">Passaggio 6: caricare i file</span><span class="sxs-lookup"><span data-stu-id="b8242-131">Step 6: Upload your files</span></span>

<span data-ttu-id="b8242-132">Per pubblicare file della Guida nuovi o aggiornati, caricare i file CAB nel percorso Internet specificato dall'elemento **HelpContentUri** nel file XML HELPINFO.</span><span class="sxs-lookup"><span data-stu-id="b8242-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="b8242-133">Caricare quindi il file XML HelpInfo nel percorso Internet specificato dal valore della chiave **HelpInfoUri** nel manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="b8242-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
