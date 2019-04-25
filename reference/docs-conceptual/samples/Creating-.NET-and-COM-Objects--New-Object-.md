---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione di oggetti .NET e COM New Object
ms.assetid: 2057b113-efeb-465e-8b44-da2f20dbf603
ms.openlocfilehash: ef8215303aacd90536d3c2ae57bc3629e202f318
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086369"
---
# <a name="creating-net-and-com-objects-new-object"></a><span data-ttu-id="cf6d6-103">Creazione di oggetti .NET e COM (New-Object)</span><span class="sxs-lookup"><span data-stu-id="cf6d6-103">Creating .NET and COM Objects (New-Object)</span></span>

<span data-ttu-id="cf6d6-104">Sono disponibili componenti software con interfacce .NET Framework e COM che consentono di eseguire molte attività di amministrazione di sistema.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-104">There are software components with .NET Framework and COM interfaces that enable you to perform many system administration tasks.</span></span> <span data-ttu-id="cf6d6-105">Windows PowerShell consente di usare questi componenti, in modo da non essere limitati alle attività eseguibili con i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-105">Windows PowerShell lets you use these components, so you are not limited to the tasks that can be performed by using cmdlets.</span></span> <span data-ttu-id="cf6d6-106">Molti dei cmdlet nella versione iniziale di Windows PowerShell non funzionano su computer remoti.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-106">Many of the cmdlets in the initial release of Windows PowerShell do not work against remote computers.</span></span> <span data-ttu-id="cf6d6-107">Verrà illustrato come aggirare questa limitazione per la gestione dei registri eventi con la classe **System.Diagnostics.EventLog** di .NET Framework direttamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-107">We will demonstrate how to get around this limitation when managing event logs by using the .NET Framework **System.Diagnostics.EventLog** class directly from Windows PowerShell.</span></span>

## <a name="using-new-object-for-event-log-access"></a><span data-ttu-id="cf6d6-108">Uso di New-Object per l'accesso ai registri eventi</span><span class="sxs-lookup"><span data-stu-id="cf6d6-108">Using New-Object for Event Log Access</span></span>

<span data-ttu-id="cf6d6-109">La libreria di classi .NET Framework include una classe denominata **System.Diagnostics.EventLog** che può essere usata per gestire i registri eventi.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-109">The .NET Framework Class Library includes a class named **System.Diagnostics.EventLog** that can be used to manage event logs.</span></span> <span data-ttu-id="cf6d6-110">È possibile creare una nuova istanza della classe di .NET Framework tramite il cmdlet **New-Object** con il parametro **TypeName**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-110">You can create a new instance of a .NET Framework class by using the **New-Object** cmdlet with the **TypeName** parameter.</span></span> <span data-ttu-id="cf6d6-111">Il comando seguente, ad esempio, crea un riferimento a un registro eventi:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-111">For example, the following command creates an event log reference:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

<span data-ttu-id="cf6d6-112">Anche se il comando ha creato un'istanza della classe EventLog, l'istanza non include dati,</span><span class="sxs-lookup"><span data-stu-id="cf6d6-112">Although the command has created an instance of the EventLog class, the instance does not include any data.</span></span> <span data-ttu-id="cf6d6-113">perché non è stato specificato un registro eventi specifico.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-113">That is because we did not specify a particular event log.</span></span> <span data-ttu-id="cf6d6-114">Come ottenere un registro eventi reale?</span><span class="sxs-lookup"><span data-stu-id="cf6d6-114">How do you get a real event log?</span></span>

### <a name="using-constructors-with-new-object"></a><span data-ttu-id="cf6d6-115">Uso dei costruttori con New-Object</span><span class="sxs-lookup"><span data-stu-id="cf6d6-115">Using Constructors with New-Object</span></span>

