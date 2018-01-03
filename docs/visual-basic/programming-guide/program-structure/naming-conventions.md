---
title: "Visual Basic の名前付け規則"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f02fd85d4796d6799a8a5b40a9137eeb79a93f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="90b74-102">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="90b74-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="90b74-103">要素は、Visual Basic アプリケーションの名前、ときに、その名前の最初の文字は、文字は英字またはアンダー スコアにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b74-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="90b74-104">ただし、アンダー スコアで始まる名前に準拠していないこと、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)。</span><span class="sxs-lookup"><span data-stu-id="90b74-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="90b74-105">次の提案は、名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="90b74-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="90b74-106">としてでは大文字で名前の独立した各単語を開始`FindLastRecord`と`RedrawMyForm`です。</span><span class="sxs-lookup"><span data-stu-id="90b74-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="90b74-107">開始、動詞を使用して、関数、およびメソッドの名前として`InitNameArray`または`CloseDialog`です。</span><span class="sxs-lookup"><span data-stu-id="90b74-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="90b74-108">開始クラス、構造体、モジュール、および、名詞とプロパティ名として`EmployeeName`または`CarAccessory`です。</span><span class="sxs-lookup"><span data-stu-id="90b74-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="90b74-109">プレフィックスが付いているインターフェイスを開始"I"、続けて名詞または名詞句の場合と同様に`IComponent`、またはインターフェイスの動作を説明するような形容詞`IPersistable`です。</span><span class="sxs-lookup"><span data-stu-id="90b74-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="90b74-110">および使用しないで、アンダー スコア、略語で混乱可能性があるために、慎重に、省略形を使用します。</span><span class="sxs-lookup"><span data-stu-id="90b74-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="90b74-111">で始め、名詞が続くイベントの種類を説明するイベント ハンドラー名、"`EventHandler`「サフィックスで」`MouseEventHandler`"です。</span><span class="sxs-lookup"><span data-stu-id="90b74-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="90b74-112">イベント引数クラスの名前が含まれる、"`EventArgs`"サフィックス。</span><span class="sxs-lookup"><span data-stu-id="90b74-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="90b74-113">ある場合、イベントの概念"before"または"after"サフィックスで使用、現在時制または過去時制として"`ControlAdd`「または」`ControlAdded`"です。</span><span class="sxs-lookup"><span data-stu-id="90b74-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="90b74-114">長であるか、または頻繁に使用される用語では、たとえば、"HTML"、「ハイパー テキスト マークアップ言語」ではなく、適切な名前の長さを保持する略語を使用します。</span><span class="sxs-lookup"><span data-stu-id="90b74-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="90b74-115">一般に、32 文字を超える変数の名前は画面解像度の低い設定読みにくくします。</span><span class="sxs-lookup"><span data-stu-id="90b74-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="90b74-116">また、省略形は、アプリケーション全体で一貫性のあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90b74-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="90b74-117">"HTML"と「ハイパー テキスト マークアップ言語」の間でのプロジェクト内にランダムに切り替え、混乱を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="90b74-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="90b74-118">外側のスコープでの名前と同じである内部スコープでの名前を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="90b74-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="90b74-119">エラーは、不正な変数にアクセスした場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="90b74-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="90b74-120">変数と同じ名前のキーワードの間の競合が発生した場合は、適切なタイプ ライブラリで前にキーワードを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90b74-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="90b74-121">たとえば、という名前の変数がある場合`Date`、組み込みを使用することができます`Date`関数を呼び出すことによってのみ<xref:System.DateTime.Date%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="90b74-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b74-122">参照</span><span class="sxs-lookup"><span data-stu-id="90b74-122">See Also</span></span>  
 [<span data-ttu-id="90b74-123">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="90b74-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="90b74-124">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="90b74-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="90b74-125">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="90b74-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="90b74-126">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="90b74-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="90b74-127">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="90b74-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
