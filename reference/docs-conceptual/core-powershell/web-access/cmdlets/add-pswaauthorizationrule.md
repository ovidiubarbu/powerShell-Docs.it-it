---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

##  <a name="synopsis"></a>RIEPILOGO

Aggiunge una nuova regola di autorizzazione al set di regole di autorizzazione di Accesso Web Windows PowerShell®.

## <a name="syntax"></a>Sintassi

###  <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>DESCRIZIONE

Il cmdlet **Add-PswaAuthorizationRule** aggiunge una nuova regola di autorizzazione al set di regole di autorizzazione di Accesso Web Windows PowerShell®.

È necessario specificare gli utenti, i computer e gli endpoint di Windows PowerShell per questa regola. È possibile specificare utenti e computer sia indicando singoli account utente e nomi di computer, sia specificando i gruppi.

Per un computer appartenente a un dominio Active Directory, il cmdlet usa l'ID di sicurezza (SID) del computer per creare la regola.
Ciò consente di usare un nome breve, un nome di dominio completo (FQDN) o un indirizzo IP per il campo **Nome computer** della pagina di accesso.

Per un computer che non appartiene a un dominio Active Directory, il cmdlet crea la regola usando il nome di computer indicato dall'amministratore. Per connettersi correttamente a questo computer, l'utente finale deve indicare il nome del computer esattamente come appare nella regola.

Se nella rete sono presenti più computer con lo stesso nome, il nome breve può restituire più di un computer. Questo può causare ambiguità quando si stabilisce una connessione. Ad esempio, se esiste una regola per il computer del gruppo di lavoro denominato "*Server1*" e un nuovo computer denominato *server1.contoso.com* viene aggiunto alla rete, la convalida eseguita con le regole di autorizzazione ha esito positivo e Accesso Web Windows PowerShell tenta di stabilire una connessione al computer "*Server1*". Non è garantito che la connessione venga stabilita con il computer del gruppo di lavoro specificato. Il tentativo può essere effettuato per il gruppo di lavoro o il computer del dominio denominato "*Server1*". Per ridurre l'ambiguità, è consigliabile usare il nome FQDN del computer di destinazione ogni volta che è possibile per creare una regola di autorizzazione.

Le regole di autorizzazione verificano le credenziali di accesso primarie degli utenti di Accesso Web Windows PowerShell, non le credenziali alternative, ovvero il secondo set di credenziali indicato nella sezione **Impostazioni di connessione facoltative** della pagina di accesso. Per un esempio, vedere l'esempio 6.

## <a name="parameters"></a>Parametri

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

Specifica il nome di un gruppo di computer in Active Directory Domain Services (AD DS) o i gruppi locali a cui la regola concede l'accesso.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByPropertyName)                |
| Accetta caratteri jolly?          | False                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;String&gt;

Specifica il nome del computer a cui la regola concede l'accesso.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByPropertyName)                |
| Accetta caratteri jolly?          | False                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;String&gt;

Specifica il nome della configurazione di sessione di Windows PowerShell, nota anche come spazio di esecuzione, a cui la regola concede l'accesso.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByPropertyName)                |
| Accetta caratteri jolly?          | False                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Specifica un oggetto **PSCredential** per un account utente che verrà usato per modificare le regole di autorizzazione di Accesso Web Windows PowerShell. Se non si aggiunge questo parametro, il cmdlet usa l'account utente attualmente connesso. Per ottenere un oggetto **PSCredential**, necessario per aggiungere le regole di autorizzazione in modalità remota, eseguire il cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-force"></a>-Force

Forza l'esecuzione del comando senza chiedere conferma all'utente.\
Richiede anche una conferma quando si immette un nome di computer semplice o breve, ad esempio un nome che non è un nome di dominio o non è completo. La conferma è richiesta per motivi di sicurezza, in modo che sia possibile usare il nome semplice per aggiungere un computer solo se il computer fa parte di un gruppo di lavoro.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | False                                |
| Accetta caratteri jolly?          | False                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String&gt;

Specifica il nome descrittivo per la regola.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | False                                |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByPropertyName)                |
| Accetta caratteri jolly?          | False                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;String\[\]&gt;