<span data-ttu-id="cf6d6-116">Per fare riferimento a un registro eventi particolare, è necessario specificare il nome del registro.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-116">To refer to a specific event log, you need to specify the name of the log.</span></span> <span data-ttu-id="cf6d6-117">**New-Object** include il parametro **ArgumentList**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-117">**New-Object** has an **ArgumentList** parameter.</span></span> <span data-ttu-id="cf6d6-118">Gli argomenti passati come valori per questo parametro vengono usati da un metodo di avvio speciale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-118">The arguments you pass as values to this parameter are used by a special startup method of the object.</span></span> <span data-ttu-id="cf6d6-119">Il metodo è chiamato *costruttore* perché viene usato per costruire l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-119">The method is called a *constructor* because it is used to construct the object.</span></span> <span data-ttu-id="cf6d6-120">Ad esempio, per ottenere un riferimento al registro applicazioni, specificare la stringa 'Application' come argomento:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-120">For example, to get a reference to the Application log, you specify the string 'Application' as an argument:</span></span>

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> <span data-ttu-id="cf6d6-121">Dato che la maggior parte delle classi principali di .NET Framework è contenuta nello spazio dei nomi System, Windows PowerShell tenterà automaticamente di trovare le classi specificate nello spazio dei nomi System se non viene trovata una corrispondenza per il nome di tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-121">Since most of the .NET Framework core classes are contained in the System namespace, Windows PowerShell will automatically attempt to find classes you specify in the System namespace if it cannot find a match for the typename you specify.</span></span> <span data-ttu-id="cf6d6-122">Questo significa che è possibile specificare Diagnostics.EventLog invece di System.Diagnostics.EventLog.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-122">This means that you can specify Diagnostics.EventLog instead of System.Diagnostics.EventLog.</span></span>

### <a name="storing-objects-in-variables"></a><span data-ttu-id="cf6d6-123">Archiviazione di oggetti nelle variabili</span><span class="sxs-lookup"><span data-stu-id="cf6d6-123">Storing Objects in Variables</span></span>

<span data-ttu-id="cf6d6-124">Può essere utile archiviare un riferimento a un oggetto, in modo da poterlo usare nella shell corrente.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-124">You might want to store a reference to an object, so you can use it in the current shell.</span></span> <span data-ttu-id="cf6d6-125">Anche se Windows PowerShell consente di eseguire numerose operazioni con le pipeline, riducendo la necessità di ricorrere alle variabili, in alcuni casi l'archiviazione di riferimenti agli oggetti nelle variabili rende più semplice la modifica di tali oggetti.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-125">Although Windows PowerShell lets you do a lot of work with pipelines, lessening the need for variables, sometimes storing references to objects in variables makes it more convenient to manipulate those objects.</span></span>

<span data-ttu-id="cf6d6-126">Windows PowerShell consente di creare variabili, che sono fondamentalmente oggetti denominati.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-126">Windows PowerShell lets you create variables that are essentially named objects.</span></span> <span data-ttu-id="cf6d6-127">L'output di qualsiasi comando di Windows PowerShell valido può essere archiviato in una variabile.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-127">The output from any valid Windows PowerShell command can be stored in a variable.</span></span> <span data-ttu-id="cf6d6-128">I nomi di variabile iniziano sempre con il carattere $.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-128">Variable names always begin with $.</span></span> <span data-ttu-id="cf6d6-129">Per archiviare il riferimento al registro applicazioni in una variabile denominata $AppLog, digitare il nome della variabile, seguito da un segno di uguale e quindi digitare il comando usato per creare l'oggetto registro applicazioni:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-129">If you want to store the Application log reference in a variable named $AppLog, type the name of the variable, followed by an equal sign and then type the command used to create the Application log object:</span></span>

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

<span data-ttu-id="cf6d6-130">Se poi si digita $AppLog, si noterà che contiene il registro applicazioni:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-130">If you then type $AppLog, you can see that it contains the Application log:</span></span>

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a><span data-ttu-id="cf6d6-131">Accesso a un registro eventi remoto con New-Object</span><span class="sxs-lookup"><span data-stu-id="cf6d6-131">Accessing a Remote Event Log with New-Object</span></span>

