---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Elenco di controllo per la creazione di risorse
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076583"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="280cb-103">Elenco di controllo per la creazione di risorse</span><span class="sxs-lookup"><span data-stu-id="280cb-103">Resource authoring checklist</span></span>

<span data-ttu-id="280cb-104">Questo elenco di controllo è un elenco di procedure consigliate durante la creazione di una nuova risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="280cb-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="280cb-105">Il modulo della risorsa contiene i file psd1 e schema.mof per ogni risorsa.</span><span class="sxs-lookup"><span data-stu-id="280cb-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="280cb-106">Verificare che la risorsa abbia una struttura corretta e contenga tutti i file necessari.</span><span class="sxs-lookup"><span data-stu-id="280cb-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="280cb-107">Ogni modulo di risorsa deve contenere un file con estensione psd1 e per tutte le risorse non composite deve essere disponibile un file schema.mof.</span><span class="sxs-lookup"><span data-stu-id="280cb-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="280cb-108">Le risorse senza schema non verranno elencate da `Get-DscResource` e gli utenti non saranno in grado di usare IntelliSense durante la scrittura di codice in base a tali moduli in ISE.</span><span class="sxs-lookup"><span data-stu-id="280cb-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="280cb-109">La struttura di directory per la risorsa xRemoteFile, che fa parte del [modulo della risorsa xPSDesiredStateConfiguration](https://github.com/PowerShell/xPSDesiredStateConfiguration), potrebbe avere questo aspetto:</span><span class="sxs-lookup"><span data-stu-id="280cb-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="280cb-110">La risorsa e lo schema sono corretti</span><span class="sxs-lookup"><span data-stu-id="280cb-110">Resource and schema are correct</span></span>

<span data-ttu-id="280cb-111">Verificare il file dello schema della risorsa (\*. schema.mof).</span><span class="sxs-lookup"><span data-stu-id="280cb-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="280cb-112">È possibile usare [Progettazione risorse DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) per sviluppare e testare lo schema.</span><span class="sxs-lookup"><span data-stu-id="280cb-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="280cb-113">Verificare che:</span><span class="sxs-lookup"><span data-stu-id="280cb-113">Make sure that:</span></span>

- <span data-ttu-id="280cb-114">I tipi di proprietà siano corretti (ad esempio, non usare il tipo String per proprietà che accettano valori numerici, ma usare invece UInt32 o altri tipi numerici)</span><span class="sxs-lookup"><span data-stu-id="280cb-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="280cb-115">Gli attributi delle proprietà siano specificati correttamente, ad esempio [key], [required], [write], [read]</span><span class="sxs-lookup"><span data-stu-id="280cb-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="280cb-116">Almeno un parametro dello schema deve essere contrassegnato come [key]</span><span class="sxs-lookup"><span data-stu-id="280cb-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="280cb-117">La proprietà [read] non può coesistere con [required], [key] o [write]</span><span class="sxs-lookup"><span data-stu-id="280cb-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="280cb-118">Se vengono specificati più qualificatori ad eccezione di [read], [key] ha la precedenza</span><span class="sxs-lookup"><span data-stu-id="280cb-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="280cb-119">Se vengono specificati [write] e [required], [required] ha la precedenza</span><span class="sxs-lookup"><span data-stu-id="280cb-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="280cb-120">Il qualificatore ValueMap è specificato dove appropriato. Esempio:</span><span class="sxs-lookup"><span data-stu-id="280cb-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="280cb-121">Il nome descrittivo è specificato ed è conforme alle convenzioni di denominazione DSC</span><span class="sxs-lookup"><span data-stu-id="280cb-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="280cb-122">Esempio: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="280cb-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="280cb-123">Ogni campo ha una descrizione significativa.</span><span class="sxs-lookup"><span data-stu-id="280cb-123">Every field has meaningful description.</span></span> <span data-ttu-id="280cb-124">L'archivio GitHub di PowerShell include esempi utili, ad esempio [.schema.mof per xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="280cb-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="280cb-125">È inoltre consigliabile usare i cmdlet **Test-xDscResource** e **Test-xDscSchema** da [Progettazione risorse DSC](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) per la verifica automatica della risorsa e dello schema:</span><span class="sxs-lookup"><span data-stu-id="280cb-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="280cb-126">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="280cb-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="280cb-127">La risorsa viene caricata senza errori</span><span class="sxs-lookup"><span data-stu-id="280cb-127">Resource loads without errors</span></span>

