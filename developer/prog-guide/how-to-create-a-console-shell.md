---
title: Come creare una Shell Console | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853497"
---
# <a name="how-to-create-a-console-shell"></a>Come creare una shell di console

Windows PowerShell fornisce uno strumento Shell marca, noto anche come il "marca-kit", che viene usato per creare una shell di console che non è estendibile. Shell creata con questo nuovo strumento non può essere esteso in un secondo momento tramite uno snap-in Windows PowerShell.

## <a name="syntax"></a>Sintassi

Di seguito è riportata la sintassi usata per eseguire la Shell di marca all'interno di un file di creazione.

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a>Parametri

Ecco una breve descrizione dei parametri della marca-Shell.

> [!CAUTION]
> Percorsi UNC delle assembly non sono supportati dalla marca-Shell.

|Parametro|Description|
|---------------|-----------------|
|-out n.exe|Obbligatorio. Il nome della shell per produrre. Il percorso è specificato come parte di questo parametro.<br /><br /> Marca shell aggiungerà ".exe" questo valore se non è specificato. **Attenzione:**  Non creare un file di output con lo stesso nome del file DLL di cui viene fatto riferimento. Se si tenta di ciò, lo strumento marca Shell crea un file con estensione cs con lo stesso nome, che sovrascriverà il file con estensione cs che contiene il codice sorgente di cmdlet.|
|-spazio dei nomi ns|Obbligatorio. Lo spazio dei nomi da utilizzare per derivato [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) classe che il kit di assicurarsi che genera l'errore e viene compilato.|
|-lib libdirectory1 [, libdirectory2,..]|Le directory in cui vengono cercate gli assembly .NET, inclusi gli assembly di Windows PowerShell, assembly specificati per il `reference` parametro, gli assembly di riferimento indiretto da un altro assembly e gli assembly di sistema di .NET.|
|-riferimento ca1.dll[,ca2.dll,...]|Elenco delimitato da virgole degli assembly da includere nella shell. Questi assembly include tutti i cmdlet e gli assembly del provider, nonché gli assembly di risorse che devono essere caricati. Se questo parametro viene omesso, una shell viene prodotto che contiene solo i cmdlet e provider principali fornite da Windows PowerShell.<br /><br /> L'assembly può essere specificato usando il percorso completo, in caso contrario, essi verrà cercati utilizzando il percorso specificato da di `lib` parametro.|
|-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]|Elenco delimitato da virgole di formattare i dati da includere nella shell. Se questo parametro viene omesso, una shell viene prodotto che contiene solo i dati di formato forniti da Windows PowerShell.|
|-typedata td1.type.ps1xml[,td2.type.ps1xml,...]|Elenco delimitato da virgole di dati di tipo da includere nella shell. Se questo parametro viene omesso, una shell viene prodotto che contiene solo i dati di tipo forniti da Windows PowerShell.|
|-origine c1.cs [, c2.cs,...]|Il nome di un file, fornito dallo sviluppatore di shell, che contiene tutto il codice sorgente necessario per compilare la shell.<br /><br /> File del codice sorgente può contenere il codice sorgente seguente:<br /><br /> -L'implementazione di gestione di autorizzazione che esegue l'override di gestione di autorizzazioni predefinito. (Questo è stato necessario fornire anche compilato in un assembly.)<br />Dichiarazioni di attributi informativi assembly: ad esempio il AssemblyCompanyAttribute AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, e AssemblyTrademarkAttribute.|
|Gestione autorizzazioni - authorizationManagerType|Tipo che contiene l'implementazione del gestore di autorizzazione. Questo può essere definito nel codice sorgente o compilato in un assembly (specificato da di `reference` parametro). Se questo parametro viene omesso, viene utilizzato il gestore di sicurezza predefinito. Il valore deve essere il nome completo del tipo, inclusi gli spazi dei nomi.|
|-win32icon i.ico|Icona per il file .exe della shell. Se non specificato, la shell avrà l'icona che il compilatore c# include (se presente).|
|-initscript p.ps1|Il profilo di avvio della shell. Il file viene fornito "come-è"; viene eseguito alcun controllo di validità dalla marca-Shell.|
|-s1.ps1[,s2.ps1 builtinscript,...]|Un elenco di script incorporato per la shell. Questi script vengono individuati prima gli script nel percorso e il relativo contenuto non può essere modificato dopo aver compilata la shell.<br /><br /> I file sono inclusi "come-è"; viene eseguito alcun controllo di validità dalla marca-Shell.|
|-risorse resourcefile.txt|Il file con estensione txt contenente della Guida in linea e banner delle risorse per la shell. La prima risorsa denominata ShellHelp e contiene il testo visualizzato se la shell viene richiamata con il `help` parametro. La seconda risorsa denominata ShellBanner e contiene il testo e le informazioni sul copyright visualizzate quando la shell viene avviata in modalità interattiva.<br /><br /> Se non viene specificato questo parametro o queste risorse non sono presenti, vengono utilizzati un generico della Guida in linea e banner.|
|-cscflags cscFlags|Flag da passare per il C# compilatore (csc.exe). Questi vengono passati invariati. Se questo parametro include spazi, deve essere racchiuso tra virgolette doppie.|
|-?<br /><br /> -Guida in linea|Visualizza il messaggio di copyright e opzioni della riga di comando verificare-Shell.|
|-verbose|Visualizza informazioni dettagliate durante la creazione della shell.|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)