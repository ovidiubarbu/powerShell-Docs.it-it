---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Modifica dello stato del computer
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "70386293"
---
# <a name="changing-computer-state"></a><span data-ttu-id="935fb-103">Modifica dello stato del computer</span><span class="sxs-lookup"><span data-stu-id="935fb-103">Changing Computer State</span></span>

<span data-ttu-id="935fb-104">Per reimpostare un computer in Windows PowerShell, usare uno strumento da riga di comando standard o una classe WMI o CIM.</span><span class="sxs-lookup"><span data-stu-id="935fb-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="935fb-105">Anche se si usa Windows PowerShell solo per eseguire lo strumento, imparare a modificare lo stato di alimentazione del computer in Windows PowerShell illustra alcuni dettagli importanti dell'uso degli strumenti esterni in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="935fb-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="935fb-106">Blocco di un computer</span><span class="sxs-lookup"><span data-stu-id="935fb-106">Locking a Computer</span></span>

<span data-ttu-id="935fb-107">L'unico modo per bloccare un computer direttamente con gli strumenti disponibili standard consiste nel chiamare la funzione **LockWorkstation ()** in **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="935fb-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="935fb-108">Questo comando blocca immediatamente la workstation.</span><span class="sxs-lookup"><span data-stu-id="935fb-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="935fb-109">Usa *rundll32.exe*, che esegue DLL di Windows (e salva le librerie corrispondenti per poterle usare più volte) per eseguire user32.dll, una libreria di funzioni di gestione di Windows.</span><span class="sxs-lookup"><span data-stu-id="935fb-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="935fb-110">Quando si blocca una workstation mentre è abilitata la funzionalità Cambio rapido utente, ad esempio in Windows XP, il computer visualizza la schermata di accesso utente invece dello screen saver dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="935fb-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="935fb-111">Per arrestare una sessione specifica in Terminal Server, usare lo strumento da riga di comando **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="935fb-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="935fb-112">Disconnessione dalla sessione corrente</span><span class="sxs-lookup"><span data-stu-id="935fb-112">Logging Off the Current Session</span></span>

<span data-ttu-id="935fb-113">È possibile usare alcune tecniche diverse per disconnettersi da una sessione nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="935fb-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="935fb-114">Il modo più semplice consiste nell'usare lo strumento da riga di comando di Desktop remoto/Servizi terminal, **logoff.exe**. Per altri dettagli, al prompt di Windows PowerShell digitare **logoff /?** .</span><span class="sxs-lookup"><span data-stu-id="935fb-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="935fb-115">Per disconnettere la sessione attiva corrente, digitare **logoff** senza argomenti.</span><span class="sxs-lookup"><span data-stu-id="935fb-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="935fb-116">È anche possibile usare lo strumento **shutdown.exe** con la relativa opzione di disconnessione:</span><span class="sxs-lookup"><span data-stu-id="935fb-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="935fb-117">Un'altra opzione prevede l'uso di WMI.</span><span class="sxs-lookup"><span data-stu-id="935fb-117">Another option is to use WMI.</span></span> <span data-ttu-id="935fb-118">La classe Win32_OperatingSystem include un metodo Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="935fb-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="935fb-119">È possibile richiamare il metodo con il contrassegno 0 per avviare la disconnessione:</span><span class="sxs-lookup"><span data-stu-id="935fb-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="935fb-120">Per altre informazioni e per individuare altre funzionalità del metodo Win32Shutdown, vedere "Metodo Win32Shutdown della classe Win32_OperatingSystem" in MSDN.</span><span class="sxs-lookup"><span data-stu-id="935fb-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="935fb-121">Infine, è possibile usare CIM con la stessa classe Win32_OperatingSystem descritta in precedenza nel metodo WMI.</span><span class="sxs-lookup"><span data-stu-id="935fb-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="935fb-122">Arresto o riavvio di un computer</span><span class="sxs-lookup"><span data-stu-id="935fb-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="935fb-123">L'arresto e il riavvio dei computer sono in genere gli stessi tipi di attività.</span><span class="sxs-lookup"><span data-stu-id="935fb-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="935fb-124">Gli strumenti per l'arresto di un computer di solito consentono anche di riavviarlo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="935fb-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="935fb-125">Sono disponibili due opzioni semplici per riavviare un computer da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="935fb-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="935fb-126">Usare Tsshutdn.exe o Shutdown.exe con gli argomenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="935fb-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="935fb-127">È possibile ottenere informazioni dettagliate sull'utilizzo con **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="935fb-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="935fb-128">o **shutdown.exe /?** .</span><span class="sxs-lookup"><span data-stu-id="935fb-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="935fb-129">È possibile eseguire le operazioni di arresto e riavvio anche direttamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="935fb-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="935fb-130">Per arrestare il computer, usare il comando Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="935fb-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="935fb-131">Per riavviare il sistema operativo, usare il comando Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="935fb-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="935fb-132">Per forzare il riavvio immediato del computer, usare il parametro -Force.</span><span class="sxs-lookup"><span data-stu-id="935fb-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
