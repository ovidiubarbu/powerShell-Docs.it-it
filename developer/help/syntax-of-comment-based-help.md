---
title: Sintassi della Guida basata sui commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083213"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="0bd8b-102">Sintassi della Guida basata sui commenti</span><span class="sxs-lookup"><span data-stu-id="0bd8b-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="0bd8b-103">In questa sezione viene descritta la sintassi della Guida basata sui commenti.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="0bd8b-104">Diagramma della sintassi</span><span class="sxs-lookup"><span data-stu-id="0bd8b-104">Syntax Diagram</span></span>

 <span data-ttu-id="0bd8b-105">La sintassi per la Guida basata sui commenti è come segue:</span><span class="sxs-lookup"><span data-stu-id="0bd8b-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="0bd8b-106">Descrizione della sintassi</span><span class="sxs-lookup"><span data-stu-id="0bd8b-106">Syntax Description</span></span>

 <span data-ttu-id="0bd8b-107">La Guida basata sui commenti viene scritto come una serie di commenti.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="0bd8b-108">È possibile digitare un simbolo di commento (#) prima di ogni riga dei commenti, oppure è possibile usare la "\<&" e "& >" simboli per creare un blocco di commento.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="0bd8b-109">Tutte le righe all'interno del blocco di commento vengono interpretate come commenti.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="0bd8b-110">Ogni sezione della Guida basata sui commenti è definito da una parola chiave e ogni parola chiave è preceduto da un punto (.).</span><span class="sxs-lookup"><span data-stu-id="0bd8b-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="0bd8b-111">Le parole chiave possono essere visualizzati in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-111">The keywords can appear in any order.</span></span> <span data-ttu-id="0bd8b-112">I nomi di parola chiave non sono tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="0bd8b-113">Un blocco di commento deve contenere almeno una parola chiave della Guida.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="0bd8b-114">Alcune delle parole chiave, come esempio, possono apparire più volte nello stesso blocco di commento.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="0bd8b-115">Il contenuto della Guida per ogni parola chiave inizia la riga dopo la parola chiave e può estendersi su più righe.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="0bd8b-116">Tutte le righe in un argomento della Guida basata sui commenti devono essere contigue.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="0bd8b-117">Se un argomento della Guida basata sui commenti segue un commento che non fa parte dell'argomento della Guida, deve esistere almeno una riga vuota tra l'ultima riga di commento non-Help e l'inizio degli argomenti della Guida basata sui commenti.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="0bd8b-118">Ad esempio, contiene il seguente argomento della Guida basata sui commenti di. Parola chiave di descrizione e il relativo valore, che è una descrizione di una funzione o script.</span><span class="sxs-lookup"><span data-stu-id="0bd8b-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```