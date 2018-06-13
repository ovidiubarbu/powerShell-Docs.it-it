---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ottenere informazioni dettagliate della Guida
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483033"
---
# <a name="getting-detailed-help-information"></a>Ottenere informazioni dettagliate della Guida
Windows PowerShell include argomenti dettagliati della Guida che illustrano i concetti e il linguaggio di Windows PowerShell. Sono inoltre disponibili argomenti della Guida per tutti i cmdlet e i provider, nonché per molti script e funzioni.

È possibile visualizzare gli argomenti della Guida al prompt dei comandi oppure visualizzarne le versioni più aggiornate nella Libreria Microsoft TechNet. Molti programmi che ospitano Windows PowerShell, come Windows PowerShell Integrated Scripting Environment, offrono funzionalità aggiuntive della Guida, come la Guida sensibile al contesto e il file della Guida compilato (con estensione chm).

## <a name="getting-help-for-cmdlets"></a>Ottenere informazioni della Guida per i cmdlet
Per ottenere informazioni della Guida sui cmdlet di Windows PowerShell, usare il cmdlet [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2). Per visualizzare ad esempio la Guida per il cmdlet [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), digitare:

```
get-help get-childitem
```

o

```
get-childitem -?
```

È anche possibile ottenere informazioni della Guida sul cmdlet Get-Help. Ad esempio:

```
get-help get-help
```

Per ottenere un elenco di tutti gli argomenti della Guida sui cmdlet nella sessione corrente, digitare:

```
get-help -category cmdlet
```

Per visualizzare una pagina alla volta di ogni argomento della Guida, usare la funzione **help** o il relativo alias **man**. Per visualizzare ad esempio la Guida per il cmdlet Get-ChildItem, digitare:

```
man get-childitem
```

o

```
help get-childitem
```

Per visualizzare informazioni dettagliate su un cmdlet, una funzione o uno script, incluse le descrizioni dei relativi parametri ed esempi della sua applicazione, usare il parametro *Detailed* del cmdlet Get-Help. Per ottenere ad esempio informazioni dettagliate sul cmdlet Get-ChildItem, digitare:

```
get-help get-childitem -detailed
```

Per visualizzare l'intero contenuto dell'argomento della Guida, usare il parametro *Full* del cmdlet Get-Help. Per visualizzare ad esempio l'intero contenuto dell'argomento della Guida per il cmdlet Get-ChildItem, digitare:

```
get-help get-childitem -full
```

Per ottenere informazioni dettagliate della Guida sui parametri di un cmdlet, usare il parametro *Parameter* del cmdlet Get-Help. Per ottenere ad esempio informazioni dettagliate della Guida per tutti i parametri del cmdlet Get-ChildItem, digitare:

```
get-help get-childitem -parameter *
```

Per visualizzare solo gli esempi di un argomento della Guida, usare il parametro *Example* di Get-Help. Per visualizzare ad esempio solo gli esempi dell'argomento della Guida per il cmdlet Get-ChildItem, digitare:

```
get-help get-childitem -examples
```

Per informazioni su come scrivere argomenti della Guida per cmdlet personalizzati, vedere [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere la Guida dei cmdlet) in MSDN Library.

