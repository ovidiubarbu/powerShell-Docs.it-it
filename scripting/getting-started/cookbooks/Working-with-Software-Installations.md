---
title: Gestione delle installazioni di software
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 9f60be9bebe9dfaa98f495c8e9a9c0d8c2fa5cc2

---

# Gestione delle installazioni di software
Le applicazioni progettate per l'uso di Windows Installer sono accessibili tramite la classe **Win32\_Product** di WMI, ma non tutte le applicazioni oggi disponibili prevedono l'uso di Windows Installer. Poiché Windows Installer offre la gamma più ampia di tecniche standard per la gestione di applicazioni installabili, questo articolo è incentrato principalmente su tali applicazioni. Le applicazioni che prevedono l'uso di procedure di installazione alternative non vengono in genere gestite da Windows Installer. Le tecniche specifiche per la gestione di queste applicazioni variano in base al software del programma di installazione e alle decisioni prese dallo sviluppatore.

> [!NOTE]
> Le applicazioni istallate tramite la copia dei relativi file nel computer non possono in genere essere gestite con le tecniche descritte in questo articolo. È possibile gestire tali applicazioni come file e cartelle usando le tecniche descritte nella sezione "Gestione di file e cartelle".

### Visualizzazione di un elenco di applicazioni di Windows Installer
Per elencare le applicazioni installate con Windows Installer in un sistema locale o remoto, usare la semplice query WMI seguente:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Per visualizzare tutte le proprietà dell'oggetto Win32\_Product, usare il parametro Properties dei cmdlet di formattazione, ad esempio Format\-List, con il valore \* (tutti).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *
Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

