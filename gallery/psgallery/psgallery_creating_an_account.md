---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: Creazione di un account PowerShell Gallery
ms.openlocfilehash: e21575320f220c1ba7ecd9bd464a814b3ebf49d9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="creating-a-powershell-gallery-account" class="xliff"></a>
## Creazione di un account PowerShell Gallery

Prima di pubblicare qualsiasi elemento in PowerShell Gallery, è necessario creare un account di PowerShell Gallery. Gli account di PowerShell Gallery devono essere collegati a un account di posta elettronica Azure Active Directory o a un account di posta elettronica Microsoft, con un dominio di outlook.com, hotmail.com e così via.

Per creare un account di PowerShell Gallery, accedere a https://PowerShellGallery.com e fare clic su "Register" (Registrazione) come nell'immagine riprodotta qui sotto. 

![Registrazione di un nuovo account](./images/CreatingAccount-Register.png)

Nella pagina successiva per usare un account Azure Active Directory, selezionare "Work or School Account" (Account aziendale o dell'istituto di istruzione) e accedere con il proprio account. Per usare un account Microsoft, ad esempio con un dominio hotmail.com o outlook.com, scegliere "Personal Account" (Account personale) ed eseguire l'accesso. 

Una volta eseguito l'accesso, verrà richiesto di creare un nome utente per PowerShell Gallery. Esaminare le condizioni per l'utilizzo e l'informativa sulla privacy di cui viene specificato il collegamento, immettere un nome utente e fare clic su Register (Registrazione).

Nota: una volta creato l'account, non è possibile modificarne il nome.  
Per altre informazioni in merito, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners).

<a id="recommended-practices-for-powershell-gallery-accounts" class="xliff"></a>
## Procedure consigliate per gli account di PowerShell Gallery

È importante che l'account di posta elettronica usato con l'account di PowerShell Gallery venga controllato attivamente.
Tutte le eventuali comunicazioni con i proprietari di elementi di PowerShell Gallery avvengono tramite l'indirizzo di posta elettronica associato all'account di PowerShell Gallery.
Se non è possibile contattare un proprietario di elementi, in alcune circostanze potrebbe essere necessario richiedere al team Operazioni di eliminare un elemento.

Le organizzazioni che pubblicano in PowerShell Gallery spesso creano un account unico per lo scopo in outlook.com o in un altro dominio dell'account Microsoft.
In molti casi tale account non viene controllato regolarmente. La procedura consigliata in questi casi è di usare l'inoltro di Outlook per inviare posta elettronica a un altro account, in genere all'interno dell'organizzazione, che verrà controllato dal proprietario dell'elemento.

Se vi sono più proprietari associati a un elemento, tutte le comunicazioni provenienti da PowerShell Gallery verranno inviate a tutti i proprietari.
Per altre informazioni sull'aggiunta di proprietari a un elemento, vedere [Gestione dei proprietari di elementi](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners). 

