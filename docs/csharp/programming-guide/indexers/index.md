---
title: "インデクサー (C# プログラミング ガイド)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
dev_langs:
- CSharp
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 784308f3073114cd0c07cf15edae527a2654edec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="ac872-102">インデクサー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ac872-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="ac872-103">インデクサーを使用すると、配列と同じようにクラスまたは構造体のインスタンスにインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ac872-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="ac872-104">インデックス値は、型またはインスタンス メンバーの明示的な指定なしで設定または取得できます。</span><span class="sxs-lookup"><span data-stu-id="ac872-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="ac872-105">インデクサーは[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)と似ていますが、そのアクセサーがパラメーターを取る点が異なります。</span><span class="sxs-lookup"><span data-stu-id="ac872-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="ac872-106">次の例は、値の割り当てと取得を行う単純な [get](../../../csharp/language-reference/keywords/get.md) アクセサー メソッドと [set](../../../csharp/language-reference/keywords/set.md) アクセサー メソッドを持つジェネリック クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="ac872-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="ac872-107">`Program` クラスは、文字列の格納用にこのクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ac872-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 <span data-ttu-id="ac872-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac872-108">[!code-cs[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac872-109">その他の例については、「[関連セクション](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac872-109">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="ac872-110">式の本文の定義</span><span class="sxs-lookup"><span data-stu-id="ac872-110">Expression Body Definitions</span></span>  
 
<span data-ttu-id="ac872-111">通常は、インデクサーの get または set アクセサーは、値を返すか値を設定する単一のステートメントで構成します。</span><span class="sxs-lookup"><span data-stu-id="ac872-111">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="ac872-112">式の本文のメンバーは、このシナリオをサポートする簡略化された構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="ac872-112">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="ac872-113">C# 6 以降、読み取り専用インデクサーは、次の例のように、式の本文のメンバーとして実装することができます。</span><span class="sxs-lookup"><span data-stu-id="ac872-113">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

<span data-ttu-id="ac872-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac872-114">[!code-cs[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]</span></span>  

<span data-ttu-id="ac872-115">式の本文は `=>` で導入され、`get` キーワードは使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ac872-115">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="ac872-116">C# 7 以降、get アクセサーと set アクセサーのどちらも、式の本文のメンバーとして実装できます。</span><span class="sxs-lookup"><span data-stu-id="ac872-116">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="ac872-117">この場合、`get` キーワードと `set` キーワードの両方を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac872-117">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="ac872-118">例:</span><span class="sxs-lookup"><span data-stu-id="ac872-118">For example:</span></span>

<span data-ttu-id="ac872-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac872-119">[!code-cs[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]</span></span>  
  
## <a name="indexers-overview"></a><span data-ttu-id="ac872-120">インデクサーの概要</span><span class="sxs-lookup"><span data-stu-id="ac872-120">Indexers Overview</span></span>  
  
-   <span data-ttu-id="ac872-121">インデクサーを使用すると、配列と同じようにオブジェクトにインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="ac872-121">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="ac872-122">`get` アクセサーは値を返します。</span><span class="sxs-lookup"><span data-stu-id="ac872-122">A `get` accessor returns a value.</span></span> <span data-ttu-id="ac872-123">`set` アクセサーは値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ac872-123">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="ac872-124">[this](../../../csharp/language-reference/keywords/this.md) キーワードは、インデクサーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac872-124">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="ac872-125">[value](../../../csharp/language-reference/keywords/value.md) キーワードは、`set` インデクサーによって割り当てられる値の定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac872-125">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="ac872-126">インデクサーは、整数値でインデックスを指定する必要はありません。個々の検索メカニズムの定義方法によります。</span><span class="sxs-lookup"><span data-stu-id="ac872-126">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="ac872-127">インデクサーはオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac872-127">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="ac872-128">インデクサーには、2 次元配列にアクセスする場合など、複数の仮パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="ac872-128">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <span data-ttu-id="ac872-129"><a name="BKMK_RelatedSections"></a> 関連セクション</span><span class="sxs-lookup"><span data-stu-id="ac872-129"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="ac872-130">インデクサーの使用</span><span class="sxs-lookup"><span data-stu-id="ac872-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="ac872-131">インターフェイスのインデクサー</span><span class="sxs-lookup"><span data-stu-id="ac872-131">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="ac872-132">プロパティとインデクサーの比較</span><span class="sxs-lookup"><span data-stu-id="ac872-132">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="ac872-133">アクセサーのアクセシビリティの制限</span><span class="sxs-lookup"><span data-stu-id="ac872-133">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ac872-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ac872-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac872-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac872-135">See Also</span></span>  
 <span data-ttu-id="ac872-136">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac872-136">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="ac872-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ac872-137">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

