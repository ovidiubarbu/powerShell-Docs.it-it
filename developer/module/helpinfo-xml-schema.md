---
title: Schema XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082465"
---
# <a name="helpinfo-xml-schema"></a>Schema XML HelpInfo

In questo argomento contiene il XML schema per i file di informazioni della Guida aggiornabile, comunemente noto come "File XML HelpInfo".

## <a name="helpinfo-xml-schema"></a>Schema XML HelpInfo

I file XML HelpInfo sono basati su XML schema seguente.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

HelpContentURI contiene l'URI della posizione della Guida del file CAB per il modulo. L'URI deve iniziare con "http" o "https". L'URI deve specificare un percorso Internet, ma non deve includere il nome del file CAB. Il **HelpContentURI** valore può essere uguale o diverso il **HelpInfoURI** valore.

SupportedUICultures rappresenta i file della Guida di modulo in tutte le impostazioni cultura dell'interfaccia utente. Contiene **UICulture** elementi, ognuno dei quali rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.

UICulture rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata. Aggiungere un **UICulture** (elemento) per ogni impostazione cultura dell'interfaccia utente in cui vengono scritti i file della Guida.

UICultureName contiene il codice di lingua per le impostazioni cultura dell'interfaccia utente in cui vengono scritti i file della Guida.

UICultureVersion contiene un numero di versione in 4 parti in "N1. N2. N3. N4 "formato che rappresenta la versione del file della Guida CAB nelle impostazioni cultura dell'interfaccia utente. Incrementare questo numero di versione ogni volta che si caricano nuovi help file CAB nelle impostazioni cultura dell'interfaccia utente specificato da **UICultureName**. Per ulteriori informazioni su questo valore, vedere "Versione Class (sistema)" in MSDN.