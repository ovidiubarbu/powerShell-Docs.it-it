---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189034"
---
# <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

## <a name="synopsis"></a>RIEPILOGO

Rimuove da Accesso Web Windows PowerShell® una regola di autorizzazione specificata.

## <a name="syntax"></a>SINTASSI

### <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regola
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Rimuove da Accesso Web Windows PowerShell una regola di autorizzazione specificata.

## <a name="parameters"></a>PARAMETRI

### <a name="-force"></a>-Force

Esegue il cmdlet senza chiedere conferma. Per impostazione predefinita il cmdlet chiede conferma prima di procedere.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Specifica gli identificatori (ID) di una o più regole da rimuovere.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue, ByPropertyName)       |
| Accetta caratteri jolly?          | False                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Specifica le regole da rimuovere.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue)                       |
| Accetta caratteri jolly?          | False                                |

### <a name="-confirm"></a>-Confirm

Richiede conferma prima di eseguire il cmdlet.

|||
|-|-|
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | False                                |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-whatif"></a>-WhatIf

Mostra gli effetti dell'esecuzione del cmdlet. Il cmdlet non viene eseguito.

|||
|-|-|
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | False                                |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INPUT

### <a name="int"></a>int\[\]

Questo cmdlet accetta una matrice di numeri interi o una matrice di oggetti PswaAuthorizationRule.

### <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Questo cmdlet accetta una matrice di numeri interi o una matrice di oggetti PswaAuthorizationRule.

## <a name="outputs"></a>OUTPUT

Questo cmdlet non genera alcun output.

## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

Questo esempio rimuove la regola di autorizzazione con ID di *2*.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>ESEMPIO 2 {#example-2 .subHeading}

In questo esempio vengono rimosse tutte le regole di autorizzazione e viene richiesta la conferma da parte dell'utente.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a>Argomenti correlati

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)