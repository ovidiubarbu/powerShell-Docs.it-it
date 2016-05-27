---
title:  Avvio di Windows PowerShell in versioni precedenti di Windows
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---

# Avvio di Windows PowerShell in versioni precedenti di Windows
Questa sezione illustra come avviare Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) in Windows® 7, Windows Server® 2008 R2 e Windows Server 2008. Spiega anche come abilitare la funzionalità facoltativa per Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008.

Per installare Windows PowerShell 4.0 nei sistemi supportati, scaricare e installare [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).

Per installare Windows PowerShell 3.0 nei sistemi supportati, scaricare e installare [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).

## Come avviare Windows PowerShell in versioni precedenti di Windows
Usare uno dei metodi seguenti per avviare la versione installata di Windows PowerShell 3.0 o Windows PowerShell 4.0, se applicabile.

#### Dal menu Start

-   Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.

-   Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.

#### Al prompt dei comandi

-   Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:

    ```
    PowerShell
    ```

    È anche possibile usare i parametri del programma PowerShell.exe per personalizzare la sessione. Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### Con privilegi amministrativi ("Esegui come amministratore")

1.  Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.

## Come avviare Windows PowerShell ISE nelle versioni precedenti di Windows
Per avviare Windows PowerShell ISE, usare uno dei seguenti metodi.

#### Dal menu Start

-   Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.

-   Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.

#### Al prompt dei comandi

-   Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:

    ```
    PowerShell_ISE
    ```

    o

    ```
    ISE
    ```

#### Con privilegi amministrativi ("Esegui come amministratore")

1.  Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.

## Come abilitare Windows PowerShell ISE nelle versioni precedenti di Windows
In Windows PowerShell 4.0 e Windows PowerShell 3.0, Windows PowerShell ISE è abilitato per impostazione predefinita in tutte le versioni di Windows. Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o Windows Management Framework 3.0.

In Windows PowerShell 2.0, Windows PowerShell ISE è abilitato per impostazione predefinita in Windows 7. In Windows Server 2008 R2 e Windows Server 2008, tuttavia, è una funzionalità facoltativa.

Per abilitare Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008, usare la procedura seguente.

#### Per abilitare Windows PowerShell Integrated Scripting Environment (ISE)

1.  Avviare Server Manager.

2.  Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.

3.  In Selezionare le funzionalità fare clic su Windows PowerShell Integrated Scripting Environment (ISE).



<!--HONumber=May16_HO2-->


