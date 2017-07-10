---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 91380210f262208fce39d596bd6c2ad05a819fbf
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="unregister-psrepository" class="xliff"></a>
# Unregister-PSRepository

Consente di annullare la registrazione di un repository.

<a id="description" class="xliff"></a>
## Descrizione

Il cmdlet Unregister-PSRepository consente di annullare la registrazione di un repository per l'utente corrente.
- L'annullamento della registrazione e la ri-registrazione del repository PSGallery sono consentiti per scenari disconnessi e aziendali.
- Per ri-registrare PSGallery è sufficiente eseguire `Register-PSRepository -Default`
- Dato che PSGallery è il repository di pubblicazione predefinito nei cmdlet Publish-Module e Publish-Script, se PSGallery non è disponibile nell'elenco dei repository registrati viene generato un errore.

<a id="cmdlet-syntax" class="xliff"></a>
## Sintassi del cmdlet

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
<a id="cmdlet-online-help-reference" class="xliff"></a>
## Riferimento per la Guida online sui cmdlet

[Unregister-PSRepository](http://go.microsoft.com/fwlink/?LinkID=517130)

<a id="example-commands" class="xliff"></a>
## Comandi di esempio

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

<a id="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios" class="xliff"></a>
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