<span data-ttu-id="cf6d6-132">I comandi usati nella sezione precedente sono destinati al computer locale. Questa operazione può essere eseguita con il cmdlet **Get-EventLog**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-132">The commands used in the preceding section target the local computer; the **Get-EventLog** cmdlet can do that.</span></span> <span data-ttu-id="cf6d6-133">Per accedere al registro applicazioni in un computer remoto, è necessario specificare sia il nome del registro che il nome (o indirizzo IP) di un computer come argomenti.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-133">To access the Application log on a remote computer, you must supply both the log name and a computer name (or IP address) as arguments.</span></span>

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

<span data-ttu-id="cf6d6-134">Dopo aver ottenuto un riferimento a un registro eventi archiviato nella variabile $RemoteAppLog, quali attività è possibile eseguire su di esso?</span><span class="sxs-lookup"><span data-stu-id="cf6d6-134">Now that we have a reference to an event log stored in the $RemoteAppLog variable, what tasks can we perform on it?</span></span>

### <a name="clearing-an-event-log-with-object-methods"></a><span data-ttu-id="cf6d6-135">Cancellazione di un registro eventi con i metodi degli oggetti</span><span class="sxs-lookup"><span data-stu-id="cf6d6-135">Clearing an Event Log with Object Methods</span></span>

<span data-ttu-id="cf6d6-136">Gli oggetti spesso includono metodi che possono essere chiamati per eseguire attività.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-136">Objects often have methods that can be called to perform tasks.</span></span> <span data-ttu-id="cf6d6-137">È possibile usare **Get-Member** per visualizzare i metodi associati a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-137">You can use **Get-Member** to display the methods associated with an object.</span></span> <span data-ttu-id="cf6d6-138">Il comando seguente e l'output selezionato mostrano alcuni dei metodi della classe EventLog:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-138">The following command and selected output show some the methods of the EventLog class:</span></span>

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

<span data-ttu-id="cf6d6-139">Il metodo **Clear ()** può essere usato per cancellare il registro eventi.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-139">The **Clear()** method can be used to clear the event log.</span></span> <span data-ttu-id="cf6d6-140">Quando si chiama un metodo, è necessario far seguire sempre il nome del metodo dalle parentesi, anche se il metodo non richiede argomenti.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-140">When calling a method, you must always follow the method name by parentheses, even if the method does not require arguments.</span></span> <span data-ttu-id="cf6d6-141">In questo modo Windows PowerShell può distinguere tra il metodo e una proprietà potenziale con lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-141">This lets Windows PowerShell distinguish between the method and a potential property with the same name.</span></span> <span data-ttu-id="cf6d6-142">Digitare il comando seguente per chiamare il metodo **Clear**:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-142">Type the following to call the **Clear** method:</span></span>

```
PS> $RemoteAppLog.Clear()
```

<span data-ttu-id="cf6d6-143">Digitare il comando seguente per visualizzare il log:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-143">Type the following to display the log.</span></span> <span data-ttu-id="cf6d6-144">Il risultato indica che il registro eventi è stato cancellato e ora ha 0 voci invece di 262:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-144">You will see that the event log was cleared, and now has 0 entries instead of 262:</span></span>

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a><span data-ttu-id="cf6d6-145">Creazione di oggetti COM con New-Object</span><span class="sxs-lookup"><span data-stu-id="cf6d6-145">Creating COM Objects with New-Object</span></span>
<span data-ttu-id="cf6d6-146">È possibile usare **New-Object** per lavorare con componenti COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="cf6d6-146">You can use **New-Object** to work with Component Object Model (COM) components.</span></span> <span data-ttu-id="cf6d6-147">I componenti includono varie librerie incluse in Windows Script Host (WSH) e applicazioni ActiveX come Internet Explorer installate nella maggior parte dei sistemi.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-147">Components range from the various libraries included with Windows Script Host (WSH) to ActiveX applications such as Internet Explorer that are installed on most systems.</span></span>

