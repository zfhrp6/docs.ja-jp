---
title: "名前空間 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
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
ms.openlocfilehash: a45339a4c3320a92c0339b1cad6345a2555ed920
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="49b11-102">名前空間 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="49b11-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="49b11-103">C# プログラミングでは、名前空間が 2 つの方法でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="49b11-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="49b11-104">最初の方法では、次のように .NET Framework で名前空間を使用して、その多くのクラスを整理します。</span><span class="sxs-lookup"><span data-stu-id="49b11-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 <span data-ttu-id="49b11-105">[!code-cs[csProgGuide #22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="49b11-105">[!code-cs[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]</span></span>  
  
 <span data-ttu-id="49b11-106">`System` は名前空間で、`Console` はその名前空間内のクラスです。</span><span class="sxs-lookup"><span data-stu-id="49b11-106">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="49b11-107">以下の例のように、`using` キーワードを使用できるため、完全な名前は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="49b11-107">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 <span data-ttu-id="49b11-108">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="49b11-108">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]</span></span>  
  
 <span data-ttu-id="49b11-109">[!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="49b11-109">[!code-cs[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]</span></span>  
  
 <span data-ttu-id="49b11-110">詳細については、「[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49b11-110">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="49b11-111">2 つ目の方法では、独自の名前空間を宣言します。これは、より大きなプログラミング プロジェクトでクラス名とメソッド名のスコープを制御するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="49b11-111">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="49b11-112">名前空間を宣言するには、以下の例のように、[namespace](../../../csharp/language-reference/keywords/namespace.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="49b11-112">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 <span data-ttu-id="49b11-113">[!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="49b11-113">[!code-cs[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]</span></span>  
  
## <a name="namespaces-overview"></a><span data-ttu-id="49b11-114">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="49b11-114">Namespaces Overview</span></span>  
 <span data-ttu-id="49b11-115">名前空間には次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="49b11-115">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="49b11-116">大きなコード プロジェクトを整理します。</span><span class="sxs-lookup"><span data-stu-id="49b11-116">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="49b11-117">`.` 演算子を使用して、区切られます。</span><span class="sxs-lookup"><span data-stu-id="49b11-117">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="49b11-118">`using directive` を使用すると、クラスごとに名前空間の名前を指定する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="49b11-118">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="49b11-119">`global` 名前空間は "ルート" 名前空間です。`global::System` は常に .NET Framework 名前空間の `System` を参照します。</span><span class="sxs-lookup"><span data-stu-id="49b11-119">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="49b11-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="49b11-120">Related Sections</span></span>  
 <span data-ttu-id="49b11-121">名前空間の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="49b11-121">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="49b11-122">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="49b11-122">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="49b11-123">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="49b11-123">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="49b11-124">方法: My 名前空間を使用する</span><span class="sxs-lookup"><span data-stu-id="49b11-124">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="49b11-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="49b11-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="49b11-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="49b11-126">See Also</span></span>  
 <span data-ttu-id="49b11-127">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="49b11-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="49b11-128">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="49b11-128">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="49b11-129">[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="49b11-129">[using Directive](../../../csharp/language-reference/keywords/using-directive.md) </span></span>  
 <span data-ttu-id="49b11-130">[:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="49b11-130">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="49b11-131">。演算子</span><span class="sxs-lookup"><span data-stu-id="49b11-131">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)

