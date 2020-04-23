---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Usare credenziali con risorse DSC
ms.openlocfilehash: fea2e3cad8d081c17853e127203f1d40d98c5de2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953978"
---
# <a name="use-credentials-with-dsc-resources"></a><span data-ttu-id="264c4-103">Usare credenziali con risorse DSC</span><span class="sxs-lookup"><span data-stu-id="264c4-103">Use Credentials with DSC Resources</span></span>

> <span data-ttu-id="264c4-104">Si applica a: Windows PowerShell 5.0, Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="264c4-104">Applies To: Windows PowerShell 5.0, Windows PowerShell 5.1</span></span>

<span data-ttu-id="264c4-105">È possibile eseguire una risorsa DSC con un set di credenziali specificato usando la proprietà **PsDscRunAsCredential** nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="264c4-105">You can run a DSC resource under a specified set of credentials by using the automatic **PsDscRunAsCredential** property in the configuration.</span></span> <span data-ttu-id="264c4-106">Per impostazione predefinita, DSC esegue ogni risorsa come account di sistema.</span><span class="sxs-lookup"><span data-stu-id="264c4-106">By default, DSC runs each resource as the system account.</span></span> <span data-ttu-id="264c4-107">In alcuni casi può essere necessario eseguirla con le credenziali di un utente, ad esempio quando si installano pacchetti MSI in un contesto utente specifico, si impostano le chiavi del Registro di sistema di un utente, si accede a una directory locale specifica dell'utente o si accede a una condivisione di rete.</span><span class="sxs-lookup"><span data-stu-id="264c4-107">There are times when running as a user is necessary, such as installing MSI packages in a specific user context, setting a user's registry keys, accessing a user's specific local directory, or accessing a network share.</span></span> <span data-ttu-id="264c4-108">**SeInteractiveLogonRight** è obbligatorio, dal computer di destinazione, per qualsiasi account specificato per **PSDSCRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="264c4-108">The **SeInteractiveLogonRight** is required, by the target machine, for any account you specify to **PSDSCRunAsCredential**.</span></span> <span data-ttu-id="264c4-109">Per altre informazioni, vedere [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants) (Costanti per i diritti utente).</span><span class="sxs-lookup"><span data-stu-id="264c4-109">For more information, see [Account Rights Constants](/windows/desktop/secauthz/account-rights-constants).</span></span>

<span data-ttu-id="264c4-110">Ogni risorsa DSC ha una proprietà **PsDscRunAsCredential** che può essere impostare su qualsiasi credenziale utente (oggetto [PSCredential](/dotnet/api/system.management.automation.pscredential)).</span><span class="sxs-lookup"><span data-stu-id="264c4-110">Every DSC resource has a **PsDscRunAsCredential** property that can be set to any user credentials (a [PSCredential](/dotnet/api/system.management.automation.pscredential) object).</span></span> <span data-ttu-id="264c4-111">Le credenziali possono essere hardcoded come il valore della proprietà nella configurazione oppure è possibile impostare il valore su [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), che chiederà all'utente le credenziali in fase di compilazione della configurazione. Per informazioni sulla compilazione di configurazioni, vedere [Configurazioni DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="264c4-111">The credential can be hard-coded as the value of the property in the configuration, or you can set the value to [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential), which will prompt the user for a credential when the configuration is compiled (for information about compiling configurations, see [Configurations](configurations.md).</span></span>

> [!NOTE]
> <span data-ttu-id="264c4-112">In PowerShell 5.0 non è supportato l'uso della proprietà **PsDscRunAsCredential** nelle configurazioni che chiamano risorse composite.</span><span class="sxs-lookup"><span data-stu-id="264c4-112">In PowerShell 5.0, using the **PsDscRunAsCredential** property in configurations calling composite resources was not supported.</span></span> <span data-ttu-id="264c4-113">In PowerShell 5.1 la proprietà **PsDscRunAsCredential** è supportata nelle configurazioni che chiamano risorse composite.</span><span class="sxs-lookup"><span data-stu-id="264c4-113">In PowerShell 5.1, the **PsDscRunAsCredential** property is supported in configurations calling composite resources.</span></span> <span data-ttu-id="264c4-114">La proprietà **PsDscRunAsCredential** non è disponibile in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="264c4-114">The **PsDscRunAsCredential** property is not available in PowerShell 4.0.</span></span>

<span data-ttu-id="264c4-115">Nell'esempio seguente `Get-Credential` viene usato per richiedere le credenziali all'utente.</span><span class="sxs-lookup"><span data-stu-id="264c4-115">In the following example, `Get-Credential` is used to prompt the user for credentials.</span></span> <span data-ttu-id="264c4-116">La risorsa **Registry** viene usata per modificare la chiave del Registro di sistema che specifica il colore di sfondo della finestra del prompt dei comandi di Windows.</span><span class="sxs-lookup"><span data-stu-id="264c4-116">The **Registry** resource is used to change the registry key that specifies the background color for the Windows command prompt window.</span></span>

```powershell
Configuration ChangeCmdBackGroundColor
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        Registry CmdPath
        {
            Key                  = 'HKEY_CURRENT_USER\SOFTWARE\Microsoft\Command Processor'
            ValueName            = 'DefaultColor'
            ValueData            = '1F'
            ValueType            = 'DWORD'
            Ensure               = 'Present'
            Force                = $true
            Hex                  = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost';
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

ChangeCmdBackGroundColor -ConfigurationData $configData
```

> [!NOTE]
> <span data-ttu-id="264c4-117">In questo esempio si presuppone che sia disponibile un certificato valido in `C:\publicKeys\targetNode.cer` e che l'identificazione personale del certificato sia il valore visualizzato.</span><span class="sxs-lookup"><span data-stu-id="264c4-117">This example assumes that you have a valid certificate at `C:\publicKeys\targetNode.cer`, and that the thumbprint of that certificate is the value shown.</span></span> <span data-ttu-id="264c4-118">Per informazioni sulla crittografia delle credenziali nei file MOF della configurazione DSC, vedere [Protezione del file MOF](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="264c4-118">For information about encrypting credentials in DSC configuration MOF files, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>
