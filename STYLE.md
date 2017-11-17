# <a name="style-guide-for-powershell-docs"></a><span data-ttu-id="20d5c-101">Guida di stile per la documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="20d5c-101">Style guide for PowerShell-Docs</span></span>


## <a name="titlesheadings"></a><span data-ttu-id="20d5c-102">Titoli/intestazioni</span><span class="sxs-lookup"><span data-stu-id="20d5c-102">Titles/Headings</span></span>

* <span data-ttu-id="20d5c-103">I titoli e le intestazioni (qualsiasi elemento preceduto da \#) devono essere seguiti da una nuova riga</span><span class="sxs-lookup"><span data-stu-id="20d5c-103">Titles/headings (anything preprended by \#) should be followed with a newline</span></span>
* <span data-ttu-id="20d5c-104">Solo la prima lettera di un titolo e gli eventuali nomi propri nel titolo devono essere in maiuscolo</span><span class="sxs-lookup"><span data-stu-id="20d5c-104">Only the first letter of a title and any proper nouns in that title should be capitalized</span></span>
* <span data-ttu-id="20d5c-105">Ogni documento deve includere un solo titolo H1</span><span class="sxs-lookup"><span data-stu-id="20d5c-105">Only 1 H1 per document</span></span>
* <span data-ttu-id="20d5c-106">In caso di modifica di contenuto di riferimento, i titoli H2 sono richiesti da platyPS e non devono essere aggiunti o rimossi perché ciò causerà un errore di compilazione</span><span class="sxs-lookup"><span data-stu-id="20d5c-106">When editing reference content, the H2s are prescribed by platyPS and should not be added or removed as it will cause a build break</span></span>
* <span data-ttu-id="20d5c-107">Usare solo intestazioni con lo stile \#, invece di intestazioni con = o \-</span><span class="sxs-lookup"><span data-stu-id="20d5c-107">Only use \# style headers (as opposed to = or \- style headers)</span></span>

### <a name="correct"></a><span data-ttu-id="20d5c-108">Corretto</span><span class="sxs-lookup"><span data-stu-id="20d5c-108">Correct</span></span>

```
# Header 1

## Header 2

### Header 3

```

### <a name="incorrect"></a><span data-ttu-id="20d5c-109">Non corretto</span><span class="sxs-lookup"><span data-stu-id="20d5c-109">Incorrect</span></span>

```
Header 1
========

Header 2
--------

### Header 3
```

## <a name="syntax"></a><span data-ttu-id="20d5c-110">Sintassi</span><span class="sxs-lookup"><span data-stu-id="20d5c-110">Syntax</span></span>

* <span data-ttu-id="20d5c-111">Nelle citazioni di un cmdlet in un paragrafo usare \\` per evidenziare i nomi dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="20d5c-111">When talking about a cmdlet in paragraph, use \\` to highlight cmdlet names</span></span>
  * <span data-ttu-id="20d5c-112">Esempio corretto: questo cmdlet `Write-Host` consente di...</span><span class="sxs-lookup"><span data-stu-id="20d5c-112">Correct Example: This `Write-Host` Cmdlet can ...</span></span>
  * <span data-ttu-id="20d5c-113">Esempio non corretto: questo cmdlet **Write-Host** consente di... e la pipeline al cmdlet out-file per...</span><span class="sxs-lookup"><span data-stu-id="20d5c-113">Incorrect Example: This **Write-Host** Cmdlet can ... and pipeline to out-file Cmdlet to ...</span></span>
* <span data-ttu-id="20d5c-114">Durante la scrittura di un articolo (diversamente dal contenuto di riferimento), la prima istanza del nome di un cmdlet deve essere un collegamento alla documentazione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="20d5c-114">When writing an article (as opposed to reference content), the first instance of a cmdlet name should be a link to the cmdlet documentation</span></span>
* <span data-ttu-id="20d5c-115">In tutti i blocchi di sintassi di PowerShell è necessario usare &#96;&#96;&#96;powershell</span><span class="sxs-lookup"><span data-stu-id="20d5c-115">All PowerShell syntax blocks should use &#96;&#96;&#96;powershell</span></span>
* <span data-ttu-id="20d5c-116">Non iniziare i comandi PowerShell con "`PS C:\>`"</span><span class="sxs-lookup"><span data-stu-id="20d5c-116">Do not start PowerShell commands with "`PS C:\>`"</span></span>
  * <span data-ttu-id="20d5c-117">Esempio corretto:</span><span class="sxs-lookup"><span data-stu-id="20d5c-117">Correct Example:</span></span>
  ```powershell
  Get-Process
  ```
  * <span data-ttu-id="20d5c-118">Esempio non corretto:</span><span class="sxs-lookup"><span data-stu-id="20d5c-118">Incorrect Example:</span></span>
  ```powershell
  PS C:\> Get-Process
  ```
* <span data-ttu-id="20d5c-119">L'output generato dai comandi di PowerShell deve essere impostato come commento per evitare l'applicazione dell'evidenziazione della sintassi</span><span class="sxs-lookup"><span data-stu-id="20d5c-119">Output emitted by PowerShell commands should be commented to prevent it from recieving syntax highlighting</span></span>
* <span data-ttu-id="20d5c-120">I nomi di proprietà e parametri devono essere in **grassetto**</span><span class="sxs-lookup"><span data-stu-id="20d5c-120">Property names and parameter names should be in **bold**</span></span>
* <span data-ttu-id="20d5c-121">I cmdlet di PowerShell sono "[scritti in base alla convenzione Pascal](https://en.wikipedia.org/wiki/PascalCase)".</span><span class="sxs-lookup"><span data-stu-id="20d5c-121">PowerShell cmdlets are "[Pascal Cased](https://en.wikipedia.org/wiki/PascalCase)".</span></span> <span data-ttu-id="20d5c-122">I verbi sono separati dai sostantivi mediante un trattino.</span><span class="sxs-lookup"><span data-stu-id="20d5c-122">Verbs are seperated from nouns by a hyphen.</span></span>

## <a name="lists"></a><span data-ttu-id="20d5c-123">Elenchi</span><span class="sxs-lookup"><span data-stu-id="20d5c-123">Lists</span></span>

* <span data-ttu-id="20d5c-124">Non terminare gli elementi di elenco con un punto (a meno che non contengano più frasi)</span><span class="sxs-lookup"><span data-stu-id="20d5c-124">Do not end list items with a period (unless they contain multiple sentences)</span></span>
* <span data-ttu-id="20d5c-125">Se l'elenco contiene più frasi, valutare la possibilità di usare un'intestazione 3/4/5 (se applicabile) dopo il concetto principale</span><span class="sxs-lookup"><span data-stu-id="20d5c-125">If your list contains multiple sentences, consider using a header 3/4/5 (as applicable) underneath your primary idea</span></span>

## <a name="links"></a><span data-ttu-id="20d5c-126">Collegamenti</span><span class="sxs-lookup"><span data-stu-id="20d5c-126">Links</span></span>

* <span data-ttu-id="20d5c-127">I collegamenti devono essere sempre contrassegnati con la sintassi di Markdown `[friendlyname](url)`</span><span class="sxs-lookup"><span data-stu-id="20d5c-127">Links are always marked up using MarkDown syntax `[friendlyname](url)`</span></span>
* <span data-ttu-id="20d5c-128">I collegamenti devono avere un nome descrittivo quando possibile, molto probabilmente il titolo della pagina collegata</span><span class="sxs-lookup"><span data-stu-id="20d5c-128">Links should have a a friendly name when applicable, most likely the title of the linked page</span></span>
  * <span data-ttu-id="20d5c-129">**Eccezione**: i collegamenti che indirizzano a siti non Microsoft devono contenere solo un URL</span><span class="sxs-lookup"><span data-stu-id="20d5c-129">**Exception**: Links going towards non-Microsoft sites should only have a URL</span></span>
* <span data-ttu-id="20d5c-130">Tutti gli elementi nella sezione "Collegamenti correlati" in fondo all'articolo devono essere impostati come collegamenti ipertestuali.</span><span class="sxs-lookup"><span data-stu-id="20d5c-130">All items in the "related links" section at the bottom should be hyperlinked.</span></span> 

## <a name="line-breaks"></a><span data-ttu-id="20d5c-131">Interruzioni di riga</span><span class="sxs-lookup"><span data-stu-id="20d5c-131">Line breaks</span></span>

* <span data-ttu-id="20d5c-132">È necessario includere interruzioni di riga semantiche</span><span class="sxs-lookup"><span data-stu-id="20d5c-132">You must include semantic line breaks</span></span>
* <span data-ttu-id="20d5c-133">Le righe devono essere limitate a 100 caratteri (elemento aperto: strumento per verificare questo aspetto)</span><span class="sxs-lookup"><span data-stu-id="20d5c-133">You should limit lines to 100char (Open item: tooling to help us validate this)</span></span>
* <span data-ttu-id="20d5c-134">È POSSIBILE rimuovere le interruzioni di riga aggiuntive per PS4 +, ma NON per PS3 (convalida richiesta)</span><span class="sxs-lookup"><span data-stu-id="20d5c-134">You CAN remove additional line breaks for PS4+, NOT ps3 (needs validation)</span></span>