<span data-ttu-id="280cb-128">Controllare se il modulo della risorse può essere caricato correttamente.</span><span class="sxs-lookup"><span data-stu-id="280cb-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="280cb-129">È possibile farlo manualmente, eseguendo `Import-Module <resource_module> -force` e verificando che non si siano verificati errori oppure creando un'automazione dei test.</span><span class="sxs-lookup"><span data-stu-id="280cb-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="280cb-130">In quest'ultimo caso, è possibile usare questa struttura nel test case:</span><span class="sxs-lookup"><span data-stu-id="280cb-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="280cb-131">La risorsa è idempotente in caso positivo</span><span class="sxs-lookup"><span data-stu-id="280cb-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="280cb-132">Una delle caratteristiche fondamentali delle risorse DSC è l'idempotenza.</span><span class="sxs-lookup"><span data-stu-id="280cb-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="280cb-133">Ciò significa che l'applicazione di una configurazione DSC che include più volte la risorsa specifica darà sempre lo stesso risultato.</span><span class="sxs-lookup"><span data-stu-id="280cb-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="280cb-134">Ad esempio, se si crea una configurazione che contiene la risorsa File seguente:</span><span class="sxs-lookup"><span data-stu-id="280cb-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="280cb-135">Dopo la prima applicazione, il file test.txt dovrebbe comparire nella cartella `C:\test`.</span><span class="sxs-lookup"><span data-stu-id="280cb-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="280cb-136">Le esecuzioni successive della stessa configurazione, tuttavia, non dovrebbero modificare lo stato del computer (ad esempio, non dovrebbe essere creata alcuna copia del file `test.txt`).</span><span class="sxs-lookup"><span data-stu-id="280cb-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="280cb-137">Per assicurarsi che una risorsa sia idempotente, è possibile chiamare ripetutamente `Set-TargetResource` quando si esegue un test diretto della risorsa oppure chiamare più volte `Start-DscConfiguration` quando si esegue un test end-to-end.</span><span class="sxs-lookup"><span data-stu-id="280cb-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="280cb-138">Il risultato sarà lo stesso dopo ogni esecuzione.</span><span class="sxs-lookup"><span data-stu-id="280cb-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="280cb-139">Scenario di modifica dell'utente test</span><span class="sxs-lookup"><span data-stu-id="280cb-139">Test user modification scenario</span></span>

