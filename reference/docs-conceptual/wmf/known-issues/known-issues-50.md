---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Problemi noti in WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147741"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="8963e-103">Problemi noti in WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8963e-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="8963e-104">I collegamenti per PowerShell non funzionano la prima volta</span><span class="sxs-lookup"><span data-stu-id="8963e-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="8963e-105">**Soluzione:** Eseguire una delle azioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8963e-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="8963e-106">Fare clic con il pulsante destro del mouse sul collegamento di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8963e-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="8963e-107">Selezionare "Windows PowerShell" per avviare il programma in modalità senza privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="8963e-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="8963e-108">Fare clic con il pulsante destro del mouse sul collegamento di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8963e-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="8963e-109">Fare clic con il pulsante destro del mouse su "Windows PowerShell" e scegliere "Esegui come amministratore" per avviare il programma in modalità con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="8963e-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="8963e-110">Dopo aver eseguito una delle azioni precedenti, i collegamenti per PowerShell funzioneranno.</span><span class="sxs-lookup"><span data-stu-id="8963e-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="8963e-111">Queste azioni devono essere eseguite una sola volta.</span><span class="sxs-lookup"><span data-stu-id="8963e-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="8963e-112">I moduli di PowerShell e le risorse DSC segnalano errori per ExecutionPolicy in Windows 7</span><span class="sxs-lookup"><span data-stu-id="8963e-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="8963e-113">In Windows 7 l'uso dei moduli di PowerShell e delle risorse DSC potrebbe causare la segnalazione di errori per ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="8963e-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="8963e-114">**Soluzione:** impostare ExecutionPolicy su **RemoteSigned** eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="8963e-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="8963e-115">La connessione a un endpoint di Exchange remoto precedente causa un arresto anomalo</span><span class="sxs-lookup"><span data-stu-id="8963e-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="8963e-116">L'endpoint di Exchange precedente reindirizza a un nuovo endpoint.</span><span class="sxs-lookup"><span data-stu-id="8963e-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="8963e-117">È presente un bug nella logica di reindirizzamento che causa un arresto anomalo.</span><span class="sxs-lookup"><span data-stu-id="8963e-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="8963e-118">**Soluzione:** connettersi direttamente al nuovo endpoint.</span><span class="sxs-lookup"><span data-stu-id="8963e-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="8963e-119">La funzionalità Registrazione inventario software viene arrestata erroneamente dopo l'installazione di WMF 5.0 in Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="8963e-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="8963e-120">Quando si installa WMF 5.0 in un computer Windows Server 2012 R2 in cui è già in esecuzione Registrazione inventario software, questa funzionalità viene arrestata erroneamente dopo l'installazione.</span><span class="sxs-lookup"><span data-stu-id="8963e-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="8963e-121">**Soluzione:** eseguire il cmdlet `Start-SilLogging` una volta dopo l'installazione di WMF, perché il processo di installazione arresta erroneamente la funzionalità Registrazione inventario software.</span><span class="sxs-lookup"><span data-stu-id="8963e-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="8963e-122">`Get-ChildItem` non funziona se si usano insieme -LiteralPath e -Recurse</span><span class="sxs-lookup"><span data-stu-id="8963e-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="8963e-123">Se un nome di directory contiene un carattere jolly non valido, `Get-ChildItem` non produrrà i risultati previsti quando si usano insieme entrambe le opzioni -LiteralPath e -Recurse.</span><span class="sxs-lookup"><span data-stu-id="8963e-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="8963e-124">**Soluzione:** non è ideale, ma la soluzione attuale consiste nell'implementare la ricorsione nello script anziché affidarsi al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8963e-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="8963e-125">Sysprep smette di funzionare dopo l'installazione di WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="8963e-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="8963e-126">Esistono due possibili soluzioni al problema in base alla versione di Windows Server in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8963e-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="8963e-127">**Soluzione:**</span><span class="sxs-lookup"><span data-stu-id="8963e-127">**Resolution:**</span></span>

- <span data-ttu-id="8963e-128">Per i sistemi che eseguono **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="8963e-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="8963e-129">Aprire PowerShell con un account amministratore</span><span class="sxs-lookup"><span data-stu-id="8963e-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="8963e-130">Eseguire il comando seguente</span><span class="sxs-lookup"><span data-stu-id="8963e-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="8963e-131">Eseguire il comando e ignorare l'errore, perché è previsto.</span><span class="sxs-lookup"><span data-stu-id="8963e-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="8963e-132">Eliminare i file nella directory \Windows\System32\Logfiles\SIL\</span><span class="sxs-lookup"><span data-stu-id="8963e-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="8963e-133">Installare tutti gli aggiornamenti Windows importanti disponibili e iniziare a usare Sysyprep normalmente.</span><span class="sxs-lookup"><span data-stu-id="8963e-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="8963e-134">Per i sistemi che eseguono **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="8963e-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="8963e-135">Dopo l'installazione di WMF 5.0 nel server in cui usare Sysprep, eseguire l'accesso come amministratore.</span><span class="sxs-lookup"><span data-stu-id="8963e-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="8963e-136">Copiare Generize.xml dalla directory `\Windows\System32\Sysprep\ActionFiles\` in un percorso esterno alla directory di Windows, ad esempio `C:\`.</span><span class="sxs-lookup"><span data-stu-id="8963e-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="8963e-137">Aprire la copia Generalize.xml con il Blocco note.</span><span class="sxs-lookup"><span data-stu-id="8963e-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="8963e-138">Trovare e rimuovere il testo seguente, di cui è necessario eliminare ogni istanza (si troveranno verso la fine del documento).</span><span class="sxs-lookup"><span data-stu-id="8963e-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="8963e-139">Salvare la copia modificata del file Generalize.xml e chiuderlo.</span><span class="sxs-lookup"><span data-stu-id="8963e-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="8963e-140">Aprire una finestra del prompt dei comandi come amministratore</span><span class="sxs-lookup"><span data-stu-id="8963e-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="8963e-141">Eseguire il comando seguente per assumere la proprietà del file Generalize.xml nella cartella system32:</span><span class="sxs-lookup"><span data-stu-id="8963e-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="8963e-142">Eseguire il comando seguente per impostare le autorizzazioni appropriate sul file:</span><span class="sxs-lookup"><span data-stu-id="8963e-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="8963e-143">Rispondere Sì al prompt di conferma.</span><span class="sxs-lookup"><span data-stu-id="8963e-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="8963e-144">Si noti che `<AdministratorUserName>` deve essere sostituito dal nome utente che è l'amministratore nel computer.</span><span class="sxs-lookup"><span data-stu-id="8963e-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="8963e-145">Ad esempio, "Amministratore".</span><span class="sxs-lookup"><span data-stu-id="8963e-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="8963e-146">Copiare il file modificato e salvato nella directory Sysprep usando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="8963e-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="8963e-147">Rispondere Sì per sovrascrivere (se non si riceve alcuna richiesta di conferma della sovrascrittura, controllare il percorso specificato).</span><span class="sxs-lookup"><span data-stu-id="8963e-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="8963e-148">Si presuppone che la versione modificata del file Generalize.xml sia stata copiata in C:\.</span><span class="sxs-lookup"><span data-stu-id="8963e-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="8963e-149">Il file Generalize.xml è ora aggiornato con la soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="8963e-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="8963e-150">Eseguire Sysprep con l'opzione generalize abilitata.</span><span class="sxs-lookup"><span data-stu-id="8963e-150">Please run Sysprep with the generalize option enabled.</span></span>