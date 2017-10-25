---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: raccolta,powershell,cmdlet,psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a>Stato di PowerShell Gallery
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RISOLTO: impossibile visualizzare singole pagine di moduli e script

__Riepilogo del problema__: i collegamenti diretti alle singole pagine di moduli e script in https://www.powershellgallery.com erano interrotti. Il problema era segnalato in tutte le aree. Il problema non influiva sui cmdlet di PowerShellGet, in altre parole Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module e Publish-Script continuavano a funzionare.

__Causa radice__: i tecnici hanno identificato la causa in un problema di visualizzazione dei pulsanti per i social media come Facebook nella pagina.  

__Risoluzione__: tecnici hanno risolto il problema disabilitando le informazioni sul conteggio di Facebook.

__Passaggi successivi__: è stato aperto un problema di rilevamento interno per correggere l'uso dell'API di Facebook.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>15/12/2016 - Impossibile inviare messaggi di posta elettronica tramite il sito Web PowerShell Gallery

__Riepilogo del problema__: tra il 13/12/2016 e il 15/12/2016, tutti i messaggi inviati tramite Contact Owners, Manage Owners, Contact Support o Report Abuse non sono stati ricevuti dagli amministratori di PowerShell Gallery.  
__Causa radice__: i tecnici hanno identificato la causa in un problema di autenticazione con il server SMTP.  
__Risoluzione__: i tecnici sono stati in grado di risolvere il problema di autenticazione e ripristinare la connessione al server SMTP.  
__Passaggi successivi__: se il messaggio di posta elettronica è stato inviato a cgadmin@microsoft.com tramite i collegamenti Contact Owners, Manage Owners, Contact Support o Report Abuse durante questo periodo e non è stata ricevuta alcuna risposta, si prega di rinviare il messaggio. Il team si scusa per l'inconveniente.   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>10/08/2016 - risolto: Impossibile inviare messaggi di posta elettronica a cgadmin@microsoft.com
__Riepilogo del problema__: tra il 05/08/2016 e il 10/08/2016 i clienti non hanno potuto inviare messaggi di posta elettronica a cgadmin@microsoft.com o usare la funzionalità Contattaci.  
__Causa radice__: i tecnici hanno individuato la causa in una modifica della configurazione dell'account di posta elettronica.  
__Risoluzione__: i tecnici hanno lavorato per risolvere il problema di configurazione.  
__Passaggi successivi__: se in questo periodo è stato usato il collegamento Contattaci o si è inviato un messaggio a cgadmin@microsoft.com senza ricevere risposta, riprovare. Grazie per la pazienza dimostrata.


