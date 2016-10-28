---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_unregister psrepository
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 7d9c24ebb20756a2f7852692532ac6ec7e558ca9

---

# Unregister-PSRepository

Consente di annullare la registrazione di un repository.

## Descrizione

Il cmdlet Unregister-PSRepository consente di annullare la registrazione di un repository per l'utente corrente.
- L'annullamento della registrazione e la ri-registrazione del repository PSGallery sono consentiti per scenari disconnessi e aziendali.
- Per ri-registrare PSGallery è sufficiente eseguire `Register-PSRepository -Default`
- Dato che PSGallery è il repository di pubblicazione predefinito nei cmdlet Publish-Module e Publish-Script, se PSGallery non è disponibile nell'elenco dei repository registrati viene generato un errore.

## Sintassi del cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## Riferimento per la Guida online sui cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## Comandi di esempio

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### L'annullamento della registrazione e la ri-registrazione del repository PSGallery sono consentiti per scenari disconnessi e aziendali.
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```




<!--HONumber=Oct16_HO2-->


