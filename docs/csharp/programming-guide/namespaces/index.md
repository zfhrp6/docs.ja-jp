---
title: 名前空間 (C# プログラミング ガイド)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a><span data-ttu-id="1a0f0-102">名前空間 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1a0f0-102">Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="1a0f0-103">C# プログラミングでは、名前空間が 2 つの方法でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-103">Namespaces are heavily used in C# programming in two ways.</span></span> <span data-ttu-id="1a0f0-104">最初の方法では、次のように .NET Framework で名前空間を使用して、その多くのクラスを整理します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-104">First, the .NET Framework uses namespaces to organize its many classes, as follows:</span></span>  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 <span data-ttu-id="1a0f0-105">`System` は名前空間で、`Console` はその名前空間内のクラスです。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-105">`System` is a namespace and `Console` is a class in that namespace.</span></span> <span data-ttu-id="1a0f0-106">以下の例のように、`using` キーワードを使用できるため、完全な名前は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-106">The `using` keyword can be used so that the complete name is not required, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 <span data-ttu-id="1a0f0-107">詳細については、「[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-107">For more information, see [using Directive](../../../csharp/language-reference/keywords/using-directive.md).</span></span>  
  
 <span data-ttu-id="1a0f0-108">2 つ目の方法では、独自の名前空間を宣言します。これは、より大きなプログラミング プロジェクトでクラス名とメソッド名のスコープを制御するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-108">Second, declaring your own namespaces can help you control the scope of class and method names in larger programming projects.</span></span> <span data-ttu-id="1a0f0-109">名前空間を宣言するには、以下の例のように、[namespace](../../../csharp/language-reference/keywords/namespace.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-109">Use the [namespace](../../../csharp/language-reference/keywords/namespace.md) keyword to declare a namespace, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a><span data-ttu-id="1a0f0-110">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="1a0f0-110">Namespaces Overview</span></span>  
 <span data-ttu-id="1a0f0-111">名前空間には次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-111">Namespaces have the following properties:</span></span>  
  
-   <span data-ttu-id="1a0f0-112">大きなコード プロジェクトを整理します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-112">They organize large code projects.</span></span>  
  
-   <span data-ttu-id="1a0f0-113">`.` 演算子を使用して、区切られます。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-113">They are delimited by using the `.` operator.</span></span>  
  
-   <span data-ttu-id="1a0f0-114">`using directive` を使用すると、クラスごとに名前空間の名前を指定する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-114">The `using directive` obviates the requirement to specify the name of the namespace for every class.</span></span>  
  
-   <span data-ttu-id="1a0f0-115">`global` 名前空間は "ルート" 名前空間です。`global::System` は常に .NET Framework 名前空間の `System` を参照します。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-115">The `global` namespace is the "root" namespace: `global::System` will always refer to the .NET Framework namespace `System`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1a0f0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a0f0-116">Related Sections</span></span>  
 <span data-ttu-id="1a0f0-117">名前空間の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0f0-117">See the following topics for more information about namespaces:</span></span>  
  
-   [<span data-ttu-id="1a0f0-118">名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="1a0f0-118">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [<span data-ttu-id="1a0f0-119">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="1a0f0-119">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [<span data-ttu-id="1a0f0-120">方法: My 名前空間を使用する</span><span class="sxs-lookup"><span data-stu-id="1a0f0-120">How to: Use the My Namespace</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a0f0-121">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1a0f0-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a0f0-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a0f0-122">See Also</span></span>  
 [<span data-ttu-id="1a0f0-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1a0f0-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1a0f0-124">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="1a0f0-124">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="1a0f0-125">using ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1a0f0-125">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="1a0f0-126">:: 演算子</span><span class="sxs-lookup"><span data-stu-id="1a0f0-126">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="1a0f0-127">。演算子</span><span class="sxs-lookup"><span data-stu-id="1a0f0-127">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)
