---
title: Scrittura della Guida per i moduli di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360560"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="28564-102">Scrittura della Guida per i moduli di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="28564-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="28564-103">I moduli di Windows PowerShell possono includere argomenti della guida sul modulo e sui membri del modulo, ad esempio cmdlet, provider, funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="28564-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="28564-104">Il cmdlet `Get-Help` Visualizza gli argomenti della Guida relativi ai moduli nello stesso formato in cui viene visualizzata la guida per altri elementi di Windows PowerShell e gli utenti usano i comandi standard `Get-Help` per ottenere gli argomenti della guida.</span><span class="sxs-lookup"><span data-stu-id="28564-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="28564-105">Questo documento illustra il formato e la posizione corretta degli argomenti della guida sui moduli e suggerisce le linee guida per il contenuto della guida del modulo.</span><span class="sxs-lookup"><span data-stu-id="28564-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="28564-106">Tipi di guida del modulo</span><span class="sxs-lookup"><span data-stu-id="28564-106">Types of Module Help</span></span>

<span data-ttu-id="28564-107">Un modulo può includere i seguenti tipi di guida.</span><span class="sxs-lookup"><span data-stu-id="28564-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="28564-108">**Guida del cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="28564-108">**Cmdlet Help**.</span></span> <span data-ttu-id="28564-109">Gli argomenti della guida che descrivono i cmdlet in un modulo sono file XML che usano lo schema della guida del comando</span><span class="sxs-lookup"><span data-stu-id="28564-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="28564-110">**Guida del provider**.</span><span class="sxs-lookup"><span data-stu-id="28564-110">**Provider Help**.</span></span> <span data-ttu-id="28564-111">Gli argomenti della guida che descrivono i provider in un modulo sono file XML che utilizzano lo schema della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="28564-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="28564-112">**Guida alla funzione**.</span><span class="sxs-lookup"><span data-stu-id="28564-112">**Function Help**.</span></span> <span data-ttu-id="28564-113">Gli argomenti della guida che descrivono le funzioni in un modulo possono essere file XML che usano lo schema della guida del comando o gli argomenti della Guida basati su commenti all'interno della funzione oppure il modulo script o script</span><span class="sxs-lookup"><span data-stu-id="28564-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="28564-114">**Guida dello script**.</span><span class="sxs-lookup"><span data-stu-id="28564-114">**Script Help**.</span></span> <span data-ttu-id="28564-115">Gli argomenti della guida che descrivono gli script in un modulo possono essere file XML che usano gli argomenti della Guida relativi ai comandi o ai commenti del modulo script o script.</span><span class="sxs-lookup"><span data-stu-id="28564-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="28564-116">**Guida concettuale ("about")** .</span><span class="sxs-lookup"><span data-stu-id="28564-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="28564-117">È possibile utilizzare un argomento della Guida concettuale ("about") per descrivere il modulo e i relativi membri e spiegare in che modo i membri possono essere utilizzati insieme per eseguire le attività.</span><span class="sxs-lookup"><span data-stu-id="28564-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="28564-118">Gli argomenti della Guida concettuale sono file di testo con codifica Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="28564-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="28564-119">Il nome file deve usare il formato `about_<name>.help.txt`, ad esempio about_MyModule. Help. txt.</span><span class="sxs-lookup"><span data-stu-id="28564-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="28564-120">Per impostazione predefinita, Windows PowerShell include più di 100 di questi concetti concettuali sugli argomenti della guida e sono formattati come l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="28564-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="28564-121">Posizione della guida del modulo</span><span class="sxs-lookup"><span data-stu-id="28564-121">Placement of Module Help</span></span>

<span data-ttu-id="28564-122">Il cmdlet `Get-Help` cerca i file degli argomenti della guida del modulo in sottodirectory specifiche della lingua della directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="28564-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="28564-123">Il diagramma della struttura di directory seguente, ad esempio, Mostra il percorso degli argomenti della Guida per il modulo SampleModule.</span><span class="sxs-lookup"><span data-stu-id="28564-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="28564-124">Nell'esempio, il segnaposto *\<ModulePath >* rappresenta uno dei percorsi nella variabile di ambiente `PSModulePath`, ad esempio $Home \documents\modules, $PSHome \modules o un percorso personalizzato specificato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="28564-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="28564-125">Recupero della guida del modulo</span><span class="sxs-lookup"><span data-stu-id="28564-125">Getting Module Help</span></span>

