---
title: "++ 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="876d6-102">++ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="876d6-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="876d6-103">インクリメント演算子 (`++`) は、オペランドを 1 ずつインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="876d6-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="876d6-104">インクリメント演算子はそのオペランド ( `++variable` および `variable++`) の前後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="876d6-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="876d6-105">コメント</span><span class="sxs-lookup"><span data-stu-id="876d6-105">Remarks</span></span>  
 <span data-ttu-id="876d6-106">1 番目の形式は前置インクリメント演算です</span><span class="sxs-lookup"><span data-stu-id="876d6-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="876d6-107">この演算の結果は、インクリメント後のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="876d6-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="876d6-108">2 番目の形式は後置インクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="876d6-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="876d6-109">この演算の結果は、インクリメント前のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="876d6-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="876d6-110">数値型と列挙型には事前定義のインクリメント演算子があります。</span><span class="sxs-lookup"><span data-stu-id="876d6-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="876d6-111">ユーザー定義型は `++` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="876d6-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="876d6-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="876d6-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="876d6-113">例</span><span class="sxs-lookup"><span data-stu-id="876d6-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="876d6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="876d6-114">See Also</span></span>  
 [<span data-ttu-id="876d6-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="876d6-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="876d6-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="876d6-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="876d6-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="876d6-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
