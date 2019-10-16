---
title: Dichiarazione di classe del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 979025ad5c34ab73dcc23d0e38ffb9acc431f15a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363520"
---
# <a name="cmdlet-class-declaration"></a>Dichiarazione della classe dei cmdlet

Una classe Microsoft .NET Framework viene dichiarata come cmdlet specificando l'attributo del **cmdlet** come metadati per la classe. L'attributo del **cmdlet** è l'unico attributo obbligatorio per tutti i cmdlet. Quando si specifica l'attributo del **cmdlet** , è necessario specificare la coppia verbo-e-nome che identifica il cmdlet per l'utente. È necessario descrivere la funzionalità di Windows PowerShell supportata dal cmdlet. Per ulteriori informazioni sulla sintassi di dichiarazione utilizzata per specificare l'attributo **cmdlet** , vedere Dichiarazione dell' [attributo del cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> L'attributo **cmdlet** viene definito dalla classe [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Le proprietà di questa classe corrispondono ai parametri di dichiarazione usati quando si dichiara l'attributo.

## <a name="nouns"></a>Nomi

Il sostantivo del cmdlet specifica le risorse su cui agisce il cmdlet. Il sostantivo distingue i cmdlet da altri cmdlet.

I sostantivi nei nomi dei cmdlet devono essere specifici e, nel caso di sostantivi generici, ad esempio *Server*, è preferibile aggiungere un prefisso breve che differenzi la risorsa da altre risorse simili. Ad esempio, un nome di cmdlet che include un sostantivo con un prefisso è `Get-SQLServer`. La combinazione di un sostantivo specifico con un verbo più generale consente all'utente di individuare rapidamente il cmdlet mediante la relativa azione e quindi di identificare il cmdlet mediante la relativa risorsa evitando la duplicazione del nome di cmdlet non necessaria.

Per un elenco di caratteri speciali che non possono essere usati nei nomi di cmdlet, vedere le [linee guida per lo sviluppo necessarie](./required-development-guidelines.md).

## <a name="verbs"></a>Verbi

Quando si specifica un verbo, le linee guida per lo sviluppo richiedono l'uso di uno dei verbi predefiniti forniti da Windows PowerShell. Utilizzando uno di questi verbi predefiniti, sarà garantita la coerenza tra i cmdlet scritti da e i cmdlet scritti da Microsoft e da altri. Il verbo "Get", ad esempio, viene usato per i cmdlet che recuperano i dati.

Per ulteriori informazioni sulle linee guida per i verbi, vedere [nomi dei verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md). Per un elenco di caratteri speciali che non possono essere usati nei nomi di cmdlet, vedere le [linee guida per lo sviluppo necessarie](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Supporto della funzionalità di Windows PowerShell

L'attributo **cmdlet** consente inoltre di specificare che il cmdlet supporta alcune delle funzionalità comuni fornite da Windows PowerShell. Questo include il supporto per le funzionalità comuni, ad esempio la conferma dei commenti e suggerimenti degli utenti, denominate supporto per la funzionalità ShouldProcess, e il supporto per le transazioni. (Il supporto per le transazioni è stato introdotto in Windows PowerShell 2,0).

Per ulteriori informazioni sulla sintassi di dichiarazione utilizzata per specificare l'attributo **cmdlet** , vedere Dichiarazione dell' [attributo del cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definizione della classe cmdlet

Il codice seguente è la definizione di una classe di cmdlet GetProc. Si noti che viene utilizzata la combinazione di maiuscole e minuscole Pascal e che il nome della classe include il verbo e il sostantivo del cmdlet.

[!code-csharp[GetProcessSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Maiuscole e minuscole Pascal

Quando si denominano i cmdlet, utilizzare la convenzione Pascal. I cmdlet `Get-Item` e `Get-ItemProperty`, ad esempio, mostrano il modo corretto per usare le maiuscole durante la denominazione dei cmdlet.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nomi dei verbi dei cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