<span data-ttu-id="cf6d6-148">**New-Object** usa Runtime Callable Wrapper di .NET Framework per creare oggetti COM, quindi esistono le stesse limitazioni valide per .NET Framework per la chiamata di oggetti COM.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-148">**New-Object** uses .NET Framework Runtime-Callable Wrappers to create COM objects, so it has the same limitations that .NET Framework does when calling COM objects.</span></span> <span data-ttu-id="cf6d6-149">Per creare un oggetto COM, è necessario specificare il parametro **ComObject** con l'identificatore programmatico o *ProgId* della classe COM da usare.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-149">To create a COM object, you need to specify the **ComObject** parameter with the Programmatic Identifier or *ProgId* of the COM class you want to use.</span></span> <span data-ttu-id="cf6d6-150">Una descrizione completa delle limitazioni per l'uso di COM e di come determinare i ProgId disponibili in un sistema esula dagli scopi di questo manuale dell'utente, ma la maggior parte degli oggetti noti da ambienti come WSH può essere usata all'interno di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-150">A complete discussion of the limitations of COM use and determining what ProgIds are available on a system is beyond the scope of this user's guide, but most well-known objects from environments such as WSH can be used within Windows PowerShell.</span></span>

<span data-ttu-id="cf6d6-151">È possibile creare gli oggetti WSH specificando questi ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary** e **Scripting.FileSystemObject**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-151">You can create the WSH objects by specifying these progids: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary**, and **Scripting.FileSystemObject**.</span></span> <span data-ttu-id="cf6d6-152">I comandi seguenti creano questi oggetti:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-152">The following commands create these objects:</span></span>

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

<span data-ttu-id="cf6d6-153">Anche se la maggior parte delle funzionalità di queste classi viene resa disponibile in altri modi in Windows PowerShell, alcune attività, come la creazione di collegamenti, sono ancora più semplici da eseguire usando le classi WSH.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-153">Although most of the functionality of these classes is made available in other ways in Windows PowerShell, a few tasks such as shortcut creation are still easier to do using the WSH classes.</span></span>

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a><span data-ttu-id="cf6d6-154">Creazione di un collegamento sul desktop con WScript.Shell</span><span class="sxs-lookup"><span data-stu-id="cf6d6-154">Creating a Desktop Shortcut with WScript.Shell</span></span>

<span data-ttu-id="cf6d6-155">Un'attività che può essere eseguita rapidamente con un oggetto COM è la creazione di un collegamento.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-155">One task that can be performed quickly with a COM object is creating a shortcut.</span></span> <span data-ttu-id="cf6d6-156">Si supponga di voler creare un collegamento sul desktop per la home directory di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-156">Suppose you want to create a shortcut on your desktop that links to the home folder for Windows PowerShell.</span></span> <span data-ttu-id="cf6d6-157">È prima di tutto necessario creare un riferimento a **Wscript.Shell**, che verrà archiviato in una variabile denominata **$WshShell**:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-157">You first need to create a reference to **WScript.Shell**, which we will store in a variable named **$WshShell**:</span></span>

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

<span data-ttu-id="cf6d6-158">Get-Member funziona con oggetti COM, quindi è possibile visualizzare i membri dell'oggetto digitando:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-158">Get-Member works with COM objects, so you can explore the members of the object by typing:</span></span>

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

