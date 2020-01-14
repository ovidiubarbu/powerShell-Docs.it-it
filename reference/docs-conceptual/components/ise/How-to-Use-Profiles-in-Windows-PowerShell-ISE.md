---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Modalità di utilizzo dei profili in Windows PowerShell ISE
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736250"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="a4050-103">Modalità di utilizzo dei profili in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4050-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="a4050-104">Questo argomento illustra come usare i profili in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="a4050-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="a4050-105">Prima di eseguire le attività in questa sezione, è consigliabile consultare [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) oppure digitare `Get-Help about_Profiles` nel riquadro della console e premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a4050-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="a4050-106">Un profilo è uno script di Windows PowerShell ISE che viene eseguito automaticamente quando si avvia una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="a4050-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>
<span data-ttu-id="a4050-107">È possibile creare uno o più profili di Windows PowerShell per Windows PowerShell ISE e usarli per configurare l'ambiente Windows PowerShell o Windows PowerShell ISE, prepararlo per l'uso, con le variabili, gli alias, le funzioni e le preferenze di colore e tipo di carattere che si vuole avere a disposizione.</span><span class="sxs-lookup"><span data-stu-id="a4050-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="a4050-108">Il profilo interessa ogni sessione di Windows PowerShell ISE avviata.</span><span class="sxs-lookup"><span data-stu-id="a4050-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="a4050-109">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire gli script e caricare un profilo.</span><span class="sxs-lookup"><span data-stu-id="a4050-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span>
> <span data-ttu-id="a4050-110">I criteri di esecuzione predefiniti, "Restricted", impediscono l'esecuzione di tutti gli script, inclusi i profili.</span><span class="sxs-lookup"><span data-stu-id="a4050-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span>
> <span data-ttu-id="a4050-111">Se si usano i criteri "Restricted", il profilo non potrà essere caricato.</span><span class="sxs-lookup"><span data-stu-id="a4050-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="a4050-112">Per altre informazioni sui criteri di esecuzione, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="a4050-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="a4050-113">Selezione di un profilo da usare in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4050-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="a4050-114">Windows PowerShell ISE supporta i profili per l'utente corrente e per tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="a4050-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="a4050-115">Supporta anche i profili Windows PowerShell che si applicano a tutti gli host.</span><span class="sxs-lookup"><span data-stu-id="a4050-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="a4050-116">Il profilo usato dipende da come si usano Windows PowerShell e Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4050-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="a4050-117">Se si usa solo Windows PowerShell ISE per eseguire Windows PowerShell, salvare tutti gli elementi in uno dei profili ISE specifici, ad esempio il profilo **CurrentUserCurrentHost** per Windows PowerShell ISE o il profilo **AllUsersCurrentHost** per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4050-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the **CurrentUserCurrentHost** profile for Windows PowerShell ISE or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="a4050-118">Se si usano più programmi host per l'esecuzione di Windows PowerShell, salvare funzioni, alias, variabili e comandi in un profilo che interessa tutti i programmi host, ad esempio il profilo CurrentUserAllHosts o il profilo **AllUsersAllHosts**, e quindi salvare le funzionalità specifiche di ISE, come la personalizzazione di colori e tipi di carattere, nel profilo **CurrentUserCurrentHost** per il profilo di Windows PowerShell ISE o il profilo **AllUsersCurrentHost** per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4050-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the **AllUsersAllHosts** profile, and save ISE-specific features, like color and font customization in the **CurrentUserCurrentHost** profile for Windows PowerShell ISE profile or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="a4050-119">I seguenti profili possono essere creati e usati in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4050-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="a4050-120">Ogni profilo viene salvato nel proprio percorso specifico.</span><span class="sxs-lookup"><span data-stu-id="a4050-120">Each profile is saved to its own specific path.</span></span>

|           <span data-ttu-id="a4050-121">Tipo di profilo</span><span class="sxs-lookup"><span data-stu-id="a4050-121">Profile Type</span></span>           |                   <span data-ttu-id="a4050-122">Percorso del profilo</span><span class="sxs-lookup"><span data-stu-id="a4050-122">Profile Path</span></span>                   |
| -------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="a4050-123">**Utente corrente, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="a4050-123">**Current user, PowerShell ISE**</span></span> | <span data-ttu-id="a4050-124">`$PROFILE.CurrentUserCurrentHost` o `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="a4050-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="a4050-125">**Tutti gli utenti, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="a4050-125">**All users, PowerShell ISE**</span></span>    | `$PROFILE.AllUsersCurrentHost`                   |
| <span data-ttu-id="a4050-126">**Utente corrente, tutti gli host**</span><span class="sxs-lookup"><span data-stu-id="a4050-126">**Current user, All hosts**</span></span>      | `$PROFILE.CurrentUserAllHosts`                   |
| <span data-ttu-id="a4050-127">**Tutti gli utenti, tutti gli host**</span><span class="sxs-lookup"><span data-stu-id="a4050-127">**All users, All hosts**</span></span>         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="a4050-128">Per creare un nuovo profilo</span><span class="sxs-lookup"><span data-stu-id="a4050-128">To create a new profile</span></span>

<span data-ttu-id="a4050-129">Per creare un nuovo profilo "Utente corrente, Windows PowerShell ISE", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="a4050-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="a4050-130">Per creare un nuovo profilo "Tutti gli utenti, Windows PowerShell ISE", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="a4050-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="a4050-131">Per creare un nuovo profilo "Utente corrente, tutti gli host", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="a4050-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="a4050-132">Per creare un nuovo profilo "Tutti gli utenti, tutti gli host", digitare:</span><span class="sxs-lookup"><span data-stu-id="a4050-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="a4050-133">Per modificare un profilo</span><span class="sxs-lookup"><span data-stu-id="a4050-133">To edit a profile</span></span>

1. <span data-ttu-id="a4050-134">Per aprire il profilo, eseguire il comando `psEdit` con la variabile che specifica il profilo da modificare.</span><span class="sxs-lookup"><span data-stu-id="a4050-134">To open the profile, run the command `psEdit` with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="a4050-135">Ad esempio, per aprire il profilo "Utente corrente, Windows PowerShell ISE", digitare: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="a4050-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="a4050-136">Aggiungere alcuni elementi al profilo.</span><span class="sxs-lookup"><span data-stu-id="a4050-136">Add some items to your profile.</span></span> <span data-ttu-id="a4050-137">Di seguito sono riportati alcuni esempi per iniziare:</span><span class="sxs-lookup"><span data-stu-id="a4050-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="a4050-138">Per modificare il colore di sfondo predefinito del riquadro della console impostandolo sul blu, nel file del profilo digitare: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="a4050-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="a4050-139">Per altre informazioni sulla variabile `$psISE` vedere [Riferimenti al modello a oggetti di Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="a4050-139">For more information about the `$psISE` variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="a4050-140">Per modificare le dimensioni del carattere impostandole su 20, nel file del profilo digitare: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="a4050-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="a4050-141">Per salvare il file del profilo, nel menu **File** fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="a4050-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="a4050-142">Le personalizzazioni verranno applicate alla successiva apertura di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4050-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4050-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4050-143">See Also</span></span>

- [<span data-ttu-id="a4050-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a4050-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="a4050-145">Introduzione a Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4050-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
