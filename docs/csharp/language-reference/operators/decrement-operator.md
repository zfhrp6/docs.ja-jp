---
title: "-- 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a><span data-ttu-id="2e615-102">-- 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2e615-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="2e615-103">デクリメント演算子 (`--`) は、オペランドを 1 ずつデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="2e615-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="2e615-104">デクリメント演算子はそのオペランド ( `--variable` および `variable--`) の前後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="2e615-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="2e615-105">1 番目の形式は前置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="2e615-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="2e615-106">この演算の結果は、デクリメント "後" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="2e615-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="2e615-107">2 番目の形式は後置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="2e615-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="2e615-108">この演算の結果は、デクリメント "前" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="2e615-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e615-109">コメント</span><span class="sxs-lookup"><span data-stu-id="2e615-109">Remarks</span></span>  
 <span data-ttu-id="2e615-110">数値型と列挙型には事前定義のデクリメント演算子があります。</span><span class="sxs-lookup"><span data-stu-id="2e615-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="2e615-111">ユーザー定義型は `--` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="2e615-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2e615-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e615-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e615-113">例</span><span class="sxs-lookup"><span data-stu-id="2e615-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2e615-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e615-114">See Also</span></span>  
 [<span data-ttu-id="2e615-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2e615-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2e615-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2e615-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2e615-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="2e615-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