<span data-ttu-id="cf6d6-159">**Get-Member** include un parametro facoltativo **InputObject** utilizzabile al posto dell'invio tramite pipe per fornire l'input a **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-159">**Get-Member** has an optional **InputObject** parameter you can use instead of piping to provide input to **Get-Member**.</span></span> <span data-ttu-id="cf6d6-160">Si potrebbe ottenere lo stesso output di cui sopra usando il comando **Get-Member -InputObject $WshShell**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-160">You would get the same output as shown above if you instead used the command **Get-Member -InputObject $WshShell**.</span></span> <span data-ttu-id="cf6d6-161">Se si usa **InputObject**, il relativo argomento viene gestito come singolo elemento.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-161">If you use **InputObject**, it treats its argument as a single item.</span></span> <span data-ttu-id="cf6d6-162">Questo significa che in presenza di più oggetti in una variabile, **Get-Member** li gestisce come una matrice di oggetti.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-162">This means that if you have several objects in a variable, **Get-Member** treats them as an array of objects.</span></span> <span data-ttu-id="cf6d6-163">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-163">For example:</span></span>

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

<span data-ttu-id="cf6d6-164">Il metodo **WScript.Shell CreateShortcut** accetta un solo argomento, ovvero il percorso del file di collegamento da creare.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-164">The **WScript.Shell CreateShortcut** method accepts a single argument, the path to the shortcut file to create.</span></span> <span data-ttu-id="cf6d6-165">È possibile digitare il percorso completo per il desktop, ma esiste un modo più semplice.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-165">We could type in the full path to the desktop, but there is an easier way.</span></span> <span data-ttu-id="cf6d6-166">Il desktop in genere è rappresentato da una cartella denominata Desktop all'interno della home directory dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-166">The desktop is normally represented by a folder named Desktop inside the home folder of the current user.</span></span> <span data-ttu-id="cf6d6-167">Windows PowerShell include una variabile **$Home** che contiene il percorso di questa cartella.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-167">Windows PowerShell has a variable **$Home** that contains the path to this folder.</span></span> <span data-ttu-id="cf6d6-168">È possibile specificare il percorso per la home directory usando questa variabile e quindi aggiungere il nome della cartella Desktop e il nome per il collegamento da creare digitando:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-168">We can specify the path to the home folder by using this variable, and then add the name of the Desktop folder and the name for the shortcut to create by typing:</span></span>

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

<span data-ttu-id="cf6d6-169">Quando si usa un elemento che sembra un nome di variabile tra virgolette doppie, Windows PowerShell tenta la sostituzione di un valore corrispondente.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-169">When you use something that looks like a variable name inside double-quotes, Windows PowerShell tries to substitute a matching value.</span></span> <span data-ttu-id="cf6d6-170">Se si usano virgolette singole, Windows PowerShell non tenta di sostituire il valore della variabile.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-170">If you use single-quotes, Windows PowerShell does not try to substitute the variable value.</span></span> <span data-ttu-id="cf6d6-171">Ad esempio, provare a digitare i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-171">For example, try typing the following commands:</span></span>

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

<span data-ttu-id="cf6d6-172">Ora esiste una variabile denominata **$lnk** che contiene un riferimento al nuovo collegamento.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-172">We now have a variable named **$lnk** that contains a new shortcut reference.</span></span> <span data-ttu-id="cf6d6-173">Per visualizzarne tutti i membri, è possibile inviarla tramite pipe a **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-173">If you want to see its members, you can pipe it to **Get-Member**.</span></span> <span data-ttu-id="cf6d6-174">L'output seguente mostra i membri che è necessario usare per completare la creazione del collegamento:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-174">The output below shows the members we need to use to finish creating our shortcut:</span></span>

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

<span data-ttu-id="cf6d6-175">È necessario specificare **TargetPath**, ovvero la cartella dell'applicazione per Windows PowerShell e quindi salvare il collegamento **$lnk** chiamando il metodo **Save**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-175">We need to specify the **TargetPath**, which is the application folder for Windows PowerShell, and then save the shortcut **$lnk** by calling the **Save** method.</span></span> <span data-ttu-id="cf6d6-176">Il percorso della cartella dell'applicazione Windows PowerShell è archiviato nella variabile **$PSHome**, quindi è possibile eseguire questa operazione digitando:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-176">The Windows PowerShell application folder path is stored in the variable **$PSHome**, so we can do this by typing:</span></span>

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a><span data-ttu-id="cf6d6-177">Uso di Internet Explorer da Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="cf6d6-177">Using Internet Explorer from Windows PowerShell</span></span>

