---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Utilizzo delle stampanti
ms.technology: powershell
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: a75d0fc653bda7b368d3e1978d828040c3e67e3f
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="working-with-printers"></a>Utilizzo delle stampanti
È possibile usare Windows PowerShell per gestire le stampanti tramite WMI e l'oggetto COM WScript.Network da WSH. Verranno usati entrambi gli strumenti per illustrare le attività specifiche.

### <a name="listing-printer-connections"></a>Elenco delle connessioni a stampanti
Il modo più semplice per elencare le stampanti installate in un computer consiste nell'usare la classe WMI **Win32_Printer**:

```
Get-WmiObject -Class Win32_Printer -ComputerName
```

È anche possibile ottenere un elenco delle stampanti tramite l'oggetto COM **Wscript.Network** generalmente usato negli script WSH:

```
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

Poiché questo comando restituisce una semplice raccolta di stringhe di nomi di porta e nomi di dispositivo stampante senza alcuna etichetta distintiva, non è facile da interpretare.

### <a name="adding-a-network-printer"></a>Aggiunta di una stampante di rete
Per aggiungere una nuova stampante di rete, usare **WScript.Network**:

```
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a>Impostazione di una stampante predefinita
Per usare WMI per impostare la stampante predefinita, individuare la stampante nella raccolta **Win32_Printer** e quindi richiamare il metodo **SetDefaultPrinter**:

```
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

**WScript.Network** è un po' più semplice da usare, perché include un metodo **SetDefaultPrinter** che accetta solo il nome della stampante come argomento:

```
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a>Rimozione di una connessione della stampante
Per rimuovere una connessione alla stampante, usare il metodo **WScript.Network RemovePrinterConnection**:

```
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```

