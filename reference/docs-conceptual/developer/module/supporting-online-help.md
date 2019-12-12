---
title: Supporto della guida online | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: 5c5707d1c533e0498c6794b60f4499e530e25813
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360660"
---
# <a name="supporting-online-help"></a><span data-ttu-id="cc510-102">Supporto per la Guida in linea</span><span class="sxs-lookup"><span data-stu-id="cc510-102">Supporting Online Help</span></span>

<span data-ttu-id="cc510-103">A partire da Windows PowerShell 3,0, esistono due modi per supportare la funzionalità `Get-Help` online per i comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc510-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="cc510-104">In questo argomento viene illustrato come implementare questa funzionalità per diversi tipi di comando.</span><span class="sxs-lookup"><span data-stu-id="cc510-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="cc510-105">Informazioni sulla Guida in linea</span><span class="sxs-lookup"><span data-stu-id="cc510-105">About Online Help</span></span>

<span data-ttu-id="cc510-106">La guida online è sempre stata una parte essenziale di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc510-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="cc510-107">Anche se il cmdlet `Get-Help` Visualizza gli argomenti della Guida al prompt dei comandi, molti utenti preferiscono l'esperienza di lettura online, inclusi la codifica dei colori, i collegamenti ipertestuali e la condivisione di idee nel contenuto della community e nei documenti basati su wiki.</span><span class="sxs-lookup"><span data-stu-id="cc510-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="cc510-108">Soprattutto, prima dell'avvento della Guida aggiornabile, la guida online forniva la versione più aggiornata dei file della guida.</span><span class="sxs-lookup"><span data-stu-id="cc510-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="cc510-109">Con l'avvento della Guida aggiornabile di Windows PowerShell 3,0, la guida online svolge ancora un ruolo fondamentale.</span><span class="sxs-lookup"><span data-stu-id="cc510-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="cc510-110">Oltre all'esperienza utente flessibile, la Guida in linea consente agli utenti che non hanno o non possono utilizzare la guida aggiornabile di scaricare gli argomenti della guida.</span><span class="sxs-lookup"><span data-stu-id="cc510-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="cc510-111">Come funziona get-help-online</span><span class="sxs-lookup"><span data-stu-id="cc510-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="cc510-112">Per consentire agli utenti di trovare gli argomenti della guida online per i comandi, il comando `Get-Help` dispone di un parametro online che apre la versione online dell'argomento della Guida per un comando nel browser Internet predefinito dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc510-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="cc510-113">Ad esempio, il comando seguente consente di aprire l'argomento della Guida in linea per il cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="cc510-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="cc510-114">Per implementare `Get-Help`-online, il cmdlet `Get-Help` Cerca un Uniform Resource Identifier (URI) per l'argomento della guida della versione online nei percorsi seguenti.</span><span class="sxs-lookup"><span data-stu-id="cc510-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="cc510-115">Il primo collegamento nella sezione collegamenti correlati dell'argomento della Guida per il comando.</span><span class="sxs-lookup"><span data-stu-id="cc510-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="cc510-116">L'argomento della guida deve essere installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc510-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="cc510-117">Questa funzionalità è stata introdotta in Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="cc510-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="cc510-118">Proprietà HelpUri di qualsiasi comando.</span><span class="sxs-lookup"><span data-stu-id="cc510-118">The HelpUri property of any command.</span></span> <span data-ttu-id="cc510-119">La proprietà HelpUri è accessibile anche quando l'argomento della Guida per il comando non è installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc510-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="cc510-120">Questa funzionalità è stata introdotta in Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="cc510-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="cc510-121">`Get-Help` Cerca un URI nella prima voce della sezione collegamenti correlati prima di ottenere il valore della proprietà HelpUri.</span><span class="sxs-lookup"><span data-stu-id="cc510-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="cc510-122">Se il valore della proprietà non è corretto o è stato modificato, è possibile eseguirne l'override immettendo un valore diverso nel primo collegamento correlato.</span><span class="sxs-lookup"><span data-stu-id="cc510-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="cc510-123">Tuttavia, il primo collegamento correlato funziona solo quando gli argomenti della guida vengono installati nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc510-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="cc510-124">Aggiunta di un URI al primo collegamento correlato di un argomento della guida del comando</span><span class="sxs-lookup"><span data-stu-id="cc510-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="cc510-125">È possibile supportare `Get-Help`-online per qualsiasi comando aggiungendo un URI valido alla prima voce nella sezione collegamenti correlati dell'argomento della guida basato su XML per il comando.</span><span class="sxs-lookup"><span data-stu-id="cc510-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="cc510-126">Questa opzione è valida solo negli argomenti della Guida basati su XML e funziona solo quando l'argomento della guida è installato nel computer dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc510-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="cc510-127">Quando l'argomento della guida è installato e l'URI viene popolato, questo valore ha la precedenza sulla proprietà **HelpUri** del comando.</span><span class="sxs-lookup"><span data-stu-id="cc510-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span>

