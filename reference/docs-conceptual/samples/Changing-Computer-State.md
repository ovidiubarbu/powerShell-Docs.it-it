---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Modifica dello stato del computer
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736914"
---
# <a name="changing-computer-state"></a><span data-ttu-id="bfda9-103">Modifica dello stato del computer</span><span class="sxs-lookup"><span data-stu-id="bfda9-103">Changing Computer State</span></span>

<span data-ttu-id="bfda9-104">Per reimpostare un computer in PowerShell, usare uno strumento da riga di comando standard o una classe WMI o CIM.</span><span class="sxs-lookup"><span data-stu-id="bfda9-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="bfda9-105">Anche se si usa PowerShell solo per eseguire lo strumento, imparare a modificare lo stato di alimentazione di un computer in PowerShell aiuta a scoprire alcuni importanti dettagli relativi all'uso di strumenti esterni in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfda9-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="bfda9-106">Blocco di un computer</span><span class="sxs-lookup"><span data-stu-id="bfda9-106">Locking a Computer</span></span>

<span data-ttu-id="bfda9-107">L'unico modo per bloccare un computer direttamente con gli strumenti disponibili standard consiste nel chiamare la funzione **LockWorkstation ()** in **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="bfda9-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="bfda9-108">Questo comando blocca immediatamente la workstation.</span><span class="sxs-lookup"><span data-stu-id="bfda9-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="bfda9-109">Usa **rundll32.exe**, che esegue le DLL di Windows (e salva le relative librerie per poterle usare più volte) per eseguire `user32.dll`, una libreria di funzioni di gestione di Windows.</span><span class="sxs-lookup"><span data-stu-id="bfda9-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="bfda9-110">Quando si blocca una workstation mentre è abilitata la funzionalità Cambio rapido utente, ad esempio in Windows XP, il computer visualizza la schermata di accesso utente invece dello screen saver dell'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="bfda9-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="bfda9-111">Per arrestare una sessione specifica in Terminal Server, usare lo strumento da riga di comando **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="bfda9-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="bfda9-112">Disconnessione dalla sessione corrente</span><span class="sxs-lookup"><span data-stu-id="bfda9-112">Logging Off the Current Session</span></span>

<span data-ttu-id="bfda9-113">È possibile usare alcune tecniche diverse per disconnettersi da una sessione nel sistema locale.</span><span class="sxs-lookup"><span data-stu-id="bfda9-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="bfda9-114">Il modo più semplice è l'uso dello strumento da riga di comando di Desktop remoto/Servizi terminal, **logoff.exe**. Per i dettagli, al prompt di PowerShell digitare `logoff /?`.</span><span class="sxs-lookup"><span data-stu-id="bfda9-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="bfda9-115">Per disconnettere la sessione attiva corrente, digitare `logoff` senza argomenti.</span><span class="sxs-lookup"><span data-stu-id="bfda9-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="bfda9-116">È anche possibile usare lo strumento **shutdown.exe** con la relativa opzione di disconnessione:</span><span class="sxs-lookup"><span data-stu-id="bfda9-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="bfda9-117">Un'altra opzione prevede l'uso di WMI.</span><span class="sxs-lookup"><span data-stu-id="bfda9-117">Another option is to use WMI.</span></span> <span data-ttu-id="bfda9-118">La classe **Win32_OperatingSystem** include un metodo **Shutdown**.</span><span class="sxs-lookup"><span data-stu-id="bfda9-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="bfda9-119">È possibile richiamare il metodo con il contrassegno 0 per avviare la disconnessione:</span><span class="sxs-lookup"><span data-stu-id="bfda9-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="bfda9-120">Per altre informazioni sul metodo **Shutdown**, vedere [Metodo Shutdown della classe Win32_OperatingSystem](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="bfda9-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="bfda9-121">Arresto o riavvio di un computer</span><span class="sxs-lookup"><span data-stu-id="bfda9-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="bfda9-122">L'arresto e il riavvio dei computer sono in genere gli stessi tipi di attività.</span><span class="sxs-lookup"><span data-stu-id="bfda9-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="bfda9-123">Gli strumenti per l'arresto di un computer di solito consentono anche di riavviarlo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="bfda9-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="bfda9-124">Sono disponibili due opzioni semplici per riavviare un computer da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfda9-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="bfda9-125">Usare **tsshutdn.exe** o **shutdown.exe** con gli argomenti appropriati.</span><span class="sxs-lookup"><span data-stu-id="bfda9-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="bfda9-126">È possibile ottenere informazioni di utilizzo dettagliate da `tsshutdn.exe /?` o `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="bfda9-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="bfda9-127">È anche possibile eseguire operazioni di arresto e riavvio direttamente da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfda9-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="bfda9-128">Per arrestare il computer, usare il comando Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="bfda9-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="bfda9-129">Per riavviare il sistema operativo, usare il comando Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="bfda9-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="bfda9-130">Per forzare il riavvio immediato del computer, usare il parametro -Force.</span><span class="sxs-lookup"><span data-stu-id="bfda9-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
