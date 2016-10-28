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
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 69df41ae0a9dfd9fb71655cf6334f60f1d39ae94

---

Stato di PowerShell Gallery
=========================


## 10/08/2016 - risolto: Impossibile inviare messaggi di posta elettronica a cgadmin@microsoft.com

__Riepilogo dell'impatto__: tra il 05/08/2016 e il 10/08/2016, i clienti non hanno potuto inviare messaggi di posta elettronica a cgadmin@microsoft.com o usare la funzionalità Contattaci.  
__Causa radice__: i tecnici hanno individuato la causa in una modifica della configurazione dell'account di posta elettronica.  
__Risoluzione__: i tecnici hanno lavorato per risolvere il problema di configurazione.  
__Passaggi successivi__: se in questo periodo è stato usato il collegamento Contattaci o si è inviato un messaggio a cgadmin@microsoft.com senza ricevere risposta, riprovare. Grazie per la pazienza dimostrata.



## 13/07/2016 - download di elementi non riuscito

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


## 19/05/2016 - download di elementi non riuscito
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




<!--HONumber=Oct16_HO2-->