<span data-ttu-id="cf6d6-178">Molte applicazioni, compresa la famiglia di applicazioni Microsoft Office e Internet Explorer, possono essere automatizzate tramite COM.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-178">Many applications (including the Microsoft Office family of applications and Internet Explorer) can be automated by using COM.</span></span> <span data-ttu-id="cf6d6-179">Internet Explorer dimostra alcune delle tecniche tipiche e dei problemi correlati all'uso delle applicazioni basate su COM.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-179">Internet Explorer illustrates some of the typical techniques and issues involved in working with COM-based applications.</span></span>

<span data-ttu-id="cf6d6-180">Per creare un'istanza di Internet Explorer, è necessario specificare il ProgId di Internet Explorer, ovvero **InternetExplorer.Application**:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-180">You create an Internet Explorer instance by specifying the Internet Explorer ProgId, **InternetExplorer.Application**:</span></span>

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

<span data-ttu-id="cf6d6-181">Questo comando avvia Internet Explorer, ma non lo rende visibile.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-181">This command starts Internet Explorer, but does not make it visible.</span></span> <span data-ttu-id="cf6d6-182">Se si digita Get-Process, si noterà che è in esecuzione un processo denominato iexplore.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-182">If you type Get-Process, you can see that a process named iexplore is running.</span></span> <span data-ttu-id="cf6d6-183">Infatti, se si esce da Windows PowerShell, l'esecuzione del processo continuerà.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-183">In fact, if you exit Windows PowerShell, the process will continue to run.</span></span> <span data-ttu-id="cf6d6-184">È necessario riavviare il computer o usare uno strumento come Gestione attività per terminare il processo iexplore.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-184">You must reboot the computer or use a tool like Task Manager to end the iexplore process.</span></span>

> [!NOTE]
> <span data-ttu-id="cf6d6-185">Gli oggetti COM avviati come processo separato, comunemente noti come *eseguibili ActiveX*, potrebbero visualizzare o meno una finestra dell'interfaccia utente all'avvio.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-185">COM objects that start as separate processes, commonly called *ActiveX executables*, may or may not display a user interface window when they start up.</span></span> <span data-ttu-id="cf6d6-186">Se creano una finestra ma non la rendono visibile, come Internet Explorer, lo stato attivo passa in genere al desktop di Windows ed è necessario rendere visibile la finestra per poter interagire con essa.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-186">If they create a window but do not make it visible, like Internet Explorer, the focus will generally move to the Windows desktop and you must make the window visible to interact with it.</span></span>

<span data-ttu-id="cf6d6-187">È possibile digitare **$ie | Get-Member** per visualizzare le proprietà e i metodi per Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-187">By typing **$ie | Get-Member**, you can view properties and methods for Internet Explorer.</span></span> <span data-ttu-id="cf6d6-188">Per visualizzare la finestra di Internet Explorer, impostare la proprietà Visible su $true digitando:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-188">To see the Internet Explorer window, set the Visible property to $true by typing:</span></span>

```powershell
$ie.Visible = $true
```

<span data-ttu-id="cf6d6-189">È quindi possibile passare a un indirizzo Web specifico tramite il metodo Navigate:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-189">You can then navigate to a specific Web address by using the Navigate method:</span></span>

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

<span data-ttu-id="cf6d6-190">È possibile recuperare contenuto di testo dalla pagina Web usando altri membri del modello a oggetti di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-190">Using other members of the Internet Explorer object model, it is possible to retrieve text content from the Web page.</span></span> <span data-ttu-id="cf6d6-191">Il comando seguente consente di visualizzare il testo HTML nel corpo della pagina Web corrente:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-191">The following command will display the HTML text in the body of the current Web page:</span></span>

