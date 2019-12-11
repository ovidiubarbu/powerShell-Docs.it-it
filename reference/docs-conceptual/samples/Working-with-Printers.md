---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Utilizzo delle stampanti
ms.openlocfilehash: 816388325cc3155f1dbd1bc15fc1736155216092
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030669"
---
# <a name="working-with-printers"></a>Utilizzo delle stampanti

È possibile usare Windows PowerShell per gestire le stampanti tramite WMI e l'oggetto COM WScript.Network da WSH. Verranno usati entrambi gli strumenti per illustrare le attività specifiche.

## <a name="listing-printer-connections"></a>Elenco delle connessioni a stampanti

Il modo più semplice per elencare le stampanti installate in un computer consiste nell'usare la classe WMI **Win32_Printer**:

```powershell
Get-WmiObject -Class Win32_Printer
```

È anche possibile ottenere un elenco delle stampanti tramite l'oggetto COM **Wscript.Network** generalmente usato negli script WSH:

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Poiché questo comando restituisce una semplice raccolta di stringhe di nomi di porta e nomi di dispositivo stampante senza alcuna etichetta distintiva, non è facile da interpretare.

## <a name="adding-a-network-printer"></a>Aggiunta di una stampante di rete

Per aggiungere una nuova stampante di rete, usare **WScript.Network**:

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>Impostazione di una stampante predefinita

Per usare WMI per impostare la stampante predefinita, individuare la stampante nella raccolta **Win32_Printer** e quindi richiamare il metodo **SetDefaultPrinter**:

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** è un po' più semplice da usare, perché include un metodo **SetDefaultPrinter** che accetta solo il nome della stampante come argomento:

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>Rimozione di una connessione della stampante

Per rimuovere una connessione alla stampante, usare il metodo **WScript.Network RemovePrinterConnection**:

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
