---
title: Spostamento in Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846f5233-43be-496a-9ca1-e3e34207cb49
---
# Spostamento in Windows PowerShell
Le cartelle sono una funzionalità ben nota dell'interfaccia Esplora file, di Cmd.exe e degli strumenti UNIX come BASH per tenere in ordine le informazioni. Comunemente chiamate anche directory, le cartelle sono utili per organizzare file e altre directory. Nella famiglia di sistemi operativi UNIX questo concetto viene esteso per trattare tutto il possibile come file. Componenti hardware specifici e connessioni di rete appaiono come file all'interno di determinate cartelle. Questo approccio non assicura che il contenuto sia leggibile o utilizzabile da determinate applicazioni, ma semplifica la ricerca di specifici elementi. Anche gli strumenti che enumerano o eseguono ricerche in file e cartelle funzionano con questi meccanismi. È inoltre possibile trovare un elemento specifico tramite il percorso del file che lo rappresenta.

Analogamente, l'infrastruttura di Windows PowerShell supporta la visualizzazione come unità di Windows PowerShell di qualsiasi cosa possa essere esplorata come un'unità disco standard di Microsoft Windows o un file system di UNIX. Un'unità di Windows PowerShell non rappresenta necessariamente un'unità reale, sia in locale o in rete. Questo capitolo descrive principalmente la modalità di spostamento nei file system, ma i concetti si applicano alle unità di Windows PowerShell non associate a file system.



<!--HONumber=Apr16_HO1-->