In alternativa, è possibile usare il parametro **Get\-WmiObject Filter** per selezionare solo Microsoft .NET Framework 2.0. Poiché il filtro usato in questo comando è di WMI, viene usata la sintassi WQL (WMI Query Language) e non quella di Windows PowerShell. Ad esempio:

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Si noti che le query WQL usano spesso caratteri come spazi o segni di uguale che hanno un significato speciale in Windows PowerShell. Per questo motivo, è consigliabile racchiudere sempre il valore del parametro Filter tra virgolette. È anche possibile usare il carattere di escape di Windows PowerShell, un apice inverso (\`), anche se potrebbe influire negativamente sulla leggibilità. Il comando seguente è equivalente a quello precedente e restituisce gli stessi risultati, ma usa l'apice inverso come escape per i caratteri speciali, invece di racchiudere tra virgolette l'intera stringa di filtro.

```
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Per elencare solo le proprietà desiderate, usare il parametro Property dei cmdlet di formattazione.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Infine, per trovare solo i nomi delle applicazioni installate, una semplice istruzione **Format\-Wide** semplifica l'output:

```
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

A questo punto sono stati illustrati i vari modi in cui è possibile esaminare le applicazioni che usano Windows Installer per l'installazione, mentre non sono state considerate le altre applicazioni. Poiché la maggior parte delle applicazioni standard registra il proprio programma di disinstallazione con Windows, è possibile gestirle localmente individuandole nel Registro di sistema di Windows.

### Visualizzazione di un elenco di tutte le applicazioni disinstallabili
Anche se non esiste nessun modo garantito per trovare tutte le applicazioni in un sistema, è possibile trovare tutti i programmi con gli elenchi visualizzati nella finestra di dialogo Installazione applicazioni. Installazione applicazioni trova queste applicazioni nella seguente chiave del Registro di sistema:

**HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

È anche possibile esaminare questa chiave per trovare applicazioni. Per semplificare la visualizzazione della chiave Uninstall, è possibile mappare un'unità di Windows PowerShell a questo percorso del Registro di sistema:

```
PS>    

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> L'unità **HKLM:** viene mappata alla radice di **HKEY\_LOCAL\_MACHINE**, quindi viene usata questa unità nel percorso della chiave Uninstall. Invece di usare **HKLM:**, è possibile specificare il percorso del Registro di sistema usando **HKLM** o **HKEY\_LOCAL\_MACHINE**. L'uso di un'unità esistente del Registro di sistema offre il vantaggio di poter completare i nomi delle chiavi tramite TAB, invece di digitarli.

In questo caso diventa disponibile un'unità "Uninstall" che è possibile usare per cercare le applicazioni installate in modo rapido e immediato. È possibile trovare il numero di applicazioni installate contando il numero delle chiavi del Registro di sistema nell'unità di Windows PowerShell Uninstall:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

È possibile eseguire altre ricerche nell'elenco di applicazioni usando varie tecniche, a partire da **Get\-ChildItem**. Per ottenere un elenco di applicazioni e salvarlo nella variabile **$UninstallableApplications**, usare il comando seguente:

```
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> In questo caso per chiarezza viene usato un nome di variabile lungo. Nell'uso effettivo, non c'è alcun motivo per usare nomi lunghi. Sebbene sia possibile usare TAB per completare i nomi delle variabili, è anche possibile usare nomi di 1-2 caratteri per velocizzare l'immissione. I nomi descrittivi più lunghi risultano più utili quando si sviluppa codice per il riutilizzo.

Per visualizzare i valori delle voci del Registro di sistema nelle chiavi sotto Uninstall, usare il metodo GetValue delle chiavi del Registro di sistema. Il valore del metodo corrisponde al nome della voce del Registro di sistema.

Per trovare ad esempio i nomi visualizzati delle applicazioni nella chiave Uninstall, usare il comando seguente:

```
PS> Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("DisplayName") }
```

Non c'è nessuna garanzia che questi valori siano univoci. Nell'esempio seguente due elementi installati vengono visualizzati come "Windows Media Encoder 9 Series":

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### Installazione di applicazioni
È possibile usare la classe **Win32\_Product** per installare i pacchetti di Windows Installer, in remoto o in locale.

> [!NOTE]
> In Windows Vista, Windows Server 2008 e nelle versioni più recenti di Windows, per installare un'applicazione è necessario avviare Windows PowerShell con l'opzione "Esegui come amministratore".

Per l'installazione in remoto, usare un percorso di rete UNC (Universal Naming Convention) per specificare il percorso del pacchetto MSI, perché il sottosistema WMI non riconosce i percorsi di Windows PowerShell. Ad esempio, per installare il pacchetto NewPackage.msi situato nella condivisione di rete \\\\AppServ\\dsp nel computer remoto PC01, digitare il comando seguente al prompt di Windows PowerShell:

```
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq "Win32_Product"}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Per le applicazioni che non usano la tecnologia Windows Installer possono essere disponibili metodi specifici per la distribuzione automatizzata. Per determinare se esiste un metodo per l'automazione della distribuzione, consultare la documentazione dell'applicazione oppure il sistema di supporto del fornitore. In alcuni casi, anche se il fornitore non progetta specificamente l'applicazione per l'automazione dell'installazione, il produttore del software del programma di installazione potrebbe avere alcune tecniche per l'automazione.

### Rimozione di applicazioni
La procedura per rimuovere un pacchetto Windows Installer tramite Windows PowerShell è molto simile a quella per installarlo. Ecco un esempio in cui il pacchetto da disinstallare viene selezionato in base al nome. In alcuni casi può risultare più semplice applicare un filtro con **IdentifyingNumber**:

```
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

La rimozione di altre applicazioni non è altrettanto semplice, neanche se viene eseguita in locale. Per trovare le stringhe di disinstallazione dalla riga di comando per queste applicazioni, estrarre la proprietà **UninstallString**. Questo metodo funziona per le applicazioni di Windows Installer e per i programmi meno recenti visualizzati nella chiave Uninstall:

```
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

Se si preferisce, è possibile filtrare l'output in base al nome visualizzato:

```
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -like "Win*"} | ForEach-Object -Process { $_.GetValue("UninstallString") }
```

Tuttavia, queste stringhe potrebbero non essere utilizzabili direttamente al prompt di Windows PowerShell senza apportare alcune modifiche.

### Aggiornamento delle applicazioni di Windows Installer
Per aggiornare un'applicazione, è necessario conoscerne il nome e il percorso del pacchetto di aggiornamento. Con queste informazioni, è possibile aggiornare un'applicazione con un singolo comando di Windows PowerShell:

```
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```




<!--HONumber=Jun16_HO4-->


