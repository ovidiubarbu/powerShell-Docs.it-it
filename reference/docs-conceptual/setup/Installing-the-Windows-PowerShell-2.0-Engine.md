---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Installazione del motore di Windows PowerShell 2.0
ms.assetid: 82928f2b-f96a-4ae6-a0d0-6e7b181da308
ms.openlocfilehash: 37a300d2f0517a819f520c44f0eb92e168444890
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="installing-the-windows-powershell-20-engine"></a>Installazione del motore di Windows PowerShell 2.0
Questo argomento illustra come installare il motore di Windows PowerShell 2.0.

Windows PowerShell 3.0 è progettato per essere compatibile con Windows PowerShell 2.0. I cmdlet, i provider, gli snap-in, i moduli e gli script scritti per Windows PowerShell 2.0 possono essere eseguiti senza modifiche in Windows PowerShell 3.0 e Windows PowerShell 4.0. Tuttavia, a causa di una modifica nei criteri di attivazione di runtime in Microsoft .NET Framework 4, i programmi host di Windows PowerShell scritti per Windows PowerShell 2.0 e compilati con Common Language Runtime (CLR) 2.0 non possono essere eseguiti senza modifiche nelle versioni successive di Windows PowerShell, compilato con CLR 4.0.

Per mantenere la compatibilità con le versioni precedenti di comandi e programmi host interessati da queste modifiche, i motori di Windows PowerShell 2.0, Windows PowerShell 3.0 e Windows PowerShell 4.0 sono progettati per l'esecuzione side-by-side. Inoltre, il motore di Windows PowerShell 2.0 è incluso in Windows Server 2012 R2, Windows 8.1, Windows 8, Windows Server 2012 e Windows Management Framework 3.0. Il motore di Windows PowerShell 2.0 deve essere usato solo quando non è possibile eseguire un programma host o uno script esistente perché non è compatibile con Windows PowerShell 3.0, Windows PowerShell 4.0 o Microsoft .NET Framework 4. È previsto che questi casi siano rari.

Il motore di Windows PowerShell 2.0 è una funzionalità facoltativa di Windows Server 2012 R2, Windows 8.1, Windows® 8 e Windows Server® 2012. Nelle versioni precedenti di Windows, quando si installa Windows Management Framework 3.0, l'installazione di Windows PowerShell 3.0 sostituisce completamente l'installazione di Windows PowerShell 2.0 nella directory di installazione di Windows PowerShell. Il motore di Windows PowerShell 2.0, invece, viene mantenuto.

Per informazioni sull'avvio del motore di Windows PowerShell 2.0, vedere [Avvio del motore di Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-windows-81-and-windows-8"></a>In Windows 8.1 e Windows 8
In Windows 8.1 e Windows 8, la funzionalità del motore di Windows PowerShell 2.0 è attivata per impostazione predefinita. Tuttavia, per usarla è necessario attivare l'opzione per Microsoft .NET Framework 3.5 richiesta. Questa sezione spiega anche come attivare e disattivare la funzionalità del motore di Windows PowerShell 2.0.

#### <a name="to-turn-on-net-framework-35"></a>Per attivare .NET Framework 3.5

1.  Nella schermata **Start** digitare **funzionalità di Windows**.

2.  Nella barra delle app****  fare clic su **Impostazioni** e quindi su **Attivazione o disattivazione delle funzionalità Windows**.

3.  Nella casella **Funzionalità Windows** fare clic su **.NET Framework 3.5 (include .NET 2.0 e 3.0** per selezionarlo.

    Quando si seleziona **.NET Framework 3.5 (include .NET 2.0 e 3.0**, la casella viene compilata per indicare che la funzionalità è selezionata solo in parte. Tuttavia, questo è sufficiente per il motore di Windows PowerShell 2.0.

#### <a name="to-turn-the-windows-powershell-20-engine-on-and-off"></a>Per attivare e disattivare il motore di Windows PowerShell 2.0

1.  Nella schermata **Start** digitare **funzionalità di Windows**.

2.  Nella barra delle app****  fare clic su **Impostazioni** e quindi su **Attivazione o disattivazione delle funzionalità Windows**.

3.  Nella finestra **Funzionalità Windows** espandere il nodo **Windows PowerShell 2.0** e fare clic sulla casella **Motore di Windows PowerShell 2.0** per selezionarla o deselezionarla.

## <a name="on-windows-server-2012-r2-and-windows-server-2012"></a>In Windows Server 2012 R2 e Windows Server 2012
Usare le procedure seguenti per aggiungere le funzionalità Motore di Windows PowerShell 2.0 e Microsoft .NET Framework 3.5. Il motore di Windows PowerShell 2.0 richiede almeno Microsoft .NET Framework 2.0.50727. È possibile soddisfare questo requisito con Microsoft .NET Framework 3.5.

#### <a name="to-add-the-net-framework-35-feature"></a>Per aggiungere la funzionalità .NET Framework 3.5

1.  In **Server Manager** scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

    In alternativa, in **Server Manager** fare clic su **Tutti i server**, fare clic con il pulsante destro del mouse sul nome di un server e quindi selezionare **Aggiungi ruoli e funzionalità**.

2.  Nella pagina **Tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**.

3.  Nella pagina **Funzionalità** espandere il nodo **Funzionalità di .NET Framework 3.5** e selezionare **.NET Framework 3.5 (include .NET 2.0 e 3.0)**.

    Le altre opzioni di tale nodo non sono necessarie per il motore di Windows PowerShell 2.0.

#### <a name="to-add-the-windows-powershell-20-engine-feature"></a>Per installare la funzionalità Motore di Windows PowerShell 2.0

-   In **Server Manager** scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

    In alternativa, in **Server Manager** fare clic su **Tutti i server**, fare clic con il pulsante destro del mouse sul nome di un server e quindi selezionare **Aggiungi ruoli e funzionalità**.

-   Nella pagina **Tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**.

-   Nella pagina **Funzionalità** espandere il nodo **Windows PowerShell (installato)** e selezionare **Motore di Windows PowerShell 2.0**

Per informazioni sull'avvio del motore di Windows PowerShell 2.0, vedere [Avvio del motore di Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md).

## <a name="on-earlier-systems"></a>Nei sistemi precedenti
Il pacchetto [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) che installa Windows PowerShell 4.0 in Windows 7, Windows Server 2008 R2 e Windows Server 2012 include il motore di Windows PowerShell 2.0. Il motore di Windows PowerShell 2.0 è abilitato e pronto per l'uso, se necessario, senza altri interventi di installazione, configurazione o impostazione.

Il pacchetto Windows Management Framework 3.0 che installa Windows PowerShell 3.0 in Windows 7, Windows Server 2008 R2 e Windows Server 2008 include il motore di Windows PowerShell 2.0. Il motore di Windows PowerShell 2.0 è abilitato e pronto per l'uso, se necessario, senza altri interventi di installazione, configurazione o impostazione.

## <a name="see-also"></a>Vedere anche
- [Requisiti di sistema di Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md)
- [Avvio di Windows PowerShell](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)
- [Avvio del motore di Windows PowerShell 2.0](Starting-the-Windows-PowerShell-2.0-Engine.md)

