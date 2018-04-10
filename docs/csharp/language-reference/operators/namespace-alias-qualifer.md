---
title: ':: 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6b4f1683e1250ed745e15ced88203ca942c75ff8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5ad66-102">:: 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5ad66-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="5ad66-103">名前空間エイリアス修飾子 (`::`) を使用して識別子を検索できます。</span><span class="sxs-lookup"><span data-stu-id="5ad66-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="5ad66-104">この例に示すように、常に 2 つの識別子の間に配置します。</span><span class="sxs-lookup"><span data-stu-id="5ad66-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 [!code-csharp[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="5ad66-105">コメント</span><span class="sxs-lookup"><span data-stu-id="5ad66-105">Remarks</span></span>  
 <span data-ttu-id="5ad66-106">名前空間エイリアス修飾子として `global` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ad66-106">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="5ad66-107">これにより、エイリアスを使用した名前空間ではなく、グローバル名前空間で検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="5ad66-107">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="5ad66-108">参照項目</span><span class="sxs-lookup"><span data-stu-id="5ad66-108">For More Information</span></span>  
 <span data-ttu-id="5ad66-109">`::` 演算子の使用例については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ad66-109">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="5ad66-110">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="5ad66-110">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5ad66-111">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5ad66-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ad66-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ad66-112">See Also</span></span>  
 [<span data-ttu-id="5ad66-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5ad66-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5ad66-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5ad66-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5ad66-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="5ad66-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="5ad66-116">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="5ad66-116">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="5ad66-117">。演算子</span><span class="sxs-lookup"><span data-stu-id="5ad66-117">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="5ad66-118">extern エイリアス</span><span class="sxs-lookup"><span data-stu-id="5ad66-118">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)
