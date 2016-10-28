---
title: Uso dell&quot;espansione dei nomi tramite TAB
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
translationtype: Human Translation
ms.sourcegitcommit: 27512f637dd44485eee38936fea4723cd17b6218
ms.openlocfilehash: b67024fb27c08e1079caad891cfc3e621a354b27

---

# Uso dell'espansione dei nomi tramite TAB
Le shell da riga di comando offrono spesso un modo per completare automaticamente i nomi di file o comandi lunghi, velocizzando l'immissione dei comandi e visualizzando suggerimenti. Windows PowerShell consente di usare il tasto **TAB** per immettere nomi di file e di cmdlet.

> [!NOTE]
> L'espansione tramite TAB è controllata dalla funzione interna TabExpansion o TabExpansion2. Poiché questa funzione può essere modificata o sottoposta a override, le informazioni seguenti sono da intendersi come una guida al comportamento della configurazione predefinita di Windows PowerShell.

Per immettere automaticamente un nome di file o un percorso usando le scelte disponibili, digitare parte del nome e premere **TAB**. Windows PowerShell espanderà automaticamente il nome usando la prima corrispondenza trovata. Premendo più volte **TAB** è possibile visualizzare in sequenza tutte le scelte disponibili.

L'espansione tramite TAB dei nomi di cmdlet è leggermente diversa. Per usare l'espansione tramite TAB per un nome di cmdlet, digitare per intero la prima parte del nome (il verbo) e il trattino che segue. È possibile immettere anche una parte più lunga del nome per ottenere una corrispondenza parziale. Ad esempio, se si digita **get-co** e quindi si preme **TAB**, Windows PowerShell proporrà automaticamente l'espansione al cmdlet **Get-Command**. Notare che viene cambiata anche la combinazione di maiuscole/minuscole in base al formato standard. Se si preme di nuovo **TAB**, Windows PowerShell lo sostituisce con l'unico altro nome di cmdlet corrispondente, ossia **Get-Content**.

È possibile usare l'espansione dei nomi tramite TAB più volte sulla stessa riga. Ad esempio, è possibile usare l'espansione tramite TAB per il nome del cmdlet **Get-Content** cmdlet immettendo:

```
PS> Get-Con<Tab>
```

Quando si preme **TAB**, il comando viene espanso in:

```
PS> Get-Content
```

È quindi possibile specificare parzialmente il percorso del file di log di installazione (Active Setup) e usare nuovamente la sostituzione tramite TAB:

```
PS> Get-Content c:\windows\acts<Tab>
```

Quando si preme **TAB**, il comando viene espanso in:

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> Uno dei limiti del processo di espansione dei nomi tramite TAB è che le pressioni di TAB vengono sempre interpretate come il tentativo di completare una parola. Se si copiano e incollano esempi di comando in una console di Windows PowerShell, assicurarsi che l'esempio non contenga tabulazioni. In caso contrario, i risultati potrebbero essere imprevedibili e quasi certamente diversi da quelli desiderati.




<!--HONumber=Oct16_HO2-->


