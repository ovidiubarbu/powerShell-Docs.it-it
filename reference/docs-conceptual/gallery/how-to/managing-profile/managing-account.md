---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Impostazioni dell'account di PowerShell Gallery
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328032"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="140a5-103">Impostazioni dell'account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="140a5-104">Un account di PowerShell Gallery è un nome visibile pubblicamente collegato a un'identità.</span><span class="sxs-lookup"><span data-stu-id="140a5-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="140a5-105">Tale identità è un ID Microsoft, ad esempio `user@hotmail.com` o `user@outlook.com`, o un account di Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="140a5-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="140a5-106">PowerShell Gallery offre le seguenti impostazioni dell'account:</span><span class="sxs-lookup"><span data-stu-id="140a5-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="140a5-107">L'account di posta elettronica associato all'account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="140a5-108">Opzioni per le notifiche di posta elettronica inviate da PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="140a5-109">L'account utente associato all'account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="140a5-110">L'immagine associata all'account di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="140a5-111">Indirizzo di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="140a5-111">Email address</span></span>

<span data-ttu-id="140a5-112">L'indirizzo di posta elettronica è la destinazione delle notifiche di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="140a5-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="140a5-113">Non deve necessariamente corrispondere all'account di accesso.</span><span class="sxs-lookup"><span data-stu-id="140a5-113">It does not have to match the login account.</span></span> <span data-ttu-id="140a5-114">Si può usare qualsiasi account di posta elettronica a cui si ha accesso.</span><span class="sxs-lookup"><span data-stu-id="140a5-114">You may use any email account you have access to.</span></span> <span data-ttu-id="140a5-115">L'indirizzo di posta elettronica non viene mai comunicato ad altri utenti direttamente da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="140a5-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Modifica dell'indirizzo di posta elettronica](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="140a5-117">Quando si immette un nuovo indirizzo di posta elettronica, PowerShell Gallery invia un messaggio di verifica a tale indirizzo.</span><span class="sxs-lookup"><span data-stu-id="140a5-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="140a5-118">Il messaggio di verifica contiene un collegamento a PowerShell Gallery per completare il processo di modifica.</span><span class="sxs-lookup"><span data-stu-id="140a5-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="140a5-119">Se non si completa il processo di verifica, tutte le notifiche vengono inviate all'indirizzo precedente.</span><span class="sxs-lookup"><span data-stu-id="140a5-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="140a5-120">Notifiche di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="140a5-120">Email notifications</span></span>

<span data-ttu-id="140a5-121">PowerShell Gallery offre le seguenti opzioni di notifica:</span><span class="sxs-lookup"><span data-stu-id="140a5-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="140a5-122">Gli altri utenti possono contattare l'utente usando PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="140a5-123">L'utente riceve una notifica quando viene eseguito il push di un pacchetto in PowerShell Gallery usando il suo account</span><span class="sxs-lookup"><span data-stu-id="140a5-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Modifica dell'indirizzo di posta elettronica](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="140a5-125">Come indicato nella pagina, le notifiche critiche inviate da PowerShell Gallery non possono essere disabilitate.</span><span class="sxs-lookup"><span data-stu-id="140a5-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="140a5-126">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="140a5-126">These include:</span></span>

- <span data-ttu-id="140a5-127">Notifiche relative alla sicurezza</span><span class="sxs-lookup"><span data-stu-id="140a5-127">Security notifications</span></span>
- <span data-ttu-id="140a5-128">Notifiche relative alla gestione dell'account dagli amministratori di PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="140a5-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="140a5-129">Notifiche relative ai test eseguiti da PowerShell Gallery per gli inoltri effettuati dall'utente</span><span class="sxs-lookup"><span data-stu-id="140a5-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="140a5-130">Modificare l'account di accesso</span><span class="sxs-lookup"><span data-stu-id="140a5-130">Change your login account</span></span>

<span data-ttu-id="140a5-131">Per modificare l'account di accesso, è necessario accedere con l'account corrente.</span><span class="sxs-lookup"><span data-stu-id="140a5-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="140a5-132">Per completare la modifica, eseguire la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="140a5-132">Use the following steps to complete the change.</span></span>

![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="140a5-134">Fare clic su **Cambia account**.</span><span class="sxs-lookup"><span data-stu-id="140a5-134">Click on **Change Account**.</span></span> <span data-ttu-id="140a5-135">In una finestra popup viene spiegato che la modifica dell'account di accesso viene applicata a tutti gli usi dell'account in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="140a5-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="140a5-136">Esaminare le informazioni, quindi fare clic su **OK** per continuare.</span><span class="sxs-lookup"><span data-stu-id="140a5-136">Review the information, then click **OK** to continue.</span></span>

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="140a5-138">Viene quindi chiesto di accedere usando il _nuovo account_.</span><span class="sxs-lookup"><span data-stu-id="140a5-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="140a5-140">Quando fa clic su **Avanti**, un messaggio indica che si è connessi con l'account corrente.</span><span class="sxs-lookup"><span data-stu-id="140a5-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="140a5-141">Scegliere l'opzione che consente di **uscire e accedere di nuovo con un altro account**.</span><span class="sxs-lookup"><span data-stu-id="140a5-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="140a5-143">Immettere la password del nuovo account.</span><span class="sxs-lookup"><span data-stu-id="140a5-143">Enter the password of the new account.</span></span> <span data-ttu-id="140a5-144">Dopo aver immesso la password, si torna alla pagina delle impostazioni dell'account, che indica che l'account di accesso è stato aggiornato.</span><span class="sxs-lookup"><span data-stu-id="140a5-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="140a5-145">Abilitare l'autenticazione a due fattori</span><span class="sxs-lookup"><span data-stu-id="140a5-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="140a5-146">L'autenticazione a due fattori è consigliabile per tutti gli utenti che pubblicano manualmente in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="140a5-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="140a5-147">Per abilitare l'autenticazione a due fattori, l'account di accesso deve avere almeno due modalità di autenticazione registrate.</span><span class="sxs-lookup"><span data-stu-id="140a5-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="140a5-148">Una è la password e le altre modalità possono essere:</span><span class="sxs-lookup"><span data-stu-id="140a5-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="140a5-149">Un numero di telefono in grado di ricevere messaggi di testo</span><span class="sxs-lookup"><span data-stu-id="140a5-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="140a5-150">Un'applicazione di autenticatore registrata, ad esempio Microsoft Authenticator per il telefono cellulare</span><span class="sxs-lookup"><span data-stu-id="140a5-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="140a5-151">Questi tipi di autenticazione devono essere configurati nelle informazioni dell'account AAD o nelle impostazioni di sicurezza dell'account dell'ID Microsoft.</span><span class="sxs-lookup"><span data-stu-id="140a5-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="140a5-152">Dopo aver abilitato l'autenticazione a due fattori, è necessario eseguire l'autenticazione con le modalità di autenticazione configurate ogni volta che si accede a PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="140a5-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="140a5-153">L'abilitazione dell'autenticazione a due fattori per il sito di PowerShell Gallery non richiede l'abilitazione dell'autenticazione a due fattori per tutti gli usi dell'account di accesso.</span><span class="sxs-lookup"><span data-stu-id="140a5-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="140a5-154">Per altre informazioni, vedere le [informazioni sulla verifica in due passaggi](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="140a5-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="140a5-155">Modifica della foto del profilo</span><span class="sxs-lookup"><span data-stu-id="140a5-155">Change your profile picture</span></span>

<span data-ttu-id="140a5-156">PowerShell Gallery si basa su Gravatar per archiviare e visualizzare l'immagine associata al profilo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="140a5-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="140a5-157">Per aggiornare l'immagine del profilo, visitare il sito [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="140a5-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
