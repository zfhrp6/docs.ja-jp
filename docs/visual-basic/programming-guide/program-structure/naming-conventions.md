---
title: Visual Basic の名前付け規則
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651919"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="a3d6a-102">Visual Basic の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="a3d6a-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="a3d6a-103">Visual Basic アプリケーションの要素に名前を付けるときは、その名前の最初の文字は、英字またはアンダー スコアにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="a3d6a-104">ただし、アンダー スコアで始まる名前は[言語への非依存性、および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)に準拠しません。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="a3d6a-105">次の提案が、名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="a3d6a-106">名前の中のそれぞれの各単語を大文字で始めます。たとえば`FindLastRecord`や`RedrawMyForm`のようにします。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="a3d6a-107">関数やメソッド名は動詞で始めます。たとえば`InitNameArray`または`CloseDialog`のようにします。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="a3d6a-108">クラス、構造体、モジュールやプロパティ名は名詞で始めます。たとえば`EmployeeName`または`CarAccessory`のようにします。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="a3d6a-109">インターフェイス名はプレフィックス"I"を付けて始め、後に名詞または名詞句を続けます。 たとえば`IComponent`のようにします。 またはインターフェイスの動作を説明するような形容詞を付けます。 たとえば`IPersistable`のようにです。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="a3d6a-110">アンダー スコアは使用しないで、略語の使用も控えてください。 なぜなら略語は混乱を招くからです。 </span><span class="sxs-lookup"><span data-stu-id="a3d6a-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="a3d6a-111">イベント ハンドラー名はイベントの種類を説明する名詞で始め、後に`EventHandler`サフィックスを続けます。 たとえば`MouseEventHandler`のようにします。 </span><span class="sxs-lookup"><span data-stu-id="a3d6a-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="a3d6a-112">`EventArgs`サフィックスを、イベント引数クラスの名前の中に含めます。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="a3d6a-113">イベントが"before"または"after"の概念を持つ時は、現在時制または過去時制のサフィックスを使います。 たとえば`ControlAdd`または`ControlAdded`のようにします。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="a3d6a-114">長い、または頻繁に使用される用語では、名前の長さを適切に維持するために略語を使用します。 たとえば、"Hypertext Markup Language"の代わりに"HTML"を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="a3d6a-115">一般的に、32 文字を超える変数の名前は低解像度のモニターでは読むことが困難です。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="a3d6a-116">また、略語はアプリケーション全体を通して一貫性のあるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="a3d6a-117">プロジェクトの中で"HTML"と"Hypertext Markup Language"をランダムに切り替えることは混乱を招く可能性があります。 </span><span class="sxs-lookup"><span data-stu-id="a3d6a-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="a3d6a-118">外部スコープで使われている名前と同じものを、内部スコープの中で使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="a3d6a-119">誤った変数がアクセスされた場合エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="a3d6a-120">同名のキーワードと変数の間でコンフリクトが起きる場合、適切な種類のライブラリを使って先立ってキーワードを識別しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a3d6a-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="a3d6a-121">たとえば、`Date`という名前の変数がある場合、 <xref:System.DateTime.Date%2A?displayProperty=nameWithType>を呼ぶことによってのみ組み込み`Date`関数を使用することができます。 </span><span class="sxs-lookup"><span data-stu-id="a3d6a-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d6a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3d6a-122">See Also</span></span>  
 [<span data-ttu-id="a3d6a-123">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="a3d6a-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="a3d6a-124">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="a3d6a-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="a3d6a-125">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="a3d6a-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="a3d6a-126">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="a3d6a-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="a3d6a-127">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="a3d6a-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
