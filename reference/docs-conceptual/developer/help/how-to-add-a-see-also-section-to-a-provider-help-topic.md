---
title: Come aggiungere una sezione vedere anche a un argomento della guida del provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367840"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Come aggiungere una sezione Vedere anche a un argomento della Guida dei provider

In questa sezione viene illustrato come popolare la sezione **vedere anche** di un argomento della guida del provider.

La sezione **vedere anche** è costituita da un elenco di argomenti correlati al provider o che possono aiutare gli utenti a comprendere e usare il provider. L'elenco di argomenti può includere la guida per i cmdlet, la guida del provider e gli argomenti della Guida concettuale ("about") in Windows PowerShell. Può inoltre includere riferimenti a libri, carta e argomenti online, inclusa una versione online dell'argomento della guida del provider corrente.

Quando si fa riferimento agli argomenti online, fornire l'URI o un termine di ricerca in testo normale. Il cmdlet `Get-Help` non collega né reindirizza gli argomenti dell'elenco. Inoltre, il parametro `Online` del cmdlet `Get-Help` non funziona con la guida del provider.

La sezione vedere anche viene creata dall'elemento `RelatedLinks` e dai tag in esso contenuti. Nel codice XML seguente viene illustrato come aggiungere i tag.

### <a name="to-add-see-also-topics"></a>Per aggiungere gli argomenti "vedere anche"

1. Nel file *AssemblyName*. dll-help. XML, all'interno dell'elemento `providerHelp`, aggiungere un elemento `RelatedLinks`. L'elemento `RelatedLinks` deve essere l'ultimo elemento nell'elemento `providerHelp`. In ogni argomento della guida del provider è consentito un solo elemento `RelatedLinks`.

   Ad esempio:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. Per ogni argomento nella sezione **vedere anche** , all'interno dell'elemento `RelatedLinks` aggiungere un elemento `navigationLink`. Quindi, all'interno di ogni elemento `navigationLink` aggiungere un elemento `linkText` e un elemento `uri`. Se non si utilizza l'elemento `uri`, è possibile aggiungerlo come elemento vuoto (\<Uri/>).

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

3. Digitare il nome dell'argomento tra i tag `linkText`. Se si specifica un URI, digitarlo tra i tag `uri`. Per indicare la versione online dell'argomento della guida del provider corrente, tra i tag `linkText`, digitare "versione online:" anziché il nome dell'argomento. In genere, il collegamento "versione online:" è il primo argomento nell'elenco vedere anche l'argomento.

   L'esempio seguente include tre argomenti vedere anche. Il primo si riferisce alla versione online dell'argomento corrente. Il secondo si riferisce a un argomento della Guida dei cmdlet di Windows PowerShell. Il terzo si riferisce a un altro argomento online.

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