---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Creazione di un account PowerShell Gallery
ms.openlocfilehash: f43d7e65bb8bf9a9bbdda9790cc622786377fa38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278782"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="62c66-103">Creazione di un account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="62c66-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="62c66-104">Prima di pubblicare qualsiasi elemento in PowerShell Gallery, è necessario creare un account di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="62c66-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="62c66-105">Gli account di PowerShell Gallery devono essere collegati a un account di accesso abilitato per la posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="62c66-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="62c66-106">Questo account può essere un account di Azure Active Directory o un ID Microsoft, ad esempio un account di posta elettronica di outlook.com o hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="62c66-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="62c66-107">Per creare un account di PowerShell Gallery, accedere a [https://PowerShellGallery.com](https://PowerShellGallery.com) e fare clic su **Accedi** come nell'immagine che segue.</span><span class="sxs-lookup"><span data-stu-id="62c66-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrazione di un nuovo account](media/creating-an-account/CreateAccount-Register.png)

<span data-ttu-id="62c66-109">Per usare un account Azure Active Directory, selezionare **Account aziendale o dell'istituto di istruzione** e accedere con il proprio account.</span><span class="sxs-lookup"><span data-stu-id="62c66-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="62c66-110">Per usare un ID Microsoft, scegliere **Account personale** ed eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="62c66-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="62c66-111">Quindi, viene richiesto di creare un nome utente per PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="62c66-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="62c66-112">Esaminare le condizioni per l'utilizzo e l'informativa sulla privacy, immettere un nome utente e fare clic su **Registra**.</span><span class="sxs-lookup"><span data-stu-id="62c66-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="62c66-113">Dopo aver creato l'account, non è possibile modificarne il nome.</span><span class="sxs-lookup"><span data-stu-id="62c66-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="62c66-114">Per altre informazioni, vedere [Gestione dei proprietari di pacchetti](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="62c66-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="62c66-115">Procedure consigliate per gli account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="62c66-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="62c66-116">È importante monitorare attivamente l'account di posta elettronica usato con l'account di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="62c66-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="62c66-117">Tutte le comunicazioni con i proprietari di pacchetti di PowerShell Gallery avvengono attraverso questo indirizzo di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="62c66-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="62c66-118">Se il team addetto alle operazioni di PowerShell Gallery non riesce a contattare un proprietario di pacchetti, può essere necessario eliminare un pacchetto.</span><span class="sxs-lookup"><span data-stu-id="62c66-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="62c66-119">Le organizzazioni che pubblicano in PowerShell Gallery spesso creano un account esterno unico a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="62c66-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="62c66-120">Si consiglia di usare l'inoltro di posta elettronica per inoltrare le notifiche a un indirizzo interno alla propria organizzazione.</span><span class="sxs-lookup"><span data-stu-id="62c66-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="62c66-121">Quando più proprietari sono associati a un pacchetto, tutte le notifiche di PowerShell Gallery vengono inviate a tutti i proprietari.</span><span class="sxs-lookup"><span data-stu-id="62c66-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="62c66-122">Per altre informazioni, vedere [Gestione dei proprietari di pacchetti](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="62c66-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
