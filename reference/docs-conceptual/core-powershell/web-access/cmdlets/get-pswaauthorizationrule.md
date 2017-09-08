---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 43997320ec7ab779b2061a0af88f97db0b7e93d6
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

##  <a name="synopsis"></a>RIEPILOGO

Restituisce un set di regole di autorizzazione di Accesso Web Windows PowerShell®.

##  <a name="syntax"></a>Sintassi

###  <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

###  <a name="name"></a>Nome
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Il cmdlet **Get-PswaAuthorizationRule** restituisce un set di regole di autorizzazione di Accesso Web Windows PowerShell®.
Se non si specifica né il parametro **Id** né il parametro **RuleName**, questo cmdlet elenca tutte le regole. Il parametro **Id** può essere usato per filtrare i risultati.

## <a name="parameters"></a>PARAMETRI

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Specifica gli identificatori (ID) delle regole che il cmdlet deve restituire. Se non è stato specificato alcun ID, il cmdlet restituisce tutte le regole di autorizzazione.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue, ByPropertyName)       |
| Accetta caratteri jolly?          | False                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

Specifica i nomi delle regole di autorizzazione da recuperare. Questo parametro restituisce tutte le regole che corrispondono esattamente ai nomi delle regole delle stringhe in questa matrice.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue, ByPropertyName)       |
| Accetta caratteri jolly?          | False                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INPUT

###  <a name="int"></a>int\[\]

Questo cmdlet accetta una matrice di numeri interi o una matrice di valori di stringa come input.

###  <a name="string"></a>String\[\]

Questo cmdlet accetta una matrice di numeri interi o una matrice di valori di stringa come input.

##  <a name="outputs"></a>OUTPUT

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Questo cmdlet genera un oggetto PswaAuthorizationRule come output.


## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

In questo esempio vengono ottenute tutte le regole.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>ESEMPIO 2

In questo esempio si ottiene una regola con ID *2*.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>ESEMPIO 3 {#example-3 .subHeading}

Questo esempio illustra come il cmdlet accetta un valore dalla pipeline.
In questo cmdlet vengono passati un ID e un nome di regola.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

##  <a name="related-topics"></a>Argomenti correlati

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
