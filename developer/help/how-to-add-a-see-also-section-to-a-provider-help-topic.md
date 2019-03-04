---
title: Come aggiungere un vedere anche sezione a un argomento della Guida di Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858347"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Come aggiungere una sezione Vedere anche a un argomento della Guida dei provider

In questa sezione illustra come popolare la **vedere anche** sezione di un argomento della Guida di provider.

Il **vedere anche** sezione è costituita da un elenco di argomenti che sono correlati al provider o può consentire all'utente di comprendere meglio e usare il provider. Nell'elenco di argomenti può includere cmdlet help, Guida del provider e concettuale ("about"), gli argomenti della Guida in Windows PowerShell. Anche possibile includere riferimenti a libri, documento e gli argomenti online, tra cui una versione online dell'argomento della Guida di provider corrente.

Quando si fa riferimento ad argomenti in linea, fornire l'URI o un termine di ricerca in testo normale. Il `Get-Help` cmdlet non collegare o reindirizzare a uno degli argomenti nell'elenco. Inoltre, il `Online` parametro del `Get-Help` cmdlet non funziona con l'aiuto di provider.

La sezione Vedere anche viene creata dal `RelatedLinks` elemento e i tag in esso contenuti. Il codice XML seguente viene illustrato come aggiungere i tag.

### <a name="to-add-see-also-topics"></a>Per aggiungere gli argomenti "Vedere anche"

1. Nel *AssemblyName*nel file con estensione dll help.xml, all'interno di `providerHelp` elemento, aggiungere un `RelatedLinks` elemento. Il `RelatedLinks` elemento deve essere l'ultimo elemento di `providerHelp` elemento. Un solo `RelatedLinks` elemento è consentito in ogni argomento della Guida di provider.

   Ad esempio:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Per ogni argomento nel **vedere anche** sezione, all'interno di `RelatedLinks` elemento, aggiungere un `navigationLink` elemento. Quindi, all'interno di ciascun `navigationLink` elemento, aggiungerne uno `linkText` elemento e l'altra `uri` elemento. Se non si usa la `uri` elemento, è possibile aggiungerlo come elemento vuoto (\<uri / >).

   Ad esempio:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. Digitare il nome dell'argomento tra il `linkText` tag. Se si specifica un URI, digitarla tra il `uri` tag. Per indicare la versione online dell'argomento della Guida del provider corrente, tra il `linkText` tag, digitare "versione Online:" anziché il nome dell'argomento. In genere, la "versione Online:" collegamento è il primo argomento dell'elenco di argomento vedere anche.

   Nell'esempio seguente include tre argomenti Vedere anche. Il primo fare riferimento alla versione online dell'argomento corrente. Il secondo fa riferimento a un argomento della Guida cmdlet di Windows PowerShell. Il terzo fa riferimento a un altro argomento online.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```