```powershell
$ie.Document.Body.InnerText
```

<span data-ttu-id="cf6d6-192">Per chiudere Internet Explorer da PowerShell, chiamare il metodo Quit():</span><span class="sxs-lookup"><span data-stu-id="cf6d6-192">To close Internet Explorer from within PowerShell, call its Quit() method:</span></span>

```powershell
$ie.Quit()
```

<span data-ttu-id="cf6d6-193">Verrà così forzata la chiusura.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-193">This will force it to close.</span></span> <span data-ttu-id="cf6d6-194">La variabile $ie non contiene più un riferimento valido anche se risulta ancora essere un oggetto COM.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-194">The $ie variable no longer contains a valid reference even though it still appears to be a COM object.</span></span> <span data-ttu-id="cf6d6-195">Se si tenta di usarla, si otterrà un errore di automazione:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-195">If you attempt to use it, you will get an automation error:</span></span>

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

<span data-ttu-id="cf6d6-196">È possibile rimuovere il riferimento rimanente con un comando come $ie = $null oppure rimuovere completamente la variabile digitando:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-196">You can either remove the remaining reference with a command like $ie = $null, or completely remove the variable by typing:</span></span>

```powershell
Remove-Variable ie
```

> [!NOTE]
> <span data-ttu-id="cf6d6-197">Non esiste uno standard comune che stabilisce se gli eseguibili ActiveX devono essere interrotti o continuare l'esecuzione quando si rimuove un riferimento a uno di essi.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-197">There is no common standard for whether ActiveX executables exit or continue to run when you remove a reference to one.</span></span> <span data-ttu-id="cf6d6-198">L'applicazione può essere o meno chiusa a seconda delle circostanze, ad esempio se l'applicazione è visibile, se al suo interno è in esecuzione un documento modificato e persino se Windows PowerShell è ancora in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-198">Depending on circumstances such as whether the application is visible, whether an edited document is running in it, and even whether Windows PowerShell is still running, the application may or may not exit.</span></span> <span data-ttu-id="cf6d6-199">Per questo motivo, è consigliabile testare il comportamento di terminazione per ogni eseguibile ActiveX da usare in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-199">For this reason, you should test termination behavior for each ActiveX executable you want to use in Windows PowerShell.</span></span>

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a><span data-ttu-id="cf6d6-200">Ottenere avvisi sugli oggetti COM con wrapping di .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf6d6-200">Getting Warnings About .NET Framework-Wrapped COM Objects</span></span>

<span data-ttu-id="cf6d6-201">In alcuni casi, un oggetto COM potrebbe disporre di un *Runtime Callable Wrapper* (RCW) di .NET Framework associato e questo verrà usato da **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-201">In some cases, a COM object might have an associated .NET Framework *Runtime-Callable Wrapper* or RCW, and this will be used by **New-Object**.</span></span> <span data-ttu-id="cf6d6-202">Dato che il comportamento dell'RCW potrebbe essere diverso da quello del normale oggetto COM, **New-Object** include un parametro **Strict** per avvisare in caso di accesso a un RCW.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-202">Since the behavior of the RCW may be different from the behavior of the normal COM object, **New-Object** has a **Strict** parameter to warn you about RCW access.</span></span> <span data-ttu-id="cf6d6-203">Se si specifica il parametro **Strict** e poi si crea un oggetto COM che usa un RCW, viene visualizzato un messaggio di avviso:</span><span class="sxs-lookup"><span data-stu-id="cf6d6-203">If you specify the **Strict** parameter and then create a COM object that uses an RCW, you get a warning message:</span></span>

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

<span data-ttu-id="cf6d6-204">Anche se l'oggetto viene comunque creato, viene segnalato che non si tratta di un oggetto COM standard.</span><span class="sxs-lookup"><span data-stu-id="cf6d6-204">Although the object is still created, you are warned that it is not a standard COM object.</span></span>