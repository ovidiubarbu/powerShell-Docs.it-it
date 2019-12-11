---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Pubblicazione di feedback sui social media o nei commenti
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327882"
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Pubblicazione di feedback sui social media o nei commenti

PowerShell Gallery supporta due approcci per gli utenti che vogliono offrire commenti e suggerimenti pubblici su un pacchetto:

- Usare i collegamenti sul lato sinistro per condividere un pacchetto su siti di social media quali Twitter, LinkedIn o Facebook.
- Usare la funzionalità dei commenti per inviare commenti su un pacchetto e consentire agli autori di monitorare i commenti sui pacchetti che pubblicano.

## <a name="social-media-feedback"></a>Commenti e suggerimenti sui social media

Per ogni pacchetto di PowerShell Gallery, sul lato sinistro della pagina sono disponibili collegamenti a Facebook, LinkedIn e Twitter.
Se si fa clic su tali collegamenti viene aperto il sito di uno dei social media, ed è possibile condividere rapidamente un collegamento al pacchetto.

Gli utenti devono eseguire l'accesso al sito che hanno scelto per condividere il pacchetto di PowerShell Gallery.

Gli utenti sono invitati a eseguire questa operazione se pensano di consigliare un pacchetto ad altri utenti.
PowerShell Gallery verifica tutte le condivisioni di un dato pacchetto sui social media e visualizza il numero di volte in cui il pacchetto è stato condiviso in ognuno di essi.
Poiché tale indicazione visualizza solo il numero di volte in cui un pacchetto è stato condiviso, verrà interpretata dagli altri utenti come il numero di "like" del pacchetto.

## <a name="comments"></a>Commenti

> [!IMPORTANT]
> L'aggiunta di commenti Livefyre viene offerta da un fornitore di terze parti e non è più supportata.
> L'aggiunta di commenti Livefyre non sarà più disponibile in PowerShell Gallery a partire dal 05/01/2019. 

PowerShell Gallery usa il servizio LiveFyre per consentire agli utenti di inviare commenti sui pacchetti.
Gli utenti che vogliono inviare consigli o commenti possono usare questa funzionalità per offrire commenti e suggerimenti visibili a chiunque visiti la pagina del pacchetto.
I proprietari del pacchetto possono seguire questi commenti e suggerimenti e riceveranno una notifica quando un utente inserisce un commento.

Il sistema dei commenti è basato su LiveFyre, un servizio separato che non è gestito da Microsoft e richiede un account di accesso univoco.
La prima volta che si vuole lasciare un commento o seguire i commenti in uno dei pacchetti, verrà richiesto di creare un account LiveFyre.

Se è stato creato un account LiveFyre e si è eseguito l'accesso, è possibile elaborare un commento per offrire commenti e suggerimenti sul pacchetto e fare clic su "Post comment..." (Pubblica commento). Il commento non sarà visibile immediatamente.
I commenti per i pacchetti della raccolta vengono moderati dagli amministratori di PowerShell Gallery e tutti i post vengono rivisti dai moderatori prima di venire pubblicati ed essere visibili ad altri utenti.
Lo scopo di moderare i commenti è garantire che siano allineati con il comportamento pubblico in base a quanto contenuto nelle [Condizioni per l'utilizzo](https://www.powershellgallery.com/policies/Terms) di PowerShell Gallery.

I proprietari dei pacchetti sono invitati a seguire i commenti inviati a LiveFyre.
È necessario un account LiveFyre ed è consigliabile usare lo stesso indirizzo di posta elettronica usato per pubblicare il pacchetto in LiveFyre.
Per seguire i commenti, accedere a LiveFyre e passare a qualsiasi pacchetto per cui si è elencati come proprietari.
Sotto la casella dei commenti, nella parte inferiore di ogni pacchetto viene visualizzato "+Follow" (Segui).
Quando si fa clic su questa opzione, LiveFyre invia un messaggio di posta elettronica all'indirizzo registrato ogni volta in cui vengono aggiunti nuovi commenti per il pacchetto.
