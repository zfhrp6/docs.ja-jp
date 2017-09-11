---
title: "++ 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f481dbe2437495b109d6d41cd24c8b4bb5b6a5b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="89f9d-102">++ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="89f9d-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="89f9d-103">インクリメント演算子 (`++`) は、オペランドを 1 ずつインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="89f9d-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="89f9d-104">インクリメント演算子はそのオペランド ( `++variable` および `variable++`) の前後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="89f9d-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89f9d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="89f9d-105">Remarks</span></span>  
 <span data-ttu-id="89f9d-106">1 番目の形式は前置インクリメント演算です</span><span class="sxs-lookup"><span data-stu-id="89f9d-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="89f9d-107">この演算の結果は、インクリメント後のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="89f9d-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="89f9d-108">2 番目の形式は後置インクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="89f9d-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="89f9d-109">この演算の結果は、インクリメント前のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="89f9d-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="89f9d-110">数値型と列挙型には事前定義のインクリメント演算子があります。</span><span class="sxs-lookup"><span data-stu-id="89f9d-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="89f9d-111">ユーザー定義型は `++` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="89f9d-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="89f9d-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="89f9d-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f9d-113">例</span><span class="sxs-lookup"><span data-stu-id="89f9d-113">Example</span></span>  
 <span data-ttu-id="89f9d-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="89f9d-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f9d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="89f9d-115">See Also</span></span>  
 <span data-ttu-id="89f9d-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="89f9d-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="89f9d-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="89f9d-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="89f9d-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="89f9d-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

