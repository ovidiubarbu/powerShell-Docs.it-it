---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a>Unregister-PSRepository

Consente di annullare la registrazione di un repository.

## <a name="description"></a>Description

Il cmdlet Unregister-PSRepository consente di annullare la registrazione di un repository per l'utente corrente.
- L'annullamento della registrazione e la ri-registrazione del repository PSGallery sono consentiti per scenari disconnessi e aziendali.
- Per ri-registrare PSGallery è sufficiente eseguire `Register-PSRepository -Default`
- Dato che PSGallery è il repository di pubblicazione predefinito nei cmdlet Publish-Module e Publish-Script, se PSGallery non è disponibile nell'elenco dei repository registrati viene generato un errore.

## <a name="cmdlet-syntax"></a>Sintassi del cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a>Riferimento per la Guida online sui cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a>Comandi di esempio

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a>L'annullamento della registrazione e la ri-registrazione del repository PSGallery sono consentiti per scenari disconnessi e aziendali.
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