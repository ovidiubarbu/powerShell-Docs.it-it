---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 3d74217621d00dfd68cad1c45d187a9c2ffb9980
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085278"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="eb615-102">Limitazioni e problemi noti</span><span class="sxs-lookup"><span data-stu-id="eb615-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="eb615-103">I collegamenti per PowerShell non funzionano la prima volta</span><span class="sxs-lookup"><span data-stu-id="eb615-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="eb615-104">**Soluzione:** Eseguire una delle azioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="eb615-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="eb615-105">Fare clic con il pulsante destro del mouse sul collegamento di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb615-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="eb615-106">Selezionare "Windows PowerShell" per avviare il programma in modalità senza privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="eb615-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="eb615-107">Fare clic con il pulsante destro del mouse sul collegamento di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb615-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="eb615-108">Fare clic con il pulsante destro del mouse su "Windows PowerShell" e selezionare "Esegui come amministratore" per avviare il programma in modalità con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="eb615-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="eb615-109">Dopo aver eseguito una delle azioni precedenti, i collegamenti per PowerShell funzioneranno.</span><span class="sxs-lookup"><span data-stu-id="eb615-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="eb615-110">Queste azioni devono essere eseguite una sola volta.</span><span class="sxs-lookup"><span data-stu-id="eb615-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="eb615-111">I moduli di PowerShell e le risorse DSC segnalano errori per ExecutionPolicy in Windows 7</span><span class="sxs-lookup"><span data-stu-id="eb615-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="eb615-112">In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="eb615-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="eb615-113">**Soluzione:** impostare ExecutionPolicy su RemoteSigned eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="eb615-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="eb615-114">La connessione a un endpoint di Exchange remoto precedente causa un arresto anomalo</span><span class="sxs-lookup"><span data-stu-id="eb615-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="eb615-115">L'endpoint di Exchange precedente reindirizza a un nuovo endpoint.</span><span class="sxs-lookup"><span data-stu-id="eb615-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="eb615-116">È presente un bug nella logica di reindirizzamento che causa un arresto anomalo.</span><span class="sxs-lookup"><span data-stu-id="eb615-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="eb615-117">**Soluzione:** connettersi direttamente al nuovo endpoint.</span><span class="sxs-lookup"><span data-stu-id="eb615-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="eb615-118">La funzionalità Registrazione inventario software viene arrestata erroneamente dopo l'installazione di WMF 5.0 in Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eb615-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="eb615-119">Quando si installa WMF 5.0 in un computer Windows Server 2012 R2 in cui è già in esecuzione Registrazione inventario software, questa funzionalità viene arrestata erroneamente dopo l'installazione.</span><span class="sxs-lookup"><span data-stu-id="eb615-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="eb615-120">**Soluzione:** eseguire il cmdlet Start-SilLogging una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.</span><span class="sxs-lookup"><span data-stu-id="eb615-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="eb615-121">`Get-ChildItem` non funziona se si usano insieme -LiteralPath e -Recurse</span><span class="sxs-lookup"><span data-stu-id="eb615-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="eb615-122">Se un nome di directory contiene un carattere jolly non valido, `Get-ChildItem` non produrrà i risultati previsti quando si usano insieme entrambe le opzioni -LiteralPath e -Recurse.</span><span class="sxs-lookup"><span data-stu-id="eb615-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="eb615-123">**Soluzione:** non è ideale, ma la soluzione attuale consiste nell'implementare la ricorsione nello script anziché affidarsi al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb615-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="eb615-124">Sysprep smette di funzionare dopo l'installazione di WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="eb615-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="eb615-125">Esistono due possibili soluzioni al problema in base alla versione di Windows Server in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="eb615-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="eb615-126">**Soluzione:**</span><span class="sxs-lookup"><span data-stu-id="eb615-126">**Resolution:**</span></span>

- <span data-ttu-id="eb615-127">Per i sistemi che eseguono **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="eb615-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="eb615-128">Aprire PowerShell con un account amministratore</span><span class="sxs-lookup"><span data-stu-id="eb615-128">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="eb615-129">Eseguire il comando seguente</span><span class="sxs-lookup"><span data-stu-id="eb615-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="eb615-130">Eseguire il comando e ignorare l'errore, perché è previsto.</span><span class="sxs-lookup"><span data-stu-id="eb615-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="eb615-131">Eliminare i file nella directory \Windows\System32\Logfiles\SIL\\</span><span class="sxs-lookup"><span data-stu-id="eb615-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="eb615-132">Installare tutti gli aggiornamenti Windows importanti disponibili e iniziare a usare Sysyprep normalmente.</span><span class="sxs-lookup"><span data-stu-id="eb615-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="eb615-133">Per i sistemi che eseguono **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="eb615-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="eb615-134">Dopo l'installazione di WMF 5.0 nel server in cui usare Sysprep, eseguire l'accesso come amministratore.</span><span class="sxs-lookup"><span data-stu-id="eb615-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="eb615-135">Copiare Generize.xml dalla directory \Windows\System32\Sysprep\ActionFiles\ in un percorso esterno alla directory Windows, ad esempio C:\.</span><span class="sxs-lookup"><span data-stu-id="eb615-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="eb615-136">Aprire la copia Generalize.xml con il Blocco note.</span><span class="sxs-lookup"><span data-stu-id="eb615-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="eb615-137">Trovare e rimuovere il testo seguente, di cui è necessario eliminare ogni istanza (si troveranno verso la fine del documento).</span><span class="sxs-lookup"><span data-stu-id="eb615-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="eb615-138">Salvare la copia modificata del file Generalize.xml e chiuderlo.</span><span class="sxs-lookup"><span data-stu-id="eb615-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="eb615-139">Aprire una finestra del prompt dei comandi come amministratore</span><span class="sxs-lookup"><span data-stu-id="eb615-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="eb615-140">Eseguire il comando seguente per assumere la proprietà del file Generalize.xml nella cartella system32:</span><span class="sxs-lookup"><span data-stu-id="eb615-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="eb615-141">Eseguire il comando seguente per impostare le autorizzazioni appropriate sul file:</span><span class="sxs-lookup"><span data-stu-id="eb615-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="eb615-142">Rispondere Sì al prompt di conferma.</span><span class="sxs-lookup"><span data-stu-id="eb615-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="eb615-143">Si noti che `<AdministratorUserName>` deve essere sostituito dal nome utente che è l'amministratore nel computer.</span><span class="sxs-lookup"><span data-stu-id="eb615-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="eb615-144">Ad esempio, "Amministratore".</span><span class="sxs-lookup"><span data-stu-id="eb615-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="eb615-145">Copiare il file modificato e salvato nella directory Sysprep usando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="eb615-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="eb615-146">Rispondere Sì per sovrascrivere (se non si riceve alcuna richiesta di conferma della sovrascrittura, controllare il percorso specificato).</span><span class="sxs-lookup"><span data-stu-id="eb615-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="eb615-147">Si presuppone che la versione modificata del file Generalize.xml sia stata copiata in C:\.</span><span class="sxs-lookup"><span data-stu-id="eb615-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="eb615-148">Il file Generalize.xml è ora aggiornato con la soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="eb615-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="eb615-149">Eseguire Sysprep con l'opzione generalize abilitata.</span><span class="sxs-lookup"><span data-stu-id="eb615-149">Please run Sysprep with the generalize option enabled.</span></span>