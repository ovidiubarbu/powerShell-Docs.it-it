---
ms.date: 03/27/2018
contributor: JKeithB
keywords: raccolta,powershell,psgallery,GDPR
title: Conformità al regolamento GDPR di PowerShell Gallery
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328322"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Conformità al regolamento GDPR di PowerShell Gallery

## <a name="overview"></a>Panoramica

A maggio 2018 è entrata in vigore una normativa europea sulla privacy, il Regolamento generale sulla protezione dei dati (GDPR, General Data Protection Regulation).
La normativa GDPR impone nuove regole ad aziende, enti governativi, enti no profit e altre organizzazioni che offrono beni e servizi a residenti dell'Unione Europea (UE) o che raccolgono e analizzano dati associati a residenti UE.
La normativa GDPR è valida ovunque ci si trovi.

> [!NOTE]
> Questo articolo illustra le procedure per eliminare dati personali da PowerShell Gallery e può essere usato per adempiere gli obblighi previsti dalla normativa. Per informazioni generali sulla normativa GDPR, vedere la [sezione GDPR del portale Service Trust](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Dati personali identificabili

PowerShell Gallery archivia le informazioni seguenti, che possono essere trasmesse dagli utenti e includere informazioni personali:

- Account di PowerShell Gallery
- Pacchetti pubblicati in PowerShell Gallery
- Corrispondenza di posta elettronica con il team PowerShell Gallery

La maggior parte degli utenti non crea un account di PowerShell Gallery.
Non è necessario un account, a meno che non si intenda pubblicare un pacchetto o usare la funzionalità "Proprietario contatto" in PowerShell Gallery.
A parte la corrispondenza di posta elettronica avviata dall'utente, PowerShell Gallery non archivia dati personali identificabili per utenti che non hanno creato un account.

Gli utenti che creano un account PowerShell Gallery possono pubblicare pacchetti in PowerShell Gallery.
È previsto che tali pacchetti siano costituiti da codice PowerShell, ma possono anche contenere altre informazioni, incluse informazioni personali.
Le informazioni seguenti visualizzano come ottenere tutti i pacchetti pubblicati in PowerShell Gallery.

## <a name="dsr-export-of-powershell-gallery-data"></a>Esportazione DSR dei dati di PowerShell Gallery

Le sezioni seguenti descrivono come PowerShell Gallery supporta le richieste DSR (Data Subject Rights, Diritti del soggetto dei dati) e illustrano come esportare le informazioni archiviate in PowerShell Gallery e come richiedere l'eliminazione di queste informazioni.

### <a name="email"></a>Email

La corrispondenza tramite posta elettronica può includere quanto segue:

- Messaggio di posta elettronica inviato ai proprietari di pacchetti di PowerShell Gallery se l'analisi del codice rileva un problema con un pacchetto pubblicato da tali proprietari in PowerShell Gallery
- Messaggio di posta elettronica inviato da qualsiasi utente al team di PowerShell Gallery usando l'indirizzo di posta elettronica disponibile nella pagina "Contattaci" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)
- Utenti registrati che usano la funzionalità "Contact Owner" (Proprietario contatto) in PowerShell Gallery per inviare posta elettronica al proprietario di un pacchetto di PowerShell Gallery

Per i messaggi di posta elettronica inviati da o a PowerShell Gallery sono previsti criteri di conservazione di 90 giorni, che supportano eventuali verifiche di sicurezza nel caso in cui venga rilevato codice dannoso in PowerShell Gallery.
In bse ai criteri i messaggi di posta elettronica vengono eliminati dopo 90 giorni.

È possibile richiedere copie di tutti i messaggi di posta elettronica scambiati tra l'indirizzo di posta elettronica dell'utente e PowerShell Gallery nei 90 giorni precedenti.
Per richiedere questa corrispondenza, inviare un messaggio di posta elettronica a [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), con il titolo: "DSR Request for emails relating to this account" (Richiesta DSR per i messaggi di posta elettronica relativi a questo account).
Nel corpo del messaggio indicare le informazioni richieste, ad esempio: Please send all emails sent to or received from this email address (Inviare tutti i messaggi di posta elettronica inviati o ricevuti da questo indirizzo di posta elettronica). Entro 7 giorni lavorativi si riceveranno tutti i messaggi che includono l'indirizzo di posta elettronica risalenti a un massimo di 90 giorni dalla data della richiesta.

### <a name="powershell-gallery-account-information"></a>Informazioni sull'account PowerShell Gallery

Se è stato creato un account di PowerShell Gallery, è possibile trovare tutte le informazioni personali archiviate in PowerShell Gallery seguendo questa procedura:

1. Accedere a PowerShell Gallery, quindi fare clic sul proprio nome utente
2. La pagina successiva visualizzata è la pagina Account, che include l'indirizzo di posta elettronica usato per l'account PowerShell Gallery

Se sono stati creati più account in PowerShell Gallery, è necessario ripetere questi passaggi per ogni account.

### <a name="packages-in-the-powershell-gallery"></a>Pacchetti in PowerShell Gallery

Per facilitare l'esportazione di pacchetti pubblicati in PowerShell Gallery, Microsoft ha pubblicato lo script "GetPSGalleryItemsForAuthor" in PowerShell Gallery.
Questo script esporta una copia di ogni versione di ogni pacchetto incluso in PowerShell Gallery sulla base delle informazioni dell'autore memorizzate nel pacchetto.

> [!NOTE]
> L'autore viene archiviato nel manifesto del pacchetto al momento della pubblicazione del pacchetto stesso.
> Non vi è garanzia che l'identità dell'autore corrisponda all'account usato in PowerShell Gallery.
> Se si usa un altro valore nel campo Autore, è necessario specificare tale valore quando si usa questo script.

È possibile scaricare lo script usando il comando PowerShell seguente:

```powershell
Save-Script Get-repository psgallery
```

Quindi è possibile eseguire direttamente lo script eseguendo il comando PowerShell seguente:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Viene richiesto di specificare l'autore e la cartella del sistema in cui salvare i pacchetti.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Eliminazione dei dati personali da PowerShell Gallery

Per eliminare l'account di PowerShell Gallery o qualsiasi pacchetto di proprietà dell'utente in PowerShell Gallery, inviare un messaggio di posta elettronica all'indirizzo cgadmin@microsoft.com con il titolo: "GDPR Request for items relating to this account" (Richiesta GDPR per elementi associati a questo account).
Nel corpo del messaggio indicare le informazioni da eliminare. Ad esempio:

- Please delete version x.y.z of my package "package name" (Eliminare la versione x.y.z del mio pacchetto "nome pacchetto")
- Please delete all versions of my package "package name" (Eliminare tutte le versioni del mio pacchetto "nome pacchetto")
- Please delete my PowerShell Gallery account (Eliminare il mio account PowerShell Gallery)

Gli amministratori di PowerShell Gallery risponderanno entro 7 giorni lavorativi.
I pacchetti specificati verranno eliminati entro 30 giorni dall'invio della richiesta.
