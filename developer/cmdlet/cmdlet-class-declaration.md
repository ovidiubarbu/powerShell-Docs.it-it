---
title: Dichiarazione di classe cmdlet | Microsoft Docs
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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068641"
---
# <a name="cmdlet-class-declaration"></a>Dichiarazione della classe dei cmdlet

Una classe di Microsoft .NET Framework è dichiarata come un cmdlet, specificando il **Cmdlet** attributo sotto forma di metadati per la classe. (Il **Cmdlet** attributo è l'unico attributo obbligatorio per tutti i cmdlet). Quando si specifica la **Cmdlet** attributo, è necessario specificare la coppia di verbo e nome che identifica il cmdlet per l'utente. E, è necessario descrivere le funzionalità di Windows PowerShell che supporta il cmdlet. Per altre informazioni sulla sintassi di dichiarazione che consente di specificare il **Cmdlet** dell'attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Il **Cmdlet** dipende dall'attributo le [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) classe. Le proprietà di questa classe corrispondono ai parametri utilizzati quando si dichiara l'attributo di dichiarazione.

## <a name="nouns"></a>Sostantivi

Il sostantivo del cmdlet consente di specificare le risorse su cui agisce il cmdlet. Il sostantivo riconosce la differenza dei cmdlet da altri cmdlet.

Sostantivi nei nomi dei cmdlet devono essere specifico e, nel caso di sostantivi generici, ad esempio *server*, è consigliabile aggiungere un prefisso breve che consentono di distinguere le risorse da altre risorse simili. Ad esempio, è un nome di cmdlet che include un sostantivo con un prefisso `Get-SQLServer`. La combinazione di un sostantivo specifico con un verbo più generale consente all'utente di individuare rapidamente i cmdlet per la relativa azione e quindi identificando il cmdlet per la propria risorsa evitando la duplicazione del nome cmdlet non necessari.

Per un elenco di caratteri speciali che non può essere usato nei nomi di cmdlet, vedere [linee guida sullo sviluppo necessari](./required-development-guidelines.md).

## <a name="verbs"></a>Verbi

Quando si specifica un verbo, le linee guida sullo sviluppo richiedono di usare uno dei verbi predefiniti forniti da Windows PowerShell. Usando uno di questi verbi predefiniti, si garantisce la coerenza tra i cmdlet personalizzati e i cmdlet che vengono scritti da Microsoft e da altri utenti. Ad esempio, il verbo "Get" viene usato per i cmdlet che recuperano i dati.

Per altre informazioni sulle linee guida per i verbi, vedere [nomi dei verbi di Cmdlet](./approved-verbs-for-windows-powershell-commands.md). Per un elenco di caratteri speciali che non può essere usato nei nomi di cmdlet, vedere [linee guida sullo sviluppo necessari](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Supporto di funzionalità di Windows PowerShell

Il **Cmdlet** attributo consente inoltre di specificare che il cmdlet supporta alcune delle funzionalità comune fornita da Windows PowerShell. Ciò include il supporto per le funzionalità comuni, ad esempio conferma di commenti e suggerimenti utente (detto supporto per la funzionalità di ShouldProcess) e supporto per le transazioni. (Supporto delle transazioni è stato introdotto in Windows PowerShell 2.0).

Per altre informazioni sulla sintassi di dichiarazione che consente di specificare il **Cmdlet** dell'attributo, vedere [dichiarazione di attributo Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definizione della classe cmdlet

Il codice seguente è la definizione per una classe cmdlet GetProc. Si noti che la convenzione Pascal maiuscole e minuscole viene utilizzata e che il nome della classe include il verbo e nome del cmdlet.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>La convenzione Pascal maiuscole e minuscole

Quando si assegna un nome cmdlet, utilizzare la convenzione Pascal maiuscole e minuscole. Ad esempio, il `Get-Item` e `Get-ItemProperty` cmdlet mostrano il modo corretto da utilizzare per l'uso delle maiuscole denominazione cmdlet.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[Dichiarazione CmdletAttribute](./cmdlet-attribute-declaration.md)

[Nomi di verbi di cmdlet](./approved-verbs-for-windows-powershell-commands.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
