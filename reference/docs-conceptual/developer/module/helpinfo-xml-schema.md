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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="0773a-102">Schema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="0773a-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="0773a-103">Questo argomento contiene i XML Schema per i file di informazioni della Guida aggiornabili, comunemente noti come "file XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="0773a-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="0773a-104">Schema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="0773a-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="0773a-105">I file XML HelpInfo sono basati sui XML Schema seguenti.</span><span class="sxs-lookup"><span data-stu-id="0773a-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="0773a-106">Elementi XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="0773a-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="0773a-107">Il file XML HelpInfo include gli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="0773a-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="0773a-108">HelpContentURI contiene l'URI del percorso dei file CAB della Guida per il modulo.</span><span class="sxs-lookup"><span data-stu-id="0773a-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="0773a-109">L'URI deve iniziare con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="0773a-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="0773a-110">L'URI deve specificare un percorso Internet, ma non deve includere il nome del file CAB.</span><span class="sxs-lookup"><span data-stu-id="0773a-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="0773a-111">Il valore di **HelpContentURI** può essere uguale o diverso dal valore di **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="0773a-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="0773a-112">SupportedUICultures rappresenta i file della Guida dei moduli in tutte le impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0773a-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="0773a-113">Contiene elementi **UICulture** , ciascuno dei quali rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.</span><span class="sxs-lookup"><span data-stu-id="0773a-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="0773a-114">UICulture rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.</span><span class="sxs-lookup"><span data-stu-id="0773a-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="0773a-115">Aggiungere un elemento **UICulture** per ogni lingua dell'interfaccia utente in cui vengono scritti i file della guida.</span><span class="sxs-lookup"><span data-stu-id="0773a-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="0773a-116">UICultureName contiene il codice della lingua per le impostazioni cultura dell'interfaccia utente in cui vengono scritti i file della guida.</span><span class="sxs-lookup"><span data-stu-id="0773a-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="0773a-117">UICultureVersion contiene un numero di versione in 4 parti in "N1. N2. N3. Formato N4 che rappresenta la versione del file CAB della guida nelle impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0773a-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="0773a-118">Incrementare questo numero di versione ogni volta che si caricano nuovi file CAB della guida nelle impostazioni cultura dell'interfaccia utente specificate da **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="0773a-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="0773a-119">Per ulteriori informazioni su questo valore, vedere la sezione relativa alla classe Version (System) in MSDN.</span><span class="sxs-lookup"><span data-stu-id="0773a-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>