---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 139c8358a24e54dec630f8c78737728330ba4aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>RIEPILOGO

Disinstalla l'applicazione Web Windows PowerShell.

## <a name="syntax"></a>SINTASSI

### <a name="default"></a>Default
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Il cmdlet **Uninstall-PswaWebApplication** disinstalla l'applicazione Web Windows PowerShell e rimuove il sito Web da IIS. Il cmdlet non disinstalla IIS o altre funzionalità installate perché sono necessarie per l'esecuzione di Windows PowerShell.

## <a name="parameters"></a>PARAMETRI

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Indica che il certificato di test creato dal cmdlet **Install\_PswaWebApplication**, con il parametro **UseTestCertificate**, viene eliminato.
Viene rimosso solo il certificato di test con lo stesso nome di quello creato dal cmdlet **Install-PswaWebApplication**.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | True                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

Specifica il nome dell'applicazione Web da disinstallare.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | 1                                    |
| Valore predefinito                        | pswa                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

Specifica il nome del sito Web in cui è installata l'applicazione Web.

|||
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Sito Web predefinito                     |
| Accetta input da pipeline?               | False                                |
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

Mostra gli effetti dell'esecuzione del cmdlet.
Il cmdlet non viene eseguito.

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

Questo cmdlet non accetta input.

## <a name="outputs"></a>OUTPUT

Questo cmdlet non restituisce output.

## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

Questo comando disinstalla l'applicazione Web Windows PowerShell.
È possibile usare questo cmdlet per disinstallare l'applicazione Web Windows PowerShell se è stata installata usando i valori predefiniti.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>ESEMPIO 2

Questo comando disinstalla l'applicazione Web Windows PowerShell ed elimina il certificato di test associato all'applicazione.
È possibile usare questo cmdlet per disinstallare l'applicazione Web Windows PowerShell se è stata installata usando i valori predefiniti e se è stato creato un certificato di test.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>ESEMPIO 3 {#example-3 .subHeading}

Questo comando disinstalla l'applicazione Web Windows PowerShell quando si specifica un sito Web personalizzato con la relativa applicazione durante l'installazione.
Il comando rimuove il sito Web denominato *MySite* e l'applicazione denominata *TestApplication* e specifica che anche i certificati di test associati all'applicazione vengono eliminati.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Argomenti correlati

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)