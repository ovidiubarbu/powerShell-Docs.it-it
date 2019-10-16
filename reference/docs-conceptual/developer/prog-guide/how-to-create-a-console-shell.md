---
title: Come creare una shell della console | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360270"
---
# <a name="how-to-create-a-console-shell"></a>Come creare una shell di console

Windows PowerShell offre uno strumento di creazione della shell, noto anche come "make-Kit", che viene usato per creare una shell della console non estendibile. Le shell create con questo nuovo strumento non possono essere estese in un secondo momento tramite uno snap-in di Windows PowerShell.

## <a name="syntax"></a>Sintassi

Di seguito è illustrata la sintassi usata per eseguire make-Shell dall'interno di un file.

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

Ecco una breve descrizione dei parametri di make-Shell.

> [!CAUTION]
> I percorsi UNC degli assembly non sono supportati da make-Shell.

|Parametro|Description|
|---------------|-----------------|
|-out n. exe|Obbligatorio. Nome della shell da produrre. Il percorso viene specificato come parte di questo parametro.<br /><br /> Se non è specificato, la funzione Make-shell aggiungerà ". exe" a questo valore. **Attenzione:**  Non creare un file di output con lo stesso nome del file con estensione dll a cui si fa riferimento. Se si tenta di eseguire questa operazione, lo strumento make-shell crea un file con estensione cs con lo stesso nome, che sovrascriverà il file con estensione cs con il codice sorgente del cmdlet.|
|-spazio dei nomi NS|Obbligatorio. Lo spazio dei nomi da usare per la classe [System. Management. Automation. Runspaces. RunspaceConfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) derivata che il kit genera e compila.|
|-lib libdirectory1 [, libdirectory2,..]|Directory in cui vengono cercati gli assembly .NET, inclusi gli assembly di Windows PowerShell, gli assembly specificati dal parametro `reference`, gli assembly a cui fa riferimento indirettamente un altro assembly e gli assembly di sistema .NET.|
|-Reference CA1. dll [, Ca2. dll,...]|Elenco delimitato da virgole degli assembly da includere nella shell. Questi assembly includono tutti gli assembly di cmdlet e provider, nonché gli assembly di risorse che devono essere caricati. Se questo parametro non è specificato, viene generata una shell che contiene solo i cmdlet e i provider principali forniti da Windows PowerShell.<br /><br /> Gli assembly possono essere specificati utilizzando il percorso completo; in caso contrario, verranno cercati utilizzando il percorso specificato dal parametro `lib`.|
|-FormatData FD1. Format. ps1xml [, FD2. Format. ps1xml,...]|Elenco delimitato da virgole dei dati di formato da includere nella shell. Se questo parametro non è specificato, viene generata una shell che contiene solo i dati di formato forniti da Windows PowerShell.|
|-TypeData TD1. Type. ps1xml [, TD2. Type. ps1xml,...]|Elenco delimitato da virgole di dati di tipo da includere nella shell. Se questo parametro non è specificato, viene generata una shell che contiene solo i dati di tipo forniti da Windows PowerShell.|
|-Source c1.cs [, c2.cs,...]|Nome di un file, fornito dallo sviluppatore della shell, che contiene il codice sorgente necessario per compilare la Shell.<br /><br /> Il file di codice sorgente può contenere uno qualsiasi dei seguenti codici sorgente:<br /><br /> : Implementazione di gestione autorizzazioni che esegue l'override del gestore autorizzazioni predefinito. Questa operazione può anche essere compilata in un assembly.<br />-Dichiarazioni dell'attributo informativo sugli assembly: ad esempio AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute e AssemblyTrademarkAttribute.|
|-AuthorizationManager authorizationManagerType|Tipo che contiene l'implementazione di gestione autorizzazioni. Questo può essere definito nel codice sorgente o compilato in un assembly (specificato dal parametro `reference`). Se questo parametro non viene specificato, viene utilizzato il gestore sicurezza predefinito. Il valore deve essere il nome completo del tipo, inclusi gli spazi dei nomi.|
|-win32icon i. ico|Icona del file exe per la Shell. Se non è specificato, la shell avrà l'icona che il compilatore c# include (se presente).|
|-initscript p. ps1|Profilo di avvio per la Shell. Il file è incluso "così com'è"; non viene eseguita alcuna verifica della validità da make-Shell.|
|-builtinscript S1. ps1 [, S2. ps1,...]|Elenco di script predefiniti per la Shell. Questi script vengono individuati prima degli script nel percorso e il relativo contenuto non può essere modificato dopo la compilazione della shell.<br /><br /> I file sono inclusi "così come sono"; non viene eseguita alcuna verifica della validità da make-Shell.|
|-Resource resourceFile. txt|Il file con estensione txt contenente le risorse della guida e del banner per la Shell. La prima risorsa è denominata ShellHelp e contiene il testo visualizzato se la shell viene richiamata con il parametro `help`. La seconda risorsa è denominata ShellBanner e contiene il testo e le informazioni sul copyright visualizzate quando la shell viene avviata in modalità interattiva.<br /><br /> Se questo parametro non viene fornito o se queste risorse non sono presenti, vengono usate una guida generica e un banner.|
|-cscflags cscFlags|Flag che devono essere passati al C# compilatore (CSC. exe). Questi vengono passati senza modifiche. Se questo parametro include spazi, deve essere racchiuso tra virgolette doppie.|
|-?<br /><br /> -Guida in linea|Visualizza il messaggio di copyright e le opzioni della riga di comando di make-Shell.|
|-Verbose|Visualizza informazioni dettagliate durante la creazione della shell.|

## <a name="see-also"></a>Vedere anche

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)