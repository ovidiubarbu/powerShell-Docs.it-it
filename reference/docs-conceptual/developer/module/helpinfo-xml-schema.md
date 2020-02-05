---
title: HelpInfo XML Schema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995999"
---
# <a name="helpinfo-xml-schema"></a>Schema XML HelpInfo

Questo argomento contiene i XML Schema per i file di informazioni della Guida aggiornabili, comunemente noti come "file XML HelpInfo".

## <a name="helpinfo-xml-schema"></a>Schema XML HelpInfo

I file XML HelpInfo sono basati sui XML Schema seguenti.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>Elementi XML HelpInfo

Il file XML HelpInfo include gli elementi seguenti.

HelpContentURI contiene l'URI del percorso dei file CAB della Guida per il modulo. L'URI deve iniziare con "http" o "https". L'URI deve specificare un percorso Internet, ma non deve includere il nome del file CAB. Il valore di **HelpContentURI** può essere uguale o diverso dal valore di **HelpInfoURI** .

SupportedUICultures rappresenta i file della Guida dei moduli in tutte le impostazioni cultura dell'interfaccia utente. Contiene elementi **UICulture** , ciascuno dei quali rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.

UICulture rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata. Aggiungere un elemento **UICulture** per ogni lingua dell'interfaccia utente in cui vengono scritti i file della guida.

UICultureName contiene il codice della lingua per le impostazioni cultura dell'interfaccia utente in cui vengono scritti i file della guida.

UICultureVersion contiene un numero di versione in 4 parti in "N1. N2. N3. Formato N4 che rappresenta la versione del file CAB della guida nelle impostazioni cultura dell'interfaccia utente. Incrementare questo numero di versione ogni volta che si caricano nuovi file CAB della guida nelle impostazioni cultura dell'interfaccia utente specificate da **UICultureName**. Per ulteriori informazioni su questo valore, vedere la sezione relativa alla classe Version (System) in MSDN.