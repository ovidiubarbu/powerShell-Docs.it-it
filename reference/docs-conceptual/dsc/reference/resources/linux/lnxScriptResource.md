---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxScript DSC per Linux
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953188"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Risorsa nxScript DSC per Linux

La risorsa **nxScript** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire script Linux in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|GetScript |Fornisce uno script per restituire lo stato corrente del computer. Questo script viene eseguito quando si richiama lo script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`. |
|SetScript |Fornisce uno script che attiva lo stato corretto per il computer. Quando si richiama lo script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), viene eseguito per primo **TestScript**. Se il blocco **TestScript** restituisce un codice di uscita diverso da 0, il blocco **SetScript** viene eseguito. Se **TestScript** restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito. Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`. |
|TestScript |Fornisce uno script che valuta se il nodo si trova attualmente nello stato corretto. Quando si richiama lo script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), questo script viene eseguito. Se restituisce un codice di uscita diverso da 0, verrà eseguito **SetScript**. Se restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito. **TestScript** viene eseguito anche quando si richiama lo script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal codice di uscita restituito da **TestScript**. **TestScript** deve includere contenuto e restituire un codice di uscita uguale a 0 se la configurazione effettiva corrisponde alla configurazione dello stato desiderato corrente e un codice di uscita diverso da 0 in caso contrario. La configurazione dello stato desiderato corrente è l'ultima configurazione applicata nel nodo che usa DSC. Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`. |
|Utente |Utente per l'esecuzione dello script. |
|Gruppo |Gruppo per l'esecuzione dello script. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="example"></a>Esempio

L'esempio seguente illustra l'uso della risorsa **nxScript** per eseguire attività aggiuntive di gestione della configurazione.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
