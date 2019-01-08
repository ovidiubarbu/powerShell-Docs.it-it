---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Avvio di Windows PowerShell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401831"
---
# <a name="starting-windows-powershell"></a>Avvio di Windows PowerShell
PowerShell è una libreria di collegamento dinamico del motore di script incorporata in più host.  Gli host più comuni che verranno avviati sono PowerShell.exe e Interactive Scripting Environment PowerShell_ISE.exe dalla riga di comando interattiva.

Per avviare Windows PowerShell® in Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, vedere [Attività di gestione comuni e navigazione](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Come avviare Windows PowerShell in versioni precedenti di Windows

Questa sezione illustra come avviare Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) in Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008. Descrive anche come abilitare la funzionalità facoltativa per Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server® 2008.

Usare uno dei metodi seguenti per avviare la versione installata di Windows PowerShell 3.0 o Windows PowerShell 4.0, se applicabile.

#### <a name="from-the-start-menu"></a>Dal menu Start

- Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.
- Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>Al prompt dei comandi

Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:

```
PowerShell
```

È anche possibile usare i parametri del programma PowerShell.exe per personalizzare la sessione. Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Con privilegi amministrativi ("Esegui come amministratore")

Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Come avviare Windows PowerShell ISE nelle versioni precedenti di Windows

Per avviare Windows PowerShell ISE, usare uno dei seguenti metodi.

#### <a name="from-the-start-menu"></a>Dal menu Start

- Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.
- Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>Al prompt dei comandi

Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:

```
PowerShell_ISE
```

o

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Con privilegi amministrativi ("Esegui come amministratore")

Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Come abilitare Windows PowerShell ISE nelle versioni precedenti di Windows

In Windows PowerShell 4.0 e Windows PowerShell 3.0, Windows PowerShell ISE è abilitato per impostazione predefinita in tutte le versioni di Windows. Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o Windows Management Framework 3.0.

In Windows PowerShell 2.0, Windows PowerShell ISE è abilitato per impostazione predefinita in Windows 7. In Windows Server 2008 R2 e Windows Server 2008, tuttavia, è una funzionalità facoltativa.

Per abilitare Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008, usare la procedura seguente.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Per abilitare Windows PowerShell Integrated Scripting Environment (ISE)

1. Avviare Server Manager.
2. Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.
3. In Selezionare le funzionalità fare clic su Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Avvio della versione a 32 bit di Windows PowerShell

Quando si installa Windows PowerShell in un computer a 64 bit, oltre alla versione a 64 bit viene installato **Windows PowerShell (x86)**, una versione a 32 bit di Windows PowerShell. Quando si esegue Windows PowerShell, viene eseguita la versione a 64 bit per impostazione predefinita.

Tuttavia, in alcuni casi potrebbe essere necessario eseguire **Windows PowerShell (x86)**, ad esempio quando si usa un modulo che richiede la versione a 32 bit o quando ci si connette in remoto a un computer a 32 bit.

Per avviare una versione a 32 bit di Windows PowerShell, usare una delle procedure seguenti.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

- Nella schermata **Start** digitare **Windows PowerShell (x86)**. Fare clic sul riquadro **Windows PowerShell x86**.
- In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.
- Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.
- Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

- Nella schermata **Start** digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.
- In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.
- Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.
- Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

- Nella schermata **Start** digitare **Windows PowerShell (x86)**. Fare clic sul riquadro **Windows PowerShell x86**.
- Se si esegue [Strumenti di amministrazione remota del server](https://go.microsoft.com/fwlink/?LinkID=304145) per Windows 8.1, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.
  Selezionare **Windows PowerShell (x86)**.
- Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.
- Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

- Nella schermata **Start** spostare il cursore nell'angolo in alto a destra, fare clic su **Impostazioni**, fare clic su **Riquadri** e quindi spostare il dispositivo di scorrimento **Mostra strumenti di amministrazione** su Sì. A questo punto digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.
- Se si esegue [Strumenti di amministrazione remota del server](https://www.microsoft.com/download/details.aspx?id=28972) per Windows 8, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**. Selezionare **Windows PowerShell (x86)**.
- Nella schermata **Start** o sul desktop digitare **PowerShell(x86)** e quindi fare clic su **Windows PowerShell (x86)**.
- Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`