<span data-ttu-id="280cb-140">È possibile verificare se `Set-TargetResource` e `Test-TargetResource` funzionano correttamente modificando lo stato del computer e quindi eseguendo nuovamente DSC.</span><span class="sxs-lookup"><span data-stu-id="280cb-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="280cb-141">Ecco i passaggi necessari per eseguire questo test:</span><span class="sxs-lookup"><span data-stu-id="280cb-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="280cb-142">Iniziare con la risorsa che non si trova nello stato desiderato</span><span class="sxs-lookup"><span data-stu-id="280cb-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="280cb-143">Eseguire la configurazione della risorsa</span><span class="sxs-lookup"><span data-stu-id="280cb-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="280cb-144">Verificare `Test-DscConfiguration` restituisce true</span><span class="sxs-lookup"><span data-stu-id="280cb-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="280cb-145">Modificare lo stato dell'elemento configurato</span><span class="sxs-lookup"><span data-stu-id="280cb-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="280cb-146">Verificare `Test-DscConfiguration` restituisce false</span><span class="sxs-lookup"><span data-stu-id="280cb-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="280cb-147">Ecco un esempio più concreto con la risorsa Registro di sistema:</span><span class="sxs-lookup"><span data-stu-id="280cb-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="280cb-148">Iniziare con una chiave del Registro di sistema che non si trova nello stato desiderato</span><span class="sxs-lookup"><span data-stu-id="280cb-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="280cb-149">Eseguire `Start-DscConfiguration` con una configurazione per mettere la risorsa nello stato desiderato e verificare che il test venga superato.</span><span class="sxs-lookup"><span data-stu-id="280cb-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="280cb-150">Eseguire `Test-DscConfiguration` e verificare che restituisca true</span><span class="sxs-lookup"><span data-stu-id="280cb-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="280cb-151">Modificare il valore della chiave in modo che non si trovi più nello stato desiderato</span><span class="sxs-lookup"><span data-stu-id="280cb-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="280cb-152">Eseguire `Test-DscConfiguration` e verificare che restituisca false</span><span class="sxs-lookup"><span data-stu-id="280cb-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="280cb-153">La funzionalità `Get-TargetResource` è stata verificata con `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="280cb-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="280cb-154">`Get-TargetResource` dovrebbe restituire i dettagli dello stato corrente della risorsa.</span><span class="sxs-lookup"><span data-stu-id="280cb-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="280cb-155">Assicurarsi di testarlo chiamando `Get-DscConfiguration` dopo aver applicato la configurazione e verificando che l'output rispecchi correttamente lo stato corrente del computer.</span><span class="sxs-lookup"><span data-stu-id="280cb-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="280cb-156">È importante eseguire il test separatamente, poiché eventuali problemi in questa area non verranno visualizzati durante la chiamata di `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="280cb-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="280cb-157">Chiamare direttamente le funzioni **Get/Set/Test-TargetResource**</span><span class="sxs-lookup"><span data-stu-id="280cb-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="280cb-158">Assicurarsi di testare le funzioni **Get/Set/Test-TargetResource** implementate nella risorsa chiamandole direttamente e verificando che funzionino come previsto.</span><span class="sxs-lookup"><span data-stu-id="280cb-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="280cb-159">Eseguire un test end-to-end tramite **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="280cb-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="280cb-160">Testare le funzioni **Get/Set/Test-TargetResource** tramite chiamata diretta è importante, ma in questo modo non verranno individuati tutti i problemi.</span><span class="sxs-lookup"><span data-stu-id="280cb-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="280cb-161">È consigliabile concentrare una parte significativa delle attività di test sull'uso di `Start-DscConfiguration` o del server di pull.</span><span class="sxs-lookup"><span data-stu-id="280cb-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="280cb-162">Questo è in effetti il modo in cui gli utenti useranno la risorsa, quindi non sottovalutare l'importanza di questo tipo di test.</span><span class="sxs-lookup"><span data-stu-id="280cb-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="280cb-163">Possibili tipi di problemi:</span><span class="sxs-lookup"><span data-stu-id="280cb-163">Possible types of issues:</span></span>

- <span data-ttu-id="280cb-164">Possibili comportamenti diversi delle credenziali e/o della sessione perché l'agente DSC viene eseguito come servizio.</span><span class="sxs-lookup"><span data-stu-id="280cb-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="280cb-165">Assicurarsi di sottoporre qualsiasi funzionalità a test end-to-end.</span><span class="sxs-lookup"><span data-stu-id="280cb-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="280cb-166">Gli errori restituiti da `Start-DscConfiguration` potrebbero essere diversi da quelli visualizzati quando si chiama la funzione `Set-TargetResource` direttamente.</span><span class="sxs-lookup"><span data-stu-id="280cb-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="280cb-167">Testare la compatibilità su tutte le piattaforme supportate da DSC</span><span class="sxs-lookup"><span data-stu-id="280cb-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="280cb-168">La risorsa dovrebbero funzionare in tutte le piattaforme supportate da DSC (Windows Server 2008 R2 e versioni successive).</span><span class="sxs-lookup"><span data-stu-id="280cb-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="280cb-169">Installare la versione più recente di WMF (Windows Management Framework) nel sistema operativo per ottenere la versione più recente di DSC.</span><span class="sxs-lookup"><span data-stu-id="280cb-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="280cb-170">Se la risorsa non funziona in alcune di queste piattaforme in base alla sua struttura di progettazione, verrà restituito un messaggio di errore specifico.</span><span class="sxs-lookup"><span data-stu-id="280cb-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="280cb-171">Assicurarsi anche che la risorsa controlli che i cmdlet chiamati siano presenti nel computer specifico.</span><span class="sxs-lookup"><span data-stu-id="280cb-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="280cb-172">In Windows Server 2012 sono stati aggiunti numerosi cmdlet nuovi, non disponibili in Windows Server 2008 R2 anche con WMF installato.</span><span class="sxs-lookup"><span data-stu-id="280cb-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="280cb-173">Verifiche nel client Windows (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="280cb-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="280cb-174">Una mancanza molto comune dei test è verificare la risorsa solo nelle versioni server di Windows.</span><span class="sxs-lookup"><span data-stu-id="280cb-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="280cb-175">Molte risorse sono progettate anche per il funzionamento su SKU client, quindi se questo è il caso, è importante non dimenticare di eseguire i test anche su queste piattaforme.</span><span class="sxs-lookup"><span data-stu-id="280cb-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="280cb-176">Get-DSCResource elenca la risorsa</span><span class="sxs-lookup"><span data-stu-id="280cb-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="280cb-177">Dopo aver distribuito il modulo, la chiamata di `Get-DscResource` dovrebbe elencare nei risultati anche la risorsa in questione.</span><span class="sxs-lookup"><span data-stu-id="280cb-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="280cb-178">Se non è possibile trovare la risorsa nell'elenco, verificare che esista il file schema.mof per la risorsa.</span><span class="sxs-lookup"><span data-stu-id="280cb-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="280cb-179">Il modulo della risorsa contiene esempi</span><span class="sxs-lookup"><span data-stu-id="280cb-179">Resource module contains examples</span></span>

<span data-ttu-id="280cb-180">Creazione di esempi di qualità che consentono ad altri utenti di capirne l'uso.</span><span class="sxs-lookup"><span data-stu-id="280cb-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="280cb-181">Ciò è fondamentale, soprattutto perché molti utenti usano il codice di esempio come documentazione.</span><span class="sxs-lookup"><span data-stu-id="280cb-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="280cb-182">In primo luogo, è necessario determinare gli esempi da includere nel modulo. È opportuno offrire come minimo esempi per i casi d'uso più importanti per la risorsa:</span><span class="sxs-lookup"><span data-stu-id="280cb-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="280cb-183">Se il modulo contiene varie risorse che devono essere usate insieme per uno scenario end-to-end, l'esempio end-to-end di base dovrebbe essere idealmente il primo.</span><span class="sxs-lookup"><span data-stu-id="280cb-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="280cb-184">Gli esempi iniziali dovrebbero essere molto semplici e illustrare come iniziare a usare le risorse in piccoli blocchi gestibili, ad esempio la creazione di un nuovo VHD</span><span class="sxs-lookup"><span data-stu-id="280cb-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="280cb-185">Gli esempi successivi dovrebbero continuare e ampliare quelli iniziali (ad esempio, creare una VM da un VHD, rimuovere una VM o modificare una VM) e illustrare le funzionalità avanzate (ad esempio, la creazione di una VM con memoria dinamica)</span><span class="sxs-lookup"><span data-stu-id="280cb-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="280cb-186">Le configurazioni di esempio devono essere parametrizzate (tutti i valori devono essere passati come parametri alla configurazione, senza valori hardcoded):</span><span class="sxs-lookup"><span data-stu-id="280cb-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

  ```powershell
  configuration Sample_xRemoteFile_DownloadFile
  {
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
  }
  ```

- <span data-ttu-id="280cb-187">È buona norma includere un esempio di come chiamare la configurazione con i valori effettivi alla fine dello script di esempio, impostandolo come commento.</span><span class="sxs-lookup"><span data-stu-id="280cb-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="280cb-188">Ad esempio, nella configurazione precedente non è così ovvio che il modo migliore per specificare UserAgent è:</span><span class="sxs-lookup"><span data-stu-id="280cb-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="280cb-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In questo caso un commento può chiarire l'esecuzione della configurazione voluta:</span><span class="sxs-lookup"><span data-stu-id="280cb-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="280cb-190">Per ogni esempio, scrivere una breve descrizione per illustrarne le funzioni e indicare il significato dei parametri.</span><span class="sxs-lookup"><span data-stu-id="280cb-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="280cb-191">Assicurarsi che siano disponibili esempi per la maggior parte degli scenari importanti per la risorsa e se non manca nulla, verificare che funzionino tutti e mettano il computer nello stato desiderato.</span><span class="sxs-lookup"><span data-stu-id="280cb-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="280cb-192">I messaggi di errore sono facili da comprendere e aiutano gli utenti a risolvere i problemi</span><span class="sxs-lookup"><span data-stu-id="280cb-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="280cb-193">Per essere utili, i messaggi di errore devono essere:</span><span class="sxs-lookup"><span data-stu-id="280cb-193">Good error messages should be:</span></span>

- <span data-ttu-id="280cb-194">Presenti: il problema principale con i messaggi di errore è che spesso non esistono, quindi assicurarsi che ci siano.</span><span class="sxs-lookup"><span data-stu-id="280cb-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="280cb-195">Facile da capire: messaggi leggibili evitando oscuri codici di errore</span><span class="sxs-lookup"><span data-stu-id="280cb-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="280cb-196">Precisi: descrivere esattamente il problema</span><span class="sxs-lookup"><span data-stu-id="280cb-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="280cb-197">Costruttivi: suggerire come risolvere il problema</span><span class="sxs-lookup"><span data-stu-id="280cb-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="280cb-198">Cortesi: non incolpare l'utente o farlo sentire a disagio</span><span class="sxs-lookup"><span data-stu-id="280cb-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="280cb-199">Assicurarsi di verificare gli errori negli scenari end-to-end (con `Start-DscConfiguration`), in quanto potrebbero essere diversi da quelli restituiti quando si eseguono direttamente le funzioni della risorsa.</span><span class="sxs-lookup"><span data-stu-id="280cb-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="280cb-200">I messaggi dei log sono facili da capire e informativi (inclusi i log -verbose, -debug ed ETW)</span><span class="sxs-lookup"><span data-stu-id="280cb-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="280cb-201">Assicurarsi che i log generati dalla risorsa siano facili da comprendere e offrano informazioni utili all'utente.</span><span class="sxs-lookup"><span data-stu-id="280cb-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="280cb-202">Le risorse dovrebbero offrire come output tutte le informazioni che potrebbero essere utili all'utente, ma non sempre la disponibilità di più log è un vantaggio.</span><span class="sxs-lookup"><span data-stu-id="280cb-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="280cb-203">È consigliabile evitare la ridondanza e output di dati senza valore aggiunto, in modo da non costringere gli utenti a scorrere centinaia di voci di log per trovare quello che cercano.</span><span class="sxs-lookup"><span data-stu-id="280cb-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="280cb-204">Naturalmente, anche l'assenza di log non è una soluzione accettabile per questo problema.</span><span class="sxs-lookup"><span data-stu-id="280cb-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="280cb-205">Durante il test, è necessario analizzare anche i log dettagliati e di debug (eseguendo `Start-DscConfiguration` con le opzioni `–Verbose` e `–Debug` in modo appropriato), oltre ai log ETW.</span><span class="sxs-lookup"><span data-stu-id="280cb-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="280cb-206">Per visualizzare i log ETW di DSC, passare al Visualizzatore eventi e aprire la cartella seguente: Applicazioni e servizi - Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="280cb-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="280cb-207">Per impostazione predefinita è abilitato il canale operativo, ma assicurarsi di abilitare i canali analitico e debug prima di eseguire la configurazione.</span><span class="sxs-lookup"><span data-stu-id="280cb-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="280cb-208">Per abilitare i canali Analitico/Debug, è possibile eseguire lo script riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="280cb-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="280cb-209">L'implementazione della risorsa non contiene percorsi hardcoded</span><span class="sxs-lookup"><span data-stu-id="280cb-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="280cb-210">Assicurarsi che non siano presenti percorsi hardcoded nell'implementazione della risorsa, in particolare se presuppongono una lingua specifica (en-us) o quando possono essere usate variabili di sistema.</span><span class="sxs-lookup"><span data-stu-id="280cb-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="280cb-211">Se la risorsa deve accedere a percorsi specifici, usare le variabili di ambiente invece di percorsi hardcoded, perché potrebbero variare in altri computer.</span><span class="sxs-lookup"><span data-stu-id="280cb-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="280cb-212">Esempio:</span><span class="sxs-lookup"><span data-stu-id="280cb-212">Example:</span></span>

<span data-ttu-id="280cb-213">Invece di:</span><span class="sxs-lookup"><span data-stu-id="280cb-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="280cb-214">È possibile scrivere:</span><span class="sxs-lookup"><span data-stu-id="280cb-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="280cb-215">L'implementazione della risorsa non contiene informazioni sull'utente</span><span class="sxs-lookup"><span data-stu-id="280cb-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="280cb-216">Assicurarsi che nel codice non siano presenti nomi di posta elettronica, informazioni su account o nomi di persone.</span><span class="sxs-lookup"><span data-stu-id="280cb-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="280cb-217">La risorsa è stata testata con credenziali valide e non valide</span><span class="sxs-lookup"><span data-stu-id="280cb-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="280cb-218">Se la risorsa accetta credenziali come parametro:</span><span class="sxs-lookup"><span data-stu-id="280cb-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="280cb-219">Verificare che la risorsa funzioni quando l'account di sistema locale (o l'account computer per risorse remote) non ha accesso.</span><span class="sxs-lookup"><span data-stu-id="280cb-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="280cb-220">Verificare che la risorsa funzioni quando vengono specificate credenziali per Get, Set e Test</span><span class="sxs-lookup"><span data-stu-id="280cb-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="280cb-221">Se la risorsa accede a condivisioni, testare tutte le varianti che bisogna supportare, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="280cb-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="280cb-222">Condivisioni Windows standard.</span><span class="sxs-lookup"><span data-stu-id="280cb-222">Standard windows shares.</span></span>
  - <span data-ttu-id="280cb-223">Condivisioni DFS.</span><span class="sxs-lookup"><span data-stu-id="280cb-223">DFS shares.</span></span>
  - <span data-ttu-id="280cb-224">Condivisioni SAMBA (se si vuole supportare Linux).</span><span class="sxs-lookup"><span data-stu-id="280cb-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="280cb-225">La risorsa non richiede input interattivo</span><span class="sxs-lookup"><span data-stu-id="280cb-225">Resource does not require interactive input</span></span>

<span data-ttu-id="280cb-226">Le funzioni **Get/Set/Test-TargetResource** dovrebbero essere eseguite automaticamente e non devono attendere l'input dell'utente in alcuna fase dell'esecuzione. Ad esempio, è consigliabile non usare `Get-Credential` all'interno di queste funzioni.</span><span class="sxs-lookup"><span data-stu-id="280cb-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="280cb-227">Se è necessario fornire l'input dell'utente, è consigliabile passarlo alla configurazione come parametro durante la fase di compilazione.</span><span class="sxs-lookup"><span data-stu-id="280cb-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="280cb-228">La funzionalità della risorsa è stata accuratamente testata</span><span class="sxs-lookup"><span data-stu-id="280cb-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="280cb-229">Questo elenco di controllo contiene gli elementi che è importante testare e/o che vengono spesso dimenticati.</span><span class="sxs-lookup"><span data-stu-id="280cb-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="280cb-230">Ci sono molti test, principalmente funzionali, specifici della risorsa da testare e che non sono menzionati in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="280cb-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="280cb-231">Non dimenticarsi dei test case negativi.</span><span class="sxs-lookup"><span data-stu-id="280cb-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="280cb-232">Procedura consigliata: il modulo della risorsa contiene una cartella Test con lo script ResourceDesignerTests.ps1</span><span class="sxs-lookup"><span data-stu-id="280cb-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="280cb-233">È buona norma creare una cartella "Test" all'interno del modulo della risorsa, creare il file `ResourceDesignerTests.ps1` e aggiungere i test con **Test-xDscResource** e **Test-xDscSchema** per tutte le risorse nel modulo specificato.</span><span class="sxs-lookup"><span data-stu-id="280cb-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="280cb-234">In questo modo è possibile convalidare rapidamente gli schemi di tutte le risorse da moduli specifici ed eseguire test di integrità prima della pubblicazione.</span><span class="sxs-lookup"><span data-stu-id="280cb-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="280cb-235">Per xRemoteFile, `ResourceTests.ps1` potrebbe essere semplice come:</span><span class="sxs-lookup"><span data-stu-id="280cb-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="280cb-236">Procedura consigliata: la cartella della risorsa contiene uno script di progettazione della risorsa per la generazione dello schema</span><span class="sxs-lookup"><span data-stu-id="280cb-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="280cb-237">Ogni risorsa dovrebbe contenere uno script di progettazione della risorsa che genera uno schema MOF della risorsa.</span><span class="sxs-lookup"><span data-stu-id="280cb-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="280cb-238">Questo file deve essere inserito `<ResourceName>\ResourceDesignerScripts` e denominato `<ResourceName>Schema.ps1`. Per la risorsa xRemoteFile questo file deve essere denominato `GenerateXRemoteFileSchema.ps1` e contenere:</span><span class="sxs-lookup"><span data-stu-id="280cb-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="280cb-239">Procedura consigliata: la risorsa supporta - WhatIf</span><span class="sxs-lookup"><span data-stu-id="280cb-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="280cb-240">Se la risorsa esegue operazioni "pericolose", è consigliabile implementare la funzionalità `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="280cb-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="280cb-241">Verificare poi che l'output di `-WhatIf` descriva correttamente le operazioni che verrebbero eseguite se il comando venisse eseguito senza l'opzione `-WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="280cb-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="280cb-242">Verificare anche che le operazioni non vengono eseguite, ovvero non vengano apportate modifiche allo stato del nodo, quando è presente l'opzione `–WhatIf`.</span><span class="sxs-lookup"><span data-stu-id="280cb-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="280cb-243">Si supponga, ad esempio, di dover eseguire il test della risorsa File.</span><span class="sxs-lookup"><span data-stu-id="280cb-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="280cb-244">Quella che segue è una configurazione semplice che crea il file `test.txt` con il contenuto "test":</span><span class="sxs-lookup"><span data-stu-id="280cb-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="280cb-245">Se si compila e poi si esegue la configurazione con l'opzione `-WhatIf`, l'output indica le esatte conseguenze dell'esecuzione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="280cb-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="280cb-246">La configurazione stessa non viene però eseguita e il file `test.txt` non viene creato.</span><span class="sxs-lookup"><span data-stu-id="280cb-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="280cb-247">Questo elenco non è esaustivo, ma tiene conto di molti importanti problemi riscontrati durante la progettazione, lo sviluppo e il test di risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="280cb-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
