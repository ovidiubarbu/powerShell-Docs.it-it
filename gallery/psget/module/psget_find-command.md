---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psget_find command
ms.technology: powershell
ms.openlocfilehash: 99091130ea89023495e5e3aacafb292f67f2db30
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="find-command"></a>Find-Command

Trova i comandi di PowerShell nei moduli.

## <a name="description"></a>Descrizione
Il cmdlet Find-Command trova i comandi di PowerShell, ad esempio cmdlet, alias, funzioni e flussi di lavoro. Find-Command cerca nei moduli dei repository registrati.
Per ogni comando trovato da questo cmdlet, viene restituito un oggetto PSGetCommandInfo. È possibile passare un oggetto PSGetCommandInfo al cmdlet Install-Module per installare il modulo che contiene il comando.

- Find-Command consente di filtrare usando i parametri di versione MinimumVersion, RequiredVersion e AllVersions.
  - Questi parametri si escludono a vicenda.
  - Questi parametri di versione sono consentiti solo con il nome del modulo singolo senza caratteri jolly.
  - Se il parametro RequiredVersion non è specificato, Find-Command restituisce la versione più recente del modulo maggiore o uguale alla versione minima specificata. Se la versione minima non è specificata, restituisce la versione più recente del modulo.
  - Se il parametro RequiredVersion è specificato, Find-Command restituisce unicamente la versione del modulo che corrisponde esattamente alla versione specificata.
- Find-Command consente di filtrare in base ai metadati del modulo usando il parametro -Tag
- Find-Command consente di filtrare in base al linguaggio di ricerca specifico del repository usando il parametro -Filter.
- Find-Command consente di filtrare in base ai moduli di tutti o alcuni dei repository registrati.

## <a name="cmdlet-syntax"></a>Sintassi del cmdlet
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Riferimento per la Guida online sui cmdlet

[Find-Command](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Comandi di esempio
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```

