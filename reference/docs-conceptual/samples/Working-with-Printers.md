---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Utilizzo delle stampanti
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 77ebb26369b6a40e9c8c7bbbc52347d614cbf083
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292994"
---
# <a name="working-with-printers"></a><span data-ttu-id="767a2-103">Utilizzo delle stampanti</span><span class="sxs-lookup"><span data-stu-id="767a2-103">Working with Printers</span></span>

<span data-ttu-id="767a2-104">È possibile usare Windows PowerShell per gestire le stampanti tramite WMI e l'oggetto COM WScript.Network da WSH.</span><span class="sxs-lookup"><span data-stu-id="767a2-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="767a2-105">Verranno usati entrambi gli strumenti per illustrare le attività specifiche.</span><span class="sxs-lookup"><span data-stu-id="767a2-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="767a2-106">Elenco delle connessioni a stampanti</span><span class="sxs-lookup"><span data-stu-id="767a2-106">Listing Printer Connections</span></span>

<span data-ttu-id="767a2-107">Il modo più semplice per elencare le stampanti installate in un computer consiste nell'usare la classe WMI **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="767a2-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="767a2-108">È anche possibile ottenere un elenco delle stampanti tramite l'oggetto COM **Wscript.Network** generalmente usato negli script WSH:</span><span class="sxs-lookup"><span data-stu-id="767a2-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="767a2-109">Poiché questo comando restituisce una semplice raccolta di stringhe di nomi di porta e nomi di dispositivo stampante senza alcuna etichetta distintiva, non è facile da interpretare.</span><span class="sxs-lookup"><span data-stu-id="767a2-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="767a2-110">Aggiunta di una stampante di rete</span><span class="sxs-lookup"><span data-stu-id="767a2-110">Adding a Network Printer</span></span>

<span data-ttu-id="767a2-111">Per aggiungere una nuova stampante di rete, usare **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="767a2-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="767a2-112">Impostazione di una stampante predefinita</span><span class="sxs-lookup"><span data-stu-id="767a2-112">Setting a Default Printer</span></span>

<span data-ttu-id="767a2-113">Per usare WMI per impostare la stampante predefinita, individuare la stampante nella raccolta **Win32_Printer** e quindi richiamare il metodo **SetDefaultPrinter**:</span><span class="sxs-lookup"><span data-stu-id="767a2-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="767a2-114">**WScript.Network** è un po' più semplice da usare, perché include un metodo **SetDefaultPrinter** che accetta solo il nome della stampante come argomento:</span><span class="sxs-lookup"><span data-stu-id="767a2-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="767a2-115">Rimozione di una connessione della stampante</span><span class="sxs-lookup"><span data-stu-id="767a2-115">Removing a Printer Connection</span></span>

<span data-ttu-id="767a2-116">Per rimuovere una connessione alla stampante, usare il metodo **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="767a2-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```