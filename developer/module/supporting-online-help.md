---
title: Supporto per la Guida Online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082142"
---
# <a name="supporting-online-help"></a><span data-ttu-id="fb9c4-102">Supporto per la Guida in linea</span><span class="sxs-lookup"><span data-stu-id="fb9c4-102">Supporting Online Help</span></span>

<span data-ttu-id="fb9c4-103">A partire da Windows PowerShell 3.0, esistono due modi per supportare il `Get-Help` funzionalità Online per i comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="fb9c4-104">In questo argomento viene illustrato come implementare questa funzionalità per i tipi di comandi diverso.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="fb9c4-105">Informazioni sulla Guida Online</span><span class="sxs-lookup"><span data-stu-id="fb9c4-105">About Online Help</span></span>

<span data-ttu-id="fb9c4-106">Guida in linea è sempre stata una parte essenziale di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="fb9c4-107">Sebbene il `Get-Help` cmdlet consente di visualizzare gli argomenti della Guida al prompt dei comandi, molti utenti preferiscono l'esperienza di lettura online, tra cui codifica a colori, collegamenti ipertestuali e la condivisione delle idee in documenti basati su wiki e contenuti della Community.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="fb9c4-108">Ancora più importante, prima dell'avvento di Guida aggiornabile, la Guida in linea fornita la versione più aggiornata dei file della Guida.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="fb9c4-109">Con l'avvento di Guida aggiornabile in Windows PowerShell 3.0, la Guida in linea ha ancora un ruolo fondamentale.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="fb9c4-110">Oltre all'esperienza dell'utente flessibile Guida in linea vengono fornite informazioni per gli utenti che non hanno o non è possibile usare la Guida aggiornabile per scaricare gli argomenti della Guida.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="fb9c4-111">Come Get-Help-Online Works</span><span class="sxs-lookup"><span data-stu-id="fb9c4-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="fb9c4-112">Per consentire agli utenti di trovare gli argomenti della Guida in linea dei comandi, il `Get-Help` command include un parametro Online che consente di aprire la versione online dell'argomento della Guida per un comando nel browser Internet predefinito dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="fb9c4-113">Ad esempio, il comando seguente consente di aprire l'argomento della Guida in linea per il `Invoke-Command` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="fb9c4-114">Per implementare `Get-Help` -Online, il `Get-Help` cmdlet è simile per un identificatore URI (Uniform Resource) per l'argomento della Guida in linea di versione nei percorsi seguenti.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="fb9c4-115">Il primo collegamento nella sezione collegamenti correlati dell'argomento della Guida per il comando.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="fb9c4-116">L'argomento della Guida deve essere installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="fb9c4-117">Questa funzionalità è stata introdotta in Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="fb9c4-118">La proprietà HelpUri di qualsiasi comando.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-118">The HelpUri property of any command.</span></span> <span data-ttu-id="fb9c4-119">La proprietà helpuri venga applicato è accessibile anche quando l'argomento della Guida per il comando non è installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="fb9c4-120">Questa funzionalità è stata introdotta in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="fb9c4-121">`Get-Help` Cerca un URI nella prima voce nella sezione collegamenti correlati prima di ottenere il valore della proprietà helpuri venga applicato.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="fb9c4-122">Se il valore della proprietà non è corretto o è stato modificato, è possibile eseguirne l'override immettendo un valore diverso nel primo collegamento correlato.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="fb9c4-123">Tuttavia, il primo collegamento correlato funziona solo quando gli argomenti della Guida siano installati nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="fb9c4-124">Aggiunta di un URI per il primo collegamento correlato di un argomento della Guida in linea di comando</span><span class="sxs-lookup"><span data-stu-id="fb9c4-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="fb9c4-125">È possibile supportare `Get-Help` -Online per qualsiasi comando mediante l'aggiunta di un URI valido per la prima voce nella sezione collegamenti correlati dell'argomento della Guida basati su XML per il comando.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="fb9c4-126">Questa opzione è valida solo in argomenti della Guida basati su XML e funziona solo quando l'argomento della Guida è installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="fb9c4-127">Quando viene installato l'argomento della Guida e l'URI viene popolato, questo valore ha la precedenza il **HelpUri** proprietà del comando.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="fb9c4-128">Per informazioni su argomenti della Guida basati su XML per i comandi, vedere [Writing XML-Based gli argomenti della Guida per i comandi](../help/writing-xml-based-help-topics-for-commands.md).</span><span class="sxs-lookup"><span data-stu-id="fb9c4-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="fb9c4-129">Per supportare questa funzionalità, l'URI deve essere specificata nel `maml:uri` elemento sotto il primo `maml:relatedLinks/maml:navigationLink` elemento il `maml:relatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="fb9c4-130">Il codice XML seguente viene illustrata la posizione corretta dell'URI.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="fb9c4-131">La "versione Online:" testo nel `maml:linkText` elemento è una procedura consigliata, ma non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="fb9c4-132">Aggiunta della proprietà helpuri venga applicato a un comando</span><span class="sxs-lookup"><span data-stu-id="fb9c4-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="fb9c4-133">Questa sezione illustra come aggiungere la proprietà helpuri venga applicato ai comandi di tipi diversi.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="fb9c4-134">Aggiunta di una proprietà helpuri venga applicato a un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fb9c4-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="fb9c4-135">Per i cmdlet scritti in C#, aggiungere un' **HelpUri** attributo alla classe del Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="fb9c4-136">Il valore dell'attributo deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="fb9c4-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="fb9c4-137">Il codice seguente mostra l'attributo HelpUri del `Get-History` classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="fb9c4-138">Aggiunta di una proprietà helpuri venga applicato a una funzione avanzata</span><span class="sxs-lookup"><span data-stu-id="fb9c4-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="fb9c4-139">Per le funzioni avanzate, aggiungere un **HelpUri** proprietà per il **CmdletBinding** attributo.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="fb9c4-140">Il valore della proprietà deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="fb9c4-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="fb9c4-141">Il codice seguente mostra l'attributo HelpUri della funzione New-calendario</span><span class="sxs-lookup"><span data-stu-id="fb9c4-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="fb9c4-142">Aggiunta di un attributo HelpUri a un comando CIM</span><span class="sxs-lookup"><span data-stu-id="fb9c4-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="fb9c4-143">Per i comandi CIM, aggiungere un **HelpUri** attributo il **CmdletMetadata** elemento nel file CDXML.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="fb9c4-144">Il valore dell'attributo deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="fb9c4-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="fb9c4-145">Il codice seguente mostra l'attributo HelpUri del comando Start-Debug CIM</span><span class="sxs-lookup"><span data-stu-id="fb9c4-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="fb9c4-146">Aggiunta di un attributo HelpUri a un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="fb9c4-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="fb9c4-147">Per i flussi di lavoro che vengono scritti nel linguaggio di Windows PowerShell, aggiungere un **. ExternalHelp** comment (direttiva) al codice del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="fb9c4-148">Il valore della direttiva deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="fb9c4-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="fb9c4-149">La proprietà helpuri venga applicato non è supportata per flussi di lavoro basati su XAML in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="fb9c4-150">Il codice seguente illustra il. Direttiva ExternalHelp in un file del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="fb9c4-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```