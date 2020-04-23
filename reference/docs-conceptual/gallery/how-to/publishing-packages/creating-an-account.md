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
# <a name="creating-a-powershell-gallery-account"></a>Creazione di un account PowerShell Gallery

Prima di pubblicare qualsiasi elemento in PowerShell Gallery, è necessario creare un account di PowerShell Gallery.
Gli account di PowerShell Gallery devono essere collegati a un account di accesso abilitato per la posta elettronica. Questo account può essere un account di Azure Active Directory o un ID Microsoft, ad esempio un account di posta elettronica di outlook.com o hotmail.com.

Per creare un account di PowerShell Gallery, accedere a [https://PowerShellGallery.com](https://PowerShellGallery.com) e fare clic su **Accedi** come nell'immagine che segue.

![Registrazione di un nuovo account](media/creating-an-account/CreateAccount-Register.png)

Per usare un account Azure Active Directory, selezionare **Account aziendale o dell'istituto di istruzione** e accedere con il proprio account. Per usare un ID Microsoft, scegliere **Account personale** ed eseguire l'accesso.

Quindi, viene richiesto di creare un nome utente per PowerShell Gallery. Esaminare le condizioni per l'utilizzo e l'informativa sulla privacy, immettere un nome utente e fare clic su **Registra**.

> [!NOTE]
> Dopo aver creato l'account, non è possibile modificarne il nome. Per altre informazioni, vedere [Gestione dei proprietari di pacchetti](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Procedure consigliate per gli account di PowerShell Gallery

È importante monitorare attivamente l'account di posta elettronica usato con l'account di PowerShell Gallery. Tutte le comunicazioni con i proprietari di pacchetti di PowerShell Gallery avvengono attraverso questo indirizzo di posta elettronica. Se il team addetto alle operazioni di PowerShell Gallery non riesce a contattare un proprietario di pacchetti, può essere necessario eliminare un pacchetto.

Le organizzazioni che pubblicano in PowerShell Gallery spesso creano un account esterno unico a tale scopo. Si consiglia di usare l'inoltro di posta elettronica per inoltrare le notifiche a un indirizzo interno alla propria organizzazione.

Quando più proprietari sono associati a un pacchetto, tutte le notifiche di PowerShell Gallery vengono inviate a tutti i proprietari. Per altre informazioni, vedere [Gestione dei proprietari di pacchetti](managing-package-owners.md).
