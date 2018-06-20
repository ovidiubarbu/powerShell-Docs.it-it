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
ms.locfileid: "34219566"
---
## <a name="creating-a-powershell-gallery-account"></a>Creazione di un account PowerShell Gallery

Prima di pubblicare qualsiasi elemento in PowerShell Gallery, è necessario creare un account di PowerShell Gallery.
Gli account di PowerShell Gallery devono essere collegati a un account di posta elettronica Azure Active Directory o a un account di posta elettronica Microsoft, con un dominio di outlook.com, hotmail.com e così via.

Per creare un account di PowerShell Gallery, accedere a https://PowerShellGallery.com e fare clic su "Register" (Registrazione) come nell'immagine che segue.

![Registrazione di un nuovo account](../../Images/CreatingAccount-Register.png)

Nella pagina successiva per usare un account Azure Active Directory, selezionare "Work or School Account" (Account aziendale o dell'istituto di istruzione) e accedere con il proprio account.
Per usare un account Microsoft, ad esempio con un dominio hotmail.com o outlook.com, scegliere "Personal Account" (Account personale) ed eseguire l'accesso.

Una volta eseguito l'accesso, verrà richiesto di creare un nome utente per PowerShell Gallery.
Esaminare le condizioni per l'utilizzo e l'informativa sulla privacy di cui viene specificato il collegamento, immettere un nome utente e fare clic su Register (Registrazione).

Nota: una volta creato l'account, non è possibile modificarne il nome.
Per altre informazioni in merito, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Procedure consigliate per gli account di PowerShell Gallery

È importante che l'account di posta elettronica usato con l'account di PowerShell Gallery venga controllato attivamente.
Tutte le eventuali comunicazioni con i proprietari di elementi di PowerShell Gallery avvengono tramite l'indirizzo di posta elettronica associato all'account di PowerShell Gallery.
Se non è possibile contattare un proprietario di elementi, in alcune circostanze potrebbe essere necessario richiedere al team Operazioni di eliminare un elemento.

Le organizzazioni che pubblicano in PowerShell Gallery spesso creano un account unico per lo scopo in outlook.com o in un altro dominio dell'account Microsoft.
In molti casi tale account non viene controllato regolarmente.
La procedura consigliata in questi casi è di usare l'inoltro di Outlook per inviare posta elettronica a un altro account, in genere all'interno dell'organizzazione, che verrà controllato dal proprietario dell'elemento.

Se vi sono più proprietari associati a un elemento, tutte le comunicazioni provenienti da PowerShell Gallery verranno inviate a tutti i proprietari.
Per altre informazioni sull'aggiunta di proprietari a un elemento, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners).