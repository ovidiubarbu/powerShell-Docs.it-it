---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: Pubblicazione di feedback sui social media o nei commenti
ms.openlocfilehash: 9e2a5a246b1caa37ad7b03e20c8f543b9e5cf530
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Pubblicazione di feedback sui social media o nei commenti

Powershell Gallery supporta due approcci per gli utenti che vogliono offrire commenti e suggerimenti pubblici su un elemento:

* Usare i collegamenti sul lato sinistro per condividere un elemento su siti di social media quali Twitter, LinkedIn o Facebook;
* Usare la funzionalità dei commenti per inviare commenti su un elemento e consentire agli autori di monitorare i commenti sugli elementi che pubblicano.

## <a name="social-media-feedback"></a>Commenti e suggerimenti sui social media
Per ogni elemento di PowerShell Gallery, sul lato sinistro della pagina sono disponibili collegamenti a Facebook, LinkedIn e Twitter.
Se si fa clic su tali collegamenti viene aperto il sito di uno dei social media, ed è possibile condividere rapidamente un collegamento all'elemento.

Gli utenti devono eseguire l'accesso al sito che hanno scelto per condividere l'elemento di PowerShell Gallery.

Gli utenti sono invitati a eseguire questa operazione se pensano di consigliare un elemento ad altri utenti.
PowerShell Gallery verifica tutte le condivisioni di un dato elemento sui social media e visualizza il numero di volte in cui l'elemento è stato condiviso in ognuno di essi.
Poiché tale indicazione visualizza solo il numero di volte in cui un elemento è stato condiviso, verrà interpretata dagli altri utenti come il numero di "like" dell'elemento.


## <a name="comments"></a>Commenti
PowerShell Gallery usa il servizio LiveFyre per consentire agli utenti di inviare commenti sugli elementi.
Gli utenti che vogliono inviare consigli o commenti possono usare questa funzionalità per offrire commenti e suggerimenti visibili a chiunque visiti la pagina dell'elemento.
I proprietari dell'elemento possono seguire questi commenti e suggerimenti e riceveranno una notifica quando un utente inserisce un commento.

Il sistema dei commenti è basato su LiveFyre, un servizio separato che non è gestito da Microsoft e richiede un account di accesso univoco.
La prima volta che si vuole lasciare un commento o seguire i commenti in uno degli elementi, verrà richiesto di creare un account LiveFyre.

Se è stato creato un account LiveFyre e si è eseguito l'accesso, è possibile elaborare un commento per offrire commenti e suggerimenti sull'elemento e fare clic su "Post comment..." (Pubblica commento). Il commento non sarà visibile immediatamente.
I commenti per gli elementi della raccolta vengono moderati dagli amministratori di PowerShell Gallery e tutti i post vengono rivisti dai moderatori prima di venire pubblicati ed essere visibili ad altri utenti.
Lo scopo di moderare i commenti è garantire che siano allineati con il comportamento pubblico in base a quanto contenuto nelle [Condizioni per l'utilizzo](https://www.powershellgallery.com/policies/Terms) di PowerShell Gallery.

I proprietari degli elementi sono invitati a seguire i commenti inviati a LiveFyre.
È necessario un account LiveFyre ed è consigliabile usare lo stesso indirizzo di posta elettronica usato per pubblicare l'elemento in LiveFyre.
Per seguire i commenti, accedere a LiveFyre e passare a qualsiasi elemento per cui si è elencati come proprietari.
Sotto la casella dei commenti, nella parte inferiore di ogni elemento viene visualizzato "+Follow".
Quando si fa clic su questa opzione, LiveFyre invia un messaggio di posta elettronica all'indirizzo registrato ogni volta in cui vengono aggiunti nuovi commenti sull'elemento.