---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Creazione di un account PowerShell Gallery
ms.openlocfilehash: 4a44b51967ea8acdd331f6b3c682fc5884bd2f54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="74a76-103">Creazione di un account PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="74a76-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="74a76-104">Prima di pubblicare qualsiasi elemento in PowerShell Gallery, è necessario creare un account di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="74a76-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="74a76-105">Gli account di PowerShell Gallery devono essere collegati a un account di posta elettronica Azure Active Directory o a un account di posta elettronica Microsoft, con un dominio di outlook.com, hotmail.com e così via.</span><span class="sxs-lookup"><span data-stu-id="74a76-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="74a76-106">Per creare un account di PowerShell Gallery, accedere a https://PowerShellGallery.com e fare clic su "Register" (Registrazione) come nell'immagine che segue.</span><span class="sxs-lookup"><span data-stu-id="74a76-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Registrazione di un nuovo account](../../Images/CreatingAccount-Register.png)

<span data-ttu-id="74a76-108">Nella pagina successiva per usare un account Azure Active Directory, selezionare "Work or School Account" (Account aziendale o dell'istituto di istruzione) e accedere con il proprio account.</span><span class="sxs-lookup"><span data-stu-id="74a76-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="74a76-109">Per usare un account Microsoft, ad esempio con un dominio hotmail.com o outlook.com, scegliere "Personal Account" (Account personale) ed eseguire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="74a76-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="74a76-110">Una volta eseguito l'accesso, verrà richiesto di creare un nome utente per PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="74a76-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="74a76-111">Esaminare le condizioni per l'utilizzo e l'informativa sulla privacy di cui viene specificato il collegamento, immettere un nome utente e fare clic su Register (Registrazione).</span><span class="sxs-lookup"><span data-stu-id="74a76-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="74a76-112">Nota: una volta creato l'account, non è possibile modificarne il nome.</span><span class="sxs-lookup"><span data-stu-id="74a76-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="74a76-113">Per altre informazioni in merito, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).</span><span class="sxs-lookup"><span data-stu-id="74a76-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="74a76-114">Procedure consigliate per gli account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="74a76-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="74a76-115">È importante che l'account di posta elettronica usato con l'account di PowerShell Gallery venga controllato attivamente.</span><span class="sxs-lookup"><span data-stu-id="74a76-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="74a76-116">Tutte le eventuali comunicazioni con i proprietari di elementi di PowerShell Gallery avvengono tramite l'indirizzo di posta elettronica associato all'account di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="74a76-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="74a76-117">Se non è possibile contattare un proprietario di elementi, in alcune circostanze potrebbe essere necessario richiedere al team Operazioni di eliminare un elemento.</span><span class="sxs-lookup"><span data-stu-id="74a76-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="74a76-118">Le organizzazioni che pubblicano in PowerShell Gallery spesso creano un account unico per lo scopo in outlook.com o in un altro dominio dell'account Microsoft.</span><span class="sxs-lookup"><span data-stu-id="74a76-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="74a76-119">In molti casi tale account non viene controllato regolarmente.</span><span class="sxs-lookup"><span data-stu-id="74a76-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="74a76-120">La procedura consigliata in questi casi è di usare l'inoltro di Outlook per inviare posta elettronica a un altro account, in genere all'interno dell'organizzazione, che verrà controllato dal proprietario dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="74a76-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="74a76-121">Se vi sono più proprietari associati a un elemento, tutte le comunicazioni provenienti da PowerShell Gallery verranno inviate a tutti i proprietari.</span><span class="sxs-lookup"><span data-stu-id="74a76-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="74a76-122">Per altre informazioni sull'aggiunta di proprietari a un elemento, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).</span><span class="sxs-lookup"><span data-stu-id="74a76-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>