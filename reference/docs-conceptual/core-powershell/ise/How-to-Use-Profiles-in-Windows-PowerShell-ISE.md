---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Modalità di utilizzo dei profili in Windows PowerShell ISE"
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="68482-103">Modalità di utilizzo dei profili in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="68482-103">How to Use Profiles in Windows PowerShell ISE</span></span>
<span data-ttu-id="68482-104">Questo argomento illustra come usare i profili in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="68482-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="68482-105">Prima di eseguire le attività in questa sezione, è consigliabile consultare [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)) oppure digitare `Get-Help about_Profiles` nel riquadro della console e premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="68482-105">We recommend that before performing the tasks in this section, you review [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="68482-106">Un profilo è uno script di Windows PowerShell ISE che viene eseguito automaticamente quando si avvia una nuova sessione.</span><span class="sxs-lookup"><span data-stu-id="68482-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="68482-107">È possibile creare uno o più profili di Windows PowerShell per Windows PowerShell ISE e usarli per configurare l'ambiente Windows PowerShell o Windows PowerShell ISE, prepararlo per l'uso, con le variabili, gli alias, le funzioni e le preferenze di colore e tipo di carattere che si vuole avere a disposizione.</span><span class="sxs-lookup"><span data-stu-id="68482-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="68482-108">Il profilo interessa ogni sessione di Windows PowerShell ISE avviata.</span><span class="sxs-lookup"><span data-stu-id="68482-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="68482-109">I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire gli script e caricare un profilo.</span><span class="sxs-lookup"><span data-stu-id="68482-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="68482-110">I criteri di esecuzione predefiniti, "Restricted", impediscono l'esecuzione di tutti gli script, inclusi i profili.</span><span class="sxs-lookup"><span data-stu-id="68482-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="68482-111">Se si usano i criteri "Restricted", il profilo non potrà essere caricato.</span><span class="sxs-lookup"><span data-stu-id="68482-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="68482-112">Per altre informazioni sui criteri di esecuzione, vedere [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span><span class="sxs-lookup"><span data-stu-id="68482-112">For more information about execution policy, see [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="68482-113">Selezione di un profilo da usare in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="68482-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>
<span data-ttu-id="68482-114">Windows PowerShell ISE supporta i profili per l'utente corrente e per tutti gli utenti.</span><span class="sxs-lookup"><span data-stu-id="68482-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="68482-115">Supporta anche i profili Windows PowerShell che si applicano a tutti gli host.</span><span class="sxs-lookup"><span data-stu-id="68482-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="68482-116">Il profilo usato dipende da come si usano Windows PowerShell e Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="68482-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="68482-117">Se si usa solo Windows PowerShell ISE per eseguire Windows PowerShell, salvare tutti gli elementi in uno dei profili ISE specifici, ad esempio il profilo CurrentUserCurrentHost per Windows PowerShell ISE o il profilo AllUsersCurrentHost per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="68482-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="68482-118">Se si usano più programmi host per l'esecuzione di Windows PowerShell, salvare funzioni, alias, variabili e comandi in un profilo che interessa tutti i programmi host, ad esempio il profilo CurrentUserAllHosts o il profilo AllUsersAllHosts, e quindi salvare le funzionalità specifiche di ISE, come la personalizzazione di colori e tipi di carattere, nel profilo CurrentUserCurrentHost per il profilo di Windows PowerShell ISE o il profilo AllUsersCurrentHost per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="68482-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="68482-119">I seguenti profili possono essere creati e usati in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="68482-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="68482-120">Ogni profilo viene salvato nel proprio percorso specifico.</span><span class="sxs-lookup"><span data-stu-id="68482-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="68482-121">Tipo di profilo</span><span class="sxs-lookup"><span data-stu-id="68482-121">Profile Type</span></span> | <span data-ttu-id="68482-122">Percorso del profilo</span><span class="sxs-lookup"><span data-stu-id="68482-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="68482-123">**Utente corrente, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="68482-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="68482-124">`$PROFILE.CurrentUserCurrentHost` o `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="68482-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="68482-125">**Tutti gli utenti, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="68482-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="68482-126">**Utente corrente, tutti gli host**</span><span class="sxs-lookup"><span data-stu-id="68482-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="68482-127">**Tutti gli utenti, tutti gli host**</span><span class="sxs-lookup"><span data-stu-id="68482-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="68482-128">Per creare un nuovo profilo</span><span class="sxs-lookup"><span data-stu-id="68482-128">To create a new profile</span></span>
<span data-ttu-id="68482-129">Per creare un nuovo profilo "Utente corrente, Windows PowerShell ISE", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="68482-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="68482-130">Per creare un nuovo profilo "Tutti gli utenti, Windows PowerShell ISE", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="68482-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="68482-131">Per creare un nuovo profilo "Utente corrente, tutti gli host", eseguire questo comando:</span><span class="sxs-lookup"><span data-stu-id="68482-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="68482-132">Per creare un nuovo profilo "Tutti gli utenti, tutti gli host", digitare:</span><span class="sxs-lookup"><span data-stu-id="68482-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="68482-133">Per modificare un profilo</span><span class="sxs-lookup"><span data-stu-id="68482-133">To edit a profile</span></span>

1. <span data-ttu-id="68482-134">Per aprire il profilo, eseguire il comando psedit con la variabile che specifica il profilo da modificare.</span><span class="sxs-lookup"><span data-stu-id="68482-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="68482-135">Ad esempio, per aprire il profilo "Utente corrente, Windows PowerShell ISE", digitare: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="68482-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="68482-136">Aggiungere alcuni elementi al profilo.</span><span class="sxs-lookup"><span data-stu-id="68482-136">Add some items to your profile.</span></span> <span data-ttu-id="68482-137">Di seguito sono riportati alcuni esempi per iniziare:</span><span class="sxs-lookup"><span data-stu-id="68482-137">The following are a few examples to get you started:</span></span>

    -   <span data-ttu-id="68482-138">Per modificare il colore di sfondo predefinito del riquadro della console impostandolo sul blu, nel file del profilo digitare: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="68482-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="68482-139">Per altre informazioni sulla variabile $psISE, vedere [Riferimenti al modello a oggetti di Windows PowerShell ISE](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="68482-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

    -   <span data-ttu-id="68482-140">Per modificare le dimensioni del carattere impostandole su 20, nel file del profilo digitare: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="68482-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="68482-141">Per salvare il file del profilo, nel menu **File** fare clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="68482-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="68482-142">Le personalizzazioni verranno applicate alla successiva apertura di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="68482-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="68482-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68482-143">See Also</span></span>
- <span data-ttu-id="68482-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span><span class="sxs-lookup"><span data-stu-id="68482-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span></span>
- [<span data-ttu-id="68482-145">Uso di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="68482-145">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

