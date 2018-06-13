---
title: -- 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 25f301bc0b2bc9bf51b0a44f26b2efabae00e452
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288802"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="65cc4-102">-- 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="65cc4-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="65cc4-103">デクリメント演算子 (`--`) は、オペランドを 1 ずつデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="65cc4-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="65cc4-104">デクリメント演算子はそのオペランド ( `--variable` および `variable--`) の前後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="65cc4-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="65cc4-105">1 番目の形式は前置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="65cc4-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="65cc4-106">この演算の結果は、デクリメント "後" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="65cc4-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="65cc4-107">2 番目の形式は後置デクリメント演算です。</span><span class="sxs-lookup"><span data-stu-id="65cc4-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="65cc4-108">この演算の結果は、デクリメント "前" のオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="65cc4-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65cc4-109">コメント</span><span class="sxs-lookup"><span data-stu-id="65cc4-109">Remarks</span></span>  
 <span data-ttu-id="65cc4-110">数値型と列挙型には事前定義のデクリメント演算子があります。</span><span class="sxs-lookup"><span data-stu-id="65cc4-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="65cc4-111">ユーザー定義型は `--` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="65cc4-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="65cc4-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="65cc4-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65cc4-113">例</span><span class="sxs-lookup"><span data-stu-id="65cc4-113">Example</span></span>  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="65cc4-114">参照</span><span class="sxs-lookup"><span data-stu-id="65cc4-114">See Also</span></span>  
 [<span data-ttu-id="65cc4-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="65cc4-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65cc4-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="65cc4-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65cc4-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="65cc4-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
