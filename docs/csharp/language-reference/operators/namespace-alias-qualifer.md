---
title: ":: 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ::_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
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
ms.openlocfilehash: 97b9fa706669244ac579602a107c092e8593567d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="ca14b-102">:: 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ca14b-102">:: Operator (C# Reference)</span></span>
<span data-ttu-id="ca14b-103">名前空間エイリアス修飾子 (`::`) を使用して識別子を検索できます。</span><span class="sxs-lookup"><span data-stu-id="ca14b-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="ca14b-104">この例に示すように、常に 2 つの識別子の間に配置します。</span><span class="sxs-lookup"><span data-stu-id="ca14b-104">It is always positioned between two identifiers, as in this example:</span></span>  
  
 <span data-ttu-id="ca14b-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca14b-105">[!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca14b-106">コメント</span><span class="sxs-lookup"><span data-stu-id="ca14b-106">Remarks</span></span>  
 <span data-ttu-id="ca14b-107">名前空間エイリアス修飾子として `global` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ca14b-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="ca14b-108">これにより、エイリアスを使用した名前空間ではなく、グローバル名前空間で検索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca14b-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="ca14b-109">参照項目</span><span class="sxs-lookup"><span data-stu-id="ca14b-109">For More Information</span></span>  
 <span data-ttu-id="ca14b-110">`::` 演算子の使用例については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca14b-110">For an example of how to use the `::` operator, see the following section:</span></span>  
  
-   [<span data-ttu-id="ca14b-111">方法: グローバル名前空間エイリアスを使用する</span><span class="sxs-lookup"><span data-stu-id="ca14b-111">How to: Use the Global Namespace Alias</span></span>](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="ca14b-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ca14b-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca14b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca14b-113">See Also</span></span>  
 <span data-ttu-id="ca14b-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca14b-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ca14b-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca14b-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ca14b-116">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca14b-116">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="ca14b-117">[名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="ca14b-117">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
 <span data-ttu-id="ca14b-118">[。演算子](../../../csharp/language-reference/operators/member-access-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ca14b-118">[. Operator](../../../csharp/language-reference/operators/member-access-operator.md) </span></span>  
 [<span data-ttu-id="ca14b-119">extern エイリアス</span><span class="sxs-lookup"><span data-stu-id="ca14b-119">extern alias</span></span>](../../../csharp/language-reference/keywords/extern-alias.md)