<span data-ttu-id="28564-126">Quando un utente importa un modulo in una sessione, gli argomenti della Guida per il modulo vengono importati nella sessione insieme al modulo.</span><span class="sxs-lookup"><span data-stu-id="28564-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="28564-127">È possibile elencare i file di argomenti della guida nel valore della chiave FileList nel manifesto del modulo, ma gli argomenti della guida non sono interessati dal cmdlet `Export-ModuleMember`.</span><span class="sxs-lookup"><span data-stu-id="28564-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="28564-128">È possibile fornire argomenti della guida sui moduli in lingue diverse.</span><span class="sxs-lookup"><span data-stu-id="28564-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="28564-129">Il cmdlet `Get-Help` Visualizza automaticamente gli argomenti della guida sui moduli nella lingua specificata per l'utente corrente nell'elemento Opzioni internazionali e della lingua nel pannello di controllo.</span><span class="sxs-lookup"><span data-stu-id="28564-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="28564-130">In Windows Vista e nelle versioni successive di Windows, `Get-Help` cerca gli argomenti della Guida in sottodirectory specifiche della lingua della directory dei moduli in base agli standard di fallback della lingua stabiliti per Windows.</span><span class="sxs-lookup"><span data-stu-id="28564-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="28564-131">A partire da Windows PowerShell 3,0, l'esecuzione di un comando `Get-Help` per un cmdlet o una funzione attiva l'importazione automatica del modulo.</span><span class="sxs-lookup"><span data-stu-id="28564-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="28564-132">Il cmdlet `Get-Help` Visualizza immediatamente il contenuto degli argomenti della guida nel modulo.</span><span class="sxs-lookup"><span data-stu-id="28564-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="28564-133">Se il modulo non contiene argomenti della guida e non sono disponibili argomenti della Guida per i comandi nel modulo sul computer dell'utente, `Get-Help` Visualizza la guida generata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="28564-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="28564-134">La guida generata automaticamente include la sintassi, i parametri e i tipi di input e output del comando, ma non include alcuna descrizione.</span><span class="sxs-lookup"><span data-stu-id="28564-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="28564-135">La guida generata automaticamente include il testo che indirizza l'utente a provare a usare il cmdlet `Update-Help` per scaricare la guida per il comando da Internet o da una condivisione file.</span><span class="sxs-lookup"><span data-stu-id="28564-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="28564-136">Si consiglia inoltre di utilizzare il parametro **online** del cmdlet `Get-Help` per ottenere la versione online dell'argomento della guida.</span><span class="sxs-lookup"><span data-stu-id="28564-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="28564-137">Supporto per la Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="28564-137">Supporting Updatable Help</span></span>

<span data-ttu-id="28564-138">Gli utenti di Windows PowerShell 3,0 e versioni successive di Windows PowerShell possono scaricare e installare i file della Guida aggiornati per un modulo da Internet o da una condivisione file locale.</span><span class="sxs-lookup"><span data-stu-id="28564-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="28564-139">I cmdlet `Update-Help` e `Save-Help` nascondono i dettagli di gestione dall'utente.</span><span class="sxs-lookup"><span data-stu-id="28564-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="28564-140">Gli utenti eseguono il cmdlet `Update-Help` e quindi usano il cmdlet `Get-Help` per leggere i file della guida più recenti per il modulo al prompt dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28564-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="28564-141">Gli utenti non devono riavviare Windows o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28564-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="28564-142">Anche gli utenti protetti da firewall e quelli senza accesso a Internet possono utilizzare la guida aggiornabile.</span><span class="sxs-lookup"><span data-stu-id="28564-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="28564-143">Gli amministratori con accesso a Internet usano il cmdlet `Save-Help` per scaricare e installare i file della guida più recenti in una condivisione file.</span><span class="sxs-lookup"><span data-stu-id="28564-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="28564-144">Quindi, gli utenti usano il parametro **path** del cmdlet `Update-Help` per ottenere i file della guida più recenti dalla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="28564-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="28564-145">Gli autori di moduli possono includere i file della guida nel modulo e usare la guida aggiornabile per aggiornare i file della Guida oppure omettere i file della guida dal modulo e usare la guida aggiornabile per installare e per aggiornarli.</span><span class="sxs-lookup"><span data-stu-id="28564-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="28564-146">Per ulteriori informazioni sulla guida aggiornabile, vedere Supporto per la [Guida aggiornabile](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="28564-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="28564-147">Supporto per la Guida in linea</span><span class="sxs-lookup"><span data-stu-id="28564-147">Supporting Online Help</span></span>

<span data-ttu-id="28564-148">Gli utenti che non possono installare i file della Guida aggiornati nei propri computer spesso si basano sulla versione online degli argomenti della guida sui moduli.</span><span class="sxs-lookup"><span data-stu-id="28564-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="28564-149">Il parametro **online** del cmdlet `Get-Help` apre la versione online di un cmdlet o di un argomento della Guida per le funzioni avanzate per l'utente nel browser Internet predefinito.</span><span class="sxs-lookup"><span data-stu-id="28564-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="28564-150">Il cmdlet `Get-Help` usa il valore della proprietà **HelpUri** del cmdlet o della funzione per trovare la versione online dell'argomento della guida.</span><span class="sxs-lookup"><span data-stu-id="28564-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="28564-151">A partire da Windows PowerShell 3,0, è possibile aiutare gli utenti a trovare la versione online degli argomenti della Guida relativi ai cmdlet e alle funzioni definendo l'attributo HelpUri nella classe cmdlet o la proprietà **HelpUri** dell'attributo di **cmdlet** .</span><span class="sxs-lookup"><span data-stu-id="28564-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="28564-152">Il valore dell'attributo è il valore della proprietà **HelpUri** del cmdlet o della funzione.</span><span class="sxs-lookup"><span data-stu-id="28564-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="28564-153">Per ulteriori informazioni, vedere [supporto](./supporting-online-help.md)per la Guida in linea.</span><span class="sxs-lookup"><span data-stu-id="28564-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28564-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="28564-154">See Also</span></span>

[<span data-ttu-id="28564-155">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="28564-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="28564-156">Supporto della Guida aggiornabile</span><span class="sxs-lookup"><span data-stu-id="28564-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="28564-157">Supporto della Guida in linea</span><span class="sxs-lookup"><span data-stu-id="28564-157">Supporting Online Help</span></span>](./supporting-online-help.md)