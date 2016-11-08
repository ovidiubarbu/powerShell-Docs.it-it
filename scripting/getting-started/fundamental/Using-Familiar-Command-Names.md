---
title: Uso di nomi di comandi familiari
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
translationtype: Human Translation
ms.sourcegitcommit: 0c22cc16f5c5becacfc07a6332c0b949f9da40e0
ms.openlocfilehash: dc235dee1af01c1f3d29118e4824d6a2b49b113a

---

# <a name="using-familiar-command-names"></a>Uso di nomi di comandi familiari
Usando un meccanismo chiamato *aliasing*, Windows PowerShell consente agli utenti di fare riferimento ai comandi con nomi alternativi. L'aliasing consente agli utenti che hanno esperienza con altre shell di riusare i nomi dei comandi comuni che già conoscono per eseguire operazioni simili in Windows PowerShell. Anche se non si parlerà in dettaglio degli alias di Windows PowerShell, è possibile usarli per acquisire familiarità con Windows PowerShell.

L'aliasing associa un nome di comando che viene digitato a un altro comando. Windows PowerShell ha ad esempio una funzione interna denominata **Clear-Host** che cancella la finestra di output. Se si digita il comando **cls** o **clear** al prompt dei comandi, Windows PowerShell lo interpreta come alias della funzione **Clear-Host** ed esegue la funzione **Clear-Host**.

Questa funzionalità consente agli utenti di imparare a usare Windows PowerShell. Per prima cosa, la maggior parte degli utenti UNIX e di Cmd.exe ha a disposizione un'ampia gamma di comandi di cui già conosce il nome e, benché i comandi equivalenti di Windows PowerShell non producano esattamente gli stessi risultati, hanno un formato tale da consentirne l'uso per eseguire le operazioni richieste senza dover prima memorizzare i nomi in Windows PowerShell. In secondo luogo, la principale fonte di frustrazione nell'imparare a usare una nuova shell quando si ha già familiarità con un'altra consiste negli errori causati dalla "memoria delle dita". Se per anni si è usato Cmd.exe, in presenza di una schermata piena di output verrà spontaneo digitare il comando **cls** e premere il tasto INVIO per cancellarla. Senza l'alias della funzione **Clear-Host** in Windows PowerShell, si otterrebbe semplicemente un messaggio di errore analogo a "**"cls" non riconosciuto come cmdlet, funzione, programma eseguibile o file script**". e non si saprebbe come procedere per cancellare l'output.

Di seguito è riportato un breve elenco di comandi UNIX e di Cmd.exe comuni utilizzabili in Windows PowerShell:

|||||
|-|-|-|-|
|cat|dir|montare|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

Se viene spontaneo usare uno di questi comandi e si vuole imparare il vero nome del comando nativo di Windows PowerShell, è possibile usare il comando **Get-Alias**:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Per rendere più leggibili gli esempi, nel Manuale dell'utente di Windows PowerShell si evita in genere l'uso degli alias. Saperne di più sugli alias a questo stadio può rivelarsi tuttavia utile se si usano frammenti arbitrari di codice di Windows PowerShell da un'altra origine o se si vogliono definire alias personalizzati. Il resto di questa sezione illustrerà gli alias standard e spiegherà come definirne di propri.

### <a name="interpreting-standard-aliases"></a>Interpretazione di alias standard
A differenza degli alias descritti in precedenza, che sono stati progettati per la compatibilità a livello di nome con altre interfacce, gli alias incorporati in Windows PowerShell sono in genere progettati per motivi di brevità. Questi nomi più brevi possono essere digitati rapidamente, ma non possono essere letti se non si conosce quello a cui fanno riferimento.

Windows PowerShell tenta di trovare un compromesso tra chiarezza e brevità, fornendo un set di alias standard che si basano sui nomi a sintassi abbreviata di verbi e sostantivi comuni. In questo modo viene garantito un set di base di alias di cmdlet comuni che sono leggibili quando se ne conoscono i nomi a sintassi abbreviata. Negli alias standard, ad esempio, il verbo **Get** è abbreviato in **g**, il verbo **Set** è abbreviato in **s**, il sostantivo **Item** è abbreviato in **i**, il sostantivo **Location** è abbreviato in **l** e il sostantivo Command è abbreviato in **cm**.

Ecco un breve esempio per illustrarne il funzionamento. L'alias standard di Get-Item deriva dalla combinazione di **g** di Get e **i** di Item: **gi**. L'alias standard di Set-Item deriva dalla combinazione di **s** di Set e **i** di Item: **si**. L'alias standard di Get-Location deriva dalla combinazione di **g** di Get e **l** di Location: **gl**. L'alias standard di Set-Location deriva dalla combinazione di **s** di Set e **l** di Location: **sl**. L'alias standard di Get-Command deriva dalla combinazione di **g** di Get e **cm** di Command: **gcm**. Non esiste un cmdlet Set-Command, ma se esistesse, il relativo alias standard deriverebbe da **s** di Set e **cm** di Command: **scm**. Per gli utenti che hanno familiarità con l'aliasing di Windows PowerShell, sarebbe evidente che l'alias **scm** fa riferimento a Set-Command.

### <a name="creating-new-aliases"></a>Creazione di nuovi alias
È possibile creare alias personalizzati usando il cmdlet Set-Alias. Le istruzioni seguenti creano ad esempio gli alias di cmdlet standard descritti in Interpretazione di alias standard:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, Windows PowerShell usa comandi simili durante l'avvio, ma questi alias non sono modificabili. Se si tenta di eseguire effettivamente uno di questi comandi, si otterrà un errore per segnalare che l'alias non può essere modificato. Ad esempio:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```




<!--HONumber=Nov16_HO1-->


