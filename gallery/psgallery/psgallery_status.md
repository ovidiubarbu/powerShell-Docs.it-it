---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: a260b9b696b41947fbbb789fd165dfe4bdac1dc3
ms.sourcegitcommit: 214b8442f05618d078837889cbb6a30b42c01edb
translationtype: HT
---
<a name="powershell-gallery-status"></a>Stato di PowerShell Gallery
=========================

## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017 - Gli utenti non possono accedere con account Azure Active Directory (AAD)

__Riepilogo del problema__: alcuni utenti non sono in grado di accedere a PowerShell Gallery usando gli account Azure AD. 
 
__Causa radice__: durante un aggiornamento per un'iterazione più sicura con AAD, non è stata eseguita una modifica delle impostazioni. Poiché i test eseguiti per convalidare la modifica non includevano determinati tipi di account AAD, la distribuzione è stata eseguita.

__Risoluzione__: I tecnici hanno identificato l'impostazione mancante e corretto il problema. 

__Passaggi successivi__: verranno modificati i test per includere un set più ampio di tipi di account AAD.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>27/03/2017 - RISOLTO: impossibile visualizzare singole pagine di moduli e script

__Riepilogo del problema__: i collegamenti diretti alle singole pagine di moduli e script in https://www.powershellgallery.com erano interrotti. Il problema era segnalato in tutte le aree. Il problema non influiva sui cmdlet di PowerShellGet, ovvero Install-Module, Install-Script, Update-Module, Update-Script e Publish-Module. Publish-Script continuava a funzionare.

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



## <a name="7132016---download-items-failed"></a>13/07/2016 - download di elementi non riuscito

__Riepilogo dell'impatto__: tra l'11/07/2016 e il 13/07/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery. Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__Causa radice preliminare__: i tecnici hanno individuato un problema con la Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery l'11/07/2016.  
__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.  
__Passaggi successivi__: ricercare la causa principale sottostante e sviluppare una soluzione per evitare che questo problema si ripresenti in futuro.


## <a name="5192016---download-items-failed"></a>19/05/2016 - download di elementi non riuscito
__Riepilogo dell'impatto__: tra il 17/05/2016 e il 19/05/2016, alcuni clienti hanno incontrato problemi di download degli elementi da PowerShell Gallery. Il problema si è probabilmente manifestato nei seguenti messaggi di errore restituiti da Install-Module/Install-Script e Save-Module/Save-Script:

```PowerShell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

__Causa radice preliminare__: i tecnici hanno individuato un problema con il provider sottostante della Rete di distribuzione dei contenuti (CDN) di Azure, che è stata distribuita a PowerShell Gallery il 17/5/2016.  
__Prevenzione__: i tecnici hanno disabilitato la CDN di Azure in PowerShell Gallery.  
__Passaggi successivi__: ricercare la causa radice sottostante e sviluppare una soluzione per evitare che il problema si ripresenti in futuro.