Specifica il nome di uno o più gruppi di utenti in Active Directory Domain Services (AD DS) o gruppi locali a cui la regola concede l'accesso.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | denominato                                |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByPropertyName)                |
| Accetta caratteri jolly?          | False                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;String\[\]&gt;

Specifica uno o più utenti a cui la regola concede l'accesso. Il nome utente può essere un account utente locale nel computer gateway o un utente di Active Directory Domain Services (AD DS).
Il formato è `domain\user` o `computer\user`.

|||  
|-|-|
| Alias                              | Nessuno                                 |
| Obbligatorio?                            | True                                 |
| Posizione?                            | 1                                    |
| Valore predefinito                        | Nessuno                                 |
| Accetta input da pipeline?               | True (ByValue, ByPropertyName)       |
| Accetta caratteri jolly?          | False                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.
Per altre informazioni, vedere [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>INPUT

###  <a name="string"></a>String

Questo cmdlet accetta una stringa o una matrice di stringhe come input.

###  <a name="string"></a>String\[\]

Questo cmdlet accetta una stringa o una matrice di stringhe come input.

##  <a name="outputs"></a>Output

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Questo cmdlet restituisce un oggetto regola di autorizzazione.

## <a name="examples"></a>ESEMPI

### <a name="example-1"></a>ESEMPIO 1

In questo esempio si concede l'accesso alla configurazione di sessione *PSWAEndpoint*, uno spazio di esecuzione con restrizioni, su *srv2* per gli utenti del gruppo *SMAdmins*. \
**Nota**: il nome del computer deve essere un nome di dominio completo (FQDN). Gli amministratori definiscono una configurazione di sessione o uno spazio di esecuzione con restrizioni, ovvero un intervallo limitato di cmdlet e attività che gli utenti finali possono eseguire. La definizione di uno spazio di esecuzione con restrizioni può impedire agli utenti di accedere ad altri computer che sono nello spazio di esecuzione di Windows PowerShell® consentito, offrendo così una connessione più protetta. Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) o [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md) (Installare e usare Accesso Web Windows PowerShell).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>ESEMPIO 2

In questo esempio si concede l'accesso alla configurazione di sessione predefinita di Windows PowerShell, `Microsoft.PowerShell`, su *srv2* per gli utenti denominati contoso\\user1, contoso\\user2 e contoso\\user3. Questo cmdlet crea tre regole, una per ogni persona.

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>ESEMPIO 3

Questo esempio illustra come inserire valori di nome utente usando la pipeline.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>ESEMPIO 4

Questo esempio illustra come tutti i parametri accettano i valori dalla pipeline in base al nome di proprietà.

\
###   <a name="section-subheading"></a>{#section .subHeading}

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a>{#section-1 .subHeading}

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a>ESEMPIO 5 {#example-5 .subHeading}

<div class="subSection">

In questo esempio viene aggiunta una regola per consentire all'utente locale denominato *PswaServer\\ChrisLocal* di accedere al server denominato *srv1.contoso.com*.

L'esempio illustra uno scenario in cui il gateway è in un gruppo di lavoro e il computer di destinazione è in un dominio. La regola di autorizzazione si applica per gli utenti locali nel gateway. Per eseguire correttamente l'autenticazione, l'utente deve indicare nella pagina di accesso di Accesso Web Windows PowerShell un secondo set di credenziali nell'area **Impostazioni di connessione facoltative**. Il server gateway usa il set di credenziali aggiuntivo per autenticare l'utente nel computer di destinazione, il server *srv1.contoso.com*.

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a>ESEMPIO 6 {#example-6 .subHeading}

<div class="subSection">

Questo esempio consente a tutti gli utenti di accedere a tutti gli endpoint in tutti i computer.
In pratica, disattiva le regole di autorizzazione.\
**Nota**: l'uso del carattere jolly `*` non è consigliato per le distribuzioni in cui la sicurezza è un fattore essenziale e deve essere considerato solo per gli ambienti di test o le distribuzioni in cui è possibile ridurre la protezione.

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); "Copy to clipboard.")

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a>Argomenti correlati 
--------------


[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\
\
[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\
\
[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\
\
[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\
\
[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\
\
[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\
\
[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)