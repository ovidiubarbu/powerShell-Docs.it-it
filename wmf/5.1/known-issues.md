---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Problemi noti in WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084964"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="fc9dd-103">Problemi noti in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="fc9dd-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="fc9dd-104">Queste informazioni sono soggette a modifiche.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="fc9dd-105">Avvio del collegamento di PowerShell come amministratore</span><span class="sxs-lookup"><span data-stu-id="fc9dd-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="fc9dd-106">Dopo l'installazione di WMF, se si tenta di avviare PowerShell come amministratore dal collegamento, è possibile che venga visualizzato il messaggio "Errore non specificato".</span><span class="sxs-lookup"><span data-stu-id="fc9dd-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="fc9dd-107">Riaprire il collegamento senza usare l'accesso come amministratore e il collegamento ora funziona anche come amministratore.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="fc9dd-108">Pester</span><span class="sxs-lookup"><span data-stu-id="fc9dd-108">Pester</span></span>

<span data-ttu-id="fc9dd-109">In questa versione vi sono due problemi che è necessario tenere presenti quando si usa Pester o Nano Server:</span><span class="sxs-lookup"><span data-stu-id="fc9dd-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="fc9dd-110">L'esecuzione di test su Pester può generare errori a causa delle differenze tra FULL CLR e CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="fc9dd-111">In particolare, il metodo di convalida non è disponibile nel tipo XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="fc9dd-112">Sei test che tentano di convalidare lo schema dei log di output NUnit hanno esito negativo.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="fc9dd-113">Attualmente un test code coverage non riesce perché la risorsa DSC *WindowsFeature* non esiste in Nano Server.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="fc9dd-114">Tuttavia, questi errori sono in genere innocui e possono essere ignorati.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="fc9dd-115">Convalida dell'operazione</span><span class="sxs-lookup"><span data-stu-id="fc9dd-115">Operation Validation</span></span>

- <span data-ttu-id="fc9dd-116">`Update-Help` ha esito negativo per il modulo Microsoft.PowerShell.Operation.Validation a causa di un URI della guida non funzionante</span><span class="sxs-lookup"><span data-stu-id="fc9dd-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="fc9dd-117">DSC dopo la disinstallazione di WMF</span><span class="sxs-lookup"><span data-stu-id="fc9dd-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="fc9dd-118">La disinstallazione di WMF non comporta l'eliminazione dei documenti MOF di DSC dalla cartella di configurazione.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="fc9dd-119">DSC non funzionerà correttamente se i documenti MOF contengono proprietà più recenti che non sono disponibili nei sistemi precedenti.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="fc9dd-120">In questo caso, eseguire lo script seguente dalla console di PowerShell con privilegi elevati per pulire gli stati di DSC.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-120">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="fc9dd-121">Account virtuali JEA</span><span class="sxs-lookup"><span data-stu-id="fc9dd-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="fc9dd-122">Le configurazioni di endpoint e sessioni JEA impostate per l'uso di account virtuali in WMF 5.0 non saranno configurate per l'uso di un account virtuale dopo l'aggiornamento a WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="fc9dd-123">Questo significa che i comandi eseguiti in sessioni JEA verranno eseguiti nel contesto dell'identità dell'utente connesso anziché di un account amministratore temporaneo, impedendo potenzialmente all'utente di eseguire comandi che richiedono privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="fc9dd-124">Per ripristinare gli account virtuali, è necessario annullare la registrazione e registrare nuovamente le configurazioni di sessioni che usano account virtuali.</span><span class="sxs-lookup"><span data-stu-id="fc9dd-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```