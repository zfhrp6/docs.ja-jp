---
title: "方法: グローバル名前空間エイリアスを使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: 23
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
ms.openlocfilehash: 1252fc107d46b1d3a1cbef0a61708edc57253910
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="e4c68-102">方法: グローバル名前空間エイリアスを使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e4c68-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="e4c68-103">グローバル[名前空間](../../../csharp/language-reference/keywords/namespace.md)のメンバーにアクセスできると、そのメンバーが同名の別のエンティティによって隠される可能性がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e4c68-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="e4c68-104">たとえば、次のコードでは、`Console` は、<xref:System> 名前空間の `Console` 型ではなく、`TestApp.Console` に解決されます。</span><span class="sxs-lookup"><span data-stu-id="e4c68-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 <span data-ttu-id="e4c68-105">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-105">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-106">[!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-106">[!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-107">`System.Console` を使用すると、`System` 名前空間が `TestApp.System` クラスによって隠されているため、依然としてエラーになります。</span><span class="sxs-lookup"><span data-stu-id="e4c68-107">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 <span data-ttu-id="e4c68-108">[!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-108">[!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-109">ただし、次のように `global::System.Console` を使用すると、このエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e4c68-109">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 <span data-ttu-id="e4c68-110">[!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-110">[!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-111">左の識別子が `global` の場合、右の識別子の検索はグローバル名前空間から開始されます。</span><span class="sxs-lookup"><span data-stu-id="e4c68-111">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="e4c68-112">たとえば、次の宣言は、グローバル空間のメンバーとして `TestApp` を参照します。</span><span class="sxs-lookup"><span data-stu-id="e4c68-112">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 <span data-ttu-id="e4c68-113">[!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-113">[!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-114">当然ながら、`System` という名前の独自の名前空間を作成することはお勧めしません。そのようなコードに遭遇することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="e4c68-114">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="e4c68-115">ただし、大型のプロジェクトでは、フォームによっては名前空間の重複が実際に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e4c68-115">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="e4c68-116">そのような場合は、グローバル名前空間修飾子によって、ルート名前空間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e4c68-116">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c68-117">例</span><span class="sxs-lookup"><span data-stu-id="e4c68-117">Example</span></span>  
 <span data-ttu-id="e4c68-118">次の例では、`System` 名前空間を使用して `TestClass` クラスを格納しています。そのため、`System` クラスによって隠されている `System.Console` クラスを参照するのに `global::System.Console` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4c68-118">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="e4c68-119">また、`System.Collections` 名前空間を参照するのに `colAlias` エイリアスを使用するため、名前空間の代わりにこのエイリアスを使用して <xref:System.Collections.Hashtable?displayProperty=fullName> のインスタンスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="e4c68-119">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=fullName> was created using this alias instead of the namespace.</span></span>  
  
 <span data-ttu-id="e4c68-120">[!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="e4c68-120">[!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]</span></span>  
  
 <span data-ttu-id="e4c68-121">**A 1**</span><span class="sxs-lookup"><span data-stu-id="e4c68-121">**A 1**</span></span>  
<span data-ttu-id="e4c68-122">**B 2**</span><span class="sxs-lookup"><span data-stu-id="e4c68-122">**B 2**</span></span>  
<span data-ttu-id="e4c68-123">**C 3**</span><span class="sxs-lookup"><span data-stu-id="e4c68-123">**C 3**</span></span>   
## <a name="see-also"></a><span data-ttu-id="e4c68-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4c68-124">See Also</span></span>  
 <span data-ttu-id="e4c68-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e4c68-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e4c68-126">[名前空間](../../../csharp/programming-guide/namespaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="e4c68-126">[Namespaces](../../../csharp/programming-guide/namespaces/index.md) </span></span>  
 <span data-ttu-id="e4c68-127">[。演算子](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e4c68-127">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 <span data-ttu-id="e4c68-128">[:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span><span class="sxs-lookup"><span data-stu-id="e4c68-128">[:: Operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) </span></span>  
 [<span data-ttu-id="e4c68-129">extern</span><span class="sxs-lookup"><span data-stu-id="e4c68-129">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)

