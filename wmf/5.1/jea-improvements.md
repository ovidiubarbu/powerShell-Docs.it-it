---
title: Miglioramenti apportati a JEA (Just Enough Administration)
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF, JEA
description: 
ms.topic: article
contributor: ryanpu
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 1b054b67bfd7b3660bac134bc8b023baf5644507
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="improvements-to-just-enough-administration-jea"></a>Miglioramenti apportati a JEA (Just Enough Administration)

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a>Copia di file vincolata in/da endpoint JEA

È ora possibile copiare in remoto file in/da un endpoint JEA e avere la certezza che l'utente che si connette non potrà copiare *nessun* file nel sistema.
A questo scopo, è necessario configurare il file PSSC in modo da consentire il montaggio di un'unità utente per la connessione degli utenti.
L'unità utente è un nuovo dispositivo PSDrive che è esclusivo per ogni utente che si connette e che viene mantenuto da una sessione all'altra.
Quando si usa Copy-Item per copiare file in o da una sessione JEA, esiste un vincolo in base al quale l'accesso è consentito solo all'unità utente.
I tentativi di copiare i file in altre unità PSDrive avranno esito negativo.

Per configurare l'unità utente nel file di configurazione della sessione JEA, usare i nuovi campi seguenti:

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

La cartella che supporta l'unità utente verrà creata in `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`

Per utilizzare l'unità utente e copiare i file in/da un endpoint JEA configurato per esporre l'unità utente, usare i parametri `-ToSession` e `-FromSession` su Copy-Item.

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

È quindi possibile scrivere funzioni personalizzate per elaborare i dati archiviati nell'unità utente e rendere disponibili tali dati agli utenti nel file di capacità del ruolo.

## <a name="support-for-group-managed-service-accounts"></a>Supporto per gli account del servizio gestiti del gruppo

In alcuni casi, per un'attività che un utente deve eseguire in una sessione JEA potrebbe essere necessario accedere a risorse che non si trovano nel computer locale.
Quando una sessione JEA è configurata per l'uso di un account virtuale, qualsiasi tentativo di accedere a tali risorse risulterà proveniente dall'identità del computer locale, non dall'account virtuale o dall'utente connesso.
In TP5 è stato abilitato il supporto per l'esecuzione di JEA nel contesto di un [account del servizio gestito del gruppo] (https://technet.microsoft.com/it-it/library/jj128431(v=ws.11\).aspx). In tal modo, risulta molto più semplice accedere alle risorse di rete usando un'identità di dominio.

Per configurare una sessione JEA per l'esecuzione con un account del servizio gestito del gruppo, usare la nuova chiave seguente nel file PSSC:

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> **Nota:** gli account del servizio gestiti del gruppo non garantiscono l'isolamento o la limitazione dell'ambito degli account virtuali.
> Ogni utente che si connette condividerà la stessa identità degli account del servizio gestiti del gruppo, che può avere le autorizzazioni necessarie per accedere all'intera azienda.
> Prestare molta attenzione quando si sceglie di usare un account del servizio gestito del gruppo e, quando possibile, dare sempre la preferenza agli account virtuali limitati al computer locale.

## <a name="conditional-access-policies"></a>Criteri di accesso condizionale

JEA è ideale per limitare le operazioni che un utente può eseguire quando si connette a un sistema per gestirlo. Il problema si pone, tuttavia, quando si vuole limitare il *periodo di tempo* in cui un utente può utilizzare JEA.
Sono state aggiunte opzioni di configurazione nei file di configurazione della sessione (con estensione pssc) per consentire di specificare gruppi di sicurezza a cui un utente deve appartenere per stabilire una sessione JEA.
Questo meccanismo può essere particolarmente utile se l'ambiente in uso è dotato di un sistema JIT (Just In Time) e si vuole consentire agli utenti di elevare i propri privilegi prima di accedere a un endpoint JEA con privilegi elevati.

Il nuovo campo *RequiredGroups* del file PSSC consente di specificare la logica per determinare se un utente può connettersi a JEA.
Si tratta di specificare una tabella hash (opzionalmente nidificata) che usi le chiavi 'And' e 'Or' per costruire le regole.
Di seguito sono riportati alcuni esempi di come usare questo campo:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a>Correzione: gli account virtuali sono ora supportati in Windows Server 2008 R2
In WMF 5.1 è ora possibile usare account virtuali in Windows Server 2008 R2, abilitando configurazioni coerenti e parità di funzionalità in Windows Server 2008 R2 - 2016.
Gli account virtuali continuano a non essere supportati quando si usa JEA in Windows 7.
