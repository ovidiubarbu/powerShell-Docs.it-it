---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: install pswawebapplication
ms.technology: powershell
ms.openlocfilehash: c15215935eb70f082d13b93a0bf040aaf00a04de
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="install-pswawebapplication"></a>Install-PswaWebApplication

##  <a name="synopsis"></a>RIEPILOGO

Configura l'applicazione Web Accesso Web Windows PowerShell® in IIS.

## <a name="syntax"></a>SINTASSI

### <a name="default"></a>Default
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Il cmdlet **Install-PswaWebApplication** consente di configurare l'applicazione Web Accesso Web Windows PowerShell. Questo cmdlet installa l'applicazione Web, la associa a un sito Web e, se necessario, crea un certificato SSL di test usando il parametro **useTestCertificate**. Per motivi di sicurezza, gli amministratori Web non devono usare un certificato di test per gli ambienti di produzione.

## <a name="parameters"></a>PARAMETRI

### <a name="-usetestcertificate"></a>-UseTestCertificate

Specifica che viene creato un certificato di test. Se questo parametro è impostato su true, il cmdlet crea un certificato di test e configura l'applicazione Web Accesso Web Windows PowerShell in modo che usi il certificato per le richieste HTTPS. Se questo parametro è impostato su false, non viene creato alcun certificato o binding. Impostare questo valore su false se si usa un altro certificato per Accesso Web Windows PowerShell.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | True                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

Specifica il nome per l'applicazione Web. Il nome viene visualizzato come parte finale dell'URL di Accesso Web Windows PowerShell.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | 1                                    |
| Valore predefinito                        | pswa                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

Specifica il nome del sito Web del server Web (IIS) in cui installare l'applicazione Web Accesso Web Windows PowerShell.

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

##  <a name="outputs"></a>OUTPUT

Questo cmdlet non genera alcun output.

## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

In questo esempio si installa l'applicazione Web PSWA usando i valori predefiniti per i parametri **WebApplicationName** (*pswa*) e **WebSiteName** (*sito Web predefinito*).

```
Install-PswaWebApplication
```

### <a name="example-2"></a>ESEMPIO 2

In questo esempio viene installata l'applicazione Web PSWA con un certificato di test, usando i valori predefiniti per i parametri **WebApplicationName** e **WebSiteName**.

```
Install-PswaWebApplication -UseTestCertificate
```

##  <a name="related-topics"></a>Argomenti correlati

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
