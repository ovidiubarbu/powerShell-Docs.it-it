---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Avvio della versione a 32 bit di Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a>Avvio della versione a 32 bit di Windows PowerShell
Quando si installa Windows PowerShell in un computer a 64 bit, oltre alla versione a 64 bit viene installato **Windows PowerShell (x86)**, una versione a 32 bit di Windows PowerShell. Quando si esegue Windows PowerShell, viene eseguita la versione a 64 bit per impostazione predefinita.

Tuttavia, in alcuni casi potrebbe essere necessario eseguire **Windows PowerShell (x86)**, ad esempio quando si usa un modulo che richiede la versione a 32 bit o quando ci si connette in remoto a un computer a 32 bit.

Per avviare una versione a 32 bit di Windows PowerShell, usare una delle procedure seguenti.

#### <a name="in-windows-server-2012-r2"></a>In Windows Server® 2012 R2

-   Nella schermata **Start** digitare **Windows PowerShell (x86)**. Fare clic sul riquadro **Windows PowerShell x86**.

-   In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.

-   Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.

-   Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>In Windows Server® 2012

-   Nella schermata **Start** digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.

-   In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.

-   Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.

-   Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>In Windows® 8.1

-   Nella schermata **Start** digitare **Windows PowerShell (x86)**. Fare clic sul riquadro **Windows PowerShell x86**.

-   Se si esegue [Strumenti di amministrazione remota del server](http://go.microsoft.com/fwlink/?LinkID=304145) per Windows 8.1, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**. Selezionare **Windows PowerShell (x86)**.

-   Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.
   
-   Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>In Windows® 8

-   Nella schermata **Start** spostare il cursore nell'angolo in alto a destra, fare clic su **Impostazioni**, fare clic su **Riquadri** e quindi spostare il dispositivo di scorrimento **Mostra strumenti di amministrazione** su Sì. A questo punto digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.

-   Se si esegue [Strumenti di amministrazione remota del server](http://www.microsoft.com/download/details.aspx?id=28972) per Windows 8, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**. Selezionare **Windows PowerShell (x86)**.

-   Nella schermata **Start** o sul desktop digitare **PowerShell(x86)** e quindi fare clic su **Windows PowerShell (x86)**.

-   Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

