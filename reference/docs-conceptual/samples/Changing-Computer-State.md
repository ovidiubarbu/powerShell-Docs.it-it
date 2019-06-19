---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Modifica dello stato del computer
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030290"
---
# <a name="changing-computer-state"></a><span data-ttu-id="e02cd-103">Modifica dello stato del computer</span><span class="sxs-lookup"><span data-stu-id="e02cd-103">Changing Computer State</span></span>

<span data-ttu-id="e02cd-104">Per reimpostare un computer in Windows PowerShell, usare uno strumento da riga di comando standard o una classe WMI.</span><span class="sxs-lookup"><span data-stu-id="e02cd-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="e02cd-105">Anche se si usa Windows PowerShell solo per eseguire lo strumento, imparare a modificare lo stato di alimentazione del computer in Windows PowerShell illustra alcuni dettagli importanti dell'uso degli strumenti esterni in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e02cd-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="e02cd-106">Blocco di un computer</span><span class="sxs-lookup"><span data-stu-id="e02cd-106">Locking a Computer</span></span>

<span data-ttu-id="e02cd-107">L'unico modo per bloccare un computer direttamente con gli strumenti disponibili standard consiste nel chiamare la funzione **LockWorkstation ()** in **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="e02cd-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="e02cd-108">Questo comando blocca immediatamente la workstation.</span><span class="sxs-lookup"><span data-stu-id="e02cd-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="e02cd-109">Usa *rundll32.exe*, che esegue DLL di Windows (e salva le librerie corrispondenti per poterle usare più volte) per eseguire user32.dll, una libreria di funzioni di gestione di Windows.</span><span class="sxs-lookup"><span data-stu-id="e02cd-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="e02cd-110">Quando si blocca una workstation mentre è abilitata la funzionalità Cambio rapido utente, ad esempio in Windows XP, il computer visualizza la schermata di accesso utente invece dello screen saver dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="e02cd-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="e02cd-111">Per arrestare una sessione specifica in Terminal Server, usare lo strumento da riga di comando **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="e02cd-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="e02cd-112">Disconnessione dalla sessione corrente</span><span class="sxs-lookup"><span data-stu-id="e02cd-112">Logging Off the Current Session</span></span>

<span data-ttu-id="e02cd-113">È possibile usare alcune tecniche diverse per disconnettersi da una sessione nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="e02cd-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="e02cd-114">Il modo più semplice consiste nell'usare lo strumento da riga di comando di Desktop remoto/Servizi terminal, **logoff.exe**. Per altri dettagli, al prompt di Windows PowerShell digitare **logoff /?**.</span><span class="sxs-lookup"><span data-stu-id="e02cd-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="e02cd-115">Per disconnettere la sessione attiva corrente, digitare **logoff** senza argomenti.</span><span class="sxs-lookup"><span data-stu-id="e02cd-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="e02cd-116">È anche possibile usare lo strumento **shutdown.exe** con la relativa opzione di disconnessione:</span><span class="sxs-lookup"><span data-stu-id="e02cd-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="e02cd-117">Una terza opzione prevede l'uso di WMI.</span><span class="sxs-lookup"><span data-stu-id="e02cd-117">A third option is to use WMI.</span></span> <span data-ttu-id="e02cd-118">La classe Win32_OperatingSystem include un metodo Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="e02cd-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="e02cd-119">È possibile richiamare il metodo con il contrassegno 0 per avviare la disconnessione:</span><span class="sxs-lookup"><span data-stu-id="e02cd-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="e02cd-120">Per altre informazioni e per individuare altre funzionalità del metodo Win32Shutdown, vedere "Metodo Win32Shutdown della classe Win32_OperatingSystem" in MSDN.</span><span class="sxs-lookup"><span data-stu-id="e02cd-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="e02cd-121">Arresto o riavvio di un computer</span><span class="sxs-lookup"><span data-stu-id="e02cd-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="e02cd-122">L'arresto e il riavvio dei computer sono in genere gli stessi tipi di attività.</span><span class="sxs-lookup"><span data-stu-id="e02cd-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="e02cd-123">Gli strumenti per l'arresto di un computer di solito consentono anche di riavviarlo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="e02cd-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="e02cd-124">Sono disponibili due opzioni semplici per riavviare un computer da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e02cd-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="e02cd-125">Usare Tsshutdn.exe o Shutdown.exe con gli argomenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="e02cd-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="e02cd-126">È possibile ottenere informazioni dettagliate sull'utilizzo con **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="e02cd-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="e02cd-127">o **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="e02cd-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="e02cd-128">È possibile eseguire le operazioni di arresto e riavvio anche direttamente da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e02cd-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="e02cd-129">Per arrestare il computer, usare il comando Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="e02cd-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="e02cd-130">Per riavviare il sistema operativo, usare il comando Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="e02cd-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="e02cd-131">Per forzare il riavvio immediato del computer, usare il parametro -Force.</span><span class="sxs-lookup"><span data-stu-id="e02cd-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