## <a name="getting-conceptual-help"></a>Ottenere informazioni della Guida concettuale
Il cmdlet Get-Help visualizza anche informazioni sugli argomenti concettuali in Windows PowerShell, inclusi gli argomenti sul linguaggio di Windows PowerShell. Gli argomenti della Guida concettuale iniziano con il prefisso "about_", ad esempio about_line_editing (il nome dell'argomento concettuale deve essere immesso in inglese anche nelle versioni di Windows PowerShell in altre lingue).

Per visualizzare un elenco di argomenti concettuali, digitare:

```
get-help about_*
```

Per visualizzare uno specifico argomento della Guida, digitare il nome dell'argomento, ad esempio:

```
get-help about_command_syntax
```

I parametri di Get-Help, come *Detailed*, *Parameter* e *Examples*, non hanno alcun effetto sulla visualizzazione degli argomenti della Guida concettuale.

## <a name="getting-help-about-providers"></a>Ottenere informazioni della Guida sui provider
Il cmdlet Get-Help visualizza informazioni sui provider di Windows PowerShell. Per visualizzare le informazioni della Guida per un provider, digitare "Get-Help" seguito dal nome del provider. Per visualizzare ad esempio la Guida per il provider del Registro di sistema, digitare:

```
get-help registry
```

Per ottenere un elenco di tutti gli argomenti della Guida sui provider nella sessione corrente, digitare:

```
get-help -category provider
```

I parametri di Get-Help, come *Detailed*, *Parameter* e *Examples*, non hanno alcun effetto sulla visualizzazione degli argomenti della Guida sui provider.

## <a name="getting-help-about-scripts-and-functions"></a>Ottenere informazioni della Guida sugli script e sulle funzioni
A molti script e funzioni di Windows PowerShell sono associati argomenti della Guida. Usare il cmdlet Get-Help per visualizzare gli argomenti della Guida per gli script e le funzioni.

Per visualizzare la Guida per una funzione, digitare "get-help" seguito dal nome della funzione. Per ottenere ad esempio informazioni della Guida per la funzione Disable-PSRemoting, digitare:

```
get-help disable-psremoting
```

Per visualizzare la Guida per uno script, digitare il percorso completo del file di script. Se lo script è in un percorso elencato nella variabile di ambiente Path, è possibile omettere il percorso dal comando.

Se ad esempio si dispone di uno script denominato "TestScript.ps1" nella directory C:\\PS-Test, per visualizzare l'argomento della Guida per lo script digitare:

```
get-help c:\ps-test\TestScript.ps1
```

I parametri progettati per la visualizzazione della Guida dei cmdlet, come *Detailed*, *Full*, *Examples* e *Parameter*, possono essere usati anche per la Guida relativa agli script e alle funzioni. Quando tuttavia si visualizza l'intera Guida, digitando "get-help \*", la Guida per le funzioni e gli script non viene visualizzata.

Per informazioni su come scrivere argomenti della Guida per funzioni e script personalizzati, vedere [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af) e [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).

## <a name="getting-help-online"></a>Ottenere informazioni della Guida online
Se si è connessi a Internet, uno dei modi migliori per ottenere assistenza è visualizzare gli argomenti della Guida online. Essendo più semplici da aggiornare, gli argomenti della Guida online sono quelli con i contenuti più attuali.

Per ottenere informazioni della Guida online, usare il parametro *Online* del cmdlet Get-Help. Il parametro *Online* del cmdlet Get-Help può essere usato solo per il cmdlet Help, la funzione Help e lo script Help. Non è possibile usare il parametro *Online* con gli argomenti concettuali (about_) o con quelli della Guida per i provider. Poiché questa funzionalità è opzionale, non funziona inoltre per gli argomenti della Guida di tutti i cmdlet, le funzioni o gli script.

Tutti gli argomenti della Guida disponibili per Windows PowerShell, inclusi gli argomenti della Guida concettuale (about_) e per i provider, sono tuttavia accessibili online nella sezione [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) della Libreria Microsoft TechNet.

Per usare il parametro *Online* del cmdlet Get-Help, usare il comando nel formato seguente.

```
get-help <command-name> -online
```

Per ottenere ad esempio la versione online dell'argomento della Guida sul cmdlet Get-ChildItem, digitare:

```
get-help get-childitem -online
```

Se è disponibile una versione online dell'argomento della Guida, si aprirà nel browser predefinito.

Se la Guida online è supportata per un argomento della Guida, è inoltre possibile visualizzare l'indirizzo Internet (URL) dell'argomento della Guida. L'indirizzo Internet compare nella sezione Collegamenti correlati di un argomento della Guida.

Per visualizzare ad esempio l'URL per la versione online del cmdlet Add-Computer, digitare:

```
get-help add-computer
```

Di seguito è riportata la prima riga nella sezione Collegamenti correlati dell'argomento.

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

Per informazioni su come offrire supporto online per argomenti della Guida personalizzati, vedere [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) e [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere la Guida dei cmdlet) in MSDN Library.

## <a name="see-also"></a>Vedere anche
- [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)