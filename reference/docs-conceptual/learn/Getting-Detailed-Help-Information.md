---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Ottenere informazioni dettagliate della Guida
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: e58814f512aa2c5914f92f942cf2a4a76956ee20
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794570"
---
# <a name="getting-detailed-help-information"></a>Ottenere informazioni dettagliate della Guida

PowerShell include articoli della Guida dettagliati che descrivono concetti correlati a PowerShell e il linguaggio PowerShell. Sono disponibili anche articoli della Guida per ogni cmdlet e provider e per molti script e funzioni.

È possibile visualizzare questi articoli nel prompt dei comandi o esaminare la versione più recente di questi articoli online nella documentazione di [PowerShell](/powershell/scripting/overview).

## <a name="getting-help-for-cmdlets"></a>Ottenere informazioni della Guida per i cmdlet

Per ottenere informazioni della Guida sui cmdlet di PowerShell, usare il cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help). Ad esempio, per ottenere informazioni della Guida sul cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem
```

o

```powershell
Get-ChildItem -?
```

È anche possibile ottenere informazioni della Guida sul cmdlet Get-Help. Ad esempio:

```powershell
Get-Help Get-Help
```

Per ottenere un elenco di tutti gli articoli della Guida sui cmdlet nella sessione, digitare:

```powershell
Get-Help -Category Cmdlet
```

Per visualizzare una pagina di ogni articolo per volta, usare la funzione `help` o l'alias associato `man`.
Ad esempio, per visualizzare la Guida per il cmdlet `Get-ChildItem`, digitare

```powershell
man Get-ChildItem
```

o

```powershell
help Get-ChildItem
```

Per visualizzare informazioni dettagliate, usare il parametro **Detailed** del cmdlet `Get-Help`. Ad esempio, per ottenere informazioni dettagliate sul cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem -Detailed
```

Per visualizzare tutto il contenuto dell'articolo della Guida, usare il parametro **Full** del cmdlet `Get-Help`. Ad esempio, per visualizzare tutto il contenuto dell'articolo della Guida per il cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem -Full
```

Per ottenere informazioni della Guida dettagliate sui parametri di un cmdlet, usare il parametro **Parameter** del cmdlet `Get-Help`. Ad esempio, per ottenere informazioni della Guida dettagliate per tutti i parametri del cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem -Parameter *
```

Per visualizzare solo gli esempi in un articolo della Guida, usare il parametro **Examples** del cmdlet `Get-Help`.
Ad esempio, per visualizzare solo gli esempi dell'articolo della Guida per il cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem -Examples
```

Per informazioni su come scrivere articoli della Guida per i cmdlet personalizzati, vedere [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets) (Come scrivere articoli della Guida sui cmdlet).

## <a name="getting-conceptual-help"></a>Ottenere informazioni della Guida di carattere concettuale

Il cmdlet `Get-Help` visualizza anche informazioni sugli articoli di carattere concettuale in PowerShell, tra cui gli articoli sul linguaggio PowerShell. Gli articoli della Guida di carattere concettuale iniziano con il prefisso "about_", ad esempio about_line_editing. Il nome dell'articolo di carattere concettuale deve essere immesso in inglese anche nelle versioni di Windows PowerShell in altre lingue.

Per visualizzare un elenco di articoli di carattere concettuale, digitare:

```powershell
Get-Help about_*
```

Per visualizzare un articolo specifico della Guida, digitarne il nome, ad esempio:

```powershell
Get-Help about_command_syntax
```

I parametri di `Get-Help`, come **Detailed**, **Parameter** ed **Examples**, non hanno effetto sulla visualizzazione di articoli della Guida di carattere concettuale.

## <a name="getting-help-about-providers"></a>Ottenere informazioni della Guida sui provider

Il cmdlet `Get-Help` visualizza informazioni sui provider di PowerShell. Per ottenere informazioni della Guida su un provider, digitare `Get-Help` seguito dal nome del provider. Per visualizzare ad esempio la Guida per il provider del Registro di sistema, digitare:

```powershell
Get-Help registry
```

Per ottenere un elenco di tutti gli argomenti della Guida sui provider nella sessione, digitare

```powershell
Get-Help -Category provider
```

I parametri di `Get-Help`, come **Detailed**, **Parameter** ed **Examples**, non hanno effetto sulla visualizzazione di articoli della Guida sui provider.

## <a name="getting-help-about-scripts-and-functions"></a>Ottenere informazioni della Guida su script e funzioni

In PowerShell sono disponibili argomenti della Guida per molti script e funzioni. Usare il cmdlet `Get-Help` per visualizzare gli argomenti della Guida per script e funzioni.

Per visualizzare la Guida per una funzione, digitare `Get-Help` seguito dal nome della funzione. Ad esempio, per ottenere informazioni della Guida per la funzione `Disable-PSRemoting`, digitare:

```powershell
Get-Help Disable-PSRemoting
```

Per visualizzare la Guida per uno script, digitare il percorso del file script. Se lo script non si trova in un percorso elencato nella variabile di ambiente Path, è necessario usare il percorso completo.

Ad esempio, per visualizzare l'articolo della Guida per uno script denominato "TestScript.ps1" nella directory C:\\PS-Test, digitare:

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

I parametri progettati per la visualizzazione della Guida dei cmdlet, funzionano anche per gli script e le funzioni. Tuttavia, la Guida per le funzioni e gli script non viene visualizzata quando si esegue `Get-Help *`.

Per informazioni sulla redazione di articoli della Guida per le funzioni e gli script, vedere gli articoli seguenti:

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>Ottenere informazioni della Guida online

La visualizzazione online degli articoli della Guida è uno dei metodi migliori per ottenere informazioni utili. Gli articoli online sono più semplici da aggiornare e offrono i contenuti più recenti.

Per ottenere informazioni della Guida online, usare il parametro **Online** del cmdlet `Get-Help`. Tutti gli articoli della Guida per PowerShell, inclusi gli articoli della Guida di carattere concettuale (About) e sui provider, sono disponibili online nella documentazione di [PowerShell](/powershell/scripting/powershell-scripting).

> [!NOTE]
> Non è possibile usare il parametro **Online** con gli articoli della Guida di natura concettuale (about_\*) o sui provider.
> Poiché la Guida online è facoltativa, non funziona per ogni cmdlet, funzione o script.

Ad esempio, per ottenere la versione online dell'articolo della Guida sul cmdlet `Get-ChildItem`, digitare:

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell visualizza l'articolo nel browser predefinito. Se la Guida online è supportata per un articolo della Guida, è anche possibile visualizzare l'URL dell'articolo. L'URL appare nella sezione Collegamenti correlati di un articolo della Guida.

Per visualizzare ad esempio l'URL per la versione online del cmdlet Add-Computer, digitare:

```powershell
Get-Help Add-Computer
```

Di seguito viene mostrata la prima riga della sezione Collegamenti correlati dell'articolo.

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

Per informazioni su come offrire supporto online per gli articoli della Guida personalizzati, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

## <a name="see-also"></a>Vedere anche

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