<span data-ttu-id="cc510-128">Per supportare questa funzionalità, l'URI deve essere visualizzato nell'elemento `maml:uri` sotto il primo elemento `maml:relatedLinks/maml:navigationLink` nell'elemento `maml:relatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="cc510-128">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="cc510-129">Nel codice XML seguente viene illustrata la posizione corretta dell'URI.</span><span class="sxs-lookup"><span data-stu-id="cc510-129">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="cc510-130">Il testo "versione online:" nell'elemento `maml:linkText` è una procedura consigliata, ma non è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="cc510-130">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

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

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="cc510-131">Aggiunta della proprietà HelpUri a un comando</span><span class="sxs-lookup"><span data-stu-id="cc510-131">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="cc510-132">In questa sezione viene illustrato come aggiungere la proprietà HelpUri ai comandi di tipi diversi.</span><span class="sxs-lookup"><span data-stu-id="cc510-132">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="cc510-133">Aggiunta di una proprietà HelpUri a un cmdlet</span><span class="sxs-lookup"><span data-stu-id="cc510-133">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="cc510-134">Per i cmdlet scritti in C#, aggiungere un attributo **HelpUri** alla classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc510-134">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="cc510-135">Il valore dell'attributo deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="cc510-135">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="cc510-136">Il codice seguente illustra l'attributo HelpUri della classe del cmdlet `Get-History`.</span><span class="sxs-lookup"><span data-stu-id="cc510-136">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="cc510-137">Aggiunta di una proprietà HelpUri a una funzione avanzata</span><span class="sxs-lookup"><span data-stu-id="cc510-137">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="cc510-138">Per le funzioni avanzate, aggiungere una proprietà **HelpUri** all'attributo di **cmdlet** .</span><span class="sxs-lookup"><span data-stu-id="cc510-138">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="cc510-139">Il valore della proprietà deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="cc510-139">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="cc510-140">Il codice seguente illustra l'attributo HelpUri della funzione New-Calendar</span><span class="sxs-lookup"><span data-stu-id="cc510-140">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="cc510-141">Aggiunta di un attributo HelpUri a un comando CIM</span><span class="sxs-lookup"><span data-stu-id="cc510-141">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="cc510-142">Per i comandi CIM, aggiungere un attributo **HelpUri** all'elemento **CMDLETMETADATA** nel file CDXML.</span><span class="sxs-lookup"><span data-stu-id="cc510-142">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="cc510-143">Il valore dell'attributo deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="cc510-143">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="cc510-144">Il codice seguente illustra l'attributo HelpUri del comando Start-debug CIM</span><span class="sxs-lookup"><span data-stu-id="cc510-144">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="cc510-145">Aggiunta di un attributo HelpUri a un flusso di lavoro</span><span class="sxs-lookup"><span data-stu-id="cc510-145">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="cc510-146">Per i flussi di lavoro scritti nel linguaggio di Windows PowerShell, aggiungere un **. Direttiva ExternalHelp** Comment nel codice del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="cc510-146">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="cc510-147">Il valore della direttiva deve essere un URI che inizia con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="cc510-147">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="cc510-148">La proprietà HelpUri non è supportata per i flussi di lavoro basati su XAML in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc510-148">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="cc510-149">Nel codice seguente viene illustrato il. Direttiva ExternalHelp in un file del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="cc510-149">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```