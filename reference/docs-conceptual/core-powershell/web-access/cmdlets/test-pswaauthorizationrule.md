---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>RIEPILOGO

Verifica se esiste una regola per un utente, un computer o un endpoint specificato.

## <a name="syntax"></a>SINTASSI

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Il cmdlet **Test-PswaAuthorizationRule** verifica se esiste una regola per un utente, un computer o un endpoint specificato.
Può essere usato anche per testare le regole di autorizzazione per verificare se la richiesta di accesso a un determinato utente, computer o endpoint è autorizzata.
Per impostazione predefinita, questo cmdlet valuta tutte le regole nel file di autorizzazione.
Tuttavia, è possibile specificare un sottoinsieme di regole da testare.

È possibile usare questo cmdlet per la risoluzione degli errori di autenticazione.

I parametri per questo cmdlet corrispondono ai campi della pagina di accesso di Accesso Web Windows PowerShell®.

## <a name="parameters"></a>PARAMETRI

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

Specifica il nome del computer da testare.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

Specifica il nome della configurazione di sessione di Windows PowerShell, nota anche come endpoint o spazio di esecuzione, per eseguire il test.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | 3                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Specifica l'URI della connessione da testare.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 2                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Specifica un oggetto **PSCredential** per un account utente che verrà usato per testare le regole di autorizzazione di Accesso Web Windows PowerShell. Se non si aggiunge questo parametro, il cmdlet usa l'account utente attualmente connesso. Per ottenere un oggetto **PSCredential**, necessario per testare le regole di autorizzazione in modalità remota, eseguire il cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Specifica un sottoinsieme di regole da testare. Se questo parametro non viene specificato, il cmdlet esegue i test su tutte le regole di autorizzazione.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue)                       |
| Accetta caratteri jolly?          | False                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

Specifica il nome dell'utente da testare.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 1                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>INPUT

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Questo cmdlet accetta una matrice di oggetti PswaAuthorizationRule come input.

## <a name="outputs"></a>OUTPUT

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Questo cmdlet genera una matrice di oggetti PswaAuthorizationRule come output.

## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

Questo esempio verifica tutte le regole di autorizzazione per visualizzare quelle che consentono all'utente *contoso\\mhanson* di connettersi al computer *srv2* e usare una configurazione di sessione di Windows PowerShell denominata *test*.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>ESEMPIO 2

In questo esempio viene eseguito un test di tutte le regole di autorizzazione per verificare quali regole si applicano all'utente *contoso\\mhanson*.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Argomenti correlati

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
