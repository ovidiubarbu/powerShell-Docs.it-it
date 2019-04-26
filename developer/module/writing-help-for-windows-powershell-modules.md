---
title: Scrittura della Guida per i moduli di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082033"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="07907-102">Scrittura della Guida per i moduli di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07907-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="07907-103">I moduli di Windows PowerShell possono includere gli argomenti della Guida sul modulo e sui membri del modulo, ad esempio cmdlet, provider, funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="07907-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="07907-104">Il `Get-Help` cmdlet consente di visualizzare gli argomenti della Guida modulo nello stesso formato quando visualizza la Guida per altri elementi di Windows PowerShell, e gli utenti utilizzano standard `Get-Help` comandi per ottenere gli argomenti della Guida.</span><span class="sxs-lookup"><span data-stu-id="07907-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="07907-105">Questo documento viene illustrato il formato e il posizionamento corretto di argomenti della Guida di modulo e suggerisce le linee guida per il contenuto della Guida di modulo.</span><span class="sxs-lookup"><span data-stu-id="07907-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="07907-106">Tipi di modulo della Guida in linea</span><span class="sxs-lookup"><span data-stu-id="07907-106">Types of Module Help</span></span>

<span data-ttu-id="07907-107">Un modulo può includere i seguenti tipi di Guida in linea.</span><span class="sxs-lookup"><span data-stu-id="07907-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="07907-108">**Guida dei cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="07907-108">**Cmdlet Help**.</span></span> <span data-ttu-id="07907-109">Gli argomenti della Guida che descrivono i cmdlet in un modulo sono file XML che utilizzano il comando Guida in linea dello schema</span><span class="sxs-lookup"><span data-stu-id="07907-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="07907-110">**Guida del provider**.</span><span class="sxs-lookup"><span data-stu-id="07907-110">**Provider Help**.</span></span> <span data-ttu-id="07907-111">Gli argomenti della Guida che descrivono i provider in un modulo sono file XML che usano il provider consentono di schema.</span><span class="sxs-lookup"><span data-stu-id="07907-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="07907-112">**Funzione Help**.</span><span class="sxs-lookup"><span data-stu-id="07907-112">**Function Help**.</span></span> <span data-ttu-id="07907-113">Gli argomenti della Guida che descrivono le funzioni in un modulo può essere utile per i file XML che utilizzano il comando dello schema o gli argomenti della Guida basata sui commenti all'interno della funzione, o lo script o modulo di script</span><span class="sxs-lookup"><span data-stu-id="07907-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="07907-114">**Lo script Help**.</span><span class="sxs-lookup"><span data-stu-id="07907-114">**Script Help**.</span></span> <span data-ttu-id="07907-115">Gli argomenti della Guida che descrivono gli script in un modulo può essere utile per i file XML che utilizzano il comando dello schema o argomenti della Guida basati su commenti nello script o nel modulo di script.</span><span class="sxs-lookup"><span data-stu-id="07907-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="07907-116">**Concettuale ("About") della Guida**.</span><span class="sxs-lookup"><span data-stu-id="07907-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="07907-117">È possibile usare un concettuale ("about"), l'argomento della Guida per descrivere il modulo e i relativi membri e per illustrare come i membri possono essere usati insieme per eseguire attività.</span><span class="sxs-lookup"><span data-stu-id="07907-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="07907-118">Argomenti della Guida concettuale sono file di testo con codifica Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="07907-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="07907-119">Il nome del file è necessario usare il `about_<name>.help.txt` formato, ad esempio about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="07907-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="07907-120">Per impostazione predefinita, Windows PowerShell include oltre 100 di queste Guida informazioni su concetti di base e sono formattati come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="07907-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="07907-121">Posizionamento della Guida dei moduli</span><span class="sxs-lookup"><span data-stu-id="07907-121">Placement of Module Help</span></span>

<span data-ttu-id="07907-122">Il `Get-Help` cmdlet cerca i file di argomento della Guida di modulo in sottodirectory specifiche del linguaggio della directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="07907-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="07907-123">Ad esempio, il diagramma di struttura di directory seguente mostra la posizione degli argomenti della Guida per il modulo SampleModule.</span><span class="sxs-lookup"><span data-stu-id="07907-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="07907-124">Nell'esempio, il  *\<ModulePath >* segnaposto rappresenta uno dei percorsi nella `PSModulePath` variabile di ambiente, ad esempio home\Documents\Modules $, $pshome\Modules o un percorso personalizzato specificato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="07907-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="07907-125">Visualizzazione della Guida di modulo</span><span class="sxs-lookup"><span data-stu-id="07907-125">Getting Module Help</span></span>

