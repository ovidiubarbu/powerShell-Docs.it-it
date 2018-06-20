---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Appendice 2 Creazione di un collegamento personalizzato per PowerShell
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949265"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a>Appendice 2 - Creazione di un collegamento personalizzato per PowerShell

La procedura seguente descrive come creare un collegamento a Windows PowerShell con diverse opzioni utili personalizzate.

1. Creare un collegamento che punta a Powershell.exe.

2. Fare clic con il pulsante destro del mouse sul collegamento e quindi scegliere **Proprietà**.

3. Fare clic sulla scheda **Opzioni**.

4. Nella sezione **Opzioni di modifica** selezionare la casella di controllo **Modifica rapida**.

    Questa impostazione consente di selezionare testo nella finestra della console di Windows PowerShell trascinando il pulsante sinistro del mouse e consente di copiare il testo negli Appunti premendo INVIO oppure facendo clic con il pulsante destro del mouse.

5. Nella sezione **Opzioni di modifica** selezionare la casella di controllo **Modalità inserimento**. Questa impostazione consente di fare clic con il pulsante destro del mouse nella finestra della console per incollare automaticamente il testo dagli Appunti.

6. Nella sezione **Cronologia comandi** digitare o selezionare un numero compreso tra 1 e 999 nella casella **Dimensioni buffer**. Questa opzione consente di impostare il numero di comandi digitati che verranno conservati nel buffer della console.

7. Nella sezione **Cronologia comandi** selezionare la casella di controllo **Elimina vecchi duplicati** per eliminare i comandi ripetuti dal buffer della console.

8. Fare clic sulla scheda **Layout**.

9. Nella sezione **Dimensioni buffer dello schermo** digitare un numero compreso trai 1 e 9999 nella casella **Altezza**. L'altezza rappresenta il numero di righe di output inserite nel buffer. Questo è il numero massimo di righe mantenute per la visualizzazione quando si scorre la finestra della console. Se il numero è inferiore rispetto all'altezza indicata nella sezione **Dimensioni finestra**, l'altezza della finestra verrà ridotta automaticamente allo stesso valore.

10. Nella sezione **Dimensioni finestra** digitare un numero compreso tra 1 e 9999 per la larghezza. Questo è il numero di caratteri visualizzati in senso orizzontale nella finestra della console. La larghezza predefinita è 80 e la formattazione dell'output di Windows PowerShell è progettata per questa larghezza.

11. Se si vuole posizionare la console in un particolare punto sul desktop all'apertura, deselezionare la casella di controllo **Posizionamento automatico** nella sezione **Posizione finestra** e quindi modificare i valori nelle caselle **Sinistra** e **Alto** nella sezione **Posizione finestra**.

12. Fare clic su **OK**.