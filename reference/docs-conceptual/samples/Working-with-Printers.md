---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Utilizzo delle stampanti
ms.openlocfilehash: 1d6b9a57ec61f06af694757dc8017d50b4dd40fe
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "78935204"
---
# <a name="working-with-printers-in-windows"></a><span data-ttu-id="60e33-103">Uso delle stampanti in Windows</span><span class="sxs-lookup"><span data-stu-id="60e33-103">Working with Printers in Windows</span></span>

<span data-ttu-id="60e33-104">È possibile usare PowerShell per gestire le stampanti tramite WMI e l'oggetto COM **WScript.Network** di WSH.</span><span class="sxs-lookup"><span data-stu-id="60e33-104">You can use PowerShell to manage printers by using WMI and the **WScript.Network** COM object from WSH.</span></span> <span data-ttu-id="60e33-105">Verranno usati entrambi gli strumenti per illustrare le attività specifiche.</span><span class="sxs-lookup"><span data-stu-id="60e33-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

## <a name="listing-printer-connections"></a><span data-ttu-id="60e33-106">Elenco delle connessioni a stampanti</span><span class="sxs-lookup"><span data-stu-id="60e33-106">Listing Printer Connections</span></span>

<span data-ttu-id="60e33-107">Il modo più semplice per elencare le stampanti installate in un computer consiste nell'usare la classe WMI **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="60e33-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-CimInstance -Class Win32_Printer
```

<span data-ttu-id="60e33-108">È anche possibile ottenere un elenco delle stampanti tramite l'oggetto COM **Wscript.Network** generalmente usato negli script WSH:</span><span class="sxs-lookup"><span data-stu-id="60e33-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="60e33-109">Poiché questo comando restituisce una semplice raccolta di stringhe di nomi di porta e nomi di dispositivo stampante senza alcuna etichetta distintiva, non è facile da interpretare.</span><span class="sxs-lookup"><span data-stu-id="60e33-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

## <a name="adding-a-network-printer"></a><span data-ttu-id="60e33-110">Aggiunta di una stampante di rete</span><span class="sxs-lookup"><span data-stu-id="60e33-110">Adding a Network Printer</span></span>

<span data-ttu-id="60e33-111">Per aggiungere una nuova stampante di rete, usare **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="60e33-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a><span data-ttu-id="60e33-112">Impostazione di una stampante predefinita</span><span class="sxs-lookup"><span data-stu-id="60e33-112">Setting a Default Printer</span></span>

<span data-ttu-id="60e33-113">Per usare WMI per impostare la stampante predefinita, individuare la stampante nella raccolta **Win32_Printer** e quindi richiamare il metodo **SetDefaultPrinter**:</span><span class="sxs-lookup"><span data-stu-id="60e33-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

<span data-ttu-id="60e33-114">**WScript.Network** è un po' più semplice da usare, perché include un metodo **SetDefaultPrinter** che accetta solo il nome della stampante come argomento:</span><span class="sxs-lookup"><span data-stu-id="60e33-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a><span data-ttu-id="60e33-115">Rimozione di una connessione della stampante</span><span class="sxs-lookup"><span data-stu-id="60e33-115">Removing a Printer Connection</span></span>

<span data-ttu-id="60e33-116">Per rimuovere una connessione alla stampante, usare il metodo **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="60e33-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