<span data-ttu-id="07907-126">Quando un utente importa un modulo in una sessione, gli argomenti della Guida per il dato modulo vengono importati nella sessione con il modulo.</span><span class="sxs-lookup"><span data-stu-id="07907-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="07907-127">È possibile elencare i file di argomento della Guida nel valore della chiave FileList nel manifesto del modulo, ma gli argomenti della Guida non sono interessati dal `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07907-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="07907-128">È possibile fornire argomenti della Guida di modulo in lingue diverse.</span><span class="sxs-lookup"><span data-stu-id="07907-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="07907-129">Il `Get-Help` cmdlet Visualizza automaticamente gli argomenti della Guida di modulo nel linguaggio specificato per l'utente corrente nell'elemento di Regional and Language Options nel Pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="07907-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="07907-130">In Windows Vista e versioni successive di Windows, `Get-Help` Cerca argomenti della Guida nella sottodirectory specifica del linguaggio della directory del modulo in conformità con gli standard di fallback language stabilita per Windows.</span><span class="sxs-lookup"><span data-stu-id="07907-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="07907-131">A partire da Windows PowerShell 3.0, che esegue un `Get-Help` comando per un cmdlet o una funzione attiva l'importazione automatica del modulo.</span><span class="sxs-lookup"><span data-stu-id="07907-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="07907-132">Il `Get-Help` cmdlet consente di visualizzare immediatamente il contenuto degli argomenti della Guida nel modulo.</span><span class="sxs-lookup"><span data-stu-id="07907-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="07907-133">Se il modulo non contiene gli argomenti della Guida e non sono disponibili argomenti della Guida per i comandi del modulo nel computer dell'utente, `Get-Help` consente di visualizzare la Guida generata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="07907-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="07907-134">La Guida generata automaticamente include la sintassi dei comandi, parametri e tipi di input e output, ma non include le eventuali descrizioni.</span><span class="sxs-lookup"><span data-stu-id="07907-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="07907-135">La Guida generata automaticamente include testo che indirizza l'utente a provare a usare il `Update-Help` cmdlet per scaricare la Guida per il comando da Internet o da una condivisione file.</span><span class="sxs-lookup"><span data-stu-id="07907-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="07907-136">Consiglia di utilizzare anche il **Online** parametro del `Get-Help` per ottenere la versione online dell'argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="07907-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="07907-137">Supporto per la Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="07907-137">Supporting Updatable Help</span></span>

<span data-ttu-id="07907-138">Gli utenti di Windows PowerShell 3.0 e versioni successive di Windows PowerShell possono scaricare e installare file della Guida aggiornati per un modulo da Internet o da una condivisione file locale.</span><span class="sxs-lookup"><span data-stu-id="07907-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="07907-139">Il `Update-Help` e `Save-Help` cmdlet nascondono i dettagli di gestione da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="07907-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="07907-140">Agli utenti di eseguire la `Update-Help` cmdlet e quindi usare il `Get-Help` cmdlet per leggere i file della Guida più recenti per il modulo al prompt dei comandi Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07907-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="07907-141">Gli utenti non sono necessario riavviare Windows o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07907-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="07907-142">Gli utenti protetti da firewall e quelli senza accesso a Internet possono usare la Guida aggiornabile, nonché.</span><span class="sxs-lookup"><span data-stu-id="07907-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="07907-143">Gli amministratori con Internet accedere utilizzare le `Save-Help` cmdlet per scaricare e installare i file della Guida più recenti in una condivisione file.</span><span class="sxs-lookup"><span data-stu-id="07907-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="07907-144">Usano quindi gli utenti il **tracciato** parametro del `Update-Help` per ottenere i file della Guida più recenti dalla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="07907-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="07907-145">Gli autori di moduli possono includere i file della Guida nel modulo e usare la Guida aggiornabile per aggiornare i file della Guida, oppure omettere i file della Guida dal modulo e usare la Guida aggiornabile per installare e aggiornare.</span><span class="sxs-lookup"><span data-stu-id="07907-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="07907-146">Per altre informazioni sulla Guida aggiornabile, vedere [supporto della Guida aggiornabile](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="07907-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="07907-147">Supporto per la Guida in linea</span><span class="sxs-lookup"><span data-stu-id="07907-147">Supporting Online Help</span></span>

<span data-ttu-id="07907-148">Gli utenti che non è possibile o non si installano aggiornato i file nei propri computer spesso si basano sulla versione online degli argomenti della Guida di modulo della Guida.</span><span class="sxs-lookup"><span data-stu-id="07907-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="07907-149">Il **Online** parametro del `Get-Help` cmdlet apre la versione online di un cmdlet o un argomento della Guida funzione avanzata per l'utente nel browser Internet predefinito.</span><span class="sxs-lookup"><span data-stu-id="07907-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="07907-150">Il `Get-Help` cmdlet Usa il valore della **HelpUri** proprietà della funzione per trovare la versione online dell'argomento della Guida o cmdlet.</span><span class="sxs-lookup"><span data-stu-id="07907-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="07907-151">A partire da Windows PowerShell 3.0, si consente agli utenti di trovare la versione online degli argomenti della Guida cmdlet e funzioni che definisce l'attributo HelpUri nella classe del cmdlet o le **HelpUri** proprietà del **CmdletBinding** attributo.</span><span class="sxs-lookup"><span data-stu-id="07907-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="07907-152">Il valore dell'attributo è il valore della **HelpUri** proprietà del cmdlet o funzione.</span><span class="sxs-lookup"><span data-stu-id="07907-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="07907-153">Per altre informazioni, vedere [supporto della Guida Online](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="07907-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07907-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="07907-154">See Also</span></span>

[<span data-ttu-id="07907-155">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="07907-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="07907-156">Supporto per la Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="07907-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="07907-157">Supporto per la Guida Online</span><span class="sxs-lookup"><span data-stu-id="07907-157">Supporting Online Help</span></span>](./supporting-online-help.md)