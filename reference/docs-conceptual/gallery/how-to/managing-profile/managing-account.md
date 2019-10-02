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
# <a name="powershell-gallery-account-settings"></a>Impostazioni dell'account di PowerShell Gallery

Un account di PowerShell Gallery è un nome visibile pubblicamente collegato a un'identità. Tale identità è un ID Microsoft, ad esempio `user@hotmail.com` o `user@outlook.com`, o un account di Azure Active Directory.

PowerShell Gallery offre le seguenti impostazioni dell'account:

- L'account di posta elettronica associato all'account di PowerShell Gallery
- Opzioni per le notifiche di posta elettronica inviate da PowerShell Gallery
- L'account utente associato all'account di PowerShell Gallery
- L'immagine associata all'account di PowerShell Gallery

## <a name="email-address"></a>Indirizzo di posta elettronica

L'indirizzo di posta elettronica è la destinazione delle notifiche di PowerShell Gallery. Non deve necessariamente corrispondere all'account di accesso. Si può usare qualsiasi account di posta elettronica a cui si ha accesso. L'indirizzo di posta elettronica non viene mai comunicato ad altri utenti direttamente da PowerShell Gallery.

![Modifica dell'indirizzo di posta elettronica](../../Images/PSGallery_AcccountEmailAddress.png)

Quando si immette un nuovo indirizzo di posta elettronica, PowerShell Gallery invia un messaggio di verifica a tale indirizzo. Il messaggio di verifica contiene un collegamento a PowerShell Gallery per completare il processo di modifica. Se non si completa il processo di verifica, tutte le notifiche vengono inviate all'indirizzo precedente.

## <a name="email-notifications"></a>Notifiche di posta elettronica

PowerShell Gallery offre le seguenti opzioni di notifica:

- Gli altri utenti possono contattare l'utente usando PowerShell Gallery
- L'utente riceve una notifica quando viene eseguito il push di un pacchetto in PowerShell Gallery usando il suo account

![Modifica dell'indirizzo di posta elettronica](../../Images/PSGallery_AccountEmailOptions.png)

Come indicato nella pagina, le notifiche critiche inviate da PowerShell Gallery non possono essere disabilitate.
Ad esempio:

- Notifiche relative alla sicurezza
- Notifiche relative alla gestione dell'account dagli amministratori di PowerShell Gallery
- Notifiche relative ai test eseguiti da PowerShell Gallery per gli inoltri effettuati dall'utente

## <a name="change-your-login-account"></a>Modificare l'account di accesso

Per modificare l'account di accesso, è necessario accedere con l'account corrente. Per completare la modifica, eseguire la procedura seguente.

![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountSettings.png)

1. Fare clic su **Cambia account**. In una finestra popup viene spiegato che la modifica dell'account di accesso viene applicata a tutti gli usi dell'account in PowerShell Gallery. Esaminare le informazioni, quindi fare clic su **OK** per continuare.

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-1.png)

2. Viene quindi chiesto di accedere usando il _nuovo account_.

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-2.png)

3. Quando fa clic su **Avanti**, un messaggio indica che si è connessi con l'account corrente.
   Scegliere l'opzione che consente di **uscire e accedere di nuovo con un altro account**.

   ![Impostazioni dell'account di accesso](../../Images/PSGallery_LoginAccountChange-3.png)

4. Immettere la password del nuovo account. Dopo aver immesso la password, si torna alla pagina delle impostazioni dell'account, che indica che l'account di accesso è stato aggiornato.


## <a name="enable-two-factor-authentication-2fa"></a>Abilitare l'autenticazione a due fattori

L'autenticazione a due fattori è consigliabile per tutti gli utenti che pubblicano manualmente in PowerShell Gallery. Per abilitare l'autenticazione a due fattori, l'account di accesso deve avere almeno due modalità di autenticazione registrate. Una è la password e le altre modalità possono essere:

- Un numero di telefono in grado di ricevere messaggi di testo
- Un'applicazione di autenticatore registrata, ad esempio Microsoft Authenticator per il telefono cellulare

Questi tipi di autenticazione devono essere configurati nelle informazioni dell'account AAD o nelle impostazioni di sicurezza dell'account dell'ID Microsoft.

Dopo aver abilitato l'autenticazione a due fattori, è necessario eseguire l'autenticazione con le modalità di autenticazione configurate ogni volta che si accede a PowerShell Gallery.

> [!IMPORTANT]
> L'abilitazione dell'autenticazione a due fattori per il sito di PowerShell Gallery non richiede l'abilitazione dell'autenticazione a due fattori per tutti gli usi dell'account di accesso. Per altre informazioni, vedere le [informazioni sulla verifica in due passaggi](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Modifica della foto del profilo

PowerShell Gallery si basa su Gravatar per archiviare e visualizzare l'immagine associata al profilo dell'utente. Per aggiornare l'immagine del profilo, visitare il sito [Gravatar.com](http://www.gravatar.com/).
