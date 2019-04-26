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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="1b952-102">Schema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1b952-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="1b952-103">In questo argomento contiene il XML schema per i file di informazioni della Guida aggiornabile, comunemente noto come "File XML HelpInfo".</span><span class="sxs-lookup"><span data-stu-id="1b952-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="1b952-104">Schema XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1b952-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="1b952-105">I file XML HelpInfo sono basati su XML schema seguente.</span><span class="sxs-lookup"><span data-stu-id="1b952-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="1b952-106">Elementi XML HelpInfo</span><span class="sxs-lookup"><span data-stu-id="1b952-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="1b952-107">Il file XML HelpInfo include gli elementi seguenti.</span><span class="sxs-lookup"><span data-stu-id="1b952-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="1b952-108">HelpContentURI contiene l'URI della posizione della Guida del file CAB per il modulo.</span><span class="sxs-lookup"><span data-stu-id="1b952-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="1b952-109">L'URI deve iniziare con "http" o "https".</span><span class="sxs-lookup"><span data-stu-id="1b952-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="1b952-110">L'URI deve specificare un percorso Internet, ma non deve includere il nome del file CAB.</span><span class="sxs-lookup"><span data-stu-id="1b952-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="1b952-111">Il **HelpContentURI** valore può essere uguale o diverso il **HelpInfoURI** valore.</span><span class="sxs-lookup"><span data-stu-id="1b952-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="1b952-112">SupportedUICultures rappresenta i file della Guida di modulo in tutte le impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="1b952-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="1b952-113">Contiene **UICulture** elementi, ognuno dei quali rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.</span><span class="sxs-lookup"><span data-stu-id="1b952-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="1b952-114">UICulture rappresenta un set di file della Guida per il modulo in una lingua dell'interfaccia utente specificata.</span><span class="sxs-lookup"><span data-stu-id="1b952-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="1b952-115">Aggiungere un **UICulture** (elemento) per ogni impostazione cultura dell'interfaccia utente in cui vengono scritti i file della Guida.</span><span class="sxs-lookup"><span data-stu-id="1b952-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="1b952-116">UICultureName contiene il codice di lingua per le impostazioni cultura dell'interfaccia utente in cui vengono scritti i file della Guida.</span><span class="sxs-lookup"><span data-stu-id="1b952-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="1b952-117">UICultureVersion contiene un numero di versione in 4 parti in "N1. N2. N3. N4 "formato che rappresenta la versione del file della Guida CAB nelle impostazioni cultura dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="1b952-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="1b952-118">Incrementare questo numero di versione ogni volta che si caricano nuovi help file CAB nelle impostazioni cultura dell'interfaccia utente specificato da **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="1b952-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="1b952-119">Per ulteriori informazioni su questo valore, vedere "Versione Class (sistema)" in MSDN.</span><span class="sxs-lookup"><span data-stu-id="1b952-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>