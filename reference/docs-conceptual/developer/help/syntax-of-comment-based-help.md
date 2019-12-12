---
title: Sintassi della Guida basata su Commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367760"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="26d10-102">Sintassi della Guida basata sui commenti</span><span class="sxs-lookup"><span data-stu-id="26d10-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="26d10-103">In questa sezione viene descritta la sintassi della Guida basata su commenti.</span><span class="sxs-lookup"><span data-stu-id="26d10-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="26d10-104">Diagramma della sintassi</span><span class="sxs-lookup"><span data-stu-id="26d10-104">Syntax Diagram</span></span>

 <span data-ttu-id="26d10-105">La sintassi per la guida basata su commenti è la seguente:</span><span class="sxs-lookup"><span data-stu-id="26d10-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="26d10-106">Descrizione della sintassi</span><span class="sxs-lookup"><span data-stu-id="26d10-106">Syntax Description</span></span>

 <span data-ttu-id="26d10-107">La guida basata su commenti viene scritta come una serie di commenti.</span><span class="sxs-lookup"><span data-stu-id="26d10-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="26d10-108">È possibile digitare un simbolo di commento (#) prima di ogni riga di commenti oppure è possibile usare i simboli "\<#" e "# >" per creare un blocco di commento.</span><span class="sxs-lookup"><span data-stu-id="26d10-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="26d10-109">Tutte le righe all'interno del blocco di commento vengono interpretate come commenti.</span><span class="sxs-lookup"><span data-stu-id="26d10-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="26d10-110">Ogni sezione della Guida basata su commenti è definita da una parola chiave e ogni parola chiave è preceduta da un punto (.).</span><span class="sxs-lookup"><span data-stu-id="26d10-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="26d10-111">Le parole chiave possono essere visualizzate in qualsiasi ordine.</span><span class="sxs-lookup"><span data-stu-id="26d10-111">The keywords can appear in any order.</span></span> <span data-ttu-id="26d10-112">I nomi delle parole chiave non fanno distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="26d10-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="26d10-113">Un blocco di commento deve contenere almeno una parola chiave della guida.</span><span class="sxs-lookup"><span data-stu-id="26d10-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="26d10-114">Alcune parole chiave, ad esempio, possono essere visualizzate più volte nello stesso blocco di commento.</span><span class="sxs-lookup"><span data-stu-id="26d10-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="26d10-115">Il contenuto della Guida per ogni parola chiave inizia sulla riga dopo la parola chiave e può estendersi su più righe.</span><span class="sxs-lookup"><span data-stu-id="26d10-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="26d10-116">Tutte le righe in un argomento della Guida basata su commenti devono essere contigue.</span><span class="sxs-lookup"><span data-stu-id="26d10-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="26d10-117">Se un argomento della guida basato su commenti segue un commento che non fa parte dell'argomento della guida, deve essere presente almeno una riga vuota tra l'ultima riga di commento non della guida e l'inizio della Guida basata su commenti.</span><span class="sxs-lookup"><span data-stu-id="26d10-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="26d10-118">Ad esempio, l'argomento della guida basato su Commenti seguente contiene. Parola chiave Description e relativo valore, che è una descrizione di una funzione o di uno script.</span><span class="sxs-lookup"><span data-stu-id="26d10-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```