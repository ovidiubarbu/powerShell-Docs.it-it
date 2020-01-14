---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Utilizzo delle stampanti
ms.openlocfilehash: 47c4f230d023ad93e2b65080feaa1dbfae803d08
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736863"
---
# <a name="working-with-printers-in-windows"></a><span data-ttu-id="68d07-103">Uso delle stampanti in Windows</span><span class="sxs-lookup"><span data-stu-id="68d07-103">Working with Printers in Windows</span></span>

<span data-ttu-id="68d07-104">È possibile usare PowerShell per gestire le stampanti tramite WMI e l'oggetto COM **WScript.Network** di WSH.</span><span class="sxs-lookup"><span data-stu-id="68d07-104">You can use PowerShell to manage printers by using WMI and the **WScript.Network** COM object from WSH.</span></span> <span data-ttu-id="68d07-105">Verranno usati entrambi gli strumenti per illustrare le attività specifiche.</span><span class="sxs-lookup"><span data-stu-id="68d07-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="68d07-106">Elenco delle connessioni a stampanti</span><span class="sxs-lookup"><span data-stu-id="68d07-106">Listing Printer Connections</span></span>

<span data-ttu-id="68d07-107">Il modo più semplice per elencare le stampanti installate in un computer consiste nell'usare la classe WMI **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="68d07-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-CimInstance -Class Win32_Printer
```

<span data-ttu-id="68d07-108">È anche possibile ottenere un elenco delle stampanti tramite l'oggetto COM **Wscript.Network** generalmente usato negli script WSH:</span><span class="sxs-lookup"><span data-stu-id="68d07-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="68d07-109">Poiché questo comando restituisce una semplice raccolta di stringhe di nomi di porta e nomi di dispositivo stampante senza alcuna etichetta distintiva, non è facile da interpretare.</span><span class="sxs-lookup"><span data-stu-id="68d07-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="68d07-110">Aggiunta di una stampante di rete</span><span class="sxs-lookup"><span data-stu-id="68d07-110">Adding a Network Printer</span></span>

<span data-ttu-id="68d07-111">Per aggiungere una nuova stampante di rete, usare **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="68d07-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="68d07-112">Impostazione di una stampante predefinita</span><span class="sxs-lookup"><span data-stu-id="68d07-112">Setting a Default Printer</span></span>

<span data-ttu-id="68d07-113">Per usare WMI per impostare la stampante predefinita, individuare la stampante nella raccolta **Win32_Printer** e quindi richiamare il metodo **SetDefaultPrinter**:</span><span class="sxs-lookup"><span data-stu-id="68d07-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="68d07-114">**WScript.Network** è un po' più semplice da usare, perché include un metodo **SetDefaultPrinter** che accetta solo il nome della stampante come argomento:</span><span class="sxs-lookup"><span data-stu-id="68d07-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="68d07-115">Rimozione di una connessione della stampante</span><span class="sxs-lookup"><span data-stu-id="68d07-115">Removing a Printer Connection</span></span>

<span data-ttu-id="68d07-116">Per rimuovere una connessione alla stampante, usare il metodo **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="68d07-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
