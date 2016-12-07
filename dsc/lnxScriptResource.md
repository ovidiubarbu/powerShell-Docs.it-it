---
title: Risorsa nxScript DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 4c575bbf0e0553e19e56bcc6edd605e36586cb94
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-for-linux-nxscript-resource"></a>Risorsa nxScript DSC per Linux

La risorsa **nxScript** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire script Linux in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    { Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| GetScript| Fornisce uno script eseguito quando si richiama il cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx). Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio #!/bin/bash.| 
| SetScript| Fornisce uno script. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), viene eseguito per primo il blocco **TestScript**. Se il blocco **TestScript** restituisce un codice di uscita diverso da 0, il blocco **SetScript** viene eseguito. Se **TestScript** restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito. Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio `#!/bin/bash`.| 
| TestScript| Fornisce uno script. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), questo script viene eseguito. Se restituisce un codice di uscita diverso da 0, il blocco SetScript viene eseguito. Se restituisce un codice di uscita uguale a 0, il blocco **SetScript** non viene eseguito. **TestScript** viene eseguito anche quando si richiama il cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal codice di uscita restituito da **TestScript**. **TestScript** deve restituire un codice di uscita uguale a 0 se l'effettiva configurazione corrisponde alla configurazione dello stato desiderato corrente e un codice di uscita diverso da 0 in caso contrario. La configurazione dello stato desiderato corrente è l'ultima configurazione applicata al nodo che usa DSC. Lo script deve iniziare con una sequenza di caratteri shebang, ad esempio 1#!/bin/bash.1| 
| User| Utente per l'esecuzione dello script.| 
| Group| Gruppo per l'esecuzione dello script.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Esempio

L'esempio seguente illustra l'uso della risorsa **nxScript** per eseguire attività aggiuntive di gestione della configurazione.

```
Import-DSCResource -Module nx 

Node $node {
nxScript KeepDirEmpty{

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

